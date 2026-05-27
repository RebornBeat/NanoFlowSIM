#### THEORY_OF_OPERATION.md

**Acoustic theory.** PZT (lead zirconate titanate) elements convert applied voltage to mechanical strain → ultrasound pulse → propagation into tissue → partial reflection at acoustic-impedance discontinuities → return to elements → element strain → voltage → digitization.

**Beamforming on the host.**
- **Receive beamforming (Delay-and-Sum)**: each channel's RF data is delayed by the time-of-flight from each focal point to each element; summed across all 128 channels per focal point. Each focal point's amplitude becomes an image pixel.
- **Plane-wave compounding**: transmit unfocused plane waves at multiple angles; coherently sum the resulting images — high frame rate with diffraction-limited resolution.
- **Synthetic aperture**: transmit from each element individually, receive on all → reconstruct an arbitrary number of focal points per acquisition.

All this is GPU-parallel and runs in real-time on a midrange phone (Snapdragon 8 Gen 2 / Apple A16 class). Higher-end host GPUs unlock advanced reconstruction (adaptive beamforming, sparse aperture compressed sensing, deep-learning beamforming).

**Signal chain.**
```
PZT array (128 elements)
  → Transmit/Receive switch (Texas TX810)
  → Low-noise amp + variable-gain amp (AFE5832 integrated)
  → 14-bit ADC at 40 MSPS × 128 (AFE5832, 8 chips)
  → FPGA (Lattice ECP5) — packetizes raw I/Q
  → USB 3.2 (Cypress FX3 or FT601)
  → Host GPU: beamforming + scan conversion + Doppler
  → Display
```

**Doppler theory.**
- **Color Doppler**: auto-correlation of consecutive RF lines reveals tissue/blood motion → velocity color overlay.
- **PW Doppler**: range-gated single position, FFT of velocity vs. time → spectral display.

**Provenance.** Raw RF I/Q is stored for the duration of any saved clip; reconstruction chain records beamforming algorithm + parameters + GPU model + driver version. Confidence: per-pixel SNR estimate + acoustic shadowing map.

#### Schematic Block Diagram

```
┌────────────────────────────────────────────────────────────────────────┐
│                      NFSIM-US-01 Probe                                  │
│                                                                          │
│   PZT Array Cartridge (128 elem) ◄── interchangeable connector ──┐     │
│                                                                    ▼     │
│   ┌───────────────────────────────────────────────────────────┐        │
│   │  Tx/Rx switches (TX810 ×16, 8 channels each)              │        │
│   └───────────────────────────────────────────────────────────┘        │
│                                  ▲                                       │
│                                  │ ±50V pulses                          │
│                                  │                                       │
│   ┌───────────────────────────────────────────────────────────┐        │
│   │  Pulser ASICs (MAX14808 ×16)                              │        │
│   │  Low-V design (no patented HV CMOS integration)           │        │
│   └───────────────────────────────────────────────────────────┘        │
│                                                                          │
│                                  ▼ receive path                          │
│   ┌───────────────────────────────────────────────────────────┐        │
│   │  TI AFE5832 ×16 (8ch LNA+VGA+14-bit ADC@40 MSPS each)     │        │
│   │  Total: 128 channels                                       │        │
│   └───────────────────────────────────────────────────────────┘        │
│                                  │ LVDS                                  │
│                                  ▼                                       │
│   ┌───────────────────────────────────────────────────────────┐        │
│   │  Lattice ECP5-85F FPGA                                    │        │
│   │  - Per-channel timing/delay generation                    │        │
│   │  - LVDS deserialization                                   │        │
│   │  - I/Q decimation (filter + downsample)                   │        │
│   │  - Packetization for USB 3.2                              │        │
│   └───────────────────────────────────────────────────────────┘        │
│                                  │                                       │
│                                  ▼                                       │
│   ┌───────────────────────────────────────────────────────────┐        │
│   │  Cypress FX3 (USB 3.2 Gen 1, 5 Gbps) — raw I/Q to host   │        │
│   │  Alt: FT601 (cheaper)                                     │        │
│   └───────────────────────────────────────────────────────────┘        │
│                                                                          │
│   nRF52840 BLE ◄── control / metadata / battery                          │
│   Status LEDs + push button                                              │
│                                                                          │
│   Power: 2000 mAh LiPo + USB-C bus power; isolated HV step-up to ±50V   │
└────────────────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary | Alternate | Notes |
|---|---|---|---|
| PZT array (5 MHz, 128 element) | Custom from Imasonic / Vermon | Asian manufacturers | ~$120 per array |
| AFE | TI AFE5832 ×16 ($25 each = $400) | AD9670 ×16 (more $) | 8ch LNA+VGA+ADC integrated |
| HV pulser | MAX14808 ×16 ($6 each = $96) | LM96550 | ±50V symmetric |
| Tx/Rx switch | TX810 ×16 ($4 each = $64) | discrete MOSFET array | High-V isolation |
| FPGA | Lattice ECP5-85F | Xilinx Spartan-7 | Open toolchain available |
| USB 3.2 bridge | Cypress FX3 ($15) | FTDI FT601 ($12) | 5 Gbps |
| BLE | nRF52840-QIAA | nRF5340 | Control/metadata |
| HV boost (±50V) | LT3471 dual boost | TPS61081 + neg charge pump | Low-V design (no HV CMOS) |
| LiPo | 2000 mAh custom | Adafruit 2500 mAh | Wireless ops |
| Connector (cartridge) | Hirose FX12 series 200-pin | Samtec custom | Interchangeable transducer |
| PCB | 8-layer ENIG (impedance-controlled) | 6-layer (if footprint smaller) | High-density |
| Enclosure | CNC aluminum + medical-grade silicone overmold | Injection molded ABS | Ergonomic |

**Total electronics + array:** ~$471 (volume-scaled).

#### Firmware Architecture

**FPGA (Lattice ECP5):**
- LVDS receivers for 16 AFE5832 chips (each emits 8 channels @ 40 MSPS × 14 bits)
- Per-channel programmable delay lines (for transmit beamforming if used)
- Receive data decimation + I/Q demodulation (mixer + low-pass + downsample to ~10 MSPS)
- Packet framing for USB 3.2

**MCU (nRF52840):**
- USB-CDC + BLE control protocol
- Probe state machine (idle / pulsing / streaming)
- Power management (battery, charger, USB PD detection)
- Heater/sensor protection (probe surface temperature monitoring; auto-shutdown if >43°C against skin per IEC 60601)

**Host software (Rust + WebGPU/Vulkan/Metal):**
- USB 3.2 capture (10–500 MB/s raw I/Q)
- Per-frame beamforming on GPU
- Scan conversion (polar → cartesian)
- Doppler processing (autocorrelation + FFT)
- Image display + clip recording
- NFS protocol packet emission per saved clip (with raw I/Q reference + reconstruction params)

**Compute target:** Phone (default), laptop, hub+CON-06. Phone runs reduced beam quality at 30 fps; laptop/CON-06 runs full quality at 60+ fps with advanced reconstruction.
