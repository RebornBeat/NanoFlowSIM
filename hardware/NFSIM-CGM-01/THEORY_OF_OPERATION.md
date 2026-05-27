#### THEORY_OF_OPERATION.md

**Sensing.** Glucose + O₂ + GOx → gluconolactone + H₂O₂. H₂O₂ oxidized at platinum working electrode (700 mV vs. Ag/AgCl reference): H₂O₂ → O₂ + 2H⁺ + 2e⁻. Current proportional to glucose concentration.

**Open membrane stack.** Outer polyurethane (selective for glucose vs. interfering substances) + interfacial layer + Nafion (cation-exchange, excludes negatively-charged ascorbate/urate interferences) + GOx immobilized in cross-linked BSA + glutaraldehyde. All reagents open-source-grade, available from Sigma-Aldrich, Worthington Biochemical, Fluka.

**Drift correction.** Real-world sensor sensitivity decreases over wear: GOx denatures, membrane biofouling, tissue inflammatory response. The drift model is a Bayesian Kalman filter:

```
state x_t = [glucose_true, sensitivity_t, offset_t]
observation y_t = sensitivity_t * glucose_true + offset_t + noise_t

dynamics:
  glucose_true: random walk per glycemic dynamics
  sensitivity_t: slow exponential decay with day + temperature dependence
  offset_t: small random walk

correction inputs:
  optional fingerstick reference (high-confidence anchor)
  meal annotation (helps prior on glucose dynamics)
  exercise annotation
  user demographics (age, BMI, history)
```

**Confidence reporting.** Each glucose reading emits: `value`, `confidence_interval_low`, `confidence_interval_high` (95% CI from Kalman filter posterior). UI shows error bars on glucose graph; large CI shaded.

**Model card.** Shipped with every sensor: training data sources, performance metrics (MARD vs. age of sensor, MARD vs. glucose range), known limitations (poor performance with high acetaminophen doses, severe dehydration), version, weights hash.

#### Schematic Block Diagram

```
┌────────────────────────────────────────────────────────────┐
│            NFSIM-CGM-01 Subcutaneous Sensor                 │
│                                                              │
│   Platinum WE wire (subcutaneous, GOx-coated)              │
│         ↓                                                    │
│   Ag/AgCl reference (skin-surface or subcutaneous)         │
│         ↓                                                    │
│   ┌──────────────────────────┐                              │
│   │  LMP91000 potentiostat   │  3-electrode amperometric  │
│   │  + 700 mV bias            │                              │
│   └──────────────────────────┘                              │
│         ↓ I2C                                                │
│   ┌──────────────────────────┐                              │
│   │ nRF52805 (BLE + MCU)     │  smallest available BLE SoC │
│   │  - Sample current 1/min  │                              │
│   │  - Apply drift model     │  TFLite Micro 12 KB         │
│   │  - BLE advertise         │                              │
│   └──────────────────────────┘                              │
│                                                              │
│   Power: CR1632 + TPS61240 boost; LDO 1.8V for MCU         │
│   Skin-side adhesive: 3M 1585N or Tegaderm-equivalent      │
│                                                              │
└────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary | Alternate | Notes |
|---|---|---|---|
| nRF52805-CAAA | (small BLE SoC) | nRF52810 | Smallest nRF |
| Potentiostat | LMP91000 | MAX30134 | 3-electrode amperometric |
| Pt wire 75 µm | Sigma-Aldrich Pt 99.99% | Alfa Aesar | WE substrate |
| Ag wire 50 µm | Sigma 99.99% | Alfa Aesar | Reference |
| Glucose oxidase | Worthington GOXC | Sigma G7141 | EC 1.1.3.4 |
| BSA cross-link | Sigma A2153 + 25% glutaraldehyde | Sigma A4503 | Enzyme matrix |
| Nafion | Sigma 274704 (5 wt%) | DuPont DE521 | Cation-selective |
| Polyurethane | Lubrizol Tecoflex | Bayer Carbothane | Outer membrane |
| Insertion needle | 30G stainless | 27G alt | One-shot inserter |
| Adhesive patch | 3M 1585N | Tegaderm 3M 1626 | Skin contact |
| Battery | CR1632 lithium coin | CR2032 (larger) | Single-use |
| Boost converter | TPS61240 | LM2776 charge pump | 1.8/3.3V from coin |
| Enclosure | Custom medical TPE overmold | Injection-molded ABS | USP Class VI |

**Total:** ~$38 per sensor at low volume; ~$15 in 100k+ volumes.

#### Firmware Architecture

**MCU:** nRF52805 (smallest nRF BLE SoC for wearable size).

**Tasks:**
- **SamplingTask** (1 min interval): wakes from sleep, applies 700 mV bias via LMP91000, samples current after 10s stabilization, returns to sleep.
- **DriftModelTask** (1 min interval): runs Bayesian Kalman filter update (~12 KB TFLite Micro model on nRF52 with CMSIS-NN); emits corrected glucose value + 95% CI.
- **BLETask** (event-driven): advertises latest reading + CI + sensor age + drift model confidence; allows reader app to subscribe to live updates.
- **PowerTask**: targets <50 µA average (BLE advertising every 1 min, sampling every 1 min, deep sleep otherwise).

**NFS protocol:** every measurement is a NFS packet with provenance: `raw_signal_ref` = current trace (stored locally, uploaded on connection), `reconstruction_chain` = drift model + weights hash + version, `confidence` = 95% CI width.
