### NFSIM-CHEM-03 — Urine Dipstick Reader

**README.** Smartphone-companion device or standalone that reads 10-panel urine dipsticks (glucose, ketones, blood, protein, pH, etc.) via colorimetric image analysis.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Strip | Standard 10-panel commercial dipstick |
| Detection | RGB color analysis, white-balance reference card |
| Connectivity | BLE 5.0 or QR-code phone capture |
| BOM | ~$55 |

**THEORY.** Color-change reagents on commercial dipsticks scanned with controlled lighting + AI color classification. Per-pad reference comparison.

**BLOCK DIAGRAM.** STM32L0 + OV2640 + white LED ring + nRF52811. Or zero-electronics version: just a precision color reference card photographed by phone camera.

**BOM.** OV2640 ($8), STM32L0 ($1.50), nRF52811 ($3), white LEDs ($1), strip slot + reference card ($5), 1000 mAh LiPo ($4), enclosure ($25), misc ($7.50). Total ~$55.

**FIRMWARE.** Capture image, segment per pad, compare to reference, emit per-analyte result.

**ASSEMBLY.** Lightbox with strip slot + diffused illumination. Camera positioned above.
