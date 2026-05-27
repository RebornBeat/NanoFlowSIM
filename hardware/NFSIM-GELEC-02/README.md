### NFSIM-GELEC-02 — Chip Capillary Electrophoresis Reader

**README.** Microfluidic chip-based capillary electrophoresis. More sensitive and faster than agarose gels. Glass or PDMS CE chip with 10 cm effective separation; laser-induced fluorescence detection. DNA sizing, SNP genotyping, protein SDS-PAGE on chip.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Chip | Glass microfluidic (Micralyne, Microfab) or custom PDMS |
| Channel | 10 cm effective length, 50 µm width |
| HV | 300–1000V for CE separation |
| Detection | 488 nm diode laser (1 mW) + avalanche photodiode (APD) |
| Applications | DNA sizing, protein SDS-PAGE, SNP genotyping |
| Time | 5–15 min per run |
| BOM | ~$280 (electronics; chips ~$50–200 each) |

**THEORY.** Sample injected electrokinetically into channel; HV separates by size+charge. Laser excites fluorescent label; APD detects emission. Smaller fragments migrate faster. Higher resolution than slab gel; less sample needed (~µL).

**BLOCK DIAGRAM.**
```
[STM32G474] ──SPI──► [DAC] → [HV amplifier 0-1000V] → CE chip electrodes
[STM32G474] ──GPIO──► [488nm laser diode + driver]
[STM32G474] ◄──ADC── [APD + TIA + filter] (fluorescence detection)
[STM32G474] ──SPI──► [nRF52840 BLE]
```

**BOM.** HV power supply (custom or commercial small module, $40), 488nm laser diode + driver ($30), APD (Hamamatsu, $80), TIA + filter ($15), STM32G474 ($4), nRF52840 ($5), chip interface (CNC PEEK holder, $30), PCB 4-layer ($25), enclosure ($30), misc ($21). Total ~$280.

**FIRMWARE.** HVControlTask, LaserTask (modulated for lock-in), DetectionTask (APD + lock-in demod), RunTask (sample injection sequence). NFS output: peak times + intensities → fragment sizes vs. ladder.

**ASSEMBLY.** Build precision optics: laser → 488 LP filter → 10× objective → APD. Build HV electrode contacts. Calibrate against DNA size ladder.
