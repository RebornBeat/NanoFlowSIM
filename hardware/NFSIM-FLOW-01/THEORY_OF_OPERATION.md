#### THEORY_OF_OPERATION.md

**Lensless holographic imaging.** A spatially-coherent light source illuminates a sample close to a bare CMOS sensor. Light scattered by the sample interferes with unscattered light, producing a hologram pattern at the sensor. With a known propagation distance (sample-to-sensor), the original image can be reconstructed by back-propagating the recorded hologram.

**Cell flow + capture.**
- Sample (e.g., diluted blood) flows through 30µm × 100µm PDMS channel at controlled rate
- LED illuminates from above; CMOS sensor records sequence of frames
- Each frame contains diffraction patterns from cells in the field of view
- AI segmentation extracts per-cell hologram patches
- Each patch is back-propagated to recover the cell image
- Classifier (CNN) assigns cell type (WBC differential: neutrophil, lymphocyte, monocyte, eosinophil, basophil; or generic RBC/PLT/WBC counting)

**Why no laser, no lenses.** The interference pattern recorded at the sensor encodes all the information needed for reconstruction. AI handles the back-propagation + denoising. No precise optics required. The flow channel is the only precision component.

**Confidence reporting.** Per-cell classification confidence + per-population count uncertainty (Poisson + classifier uncertainty propagation).

**Variants documented (selectable add-on).**
- **Inertial focusing (Dean flow)**: curved channel exploits inertial migration of cells to a single streamline; better defined cell position; mechanical only (no acoustic). Add-on PCB swaps the simple straight-channel for a curved Dean-flow channel.
- **Acoustic focusing**: piezoelectric standing wave focuses cells to a single line; commercial alternative used by Attune but encumbered for diagnostic flow cytometry by ThermoFisher patents. Available as a documented alternative for non-diagnostic research use.

#### Schematic Block Diagram

```
┌────────────────────────────────────────────────────────────────────┐
│                  NFSIM-FLOW-01 Portable Cytometer                   │
│                                                                      │
│   Sample reservoir + diluter ──► [Syringe pump or peristaltic]     │
│                                              │                       │
│                                              ▼                       │
│   ┌────────────────────────────────────────────────────────┐       │
│   │   PDMS microfluidic chip (replaceable)                  │       │
│   │   - Inlet → 30µm × 100µm channel → outlet               │       │
│   │   - Mounted directly above CMOS sensor                   │       │
│   └────────────────────────────────────────────────────────┘       │
│                                              ▼                       │
│   470 nm coherent LED + 50 µm pinhole                                │
│              │ (spatial filter for coherent illumination)            │
│              ▼                                                       │
│   ┌────────────────────────────────────────────────────────┐       │
│   │   IMX477 12.3 MP CMOS (Pi HQ Camera)                    │       │
│   │   - Records diffraction patterns                         │       │
│   │   - 60 fps capture                                       │       │
│   └────────────────────────────────────────────────────────┘       │
│                                              │ CSI                   │
│                                              ▼                       │
│   ┌────────────────────────────────────────────────────────┐       │
│   │   Raspberry Pi CM4 (or stream to host)                  │       │
│   │   - Frame capture                                        │       │
│   │   - Cell detection (lightweight on-Pi)                   │       │
│   │   - AI reconstruction (offload to CON-06/laptop)         │       │
│   │   - NFS gRPC stream                                      │       │
│   └────────────────────────────────────────────────────────┘       │
│                                                                      │
│   ┌────────────────────────────────────────────────────────┐       │
│   │   STM32G030 (microfluidic + pump control)              │       │
│   │   - Syringe pump stepper (TMC2209)                      │       │
│   │   - Bubble detector (optical photodiode)                │       │
│   │   - Pressure sensor                                     │       │
│   └────────────────────────────────────────────────────────┘       │
│                                                                      │
│   Optional add-on: inertial focusing curved channel                  │
│   Optional add-on: acoustic focusing piezo (with frequency driver)  │
└────────────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary | Alternate | Notes |
|---|---|---|---|
| CMOS sensor | IMX477 (Pi HQ Camera) | IMX219 (cheaper, 8MP) | Bare sensor optimal but Pi HQ also works |
| Coherent LED | 470 nm 1W + 50 µm pinhole | 405 nm UV alternative | Pinhole creates spatial coherence |
| Compute | Pi CM4 (4 GB) | RK3588 SoM | On-board cell detection |
| Microfluidic chip | PDMS replica from SU-8 master | Cyclic olefin polymer COP molded | Replaceable consumable |
| Syringe pump | NEMA8 + TMC2209 + 1 mL syringe | Peristaltic Verderflex | Sample drive |
| Bubble detector | OPT101 + reference LED | IR photodiode pair | Safety + flow monitoring |
| Pressure sensor | BMP581 modified | MS5803-01BA | Flow integrity |
| MCU | STM32G030F6P6 | STM32L0 | Pump + sensor |
| BLE | nRF52840 | nRF52833 | Wireless link |
| Optional acoustic add-on | 1 MHz piezo + Si5351 driver | — | Acoustic focusing variant |
| Optional inertial focusing | Curved-channel PDMS chip | — | Variant chip |
| PCB | 4-layer FR4 | 2-layer for simpler builds | |
| Enclosure | CNC aluminum + light-tight | 3D-printed FDM | Dark chamber for camera |

**Total:** ~$380 reader; consumable chips ~$3 each in volume.

#### Firmware Architecture

**STM32G030 (fluidic control):** syringe pump stepper, bubble detection, pressure feedback, NFS commands over BLE.

**Pi CM4 (camera + on-device pre-processing):** captures frames at 60 fps, runs lightweight cell detection (locate diffraction patterns), packages frame + ROI metadata for upload to compute target.

**Compute target host (CON-06 / laptop):**
- `nfsim-flow-reconstruction` (Rust + GPU)
- Back-propagation reconstruction per cell
- Cell type classification CNN
- Population counting + statistics
- NFS protocol packet emission with provenance: raw frames + reconstruction model + weights hash + per-cell classification confidence
