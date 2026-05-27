#### THEORY_OF_OPERATION.md

**Magnet.** Halbach array of NdFeB (N52 grade) magnets arranged so the magnetic field is concentrated on one side and canceled on the other. Field is in the bore direction. ~50 mT achievable with passive permanent magnets at this scale.

**Imaging physics.** RF pulse at the Larmor frequency (γB₀ = 2.1 MHz at 50 mT for 1H) tips proton magnetization; relaxation produces signal detected by receive coil. Gradients spatially encode the signal. K-space sampled; reconstructed via FFT (classical) + AI denoiser (FastMRI).

**Low-field trade-offs.** SNR scales with B₀^7/4 (approximately). 50 mT has ~30× lower SNR than 1.5T. **AI reconstruction compensates**: FastMRI models learn to denoise + super-resolve low-field images using high-field training data.

**Reconstruction chain.**
```
raw k-space (preserved)
  → density compensation
  → FFT initial image (low quality)
  → FastMRI U-Net super-resolution (open weights)
  → optional: deep iterative refinement (compressed sensing prior)
  → per-voxel uncertainty map (Bayesian NN output)
  → DICOM with confidence overlay metadata
```

**Confidence reporting.** Per-voxel uncertainty heatmap from Bayesian U-Net dropout sampling. UI shades high-uncertainty regions. Professional Mode shows "raw FFT vs. AI reconstructed" toggle.

**Clinical positioning.** Low-field MRI is excellent for: hydrocephalus monitoring in infants, stroke triage, large MS lesions, knee meniscus tears. It is NOT appropriate as a sole diagnostic for: small brain metastases, subtle hippocampal atrophy, fine cartilage defects. The UI displays clinical applicability per region.

#### Schematic Block Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                       NFSIM-MRI-01 System                            │
│                                                                       │
│   ┌─────────────────────────┐                                        │
│   │ Halbach NdFeB Array     │  50 mT @ isocenter                    │
│   │  - Outer ring N52        │                                        │
│   │  - Inner shim ring       │                                        │
│   │  - Passive shimming      │  Mech precision: 50 µm placement     │
│   └─────────────────────────┘                                        │
│                                                                       │
│   ┌─────────────────────────┐                                        │
│   │ Gradient coils (X/Y/Z)  │  100 mT/m peak, water-cooled         │
│   └─────────────────────────┘                                        │
│              ▲                                                        │
│              │                                                        │
│   ┌─────────────────────────┐                                        │
│   │ Gradient drivers (3×)   │  ±40V, 50A each, full-bridge class-D │
│   │ (custom or HiTechTrader)│                                        │
│   └─────────────────────────┘                                        │
│              ▲                                                        │
│              │                                                        │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │ MaRCoS console (Red Pitaya STEMlab 125-14 SDR)              │   │
│   │  - DDS for RF generation (2.1 MHz)                          │   │
│   │  - Gradient waveform generation                              │   │
│   │  - RF receive ADC (125 MS/s, 14-bit)                        │   │
│   │  - SCPI-style command interface to host                      │   │
│   └─────────────────────────────────────────────────────────────┘   │
│              ▲                                                        │
│              │                                                        │
│   ┌─────────────────────────┐                                        │
│   │ RF Tx amplifier (100W)  │  Class-D push-pull, 2.1 MHz CF       │
│   │ RF Tx/Rx switch         │  PIN-diode + low-loss path           │
│   │ RF preamp + LNA          │  <0.5 dB NF                          │
│   └─────────────────────────┘                                        │
│              ▲                                                        │
│              │                                                        │
│   ┌─────────────────────────┐                                        │
│   │ Tx/Rx coil (birdcage     │  Application-specific (head, knee)  │
│   │ or solenoid)             │                                        │
│   └─────────────────────────┘                                        │
│                                                                       │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │ Host: CON-06 Edge Compute Module (Jetson Orin Nano)         │   │
│   │  - nfsim-mri-reconstruction (Rust + ONNX Runtime + BART)    │   │
│   │  - FastMRI U-Net (open weights)                              │   │
│   │  - Per-voxel uncertainty (Bayesian dropout)                  │   │
│   │  - DICOM output                                              │   │
│   │  - Patient body map integration                              │   │
│   └─────────────────────────────────────────────────────────────┘   │
│                                                                       │
│   Power: AC mains → 12V/24V/48V rails for amps; gradient water cool │
└─────────────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary | Alternate | Notes |
|---|---|---|---|
| NdFeB magnets (N52) | Bulk bricks from K&J Magnetics | China supplier (cheaper, verify grade) | ~$1,500 |
| Halbach assembly fixturing | Custom CNC aluminum | 3D-printed jigs (less precise) | $400 |
| Gradient coil wire | 22 AWG enamel copper, ~500 m | Custom water-cooled hollow wire | $200 |
| Gradient amplifiers ×3 | HiTechTrader surplus or custom class-D | Apex MP108 (commercial) | $600 each surplus or $1500 custom — bom assumes surplus |
| MaRCoS console (Red Pitaya) | STEMlab 125-14 | STEMlab 16ch (more $) | $450 |
| RF amp 100W | Custom class-D (PA0FRI design) or RF Concepts | $400 |
| RF Tx/Rx switch | PIN diode network | RF relay (slower switching) | $50 |
| RF preamp | DXE-RPA-2 or custom LNA | MiniCircuits ZFL-500HLN | $80 |
| RF coil | Custom birdcage (head) + saddle (knee) | Surplus 1.5T coils retuned | $200 |
| Mechanical frame | Welded aluminum + casters | Bosch Rexroth aluminum extrusion | $400 |
| Patient table | CNC aluminum + foam padding | Adjustable hospital table modification | $300 |
| Water cooling | 12V pump + radiator + 5L reservoir | Aquarium pump (simpler) | $80 |
| CON-06 Edge Compute (Orin Nano) | NVIDIA Jetson Orin Nano dev kit | RK3588 (cheaper, lower perf) | $500 |
| Display | 24" 1440p touch monitor | 22" 1080p | $300 |
| RF shielded room (optional but recommended) | Aluminum mesh enclosure | Faraday-tent in clinical setting | $400 |

**Total:** ~$4,520 (without optional RF shielded room).

#### Firmware Architecture

**MaRCoS firmware (FPGA + ARM on Red Pitaya):**
- Open-source MaRCoS project: pulse sequence engine, DDS, gradient waveform synthesis, RF receive ADC
- SCPI-style command interface to host

**Host software stack (CON-06 / laptop):**
- `nfsim-mri-sequencer` — pulse sequence library (FLASH, GRE, SE, RARE, DWI)
- `nfsim-mri-acquisition` — k-space capture and storage (raw_signal_ref preserved)
- `nfsim-mri-reconstruction` — BART for classical recon + ONNX FastMRI U-Net for AI super-resolution + Bayesian uncertainty
- `nfsim-mri-viewer` — DICOM viewer with confidence overlay + raw-vs-reconstructed toggle
- `nfsim-mri-protocol-library` — pre-validated sequences per region (brain T2, knee PD-fat-sat, infant T1)

**NFS protocol:** every saved series emits an NFS packet with full provenance: raw k-space path, sequence parameters, reconstruction chain (model + weights hash), confidence summary.
