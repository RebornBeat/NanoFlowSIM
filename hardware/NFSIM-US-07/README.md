### NFSIM-US-07 — Endocavity Probe (transvaginal/transrectal)

**README.** Curved 128-element PZT probe for transvaginal (gynecologic) or transrectal (prostate) imaging. Single-use sterile sleeve compatible. Same electronics core as US-01.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Transducer | Curved 128-element PZT, 6.5 MHz center |
| Curvature radius | 13 mm |
| Field of view | 160° |
| Depth | 0–10 cm |
| Electronics | Same as US-01 (AFE5832, ECP5 FPGA, USB 3.2) |
| Sterilization | EtO sleeve (single-use) + Cidex OPA wipe |
| BOM | ~$310 |

**THEORY.** Curved array gives wide field of view through cavity. Beamforming on host (same as US-01).

**BLOCK DIAGRAM.** Identical to US-01 but with curved array and different cartridge geometry.

**BOM.** Curved 128-el PZT (~$80), AFE5832 ×16 + pulsers + ECP5 + FX3 (~$200), enclosure with grip + sleeve interface (~$30). Total ~$310.

**FIRMWARE.** US-01 firmware with cartridge-type identifier; host renders curved scan-conversion.

**ASSEMBLY.** Curved array bonded to specialized cartridge body. Sterile sleeve interface (rolled latex sleeve over probe shaft).
