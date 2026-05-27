### NFSIM-DEL-01 — Insulin Patch Pump

**README.** Wearable insulin patch pump compatible with OpenAPS/Loop closed-loop control. Piezoelectric micro-pump with reservoir + cannula + skin adhesive.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Reservoir | 1.5 mL insulin |
| Pump | Bartels mp6 piezoelectric micro-pump |
| Cannula | 6 mm soft cannula (one-shot inserter) |
| Dose resolution | 0.05 U |
| Wear | 3 days |
| Connectivity | BLE 5.0 + Wi-Fi (closed-loop with CGM-01) |
| Safety | Occlusion detection, hardware interlock, fail-safe basal |
| BOM | ~$95 |

**THEORY.** Micro-pump delivers insulin from reservoir through cannula into subcutaneous tissue. Closed-loop with CGM-01 via OpenAPS/Loop algorithm (running on phone).

**SAFETY.** Critical safety device. Multi-redundant occlusion detection (pressure sensor + flow sensor). Hardware interlock requires confirmation before bolus. Audit log signed with device key.

**BLOCK DIAGRAM.** STM32H7 (safety-rated firmware) + Bartels mp6 driver + pressure sensor + cannula insertion mechanism + BLE.

**ASSEMBLY.** Critical: USP Class VI cannula. Sterile assembly. Per-batch validation. Full IEC 60601-1 + ISO 13485 quality system for clinical use.
