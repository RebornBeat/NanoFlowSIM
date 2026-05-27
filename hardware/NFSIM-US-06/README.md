### NFSIM-US-06 — Transcranial Doppler Headband

**README.** Bilateral 2 MHz pulsed-wave Doppler measuring middle cerebral artery flow velocity through the temporal acoustic window. Stroke monitoring, vasospasm detection, autoregulation studies.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Mode | Pulsed-wave Doppler with range gate |
| Frequency | 2 MHz |
| Transducers | 2 (bilateral temporal windows) |
| Depth gate | 30–80 mm (selectable) |
| Velocity range | 0–250 cm/s |
| Connectivity | BLE 5.0 |
| Battery | 1000 mAh, 8h continuous |
| BOM | ~$220 |

**THEORY.** PW Doppler with range-gating allows velocity measurement at a specific depth (the MCA, typically 45–55 mm through the temporal bone). The skull attenuates 2 MHz significantly; specific bone-thin "acoustic windows" allow penetration.

**BLOCK DIAGRAM.** Per side: 2 MHz PZT focused element + ±60V pulser + AFE5832 4-ch + STM32H7 (range gating + Doppler FFT) → BLE to phone. Headband mechanical positioner.

**BOM.** 2 MHz focused PZT ×2 ($60), AFE5832 ($25), pulser ($20), STM32H7 ($15), BLE ($5), headband + foam ($40), PCB ($15), misc ($40). Total ~$220.

**FIRMWARE.** PW pulse sequence; range gate; complex demod; FFT for velocity spectrum; NFS streaming.

**ASSEMBLY.** Padded headband with mechanical positioners for each temporal window. Coupling gel pads.
