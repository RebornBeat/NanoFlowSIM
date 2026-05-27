### NFSIM-XRAY-01 — Portable X-Ray with Wireless FPD

**README.** Battery-powered portable X-ray generator + wireless flat-panel detector (FPD). Field deployable. ~80 kVp / 100 mAs capability for chest, extremities, dental.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| X-ray tube | Stationary anode, oil-cooled, 40–90 kVp |
| Current | 20–100 mAs |
| Battery | 5000 mAh @ 14.8V LiPo, ~50 exposures per charge |
| FPD | 14×17" amorphous-silicon CsI, wireless |
| FPD resolution | 3000×3000 pixels, 14-bit |
| Wireless | Wi-Fi 6 5 GHz to host |
| Tube weight | ~4 kg with battery |
| BOM | ~$4,200 |

**THEORY.** Conventional X-ray. Tube emits X-rays; detector captures attenuation map; image displayed on host. Wireless FPD eliminates film/CR workflow.

**BLOCK DIAGRAM.** Tube + HV power supply (60–100 kV battery-driven via flyback) + STM32 controller + safety interlocks; FPD with built-in image processor + Wi-Fi. Host runs image enhancement + dose tracking.

**BOM.** X-ray tube + collimator (custom or surplus, $1500), HV supply + battery ($800), wireless FPD ($1500 — used 14×17" CsI), controller electronics ($200), enclosure + lead shielding ($200). Total ~$4,200.

**FIRMWARE.** Exposure timer + safety interlock; dose accumulator; image transfer via Wi-Fi.

**ASSEMBLY.** Critical: regulatory compliance for radiation safety. Lead shielding around tube. Operator badge dosimetry. Site licensing per jurisdiction.
