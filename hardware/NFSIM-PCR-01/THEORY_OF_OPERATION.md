#### THEORY_OF_OPERATION.md

**Why thin-film heating wins on speed.** Conventional thermocyclers heat an aluminum block (~100 g thermal mass). The block dominates the heat-up/cool-down time. NFSIM-PCR-01's primary mode bonds a thin-film resistive heater (~100 µm) directly to a microfluidic chip carrier. The thermal mass to heat is only the chip + the 5 µL reaction volume. Combined with Peltier-assisted cooling beneath the chip carrier, this yields 8°C/s heating and 6°C/s cooling.

**PCR chemistry.** Standard PCR three-stage cycle:
1. **Denaturation** (94–98°C, 20–30s): DNA strands separate
2. **Annealing** (50–65°C, 20–40s): primers bind
3. **Extension** (72°C, 30s–2 min per kb): polymerase synthesizes new strand

**Real-time monitoring.** Each chamber has a dedicated 470 nm LED + 520 nm photodiode for SYBR Green or FAM fluorescence monitoring. The MCU samples fluorescence at the end of each extension stage. The AI classifier (15 KB TFLite Micro 1D-CNN) labels the curve as `negative` / `positive_likely` / `positive_strong` / `inconclusive` based on shape, baseline, and amplification efficiency.

**Confidence reporting.** Every run emits a confidence record with: Ct value, amplification efficiency %, baseline RFU, endpoint RFU, classifier confidence (0–1).

**Compute targeting.** The device performs only acquisition + basic feature extraction. Full curve fitting (5-parameter logistic), absolute quantification, multi-target deconvolution all run on the user-selected compute target.

#### Schematic Block Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                       NFSIM-PCR-01 Main PCB                          │
│                                                                       │
│   USB-C ──► [FUSB302] ──► [BQ24075] ──► [Protection IC] ──► LiPo    │
│       │                       │                                       │
│       └───► [USB-CDC]         └──► [TPS61085 Boost 5V 3A] ──► Rails │
│                                                                       │
│   [STM32G474] ◄────────► [W25Q128 16MB SPI Flash]                    │
│       │                                                               │
│       ├──► PID Loop (Chamber Temp) ──► [DRV8876 H-Bridge] ──► Peltier│
│       │                              ┌────────────────────┐           │
│       │   Thin-Film Heater ◄─── PWM ─┤                    │           │
│       │   (Thermal Sprint)            │                    │           │
│       │                                                                │
│       ├──► PID Loop (Lid Temp) ──► [MOSFET] ──► Kapton Lid Heater    │
│       │                                                               │
│       ├──► ADC ◄── [NTC ×4: chamber center, edge, sink, ambient]     │
│       ├──► ADC ◄── [INA219 Peltier current sense]                    │
│       ├──► ADC ◄── [OPT101 ×8 photodiode array, fluorescence]        │
│       ├──► GPIO ──► [470nm LED ×8 drive, multiplexed]                │
│       │                                                               │
│       ├──► SPI ──► [ST7789 2.4" TFT 240×320]                         │
│       ├──► GPIO ◄── [4× tactile buttons]                              │
│       │                                                               │
│       └──► SPI ──► [nRF52840 BLE Co-Processor]                       │
│                          └──► PCB Antenna (2.4 GHz)                   │
│                                                                       │
│   [MAX17055 fuel gauge] ◄──I2C──► STM32G474                          │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│                  NFSIM-PCR-01 Thermal Block PCB                      │
│                                                                       │
│   ┌──────────────────────────────────────────┐                      │
│   │ Thin-Film Heater (Thermal Sprint, primary)│ ──► Chip Carrier    │
│   └──────────────────────────────────────────┘                      │
│   ┌──────────────────────────────────────────┐                      │
│   │ Aluminum Block + Peltier (legacy mode)   │ ──► 8-Tube Strip     │
│   └──────────────────────────────────────────┘                      │
│                                                                       │
│   Peltier (×2 parallel) ◄── 5V 12A bus from main PCB                │
│   30mm fan (5V) ──► Heat sink beneath Peltier cold side              │
│   Vapor chamber + finned extrusion                                   │
└─────────────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary part | Alternate | Source |
|---|---|---|---|
| MCU | STM32G474RET6 | STM32G491RET6 | Mouser / LCSC |
| BLE | nRF52840-QIAA | nRF52833-QIAA | Mouser / LCSC |
| Peltier (legacy) | TEC1-12706 ×2 | TES1-12704 | LCSC / AliExpress |
| Peltier driver | DRV8876PWPR ×2 | DRV8876N | LCSC / Mouser |
| Thin-film heater (Thermal Sprint) | Custom Kapton heater 5W on chip carrier | Polyimide thick-film heater | DuPont / Minco |
| Fuel gauge | MAX17055REWL+ | MAX17048G | Mouser / LCSC |
| Charger | BQ24075RGTR | MCP73831 | LCSC / Mouser |
| USB-C PD | FUSB302MPX | TPS65987DDH | LCSC / Mouser |
| Boost converter | TPS61085DBVR | TPS61240 | LCSC |
| LDO 3.3V | AMS1117-3.3 | LM1117-3.3 | LCSC |
| Current sense | INA219BIDR | INA226 | LCSC |
| SPI flash | W25Q128JVSIQ | MX25L12835F | LCSC |
| Display | 2.4" TFT (ST7789, 240×320) | 1.3" OLED (SSD1306, fallback) | AliExpress / Mouser |
| Fan | 30×30×10mm 5V | 25×25×7mm 5V | LCSC |
| Aluminum block (legacy) | Custom CNC 6061 | Cast aluminum | Local machine shop |
| Vapor chamber | 60×40mm copper VC | Heat pipe + finned sink | AliExpress |
| Kapton heater (lid) | 5V 5W 70×30mm | Polyimide heater | AliExpress / Minco |
| NTC thermistors ×6 | SDNT2012X103F3950 | NTC 10kΩ B=3950 | LCSC |
| Photodiode + amp ×8 | OPT101 | TSL257 + opamp | Mouser |
| LED 470nm ×8 | OSRAM LT A67K | Cree CLA1A-MKW | LCSC / Mouser |
| Thermal interface | Arctic Silver 5 | Kingpin KPx | Amazon |
| LiPo 3000 mAh | Custom pack | Adafruit 3000mAh | Adafruit / Amazon |
| PCB 4-layer 2oz Cu | JLCPCB 4L ENIG | PCBWay 4L | JLCPCB / PCBWay |
| Enclosure | PETG FDM print | Injection-molded ABS (production) | Local print / mold shop |

#### Firmware Architecture

**RTOS:** FreeRTOS 10.5.1 on STM32G474.

**Tasks:**
- **ThermalControlTask** (priority 7, 10 ms): reads NTC thermistors via ADC DMA, runs PID for chamber and lid, drives PWM to thin-film heater / Peltier. Mode switch (Thermal Sprint vs. legacy) loads different PID gains.
- **OpticsTask** (priority 6, 100 ms): multiplexes LED drive, samples OPT101 photodiodes via ADS1115 ×2 over I2C, applies lock-in demodulation for 1 kHz LED modulation, emits per-chamber RFU per cycle.
- **ProtocolRunnerTask** (priority 6, 100 ms): runs the loaded PCR protocol state machine. Loads protocol JSON from W25Q128. Emits "stage complete," "cycle complete," "protocol complete" events.
- **MLClassifierTask** (priority 5, on event): on cycle completion, runs the amplification curve classifier (15 KB INT8 TFLite Micro 1D-CNN on STM32G474 via CMSIS-NN). Emits go/no-go + confidence.
- **BLECommsTask** (priority 5, 50 ms): manages nRF52840 over SPI. Implements NFS GATT services: Device Control (0x180A custom + 0x4a6e7300-1000), Data Stream (0x4a6e7300-2000), Metadata (0x4a6e7300-3000).
- **DisplayTask** (priority 4, 50 ms): LVGL UI on ST7789 TFT.
- **BatteryTask** (priority 2, 1000 ms): MAX17055 polling.
- **MaintenanceTask** (priority 1, 10000 ms): watchdog, OTA, error log.

**NFS protocol integration:** standard NFS BLE GATT (see §19.3 of TECHNICAL_DOCUMENTATION.md). Session-end packet includes the full thermal profile, fluorescence trace, AI classifier output, and a `provenance` block with raw thermal/optics data references.

**Compute target hint:** stored in NVS; default `phone`. Configurable per session via NFS:CONFIGURE command.
