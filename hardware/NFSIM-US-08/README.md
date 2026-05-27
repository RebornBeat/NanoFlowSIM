### NFSIM-US-08 — Fetal Doppler Wearable

**README.** Wearable fetal heart rate Doppler for home monitoring during pregnancy. 2–3 MHz CW Doppler with on-device fetal heart rate extraction. NOT a fetal monitoring NST replacement — for reassurance/education only, with clear regulatory positioning.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Mode | CW Doppler |
| Frequency | 2.5 MHz |
| Audio output | Audible fetal heartbeat |
| BPM extraction | On-device peak detection |
| Connectivity | BLE 5.0 |
| Battery | 500 mAh, 4h continuous |
| BOM | ~$65 |

**THEORY.** Same as US-05 but at 2.5 MHz for deeper penetration (uterus). Audio output + BPM extraction. Important regulatory positioning: NOT for replacement of clinical fetal monitoring.

**BLOCK DIAGRAM.** Identical concept to US-05 with 2.5 MHz PZT and abdominal patch form factor.

**BOM.** 2.5 MHz PZT ×2 ($20), Si5351 ($2), nRF52840 ($5), audio AFE + speaker ($12), 500 mAh LiPo ($5), patch enclosure ($15), misc ($6). Total ~$65.

**FIRMWARE.** Audio-rate streaming + peak detection for BPM. Speaker output. NFS BLE for monitoring.

**ASSEMBLY.** Abdominal patch with hydrogel coupling. Small speaker.
