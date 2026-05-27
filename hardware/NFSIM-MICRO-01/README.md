### NFSIM-MICRO-01 — Digital Pathology Microscope

**README.** Motorized X-Y-Z microscope stage + IMX477 + open AI for tissue analysis. Whole slide imaging (40×) for digital pathology. Used in field clinics for histopathology, parasite detection (malaria, TB on AFB stain), urine sediment.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Magnification | 4×, 10×, 40× (turret) |
| Stage | Motorized X-Y, 75 × 50 mm travel; motorized Z focus |
| Camera | IMX477 12.3 MP (Raspberry Pi HQ Camera) |
| Whole-slide imaging | Tile + stitch, ~10 min per 1 cm² at 40× |
| AI applications | Malaria parasite detection, AFB detection, urine sediment classification |
| Compute | Raspberry Pi CM4 onboard |
| Connectivity | Wi-Fi + USB-C |
| BOM | ~$520 |

**THEORY.** Standard transmitted-light microscope with motorized stage. Tile-and-stitch imaging at high magnification. AI models trained on open digital pathology datasets (e.g., NIH malaria, BBBC, TUPAC).

**BLOCK DIAGRAM.** Pi CM4 + stepper drivers (TMC2209 ×3) + IMX477 + LED illumination + turret control. AI inference on Pi CM4 (or upload to host).

**BOM.** Optics (objective set 4×/10×/40× ~$200), stepper motors + drivers ($60), IMX477 + lens ($55), Pi CM4 + carrier ($60), LED illumination ($20), mechanical frame ($80), PCB ($25), misc ($20). Total ~$520.

**FIRMWARE.** Stage motion control + camera capture; tile stitching; AI inference. NFS protocol upload to patient record.

**ASSEMBLY.** Mechanical precision critical — use precision linear rails. Calibrate magnification with calibration slide.
