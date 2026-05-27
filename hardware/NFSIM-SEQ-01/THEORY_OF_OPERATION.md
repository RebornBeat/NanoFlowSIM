#### THEORY_OF_OPERATION.md

**Why wild-type Aerolysin.** Aerolysin is a bacterial toxin that self-assembles into a heptameric β-barrel pore in lipid membranes. Its hourglass geometry — with a constriction of ~1 nm at the trans side — gives it excellent single-base discrimination in published academic work. It is wild-type (no engineering), widely cited in the academic nanopore literature (Cao et al., Maglia group), and not encumbered by ONT patents on CsgG.

**Why MspA wild-type.** Mycobacterium smegmatis Porin A is a naturally narrow porin used in academic nanopore sequencing for over a decade. Octameric, ~1.2 nm constriction. Available from academic labs (Niederweis group constructs) and reproducible in standard E. coli expression.

**Why Phi29 wild-type.** Phi29 DNA polymerase is a φ29 bacteriophage replication enzyme with strong strand-displacement and processivity. It binds DNA and translocates it at a controllable rate. Wild-type Phi29 is sold openly by NEB (M0269S) and is the historical workhorse of nanopore research before ONT's proprietary helicases became dominant.

**Why voltage feedback.** ONT controls translocation speed primarily via engineered motor proteins. NanoFlowSIM uses a software feedback loop: when the ionic current signature indicates translocation is occurring too fast (event duration < target), the applied voltage is dynamically reduced for that channel, slowing the translocation. This is a published technique and reduces dependence on any specific motor protein.

**Signal chain.**
```
DNA + motor (cis chamber)
  → enters pore under applied bias
  → translocates one base at a time
  → modulates ionic current (each k-mer signature)
  → analog TIA (OPA637, 100 MΩ feedback)
  → 4-pole Bessel anti-alias 5 kHz
  → 16/24-bit ADC at 25 kHz
  → FPGA event segmentation
  → USB 3.0 to host
  → community-trained Bonito basecaller (CRNN + CTC)
  → FASTQ + per-base Phred
  → minimap2 alignment
  → variant calling (medaka / PEPPER-DeepVariant / Clair3)
```

**Provenance and raw signal.** Every read's raw squiggle is preserved as pod5 format. The reconstruction chain records: basecaller model identity + weights hash, alignment tool + reference, variant caller. Users can re-basecall raw squiggles with future improved models.

**Confidence reporting.** Per-base Phred quality, plus a per-read summary mean Q-score. The patient body map UI shades low-confidence regions of any reported variant.

#### Schematic Block Diagram

```
┌──────────────────────────────────────────────────────────────────────┐
│                 NFSIM-SEQ-01 Patch Clamp Amplifier                    │
│                                                                        │
│   Flow Cell ────► Ag/AgCl trans electrode ──► Reference (gnd)        │
│   Flow Cell ────► Ag/AgCl cis electrode  ──┐                         │
│                                              ▼                         │
│                              ┌──────────────────────────────┐         │
│                              │ Headstage (Rogers 4350B PCB) │         │
│                              │                                │         │
│                              │  Guard ring ─┐                 │         │
│                              │              ▼                 │         │
│                              │  ┌────────────────────┐        │         │
│                              │  │ OPA637 (input op)  │ ──► TIA│         │
│                              │  │ Rf = 100 MΩ        │        │         │
│                              │  │ Cf = 0.1 pF        │        │         │
│                              │  └────────────────────┘        │         │
│                              └──────────────┬────────────────┘         │
│                                              │ voltage out (1pA → 100µV)│
│                                              ▼                         │
│                              ┌──────────────────────────────┐         │
│                              │ 4-pole Bessel LPF, 5 kHz     │         │
│                              │ (cascaded Sallen-Key, OPA2134)│         │
│                              └──────────────┬────────────────┘         │
│                                              ▼                         │
│                              ┌──────────────────────────────┐         │
│                              │ ADS1256 24-bit ADC @ 25 kSPS │         │
│                              │ (or AD7177 32-bit for low noise)│       │
│                              └──────────────┬────────────────┘         │
│                                              │ SPI                     │
│                                              ▼                         │
│                              ┌──────────────────────────────┐         │
│                              │ Lattice iCE40HX8K FPGA       │         │
│                              │ (Open toolchain: yosys+nextpnr)│       │
│                              │  - Event detection            │         │
│                              │  - Voltage feedback control   │         │
│                              │  - USB 3.0 framing            │         │
│                              └──────────────┬────────────────┘         │
│                                              ▼                         │
│                              ┌──────────────────────────────┐         │
│                              │ FT232H USB FIFO bridge       │         │
│                              │ (40 Mbps to host)             │         │
│                              └──────────────┬────────────────┘         │
│                                              ▼                         │
│                                          USB 3.0 to host               │
│                                                                        │
│   Voltage clamp DAC:                                                   │
│   ┌──────────────────────┐                                            │
│   │ AD5791 20-bit DAC    │ ──► trans electrode (sets sequencing V)   │
│   │ ±10V output           │                                            │
│   └──────────────────────┘                                            │
│                                                                        │
│   Faraday shield: aluminum enclosure, grounded                         │
│   Temperature control: Peltier base plate, 18–40°C ±0.1°C              │
└──────────────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary part | Alternate | Notes |
|---|---|---|---|
| Input op-amp (headstage) | OPA637 | LMP7721 | Ultra-low bias current, FET input |
| Feedback resistor | 100 MΩ Vishay precision | Ohmite HVR | 0.1% tolerance critical |
| Filter op-amp | OPA2134 ×2 | OPA1612 | Low noise, audio-grade |
| Voltage clamp DAC | AD5791BRUZ | AD5760 | 20-bit ±10V |
| ADC | ADS1256IDBT | AD7177-2 | 24-bit for ADS1256, 32-bit for AD7177 |
| FPGA | Lattice iCE40HX8K eval board | Digilent Cmod A7 (Artix-7) | Open toolchain for iCE40 |
| USB bridge | FT232H (or FT601Q for USB 3.0) | Cypress FX3 | High-speed serial |
| Headstage PCB | Rogers 4350B 2-layer | Rogers 4003 | Low dielectric loss for pA measurement |
| Aluminum Faraday shield | Custom CNC | Hammond enclosure modified | Grounded shielding |
| Flow cell body | Polycarbonate CNC | 3D-printed Form 3+ Clear V4 | 2-chamber design |
| PTFE film 25 µm | Saint-Gobain Teflon film | Goodfellow PTFE | Membrane aperture base |
| Ag wire 0.5mm | Sigma 99.99% pure | Alfa Aesar | For Ag/AgCl electrodes |
| Peltier (temp control) | TEC1-12706 | Peltier 20W | Base plate cooling/heating |
| Reagents (per kit) | α-HL: Sigma H9395 (or Aerolysin from academic) + DPhPC: Avanti 850356C + Phi29: NEB M0269S | — | Wetware, ~$250 per starter kit |

#### Firmware Architecture

**FPGA logic (iCE40HX8K):**
- SPI master for ADC at 25 kHz sample rate
- Voltage clamp DAC driver
- Real-time event detection (threshold + hysteresis + minimum dwell time)
- Voltage feedback control loop (1 kHz update rate)
- USB 3.0 framing for high-throughput data

**MCU firmware (none — FPGA-only data path):** the device is "headless" from the user's perspective. Configuration and monitoring happen via the host laptop (or CON-06) over USB.

**Host software (Python or Rust):**
- `nfsim-seq-client` — opens USB connection, streams raw squiggles to disk
- `nfsim-basecaller` — Bonito-architecture CRNN basecaller, trained on community wild-type pore datasets
- `nfsim-alignment` — minimap2 wrapper
- `nfsim-variant` — medaka / PEPPER-DeepVariant integration
- NFS protocol packets emitted for each completed read

**Compute target:** primarily **laptop** (PyTorch + CUDA) or **CON-06 Edge Compute Module** (Jetson Orin Nano with CUDA, or RK3588 with OpenCL). Phone is not a supported target for full basecalling (too compute-intensive).
