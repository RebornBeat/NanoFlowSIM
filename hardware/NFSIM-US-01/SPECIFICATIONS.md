#### SPECIFICATIONS.md

| Parameter | Value |
|---|---|
| Transducer | 128-element PZT linear array, interchangeable cartridges |
| Cartridge frequencies | 3.5 MHz (abdominal), 5 MHz (general), 7.5 MHz (vascular/MSK), 12 MHz (small parts) |
| Element pitch | 0.3 mm (5 MHz cart) / 0.2 mm (7.5 MHz) |
| Pulse voltage | ±50V (low-V driver for safety) |
| Pulse types | Bipolar, 2-cycle, chirp (selectable) |
| ADC | 14-bit, 40 MSPS per channel, 128 channels (TI AFE5832) |
| Beamforming | Software on host (CUDA/Metal/Vulkan/OpenCL) |
| Frame rate | 30–60 fps (B-mode); 200+ fps (plane-wave compound) |
| Depth | 2–25 cm (frequency-dependent) |
| Modes | B-mode, M-mode, Color Doppler, PW Doppler, Power Doppler |
| Connectivity | USB 3.2 Gen 1 (5 Gbps data) + BLE 5.0 (control) |
| Power | USB-C bus power (5V 1.5A) + 2000 mAh LiPo for wireless ops |
| Probe dimensions | 150 × 45 × 30 mm |
| Probe weight | 280g |
| BOM target | ~$471 |
| Compute target | Phone GPU (default), laptop GPU, hub+CON-06 |
