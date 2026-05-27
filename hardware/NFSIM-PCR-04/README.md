### NFSIM-PCR-04 — RPA Room-Temperature Reader

**README.** Recombinase Polymerase Amplification reader. Works at 25–42°C — body temperature range. Minimal electronics; can be powered passively (exothermic hand-warmer for heating) for zero-power field operation. 10–20 min results. Lateral flow output option for no-optics variant.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Method | RPA (TwistAmp kits compatible) |
| Temp | 25–42°C (37°C optimal) |
| Heating | Small resistive heater 1W + STM32L0 PID, OR passive hand-warmer |
| Detection | Lateral flow strip (camera reader) OR fluorescence (OPT101) |
| Time | 10–20 min |
| Sample | 8-tube strip |
| Power | USB-C 5V 0.5A or 1000 mAh LiPo |
| BOM | ~$45 |

**THEORY.** Recombinase proteins (uvsX, uvsY from T4 phage) form filaments on primers and search dsDNA for complementary sequence. When found, they invade the duplex (no denaturation needed). Single-strand binding protein stabilizes. Strand-displacing polymerase extends. Result: isothermal amplification at low temperatures. Compatible with lateral-flow strip readout (5'-biotin + 5'-FAM labeled primers → amplicon captured at streptavidin line, FAM detected at anti-FAM line).

**BLOCK DIAGRAM.**
```
USB-C → [Charger] → 3.3V LDO
[STM32L0] ──PWM──► [MOSFET] ──► [Resistive heater 1W] (37°C setpoint)
              ◄──NTC──
[STM32L0] ──SPI──► [nRF52811 BLE]
[STM32L0] ──I2C──► [SSD1306 OLED]
Optional optics: [OV2640 cam] for lateral flow OR [OPT101 + LED] for fluorescence
```

**BOM.** STM32L0 ($1.50), nRF52811 ($3), heater + NTC ($3), OPT101 or OV2640 ($4-8), 1000 mAh LiPo ($3), PCB 2-layer ($5), enclosure ($5), passives + misc ($5–8). Total ~$45.

**FIRMWARE.** Bare-metal with FreeRTOS-Lite. Heater PID, lateral flow camera capture (or fluorescence sampling), NFS BLE output.

**ASSEMBLY.** 2-layer PCB. Mount heater + NTC under sample wells. Install camera (lateral flow variant) or LED+OPT101 (fluorescence variant). Calibrate at 37°C. Validate with reference RPA assay.
