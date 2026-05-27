### NFSIM-CRISPR-03 — Electrochemical Reader

**README.** Lowest-power, no-optics CRISPR (or general electrochemistry) reader. Potentiostat reads electrochemical signal from screen-printed electrode strips. Cas12 collateral cleavage releases an electrode-blocking aptamer → current change. Works with many other electrochemical assays.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Method | Amperometry / potentiometry (electrochemistry only) |
| Electrode | Screen-printed carbon electrode (SPE) strip |
| Potentiostat | LMP91000 (3-electrode, I2C) |
| Detection range | 1 pA – 1 mA |
| Time | 20–40 min (isothermal reaction) |
| Power | USB-C 5V or 1000 mAh LiPo |
| BOM | ~$40 + $3–8/test strip |

**THEORY.** Screen-printed electrode strip is functionalized with an aptamer that blocks the electrode surface (high impedance, low current). When Cas12 (or other nuclease) activates on target detection, it cleaves the aptamer, exposing the electrode surface — current rises measurably. Same principle works for other nuclease-based diagnostics, enzyme-based glucose-like measurements, or any redox-active analyte.

**BLOCK DIAGRAM.**
```
USB-C → 5V → [STM32L0 + nRF52811]
[STM32L0] ──I2C──► [LMP91000 potentiostat] ──► [3-electrode SPE strip]
                                                    ├── Working electrode
                                                    ├── Reference electrode (Ag/AgCl printed)
                                                    └── Counter electrode (carbon)
[STM32L0] ──I2C──► [SSD1306 OLED]
[nRF52811] ──BLE──► Host
```

**BOM.** LMP91000 ($3), STM32L0 ($1.50), nRF52811 ($3), strip connector ($1), 1" OLED ($2), 1000 mAh LiPo ($3), PCB ($5), enclosure ($5), passives ($16.50 buffer). Total ~$40.

**FIRMWARE.** Bare-metal. PotentiostatTask configures LMP91000 (bias voltage, gain) per assay; samples current at 1 Hz; emits raw current trace via BLE NFS packet.

**ASSEMBLY.** Trivial 2-layer PCB. Strip connector accepts standard SPE strips. Calibrate with reference redox couple (e.g., 1 mM ferricyanide).
