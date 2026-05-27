### NFSIM-SEQ-02 — Solid-State Nanopore Research Board

**README.** Development platform for solid-state nanopore research. 4-channel patch clamp amplifier infrastructure for testing custom-fabricated SiN, MoS₂, hBN, or Graphene nanopore chips. More stable than biological pores; reusable; tunable size.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Membrane | SiN (10–50 nm), MoS₂, hBN, Graphene on Si substrate |
| Pore diameter | 1–20 nm (fabrication-dependent) |
| Chip format | 5 × 5 mm with PDMS gasket |
| Voltage clamp | ±1V, 1 mV resolution |
| Current range | 1 pA – 10 nA |
| Bandwidth | DC to 100 kHz |
| Sampling | 500 kHz, 16-bit |
| Noise floor | <3 pA RMS at 10 kHz |
| Channels | 4 independent |
| Interface | USB 3.0 + SPI extension for FPGA |
| BOM | ~$280 |

**THEORY.** Solid-state nanopores are drilled through thin dielectric membranes (SiN ~10 nm thick) using TEM, He-ion microscope, or dielectric breakdown. Ionic current modulates as analytes (DNA, proteins, polymers) translocate. Higher noise than biological pores but unlimited shelf life, tunable size, mechanically robust. Used for: protein detection, single-molecule sensing, polymer characterization, education on patch-clamp electronics.

**BLOCK DIAGRAM.**
```
4× Independent TIA channels (AD8625 or OPA827, FET input)
  ├── Switchable feedback: 500 MΩ (high sensitivity) / 50 MΩ (high BW)
  ├── Per-channel DAC (AD5541A 16-bit) → LT1010 buffer → trans electrode
  ├── ADC: ADS8860 1 MSPS 16-bit per channel
  └── Xilinx Artix-7 FPGA (Digilent Basys 3 or Arty A7)
        ├── Real-time event detection (threshold + hysteresis)
        ├── Dwell time / blockade depth extraction
        └── USB 3.0 via FT601 (200 MB/s)
Chip interface: PDMS gasket + spring-loaded Ag/AgCl contact pins
Peltier temperature control: 10–60°C ±0.1°C
```

**BOM.** AD8625×4 ($60), OPA827 alt, AD5541A×4 ($40), ADS8860×4 ($80), Artix-7 board ($60), FT601 ($12), Rogers 4-layer PCB ($25), enclosure + chip holder ($15). Total ~$280.

**FIRMWARE.** FPGA-only data path. Python host: chip characterization, event analysis, data export.

**ASSEMBLY.** Order PCBs. Hand-solder JFET-input amps with extreme cleanliness. Build PDMS chip holder. Pair with academically-sourced SiN nanopore chips (~$50–$500/chip).
