### NFSIM-PCR-03 — LAMP Isothermal Reader

**README.** Loop-mediated isothermal amplification reader. Fixed 65°C heater. Real-time fluorescence in 2 channels. 15–30 min results. Compatible with published LAMP primers for COVID-19, influenza, HIV, malaria, Zika, TB, etc.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Method | LAMP (or RPA at 37°C) |
| Setpoint | 65°C ±0.5°C (programmable 60–70°C) |
| Sample | 8-tube 0.2 mL strip |
| Detection | 470 nm LED + OPT101 ×8 (FAM/SYBR-Green) + 530 nm LED + 610 nm filter ×8 (ROX) |
| Time | 15–30 min |
| Power | USB-C 5V 1A or 2000 mAh LiPo |
| Connectivity | USB-C + BLE 5.0 |
| BOM | ~$93 |

**THEORY.** LAMP uses 4–6 primers that form stem-loops on the target; Bst polymerase amplifies isothermally at 65°C with no thermal cycling. SYTO-9 / SYBR Green intercalation produces fluorescence rise on amplification. Alternative: colorimetric phenol red pH indicator turns pink→yellow on amplification (no optics needed, lowest cost variant).

**BLOCK DIAGRAM.**
```
USB-C → [Charger + LDO] → 5V/3.3V rails
[STM32G474] ──PID──► [MOSFET] ──► Resistive heater in aluminum block
              ◄──NTC×2── (block + ambient)
[STM32G474] ──GPIO──► [470nm LED + 530nm LED] (1 kHz modulated)
[STM32G474] ◄──I2C──► [ADS1115 ×2] ◄── [OPT101 ×16] (FAM ch + ROX ch per well)
[STM32G474] ──SPI──► [nRF52840 BLE] ──► PCB antenna
[STM32G474] ──I2C──► [SSD1306 1.3" OLED]
```

**BOM.** STM32G474, nRF52840, ADS1115×2, OPT101×16 ($14), Nichrome heater 5W, aluminum block (CNC ~$18), 470nm LED ×2 + 530nm ×2, bandpass filters (Chroma) ×16 ($20), SSD1306 OLED ($2), 2000 mAh LiPo, PCB 4-layer (~$10). Total ~$93.

**FIRMWARE.** FreeRTOS. ThermalControlTask (heater PID), OpticsTask (LED multiplex + lock-in demodulation), ReactionTask (run timer + curve recording), CommsTask (BLE NFS streaming). Optional on-device AI classifier for amplification curve (15 KB INT8 1D-CNN; chemistry-agnostic).

**ASSEMBLY.** Standard SMD. Mill aluminum heating block. Embed thermistors. Mount nichrome heater under block. Install LED + filter + OPT101 above each well. Calibrate temperature against NIST probe. Run reference LAMP positive control.
