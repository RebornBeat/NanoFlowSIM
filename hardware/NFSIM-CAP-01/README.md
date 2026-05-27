### NFSIM-CAP-01 — GI Optical Camera + Chemistry Capsule

**README.** Standard pill-cam style optical imaging plus pH and oxygen sensors. 8h transit time; ~30,000 images per session; chemistry data interleaved.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Dimensions | 11 × 26 mm |
| Imaging | OV6948 micro camera (200×200 px) or OmniVision OV6946 |
| Frame rate | 2 fps continuous; 4–8 fps adaptive (motion-triggered) |
| Illumination | 4× white LEDs (PWM-dimmed) |
| Sensors | pH (ISFET), O₂ (Clark electrode), temperature (NTC) |
| Battery | 100 mAh, 8h life |
| Wireless | 434 MHz FSK, ~500 kbps |
| BOM | ~$390 |

**THEORY.** Capsule traverses GI tract under peristalsis. Images mucosa; pH localizes to GI region (stomach <2, duodenum ~6, jejunum ~7, colon ~6); O₂ tracks aerobic-to-anaerobic transition.

**BLOCK DIAGRAM.** ESP32-S3 + OV6948 camera + Si4463 radio + ISFET pH + Clark electrode + NTC + 6-axis IMU + 100 mAh battery + LEDs.

**ASSEMBLY.** Stack components vertically in 11mm cylindrical shell. Optical-grade transparent endcap for camera. Sealed with USP Class VI epoxy. Pressure-test before use.
