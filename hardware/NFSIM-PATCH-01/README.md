### NFSIM-PATCH-01 — Multi-Modal Biopotential + Motion Patch

**README.** Foundational "Context Engine" patch for the Multi-Modal Fusion AI layer. ECG + 6-axis accelerometer + skin temperature + EDA, all from a single adhesive patch.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| ECG | 1 lead, 250 Hz, 24-bit (ADS1291) |
| IMU | LSM6DSO 6-axis, 25 Hz |
| Temperature | NTC + MAX30205 reference |
| EDA | 2-electrode skin conductance via AC bridge, 4 Hz |
| Wear | 14-day patch, replaceable adhesive |
| Connectivity | BLE 5.0 |
| Battery | 200 mAh, 14d continuous |
| BOM | ~$48 |

**THEORY.** Multi-modal correlated time-series feed Multi-Modal Fusion AI: e.g., ECG + IMU + EDA together → stress event identification; ECG + temp → fever differentiation from exercise tachycardia; etc. Each individual signal is useful; the multi-modal correlation reveals patterns no single sensor sees.

**BLOCK DIAGRAM.** ADS1291 (ECG) + LSM6DSO (IMU) + MAX30205 + NTC (temp) + LMP91000 (EDA via AC bridge) → nRF52840 → BLE.

**ASSEMBLY.** Compact adhesive patch with electrodes positioned for ECG + EDA. IMU + temp internal.
