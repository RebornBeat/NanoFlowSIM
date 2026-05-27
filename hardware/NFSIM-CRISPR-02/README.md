### NFSIM-CRISPR-02 — Lateral Flow Reader

**README.** Camera-based lateral flow strip reader. AI line detection. Simplest CRISPR diagnostic reader: no fluorescence optics, just a camera + AI. Reads any standard lateral flow strip (positive/negative/invalid + confidence).

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Camera | OV2640 2 MP CMOS |
| Illumination | White LED 5 mm, diffused |
| AI model | MobileNet-tiny INT8 (15 KB) — strip image → {positive, negative, invalid} + confidence |
| Strip compatibility | Any standard nitrocellulose lateral flow (CRISPR, pregnancy, antigen, antibody, etc.) |
| Time | 5 seconds image + classification |
| Power | USB-C 5V 0.5A |
| Battery | 1000 mAh |
| BOM | ~$35 + $5/strip (reagents) |

**THEORY.** A standard lateral flow strip: capillary action pulls sample from inlet through reagent zone (CRISPR-cleaved reporter or antibody-conjugated nanoparticles) to test/control lines. Test line presence/absence indicates positive/negative. AI model trained on thousands of strip images handles lighting variation, strip orientation, partial bands. Hardware is chemistry-agnostic: works for SHERLOCK reporter strips (license required), Toehold-switch strips (license-free), antigen strips, antibody strips, etc.

**BLOCK DIAGRAM.**
```
USB-C → 5V → [STM32L0 + nRF52811]
[STM32L0] ──I2C──► [SSD1306 1" OLED]
[STM32L0] ──UART──► [OV2640 camera module]
                    └── White LED (constant on during capture)
[nRF52811] ──BLE──► Host
```

**BOM.** OV2640 module ($8), STM32L0 ($1.50), nRF52811 ($3), white LED + diffuser ($1), 1" OLED ($2), 1000 mAh LiPo ($3), PCB ($5), enclosure ($5), passives/misc ($6). Total ~$35.

**FIRMWARE.** Bare-metal. CameraTask captures strip image on user trigger. MLClassifierTask runs MobileNet-tiny on STM32H7 alternative (or sends raw image to phone for inference on simpler MCU). NFS BLE result packet: {result, confidence, raw_image_ref}.

**ASSEMBLY.** Trivial 2-layer PCB. Mount camera 8 cm above strip well, with white LED diffuser between camera and strip. Calibrate against reference strips (known positive + known negative).
