### NFSIM-US-05 — Radial Artery Doppler Wristband

**README.** Wristband-form 8 MHz continuous-wave Doppler for arterial blood flow velocity at the radial artery. Pulse waveform + vascular age estimation + pulse wave velocity for arterial stiffness.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Mode | Continuous-wave Doppler |
| Frequency | 8 MHz |
| Transducer | 2-element PZT (Tx + Rx) angled at 60° to vessel |
| Audio output | Doppler shift → audible (200 Hz – 2 kHz) |
| Velocity range | 0–2 m/s |
| Connectivity | BLE 5.0 |
| Battery | 250 mAh, 12h continuous |
| BOM | ~$95 |

**THEORY.** CW Doppler: continuous transmit, continuous receive; mixing produces Doppler-shifted signal proportional to blood velocity. Audible Doppler signal heard for trained operators; velocity envelope extracted on host for cardiovascular metrics.

**BLOCK DIAGRAM.** nRF52840 + Si5351 RF generator (8 MHz) + Tx amp → PZT Tx; Rx PZT → preamp → mixer → audio LP filter → ADC → BLE stream. Velocity extraction on phone.

**BOM.** 8 MHz PZT ×2 ($25), Si5351 ($2), nRF52840 ($5), audio AFE ($8), 250 mAh LiPo ($4), wristband strap + enclosure ($20), PCB ($8), misc ($23). Total ~$95.

**FIRMWARE.** Audio-rate streaming + on-device envelope extraction (simple). NFS BLE protocol.

**ASSEMBLY.** Standard wristband form factor. PZTs positioned for 60° angle to radial artery. Hydrogel coupling.
