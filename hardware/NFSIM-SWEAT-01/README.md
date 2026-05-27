### NFSIM-SWEAT-01 — Sweat Chemistry Patch

**README.** Adhesive sweat-sensing patch measuring electrolytes (Na⁺, K⁺, Cl⁻, glucose, lactate, urea, pH) via microfluidic channels + ion-selective electrodes + enzymatic amperometric.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Sensing | ISE (Na, K, Cl, pH) + amperometric (glucose, lactate, urea) |
| Microfluidic | Iontophoresis pilocarpine-driven sweat stim + capillary collection |
| Duration | 4–8h continuous |
| Connectivity | BLE 5.0 |
| Battery | 200 mAh, 24h standby + 8h active |
| BOM | ~$95 |

**THEORY.** Sweat collected via microfluidic capillary into reaction chamber. ISEs detect electrolyte concentrations (Nernst equation). Enzymatic sensors with H₂O₂ amperometry for glucose/lactate. Hot summer day or exercise produces sufficient natural sweat; pilocarpine iontophoresis induces if needed.

**BLOCK DIAGRAM.** Microfluidic patch with patterned electrodes → LMP91000 (amperometric) + MCP3424 (potentiometric ISE) → nRF52840 → BLE.

**BOM.** LMP91000 + MCP3424 ($8), nRF52840 ($5), screen-printed electrode array ($15), microfluidic PDMS ($10), iontophoresis driver ($8), 200 mAh LiPo ($4), adhesive + enclosure ($25), misc ($20). Total ~$95.

**FIRMWARE.** Multi-channel sampling, ISE calibration, enzyme decay tracking. NFS BLE streaming.

**ASSEMBLY.** Bond microfluidic to electrode array. Patch backing. Adhesive.
