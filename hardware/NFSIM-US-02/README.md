### NFSIM-US-02 — Wearable Ultrasound Patch

**README.** Adhesive wearable ultrasound patch (~20×40 mm) for continuous monitoring of a single region (carotid artery, fetal heart, bladder volume, IVC diameter for fluid status). PVDF film transducer — flexible, low-voltage, conforms to skin.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Transducer | PVDF film, 16-element 1D array |
| Frequency | 3.5 MHz (deep) or 7.5 MHz (shallow) variants |
| Drive voltage | ±20V (PVDF low-V) |
| Form factor | 25×50×4 mm patch |
| Adhesive | 3M Tegaderm-compatible medical adhesive |
| Connectivity | BLE 5.0 + optional 2.4 GHz proprietary high-throughput |
| Battery | 200 mAh LiPo, ~24h continuous M-mode |
| Mode | M-mode primarily, basic B-mode via SAFT reconstruction on host |
| BOM | ~$320 |

**THEORY.** PVDF film bonded to flexible PCB conforms to skin. M-mode: single line vs. time — captures motion (vessel wall pulsation, fetal heart, diaphragm). B-mode reconstruction via synthetic aperture on host (phone or hub).

**BLOCK DIAGRAM.**
```
PVDF 16-element array (flex)
  → 16:4 mux (MAX14661)
  → ±20V pulser + Tx/Rx
  → 4-ch AFE (TI AFE5805 or AD9670)
  → 12-bit ADC @ 20 MSPS
  → nRF52840 (BLE) — emits RF I/Q chunks
  → BLE to phone OR custom 2.4 GHz to hub for higher throughput
```

**BOM.** PVDF film + electrode patterning ($25), pulser + AFE ($60), nRF52840 ($5), 16:4 mux ($8), flex PCB ($30), battery ($8), enclosure + adhesive ($25), misc ($24), assembly ($135). Total ~$320.

**FIRMWARE.** Acquisition state machine (continuous M-mode, periodic B-mode synth aperture). BLE NFS streaming. Skin temperature monitoring (auto-shutoff >43°C).

**ASSEMBLY.** Flex PCB. PVDF bonded with acoustic coupling gel pad. Encapsulate in medical-silicone. Adhesive backing per use.
