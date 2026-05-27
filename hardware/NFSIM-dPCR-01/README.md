### NFSIM-dPCR-01 — Digital Droplet PCR

**README.** Absolute DNA quantification via droplet partitioning. Microfluidic chip generates 10,000–20,000 ~1 nL droplets; standard PCR cycling on NFSIM-PCR-01 carrier; endpoint fluorescence imaging counts positive droplets; Poisson statistics give absolute concentration. Critical for liquid biopsy (ctDNA at 0.01% VAF), viral load, copy number variation.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Partition | T-junction microfluidic, oil-water emulsion |
| Droplet volume | ~1 nL |
| Droplets per run | 10,000–20,000 |
| Reaction volume | 20 µL |
| Detection | Endpoint imaging, 2-color (FAM 520 nm + HEX/VIC 556 nm) |
| Dynamic range | 1–100,000 copies/µL |
| Sensitivity | 1 copy/20 µL |
| Run time | 90–120 min (cycling + imaging) |
| Power | 12V DC or battery |
| BOM | ~$285 |

**THEORY.** Sample diluted so each droplet contains 0 or 1 template molecule (Poisson). PCR amplifies; positive droplets fluoresce, negative droplets don't. Counts → Poisson: concentration = −ln(1 − P_pos) / V_droplet. No standard curve needed → absolute quantification. Enables: ctDNA detection at 0.01% variant allele frequency, viral load monitoring (HBV, HIV transplant), copy number variation, rare cell allele detection.

**BLOCK DIAGRAM.**
```
[Syringe pumps ×2: aqueous + oil] ──► [PDMS T-junction chip] ──► droplets
                                                                    │
                                                                    ▼
[Chip sealed + placed in NFSIM-PCR-01 thermal block] ──► cycling
                                                                    │
                                                                    ▼
[Imaging station: 470/530 nm LED + 2-color filter wheel + IMX477 camera]
                                                                    │
                                                                    ▼
[Pi CM4 or laptop] ──► OpenCV watershed segmentation ──► Poisson stats ──► copies/µL
```

**BOM.** Syringe pumps with TMC2209 + NEMA8 ×2 ($50), PDMS chip (SU-8 master fabrication or 3D printed) ($30), microscope optics + LEDs + filters ($60), IMX477 (Pi HQ Cam) + Pi CM4 ($60), STM32H7 controller ($8), nRF52840 BLE ($5), PCB 4-layer ($25), enclosure ($25), misc ($22). Total ~$285.

**FIRMWARE.** STM32H7 controls droplet generation (pump rates); coordinates with NFSIM-PCR-01 for cycling; triggers imaging station. Pi CM4 runs droplet detection + Poisson statistics. Output: NFS packet with target, copies/µL, 95% CI.

**ASSEMBLY.** SU-8 master for PDMS replication (academic or contract foundry) OR Form 3+ printed master. Cast PDMS replicas. Assemble syringe pumps. Build imaging station. Calibrate against known concentration standards.
