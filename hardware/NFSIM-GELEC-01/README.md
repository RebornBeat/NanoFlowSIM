### NFSIM-GELEC-01 — Portable Gel Electrophoresis (full system, modernized)

**README.** Full agarose gel electrophoresis in a lunchbox-sized unit. Supports any agarose concentration; SYBR Safe pre-staining; UV-safe blue light excitation (470 nm); 5 MP CMOS imaging. Used as QC for PCR products, fragment sizing, restriction digests, plasmid verification. Modernizes the 1950s technique with digital readout.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Gel | 70 × 60 mm mini gel (custom or commercial) |
| Lanes | 6–15 |
| Voltage | 50–200V DC, 500 mA max, software-limited |
| Run time | 20–45 min |
| Stain | SYBR Safe (pre-stained or post-stained) |
| Excitation | 470 nm blue LED array (12× 1W) |
| UV variant | 365 nm UV with safety interlock + UV goggles |
| Detection | OV5647 5 MP or Pi HQ Camera 12.3 MP |
| Buffer | 400 mL internal (1× TAE or TBE) |
| Power | USB-C or 12V DC |
| BOM | ~$110 |

**THEORY.** Same as PCR-02 strip reader but with full-size gel and user-cast agarose for research flexibility. Lane detection + band sizing AI vs. ladder reference. Modernized: no human reading of UV exposure required.

**BLOCK DIAGRAM.** Same as PCR-02 with larger HV section (500 mA), bigger gel tray, more LEDs (12 vs 2).

**BOM.** EMCO Q101-5 HV module ($12) — or custom flyback for higher current ($25), Pi Zero 2W + camera ($23), STM32G030 control ($1.50), 470nm LEDs ×12 ($12), 520nm filter ($5), interlock switch ($2), polycarbonate tank ($8), platinum electrodes ($6), PCB ($10), enclosure ($25), misc ($10). Total ~$110.

**FIRMWARE.** Same as PCR-02 but with selectable voltage 50–200V and run time 20–60 min. Door interlock mandatory.

**ASSEMBLY.** Build polycarbonate tank with carbon-rod electrode mounts. HV section with proper isolation. Pi Zero captures images at 30s intervals + final. Calibrate against ladder.

