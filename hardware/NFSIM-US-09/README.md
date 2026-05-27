### NFSIM-US-09 — Ultrasound Needle Guide

**README.** Clip-on linear array attachment for any standard needle (biopsy, central line, regional anesthesia). Real-time needle tracking in ultrasound image plane. Connects to US-01 host display.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Type | 10 MHz linear 64-element PZT, micro form factor |
| Field | 3 cm depth |
| Needle compatibility | 18-25 gauge standard |
| Integration | Plugs into US-01 cartridge slot or USB-C standalone |
| BOM | ~$145 |

**THEORY.** Mounts on needle hub; transducer images perpendicular to needle path; needle tip visible as bright reflector in image. AI on host enhances needle tip detection.

**BOM.** 10 MHz 64-el PZT ($45), AFE5832 ×8 ($50), pulsers + FPGA ($30), clip-on enclosure ($20). Total ~$145.

**FIRMWARE.** Same architecture as US-01, smaller channel count. Host AI for needle tip detection.

**ASSEMBLY.** Linear array bonded to clip-on housing. Sterile single-use cover per procedure.
