#### THEORY_OF_OPERATION.md

**The hardware does three independent things:**
1. **Maintain temperature** at two independent setpoints (zones can be 65°C for LAMP and 37°C for CRISPR reaction, or both at 37°C for RPA, etc.)
2. **Excite and measure fluorescence** in two spectral channels per well, with lock-in demodulation to suppress ambient light
3. **Optionally photograph lateral flow strips** and run AI line detection

**The hardware does NOT** know about CRISPR. It does not identify pathogens. It does not call positive/negative. Those decisions belong to the assay chemistry + analysis software the user provides.

**Reference chemistries (open protocols included):**

- **Toehold switch + RPA** (license-free): RPA amplifies target → amplified product opens a Toehold RNA switch → downstream reporter gene produces fluorescence or color change. No CRISPR nuclease patent infringement.
- **PfAgo (Argonaute)** (license-free): bacterial Argonaute protein cuts target DNA using DNA guides. Different IP family from CRISPR.
- **LAMP + intercalating dye** (license-free): isothermal amplification, SYTO-9 or SYBR Green fluorescence rise.
- **TaqMan / molecular beacon** (well-established): probe-based fluorescence.

**Licensed chemistries (user-licensed):**
- **Cas12 (DETECTR)** — license from Sherlock Biosciences / Mammoth
- **Cas13 (SHERLOCK)** — license from Sherlock Biosciences / Broad

**Signal chain.**
```
Sample → loaded in well → heated to setpoint
  → user-supplied chemistry executes
  → fluorescence (or color change for lateral flow) emerges
  → 470/530 nm LED illuminates well (1 kHz modulated)
  → 520/610 nm SiPM detects emission
  → lock-in demodulator extracts signal at 1 kHz
  → ADC at 16-bit, ~10 Hz update
  → MCU emits RFU vs. time trace per channel per well
  → host runs assay-specific analysis (e.g., positive if RFU > threshold at t=30 min)
```

**Confidence reporting.** The device reports raw RFU traces with timestamps. The assay analysis software (user-supplied or NanoFlowSIM-provided open reference) interprets and emits confidence per detection.

#### Schematic Block Diagram

```
┌──────────────────────────────────────────────────────────────────────┐
│                 NFSIM-CRISPR-01 Programmable Fluorometer              │
│                                                                        │
│   USB-C ──► [FUSB302] ──► [BQ24075] ──► [LiPo + protection]          │
│                                                                        │
│   [STM32F411] ◄──I2C──► [ADS1115 ×2 (8 channels, 16-bit)]            │
│       │                                                                │
│       ├──► PWM ──► [Heater Zone 1] (NTC feedback, PID)                │
│       ├──► PWM ──► [Heater Zone 2] (NTC feedback, PID)                │
│       │                                                                │
│       ├──► GPIO ──► [470 nm LED ×8] (multiplex, 1 kHz mod)            │
│       ├──► GPIO ──► [530 nm LED ×8] (multiplex, 1 kHz mod)            │
│       │                                                                │
│       ├──► ADC ◄── [MicroFC-10035 SiPM ×16 + OPA380 TIA]              │
│       │     (or OPT101 ×16 alternative for lower cost)                 │
│       │                                                                │
│       ├──► SPI ──► [2.4" TFT display]                                  │
│       ├──► SPI ──► [nRF52840 BLE]                                      │
│       │                                                                │
│       └──► I2C ──► [Lateral flow add-on: OV2640 camera]                │
│                                                                        │
│   Light isolation: black anodized aluminum optical block               │
│   Excitation filter: 475/35 nm + 535/30 nm bandpass                   │
│   Emission filter: 520/35 nm + 610/40 nm bandpass                     │
│   Excitation-emission paths at 90° to minimize bleedthrough            │
└──────────────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary | Alternate | Notes |
|---|---|---|---|
| MCU | STM32F411CEU6 | STM32G474RET6 | Cortex-M4 with FPU |
| BLE | nRF52840-QIAA | nRF5340 | BLE 5.0 |
| SiPM detector ×16 | onsemi MicroFC-10035 | OPT101 (cheaper, lower sensitivity) | Single-photon-class sensitivity |
| TIA op-amp | OPA380 ×4 | AD8552 | High-speed for lock-in |
| ADC | ADS1115 ×2 | ADS1256 | I2C, 4-channel, 16-bit |
| Heater elements | Kapton flexible 5W ×2 | Resistive nichrome | One per zone |
| NTC thermistors ×4 | 10kΩ B=3950 | NTC 100kΩ | Per zone center + edge |
| LED 470 nm ×8 | OSRAM LT A67K | LumiLEDs L1Cx | FAM excitation |
| LED 530 nm ×8 | OSRAM LCG H9PP | LumiLEDs L1Cx-Green | ROX excitation |
| Excitation filter 475/35 | Chroma ET475/35x | Edmund Optics | Bandpass |
| Excitation filter 535/30 | Chroma ET535/30x | — | Bandpass |
| Emission filter 520/35 | Chroma ET520/35m | — | FAM detection |
| Emission filter 610/40 | Chroma ET610/40m | — | ROX detection |
| Optical block | Black anodized 6061 aluminum | Black Delrin (cheaper, slightly less ideal) | Light isolation |
| Display | 2.4" TFT ILI9341 | 1.3" OLED SSD1306 | UI |
| Camera (lateral flow add-on) | OV2640 module | OV5640 (higher res) | For strip imaging |
| PCB | 4-layer FR4 | 6-layer for tighter EMI | Standard |
| Reagents | User-supplied | NanoFlowSIM reference kits | Per assay |

#### Firmware Architecture

**RTOS:** FreeRTOS on STM32F411.

**Tasks:**
- **ThermalControlTask** (priority 7, 10 ms): two independent PID loops for the two heater zones.
- **OpticsTask** (priority 6, 50 ms): multiplexes LED drive, samples SiPM via ADS1115, performs software lock-in demodulation at 1 kHz, emits per-channel per-well RFU at ~10 Hz.
- **LateralFlowTask** (priority 5, on event): when lateral flow add-on present, captures image, runs AI line detection (15 KB TFLite Micro MobileNet-tiny INT8), emits positive/negative/invalid + confidence.
- **NFSCommsTask** (priority 5): BLE GATT + USB-CDC. The data stream is chemistry-agnostic — just RFU vs. time per well per channel + metadata about which chemistry the user identified.
- **AssayMetadataTask** (priority 3): accepts a user-supplied assay descriptor (chemistry type, target, expected positive threshold, expected time) which is stored alongside the run.

**Importantly:** the firmware does **not** include any "CRISPR positive call" logic. It emits raw RFU and lets the host determine positive/negative based on the assay descriptor. This keeps the firmware patent-clear regardless of which chemistry the user runs.
