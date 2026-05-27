### NFSIM-PCR-02 — Gel-Slip Strip Reader

**README.** Pre-cast disposable polymer gel strips in a pocket reader. Blue-light excitation of SYBR Safe, CMOS imaging, AI lane/band detection. 8–12 min runs, no gel preparation required.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Gel format | Disposable 70×20×2 mm pre-cast agarose (1.5% / 0.8% / 3.0% variants) |
| Lanes | 8 + 1 ladder |
| Separation range | 50 bp – 10 kb (gel-dependent) |
| Run time | 8–12 min at 200V |
| Voltage | 200V DC, 30 mA max, software-limited |
| Excitation | 470 nm blue LED array (UV variant available, safety-interlocked) |
| Detection | OV5647 5 MP or Pi HQ Camera 12.3 MP |
| Compute target | Phone or hub (image analysis) |
| BOM | ~$83 reader + ~$3/strip |

**THEORY.** Standard agarose gel electrophoresis. DNA migrates from negative to positive terminal under applied DC field; smaller fragments migrate faster. SYBR Safe intercalates DNA and fluoresces under blue (470 nm) excitation, peaking at 520 nm. CMOS sensor captures emission through a 520 nm long-pass filter. AI lane detection segments lanes; per-lane intensity profile + ladder calibration produces fragment size estimates. Used as a QC tool: did the PCR (NFSIM-PCR-01) work? Is the fragment the right size? Is there contamination?

**SCHEMATIC BLOCK DIAGRAM.**
```
USB-C 5V → [HV boost EMC0 Q101-5 or MC34063+xfmr] → 0-300V DC → Platinum electrodes
                                                                    ↑
                                          [STM32G030] ←PWM─────────┘ (regulate)
                                              │
                                              ├──I2C──► [INA219 HV current sense]
                                              ├──GPIO──► Door interlock switch
                                              ├──GPIO──► 470 nm LED array drive
                                              └──UART──► [Pi Zero 2W] ──CSI──► [OV5647 cam]
                                                            │
                                                            └──WiFi/USB──► Host
```

**BOM.**
| Component | Primary | Alt | Notes |
|---|---|---|---|
| HV module | EMCO Q101-5 (5V→0-300V) | Custom flyback w/ TL431 fb | Compact, regulated |
| Imaging compute | Raspberry Pi Zero 2W | Pi Compute Module 4 | Pi-OS, OpenCV |
| Camera | OV5647 (Pi cam) | Pi HQ Camera (12.3MP IMX477) | Higher res optional |
| MCU | STM32G030F6P6 | STM32L0 | HV control + safety |
| BLE | nRF52840 module | nRF52833 | Wireless |
| Current monitor | INA219 | INA226 | HV current safety |
| LED 470nm ×12 | OSRAM LCB G6SP | LumiLEDs L1Cx | Blue excitation |
| 520nm LP filter | Acrylic sheet | Chroma ET520lp | Cuts blue excitation |
| Door interlock | Mechanical microswitch | Hall sensor + magnet | Mandatory safety |
| Strips | Custom pre-cast agarose 1.5% (and variants) | Generic gel cassettes | Disposable, ~$3 each |

**FIRMWARE.**
- **HVControlTask**: regulates HV via PWM feedback from voltage divider; software current limit cuts power if INA219 reads >30 mA; door interlock kills HV immediately if opened.
- **TimerTask**: programmable run timer (15–60 min); HV auto-off at completion.
- **CommsTask**: NFS over BLE; STM32 sends voltage, current, time, door state. Image capture trigger sent to Pi Zero.
- **Pi side**: captures images at 30-second intervals during run, final image at end; runs lane detection + band size estimation; emits NFS result packet.

**ASSEMBLY.**
1. Order JLCPCB 2-layer PCB + EMCO HV module + Pi Zero + camera.
2. Assemble HV section with care: HV traces ≥2.5 mm clearance; physical isolation between HV and logic.
3. Mount Pi Zero on standoffs; route CSI cable to camera mounted above gel tray.
4. Install platinum electrodes (sealed in epoxy at the carbon-rod terminals).
5. Install door microswitch; verify interlock cuts HV when door opened.
6. Calibrate HV regulation against multimeter (200V setpoint should be 200±2V).
7. Run reference gel with 1 kb ladder; verify ladder bands resolve at expected positions.
