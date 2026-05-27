# NanoFlowSIM

**Integrated Precision Medicine Platform — Open-Source Portable Biosensing Ecosystem + Multi-Layered Nanoparticle Simulation + Living Patient Body Map**

> *Every measurement. Every modality. Every moment. One platform.*

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Three Pillars of NanoFlowSIM](#2-three-pillars-of-nanoflowsim)
3. [Simulation Framework](#3-simulation-framework)
4. [Patient Data Architecture & Living Body Map](#4-patient-data-architecture--living-body-map)
5. [UI/UX Specification — Consumer & Professional](#5-uiux-specification--consumer--professional)
6. [Data Integration — Full Loop (Current + Future)](#6-data-integration--full-loop-current--future)
7. [Biological Sensing Domain Encyclopedia](#7-biological-sensing-domain-encyclopedia)
8. [Open-Source Hardware Ecosystem — All Devices](#8-open-source-hardware-ecosystem--all-devices)
   - [Domain A: Molecular / Genomic](#domain-a-molecular--genomic)
   - [Domain B: Structural / Anatomical Imaging](#domain-b-structural--anatomical-imaging)
   - [Domain C: Chemical / Metabolic](#domain-c-chemical--metabolic)
   - [Domain D: Electrical / Bioelectric](#domain-d-electrical--bioelectric)
   - [Domain E: Ingestible / Traversing Capsules](#domain-e-ingestible--traversing-capsules)
   - [Domain F: Flow Cytometry & Environmental](#domain-f-flow-cytometry--environmental)
9. [Universal NFS Communication Protocol](#9-universal-nfs-communication-protocol)
10. [Firmware Architecture (Universal)](#10-firmware-architecture-universal)
11. [Software Stack](#11-software-stack)
12. [Monorepo Structure](#12-monorepo-structure)
13. [Production, Manufacturing & Quality](#13-production-manufacturing--quality)
14. [Regulatory & Legal](#14-regulatory--legal)
15. [Roadmap](#15-roadmap)
16. [License](#16-license)

---

## 1. Project Overview

NanoFlowSIM is a three-pillar precision medicine ecosystem built on the principle that every layer of biological information — structural, electrical, chemical, molecular, genomic — should be simultaneously accessible, open-source, portable, continuously monitored, and unified into a single living model of the patient.

### The Problem NanoFlowSIM Solves

Modern medicine is fragmented across institutional silos:

| Domain | Typical Siloed System |
|---|---|
| Structural imaging | Hospital radiology department |
| ECG / cardiac | Cardiology clinic |
| Genomics / SNPs | Specialized genetics lab |
| Continuous glucose | Endocrinology/diabetes care |
| Blood chemistry | Clinical laboratory |
| Neural signals | Neurology |
| Nanoparticle therapy design | Research institution |

No single system integrates all of these into a continuous, patient-owned, portable, open-source platform.

NanoFlowSIM changes this entirely.

### What NanoFlowSIM Is

A unified open-source ecosystem comprising:

**Pillar 1 — Simulation Engine:** A Rust-based nanoparticle behavior simulation framework that models therapeutic delivery at molecular, cellular, tissue, and systemic levels, integrating patient-specific genomic, proteomic, and physiological data.

**Pillar 2 — Living Patient Body Map:** A personal health data platform where every data point from every sensing modality maps to an anatomical region of a 3D human body model. Historical, episodic, and live continuous data all coexist on the same model. The patient owns their data entirely.

**Pillar 3 — Open-Source Portable Hardware Ecosystem:** 30+ portable, open-hardware biosensing devices spanning all biological sensing domains — designed to be built from KiCad schematics, assembled from JLCPCB-compatible BOMs, flashed with open firmware, and operated with open software that natively integrates into the NanoFlowSIM platform.

---

## 2. Three Pillars of NanoFlowSIM

### Pillar 1: Simulation Engine

The NanoFlowSIM simulation engine is a Rust workspace that models nanoparticle therapeutics across four computational layers:

- **Molecular Layer:** Receptor-ligand binding kinetics, CRISPR guide RNA efficiency modeling, payload encapsulation stability under pH/enzymatic conditions, ligand density optimization
- **Cellular Layer:** Endocytosis modeling, endosomal escape probability, intracellular trafficking, payload release kinetics, gene editing efficiency, off-target risk scoring
- **Tissue Layer:** Tissue permeability modeling (EPR effect, vascular extravasation), immune cell infiltration, tumor microenvironment modeling, tissue heterogeneity mapping
- **Systemic Layer:** Bloodstream circulation time prediction, immune clearance modeling (mononuclear phagocyte system), organ distribution, pharmacokinetics

**Key simulation capabilities:**

- Multi-therapy hybrid simulation (CRISPR + chemotherapy + immunotherapy in simultaneous configuration)
- Automated therapy combination screening with ML-ranked output
- Back-testing against clinical trial data and patient outcomes
- Patient-specific customization driven by genomic, proteomic, and imaging input
- Nanoparticle design parameter sweep (size, shape, surface chemistry, payload type)
- Blood-brain barrier crossing simulation
- Pathogen reservoir targeting (HIV latent reservoirs, herpesvirus neural latency)

### Pillar 2: Living Patient Body Map

A persistent, patient-owned health record system that anchors every data point to an anatomical region using the UBERON ontology (Uber Anatomy Ontology — a cross-species anatomical reference).

The body map exists at five levels of resolution:

| Level | Description | Data Required |
|---|---|---|
| 0 | Generic anatomical mesh | None |
| 1 | Anthropometric-matched mesh | Height, weight, age, sex |
| 2 | Imaging-derived patient mesh | DICOM CT/MRI segmentation |
| 3 | Functional overlay | Live sensor streams active |
| 4 | Molecular overlay | Genomic variants, cfDNA, nanoparticle trajectories |

### Pillar 3: Hardware Ecosystem

30+ open-source portable biosensing devices across six sensing domains. Each device:

- Runs open firmware (C/C++ or Rust, FreeRTOS or Zephyr)
- Communicates via the NFS universal protocol (BLE 5.0 GATT + USB-C + JSON)
- Tags all data with UBERON anatomical codes
- Integrates directly with NanoFlowSIM desktop, mobile, and web clients
- Is reproducible from KiCad source files via JLCPCB or equivalent PCB fab

---

## 3. Simulation Framework

### Architecture

```
nanoflowsim-simulation/        (Rust workspace)
├── nfsim-core/                 Shared types, physics constants, UBERON codes
├── nfsim-molecular/            Ligand-receptor kinetics, CRISPR modeling
├── nfsim-cellular/             Endocytosis, trafficking, release models
├── nfsim-tissue/               Permeability, immune, heterogeneity
├── nfsim-systemic/             PK/PD, circulation, clearance
├── nfsim-ml/                   Therapy combination ranking, prediction
├── nfsim-backtesting/          Clinical data comparison, validation
├── nfsim-visualization/        3D trajectory output, heatmap generation
├── nfsim-grpc/                 gRPC API for frontend communication
└── nfsim-cli/                  Command-line simulation runner
```

### Molecular Layer — Core Models

**Receptor-Ligand Binding Kinetics**

Uses a stochastic Gillespie algorithm to model:
- Association rate constant (k_on): ligand-receptor binding events
- Dissociation rate constant (k_off): unbinding probability
- Effective affinity (K_D = k_off / k_on)
- Surface density effects (multivalent binding cooperativity)
- Receptor internalization following binding

Key parameters:
```toml
[ligand_config]
ligand_type = "anti-HER2 antibody fragment"
density_per_nm2 = 0.15
k_on_M_per_s = 1.2e5
k_off_per_s = 1.1e-4
receptor_expression_level = "high"  # from patient proteomic data
```

**CRISPR Activation Modeling**

Models CRISPR-Cas9 / CRISPR-Cas12a / CRISPR-Cas13 delivery and activity:
- Guide RNA binding efficiency at target locus (based on GC content, secondary structure)
- Off-target site scoring (using patient genome VCF input)
- Cas protein expression timeline post-delivery
- Gene editing efficiency distribution (probabilistic)
- Immune recognition probability of Cas protein

**Payload Encapsulation Stability**

Simulates payload retention under physiological conditions:
- pH-triggered release (lysosomal pH ~4.5–5.0)
- Enzymatic cleavage release (cathepsin B, matrix metalloproteinases)
- Temperature-responsive release
- Oxidative stress-triggered release
- Payload degradation rate under each condition

### Cellular Layer — Core Models

**Endocytosis Model**

Pathway probabilities depending on nanoparticle size and surface:
- Clathrin-mediated endocytosis: optimal for 120–200 nm, positively charged
- Caveolae-mediated: 60–80 nm
- Macropinocytosis: >500 nm or fluid-phase uptake
- Direct membrane penetration: <10 nm, cell-penetrating peptides

**Endosomal Escape Model**

Critical bottleneck for therapeutic delivery:
- Proton sponge effect (polyethylenimine, chloroquine analogs)
- Membrane destabilization probability at pH 4.5–5.5
- Fusogenic lipid activation timing
- Payload release fraction following escape

**Intracellular Distribution**

Tracks payload after endosomal escape:
- Nuclear localization signal (NLS) efficiency for gene therapy payloads
- Cytoplasmic retention probability
- Organelle-specific delivery (mitochondria, ER) for specialized therapeutics

### Tissue Layer — Core Models

**Enhanced Permeability and Retention (EPR) Effect**

Models nanoparticle accumulation in tumor tissue:
- Vascular pore size distribution (tumor-specific, patient-derived from imaging)
- Interstitial fluid pressure modeling (barrier to delivery)
- Lymphatic drainage deficiency in tumors
- Active targeting contribution vs. passive EPR

**Tissue Permeability Matrix**

```
tissue_type: liver, tumor, muscle, brain, lymph_node, bone_marrow
properties:
  vascular_pore_size_nm: [10-100]
  blood_flow_ml_per_g_per_min: [tissue-specific]
  interstitial_pH: [6.5-7.4]
  immune_cell_density: [cells/mm3]
  matrix_density: [g/cm3]
```

**Blood-Brain Barrier Model**

Specialized model for CNS drug delivery:
- Tight junction permeability modeling
- Receptor-mediated transcytosis pathways (transferrin receptor, LRP1)
- Efflux pump expression (P-glycoprotein)
- Surface modifications that enhance BBB crossing

### Systemic Layer — Core Models

**Pharmacokinetic Model**

Two-compartment PK model:
- Central compartment: blood plasma
- Peripheral compartment: tissue distribution
- Clearance: hepatic (kupffer cell uptake), renal (size-dependent filtration)
- Half-life calculation based on surface modification (PEGylation, zwitterionic coating)

**Immune Clearance Model**

Mononuclear phagocyte system (MPS) modeling:
- Opsonization probability (IgG, complement protein adsorption)
- Kupffer cell uptake rate (liver)
- Splenic filtration (rigid particles >200 nm)
- Pre-existing anti-PEG antibody effect (patient-specific)
- Protein corona formation kinetics

### Machine Learning Integration

**Therapy Combination Ranking**

Input: patient genomic profile + tumor transcriptomics + current drug panel
Output: ranked list of therapy combinations with predicted efficacy scores

Model architecture:
- Gradient-boosted tree ensemble (XGBoost base) for tabular patient features
- Ordinal output with confidence intervals
- Trained on aggregated clinical trial outcomes + published literature
- Continuously updated as new validation data enters platform

**Nanoparticle Design Optimizer**

Bayesian optimization loop over:
- Size (10–500 nm)
- Surface charge (zeta potential)
- Ligand type and density
- Payload type and loading efficiency
- Surface coating chemistry

Objective: maximize targeting efficiency while minimizing immune clearance and off-target toxicity.

### Back-Testing System

When clinical outcome data is available:
1. Load simulation parameters that produced a historical treatment plan
2. Re-run simulation with same inputs
3. Compare predicted vs. actual outcomes
4. Automatically adjust model parameters to reduce prediction error
5. Update model weights in production pipeline

---

## 4. Patient Data Architecture & Living Body Map

### Core Design Philosophy

Every piece of biological data a person generates — from a one-time genome sequencing to a continuous 14-day ECG patch to a single hospital visit CBC — attaches to an anatomical region of their 3D body model.

The body is the universal anchor. Not folders. Not tables. Not departments.

When a user clicks on their heart in the 3D view, they see:
- Historical ECG recordings (episodic)
- Continuous ECG patch data (if active)
- Blood biomarkers relevant to cardiac function (troponin, BNP, cholesterol)
- Genomic variants associated with cardiac risk (BRCA, LQTS genes, etc.)
- Any nanoparticle simulation runs that targeted cardiac tissue
- Ultrasound/imaging data of the heart (if uploaded)
- Medication history affecting cardiac function

### UBERON Anatomical Tagging System

All data is tagged with UBERON ontology codes. Examples:

| UBERON Code | Anatomical Region | Relevant Data Types |
|---|---|---|
| UBERON:0000948 | Heart | ECG, cardiac enzymes, echo, coronary imaging |
| UBERON:0002048 | Lung | SpO2, spirometry, chest X-ray, breath analysis |
| UBERON:0002107 | Liver | LFTs, hepatic imaging, drug metabolism SNPs |
| UBERON:0001987 | Placenta | Maternal-fetal monitoring (pregnancy mode) |
| UBERON:0001017 | Central nervous system | EEG, MRI brain, cognitive markers |
| UBERON:0002113 | Kidney | Creatinine, GFR, renal imaging |
| UBERON:0000178 | Blood | CBC, metabolic panels, cfDNA, SNPs |
| UBERON:0001416 | Skin | Temperature, sweat sensors, dermatology imaging |
| UBERON:0004537 | Bloodstream (systemic) | Default anchor for lab values without organ specificity |

**Systemic/Blood Data Anchoring Logic:**

Lab values that don't map cleanly to one organ (e.g., cholesterol, HbA1c, inflammatory markers) are:
1. Anchored to bloodstream overlay by default (UBERON:0004537)
2. AI suggests a primary organ anchor based on clinical context
3. User can override and assign additional region tags
4. The data displays in both the bloodstream view AND the suggested organ view

### Data Model

```
PatientProfile {
  patient_id: UUID (patient-generated, locally derived)
  created_at: ISO8601
  anthropometrics: { height_cm, weight_kg, age, biological_sex, ethnicity }
  body_map_level: 0..4

  DataRecord[] {
    record_id: UUID
    timestamp: ISO8601
    source_device: DeviceID | "manual_entry" | "hospital_import" | "wearable_sync"
    data_type: enum DataType
    uberon_primary: UBERON code
    uberon_secondary: [UBERON codes]  // multi-region data
    is_continuous: bool
    continuous_session_id: UUID | null
    raw_data: JSON | binary blob
    processed_data: JSON
    quality_score: 0.0..1.0
    notes: string
    attachments: [FileRef]
    simulation_linked: [SimulationRunID]
  }

  ActiveSessions[] {
    session_id: UUID
    device_id: DeviceID
    started_at: ISO8601
    data_type: DataType
    sampling_rate_hz: f32
    uberon_region: UBERON code
    stream_endpoint: WebSocket URL | BLE characteristic UUID
  }

  SimulationRuns[] {
    run_id: UUID
    created_at: ISO8601
    nanoparticle_config: JSON
    therapy_config: JSON
    patient_data_snapshot_id: UUID
    results: SimulationResults
    status: Queued | Running | Complete | Failed
  }
}
```

### Data Storage Architecture

**Client-side (local-first):**
- SQLite database (desktop: Electron + better-sqlite3, mobile: expo-sqlite)
- MinIO-compatible local object storage for binary data (DICOM, FASTQ, FCS)
- Encrypted at rest using platform keychain
- Full offline capability for all core features

**Sync architecture:**
- Optional cloud sync to patient-controlled server
- Self-hosted option: Docker compose (Django + PostgreSQL + MinIO + Redis)
- Federated option: DID-based identity, BitTorrent-style data seeding
- FHIR R4 compliant data exchange for hospital integrations
- End-to-end encrypted when syncing

**Hospital Record Integration:**
- FHIR R4 REST API client
- HL7 v2 parser for legacy hospital exports
- DICOM receiver for imaging imports
- PDF parser (AI-assisted) for scanned records
- Direct integration hooks for Epic, Cerner, Allscripts via FHIR

---

## 5. UI/UX Specification — Consumer & Professional

### Design Principles

1. **The body is the interface.** Not menus. Not categories. The 3D human body is the primary navigation element.
2. **Data capture first, AI second.** Every feature that captures data takes visual priority over AI insights.
3. **Two modes, same data.** Consumer view and Professional view show identical underlying data with different visualization depth.
4. **Live and historical coexist.** Active sensor streams glow/pulse in real-time. Historical data is always accessible by scrubbing a timeline. Both views are always simultaneously available.
5. **Click to add, click to view.** Any region of the body can be clicked to see existing data OR to add new data. Empty regions invite data entry.

### The 3D Body Map Interface

**Rendering:** Three.js scene (desktop/web) or ARKit/ARCore scene (mobile). Two mesh variants:
- Male reference mesh (SMPL model or equivalent open-source anatomical mesh)
- Female reference mesh
- Pregnancy overlay mode (maternity variant)
- Pediatric scaling mode

**Layer System (toggleable):**

```
Layer 0: Surface skin mesh (external anatomy)
Layer 1: Skeletal mesh (bones, joints)
Layer 2: Vascular mesh (major arteries, veins, heart)
Layer 3: Organ mesh (liver, lungs, kidneys, brain, stomach, etc.)
Layer 4: Neural overlay (brain, spinal cord, peripheral nerves)
Layer 5: Lymphatic overlay
Layer 6: Data heatmap overlay (sensor data visualized as colored regions)
Layer 7: Nanoparticle trajectory overlay (simulation output)
Layer 8: Genomic variant overlay (regions with known variants highlighted)
```

**Interaction Model:**

- **Hover:** Region label appears, data count badge shows (e.g., "Heart — 47 records")
- **Click:** Side panel opens with region detail view
- **Long press / right click:** Context menu — "Add data", "View history", "Run simulation here", "Export region data"
- **Pinch/zoom:** Navigate between full-body view and organ-level zoom
- **Timeline scrubber:** Drag to see body state at any historical moment (data heatmap updates to show state at that time)

**Data Visualization on Body:**

| Data Type | Visual Representation |
|---|---|
| Active continuous sensor | Pulsing glow in sensor color (blue=ECG, green=glucose, orange=SpO2, purple=EEG) |
| Recent episodic data (<30 days) | Solid region highlight |
| Old data (>30 days) | Faint ring around region |
| No data for region | Neutral mesh color, faint "+" icon on hover |
| Alert/anomaly | Red pulse animation |
| Nanoparticle simulation active | Particle stream animation following vascular paths |

### Consumer Mode — Interface Layout

```
┌─────────────────────────────────────────────────────────────────────────┐
│  NanoFlowSIM                                    [⚙ Settings] [👤 Profile] │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│   ┌──────────────────────┐    ┌───────────────────────────────────────┐  │
│   │                      │    │  REGION DETAIL: Heart                  │  │
│   │    [3D Body View]    │    │  ─────────────────────────────────    │  │
│   │                      │    │  📡 LIVE: ECG Patch (2 days remaining) │  │
│   │   [rotating human    │    │  ┌─────────────────────────────────┐  │  │
│   │    anatomy mesh]     │    │  │  ~~~heartbeat waveform~~~       │  │  │
│   │                      │    │  └─────────────────────────────────┘  │  │
│   │   ● Heart (live)     │    │  HR: 68 bpm  HRV: 42ms  Rhythm: NSR  │  │
│   │   ● Glucose (live)   │    │                                        │  │
│   │   ○ Brain (47 recs)  │    │  📋 HISTORY                           │  │
│   │                      │    │  • 2026-05-20: 12-lead ECG — Normal   │  │
│   │                      │    │  • 2026-04-15: Echo — EF 62%          │  │
│   │                      │    │  • 2026-03-01: Troponin — <0.01 ng/mL │  │
│   │                      │    │  • 2025-11-10: Cholesterol panel       │  │
│   │                      │    │  [View all 23 cardiac records →]       │  │
│   │                      │    │                                        │  │
│   │                      │    │  🧬 GENOMICS (2 variants)             │  │
│   │                      │    │  • SCN5A rs7626962 — ↑ LQT risk       │  │
│   │                      │    │  [View details →]                      │  │
│   │                      │    │                                        │  │
│   │                      │    │  [+ Add Data]  [🔬 Run Simulation]    │  │
│   └──────────────────────┘    └───────────────────────────────────────┘  │
│                                                                           │
│   [Timeline] ──────────────────────────────────────● Now                  │
│              2023                2024               2025     2026          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Consumer Mode Features:**
- Simplified language (no medical jargon by default, toggle for clinical terms)
- AI Health Summary: one-paragraph plain-English summary of what the body's data shows
- Trend indicators: is X going up, down, or stable over selected time window
- Device connection wizard: step-by-step pairing for NFS hardware
- Hospital record import: guided FHIR connection or PDF upload
- Export my data: full JSON/FHIR export of all personal records
- Emergency data card: QR-code-accessible emergency medical summary

### Professional Mode — Interface Layout

All consumer features plus:

**Left Panel — Region Navigator:**
Full UBERON ontology tree browsable, with record counts per organ system. Supports multi-select for comparative analysis.

**Center — 3D View with Clinical Layers:**
Additional layer toggles for:
- Vascular anatomy with blood flow simulation overlay
- Tumor microenvironment model (if oncology data present)
- Nanoparticle distribution heatmap from simulation runs
- Multi-timepoint comparison (ghost mesh of body state at past timestamp vs. current)

**Right Panel — Clinical Data Viewer:**

Tabbed interface:
1. **Vitals & Monitoring:** All time-series data with full-resolution waveform viewer (ECG scrollable at 25mm/s standard, EEG spectrogram, glucose 7-day AGP)
2. **Lab Results:** Structured table of all blood/urine/genetic lab values with reference ranges, trend arrows, and delta-from-last-value display
3. **Imaging:** DICOM viewer (Cornerstone.js) embedded inline with 3D segmentation overlay
4. **Genomics:** Variant browser with clinical classification (pathogenic / likely pathogenic / VUS / benign), pathway enrichment viewer, pharmacogenomics table
5. **Simulation:** Nanoparticle simulation launcher with parameter configuration, real-time progress, and output visualization
6. **Research Cohort:** (Institution accounts) De-identified population comparisons, aggregated outcome data

**Professional Mode Additional Features:**
- Full DICOM import and viewing with measurement tools
- VCF/FASTQ file import and variant annotation
- FCS file import for flow cytometry data
- FHIR R4 full read/write access
- API key management for programmatic access
- Audit log of all data access
- Multi-patient dashboard (clinic/hospital accounts)
- Direct NanoFlowSIM simulation launcher from any data region
- mzML import for metabolomics/proteomics
- Pharmacogenomics drug interaction checker (using patient CYP variant data)

### Data Entry Flows

**Manual Entry — Blood Test Results:**
```
1. Tap region OR tap "+" → "Add Lab Result"
2. Select test type from searchable list (ICD-10 / LOINC code lookup)
3. Enter value + units (auto-suggested units for selected test)
4. Enter date/source (hospital name, self-collected)
5. Optional: upload PDF/image of original report
6. System auto-assigns UBERON codes and creates record
7. Record appears immediately on body map + history timeline
```

**Hospital Import:**
```
1. Tap "Import Records" → "Connect to Hospital"
2. Enter hospital name (searches FHIR directory) OR upload export file
3. FHIR OAuth2 authorization with hospital MyChart / patient portal
4. System fetches available records: labs, notes, imaging, medications
5. Preview + approve import (user controls what to import)
6. All records parsed, UBERON-tagged, and added to body map
7. DICOM images stored in local MinIO, accessible in DICOM viewer
```

**NFS Device Connection:**
```
1. Tap "+" on body region OR tap device icon in toolbar
2. Select device type from list (or scan QR code on device)
3. BLE pairing wizard (or USB-C cable detection)
4. Device calibration / patient ID assignment
5. Session starts, data streams in real-time
6. Body map region glows live with streaming data
7. Session ends: all data saved, processed, archived
```

### Mobile-Specific UX

React Native / Expo implementation:

- **Home screen widget:** Glanceable current vitals (glucose, HR, SpO2, steps) without opening app
- **AR overlay mode:** Point phone camera at body → AR overlay shows live sensor data on corresponding body region
- **Notification system:** Configurable alerts for threshold breaches (glucose too high/low, arrhythmia detected, medication reminder)
- **Offline mode:** Full data viewing and manual entry works offline; syncs when connection restored
- **Health app sync:** Apple Health / Google Health Connect bidirectional sync for steps, sleep, HR data from native health apps
- **Camera capture:** Photograph medical documents, prescriptions, test results for OCR-assisted import
- **Voice entry:** Dictate symptoms, notes, medication changes into the record

---

## 6. Data Integration — Full Loop (Current + Future)

### Non-Continuous Data Sources (Current, Supported Now)

| Format | Data Type | Integration Method |
|---|---|---|
| VCF (Variant Call Format) | SNPs, genomic variants | Direct import, annotation via VEP |
| FASTQ | Raw sequencing reads | NFSIM-SEQ-01 output, 3rd-party upload |
| DICOM | CT, MRI, X-ray, ultrasound | DICOM receiver + Cornerstone.js viewer |
| FHIR R4 JSON/XML | Hospital records, labs, medications | FHIR client with OAuth2 |
| HL7 v2 | Legacy hospital data | HL7 parser |
| PDF | Scanned lab reports, imaging reports | OCR + AI-assisted structured extraction |
| FCS (Flow Cytometry Standard) | Flow cytometry events | NFSIM-FLOW-01 output, direct import |
| mzML | Mass spectrometry data | Proteomics/metabolomics import |
| CSV / Excel | Self-reported data, wearable exports | Structured import wizard |
| JPEG/PNG | Pathology slide scans, dermatology photos | Image attachment with AI annotation |
| 23andMe / AncestryDNA raw | Consumer genomics | Raw file import, LIFTOVER to GRCh38 |

### Continuous Data Sources (Current, Supported Now)

| Device / Source | Data Type | Integration |
|---|---|---|
| NFSIM-ECG-01 patch | Single-lead ECG continuous | BLE GATT NFS profile |
| NFSIM-ECG-02 vest | 12-lead ECG 24h | BLE GATT NFS profile |
| NFSIM-EEG-01 headset | EEG 8-16ch | BLE GATT NFS profile |
| NFSIM-CGM-01 | Glucose interstitial | NFC + BLE NFS profile |
| NFSIM-SWEAT-01 | Sweat electrolytes | BLE NFS profile |
| Dexcom G7 | Glucose (via Dexcom API) | OAuth REST API integration |
| Abbott FreeStyle Libre | Glucose (via LibreView API) | OAuth REST API |
| Apple Watch | HR, SpO2, sleep, HRV, ECG | Apple Health HealthKit API |
| Fitbit / Garmin / Polar | HR, HRV, sleep, GPS | OAuth REST APIs |
| Oura Ring | Sleep, HRV, temperature | Oura REST API |
| WHOOP | Recovery, strain, sleep | WHOOP REST API |
| Withings BP monitor | Blood pressure | Withings OAuth API |
| Generic BLE HR monitor | Heart rate | BLE GATT HRS profile |
| Dräger / Masimo SpO2 | Pulse oximetry | BLE GATT custom profile |

### Continuous Data Sources (Future, Architecture Pre-Built)

The data model, storage schema, and API endpoints are designed today to accept these future data types without schema migration:

| Future Device / Technology | Data Type | Current Status |
|---|---|---|
| cfDNA liquid biopsy monitor | Circulating tumor DNA, cell-free DNA fragments | Experimental |
| Continuous proteomics patch | Real-time protein expression markers | Research |
| Continuous nanopore | Real-time genomic surveillance | NFSIM-SEQ-01 moves toward this |
| Ingestible continuous capsule | GI tract continuous chemistry, microbiome | NFSIM-CAP series |
| Wearable NIRS metabolomics | Real-time tissue metabolites | NFSIM-OXY-01 moves toward this |
| Aptamer-based hormone sensor | Cortisol, insulin, estrogen continuous | Research |
| Neural implant data stream | Intracortical neural firing patterns | BCI research |
| Epigenetic methylation monitor | DNA methylation state changes | Experimental |
| Microfluidic real-time CBC | Continuous blood cell counts | Research |
| Sweat-based cfDNA | DNA fragments in sweat | Emerging research |

### Data Pipeline Architecture

```
[NFS Device] ──BLE/USB──→ [NFS Client App]
[Hospital FHIR] ─────────→ [FHIR Importer]     → [Ingest Layer]
[3rd-party Wearable API] → [OAuth Poller]              │
[Manual Entry] ──────────→ [Entry Form]                │
                                                        ▼
                                             [UBERON Tagger]
                                                   (auto-assign anatomical codes)
                                                        │
                                                        ▼
                                             [Quality Scorer]
                                                   (signal quality, completeness)
                                                        │
                                                        ▼
                                             [Local SQLite + MinIO]
                                                        │
                                            ┌───────────┴───────────┐
                                            ▼                       ▼
                                    [3D Body Map]          [Simulation Engine]
                                    (visualization)        (Pillar 1 input)
                                            │
                                            ▼
                                    [Optional: Cloud Sync]
                                    (patient-controlled, E2E encrypted)
```

---

## 7. Biological Sensing Domain Encyclopedia

This section documents the complete engineering evolution of each biological sensing domain — from historical origins through the portable era — specifically to inform the design of each NanoFlowSIM hardware device and to explain *why* each design choice was made.

### 7.1 Domain: Molecular / Genomic Sensing

**What It Measures:** DNA, RNA, proteins, pathogens, mutations, epigenetic marks, microbial genomes, cell-free nucleic acids.

**Why It Matters for NanoFlowSIM:** Genomic data is the highest-information layer of patient biology. SNPs, somatic mutations, and gene expression profiles directly drive nanoparticle targeting parameters, CRISPR payload design, and therapy combination selection.

#### Phase 0 — Pre-Molecular Era (Pre-1950s)
Biology was purely observational. Disease was studied through symptoms, anatomy, and cell morphology under light microscopes. The information layer of DNA was completely invisible.

#### Phase 1 — DNA Discovery Era (1950s–1970s)
Watson and Crick elucidated DNA's double-helix structure in 1953. The genetic code was cracked through the 1960s. For the first time, biologists needed instruments capable of handling, separating, and visualizing DNA.

**Technology: Gel Electrophoresis**

Core physics: DNA carries a uniform negative charge-to-mass ratio. In an electric field through a porous gel matrix, smaller DNA fragments migrate faster than larger ones.

Hardware stack:
```
- Gel casting tray: borosilicate glass or acrylic, 10×14 cm standard
- Agarose gel: 0.5–2.0% concentration (higher = resolves smaller fragments)
- TBE or TAE buffer: ionic conductor (Tris-Borate-EDTA or Tris-Acetate-EDTA)
- Electrodes: platinum wire (non-reactive)
- Power supply: 50–150V DC, 10–500 mA capacity
- DNA stain: ethidium bromide (intercalating, original) → SYBR Safe (safer modern alt)
- UV transilluminator: 302nm UV excites EtBr/SYBR → visible orange fluorescence
- Polaroid/CCD camera: capture gel image
```

Signal chain:
```
DNA sample + loading dye
→ pipetted into wells
→ 60–120 min electrophoresis
→ ethidium bromide or SYBR staining
→ UV illumination
→ fluorescence emission at 590nm
→ band pattern = size estimation
```

Limitations: qualitative, slow, manual, radiation hazard (UV + EtBr), no sequencing.

**NanoFlowSIM derivative: NFSIM-GELEC-01** — see Section 8.

#### Phase 2 — PCR Revolution (1980s)
Kary Mullis invented Polymerase Chain Reaction in 1983 (Nobel Prize 1993). This was arguably the most important tool invention in molecular biology.

Core principle: Exponential amplification of a specific DNA target region. Starting from 1 molecule, 35 PCR cycles theoretically yield 2³⁵ = 34 billion copies.

Three-stage thermal cycle:
```
1. Denaturation: 94–98°C for 20–30s
   → hydrogen bonds between strands break
   → double-stranded DNA → single-stranded DNA

2. Annealing: 50–65°C for 20–40s (primer-specific, calculated as Tm - 5°C)
   → custom oligonucleotide primers bind to their complementary sequences
   → primers define the region to be amplified

3. Extension: 72°C for 1 min/kb (Taq polymerase optimum)
   → DNA polymerase extends from primer, synthesizing new strand
   → doubling of target region per cycle
```

Original PCR hardware stack:
```
- Thermal block: aluminum, drilled for 0.2mL or 0.5mL PCR tubes, 96-well, or 384-well
- Resistive heaters: embedded in block, nichrome wire, 200–500W
- Peltier coolers: paired with heaters for active cooling
- Thermistors/RTDs: ±0.1°C accuracy sensors embedded in block
- Heat lid: prevents condensation on tube caps (typically 105°C)
- Microcontroller: PID control loop for temperature ramp rate
- Power electronics: MOSFETs driving heaters, H-bridge for Peltier direction
- User interface: LCD display + keypad for protocol programming
- PC connectivity: RS-232 or USB for protocol upload
```

Why early PCR machines were large:
- Thermal mass of aluminum block required powerful heating
- Multiple tube wells needed uniform temperature (thermal gradient <0.5°C block-to-block)
- Cooling required forced air or liquid cooling systems
- 96-well format = high thermal load

**Evolution to portable PCR:**

| Generation | Size | Power | Key Technology |
|---|---|---|---|
| Lab thermocycler (1990s) | Desktop, 5–15 kg | 200–500W | Resistive heating, forced air |
| Compact thermocycler (2000s) | 2–5 kg | 80–200W | Better Peltier efficiency |
| OpenPCR (2012) | 1.5 kg | ~50W | Arduino, exposed design, open source |
| Portable qPCR (2015+) | 0.5–1 kg | 20–50W | Battery, microfluidics, smartphone readout |
| Hand-held PCR (2020+) | <200g | 5–15W | MEMS chambers, ultra-thin Peltier, coin battery |
| Individual-tube PCR (near future) | <50g | 2–5W | Nanoliter chambers, IR heating |

**qPCR (Quantitative PCR) additions:**
Standard PCR tells you "is target present (yes/no)." qPCR adds real-time fluorescence detection to quantify DNA amount during amplification.

Additional hardware for qPCR:
```
- Excitation source: LED array (blue 470nm, white) or solid-state laser
- Optical filters: bandpass filters per fluorophore channel (FAM, HEX, ROX, Cy5)
- Photodiode or CMOS sensor: measures fluorescence intensity per cycle
- ADC: converts photodiode current to digital value
- DSP: background subtraction, baseline correction
- Ct calculation: cycle at which fluorescence exceeds threshold = quantification
```

**Digital PCR:**
DNA partitioned into tens of thousands of nanoliter droplets (ddPCR) or nanoliter wells. Each partition contains ≤1 DNA molecule. After amplification, count positive wells. Poisson statistics give absolute molecule count — no standard curve needed. Extreme sensitivity for rare mutations (e.g., circulating tumor DNA at 0.01% variant allele frequency).

**NanoFlowSIM derivatives: NFSIM-PCR-01 through PCR-04, NFSIM-dPCR-01**

#### Phase 3 — DNA Sequencing (1970s–2000s)

**Sanger Sequencing (First Generation, 1977)**

Chain-termination method (ddNTP incorporation). Fluorescently labeled dideoxy nucleotides randomly terminate synthesis. Fragment sizes reveal sequence.

Hardware stack:
```
- Capillary array: 48–96 capillaries of polymer-filled fused silica
- High-voltage power supply: 10–15 kV for capillary electrophoresis
- Laser: 488nm argon-ion laser excitation
- Four-color detection: CCD or PMT array per fluorophore (FAM, JOE, TAMRA, ROX)
- Thermal control for capillary: maintains polyacrylamide denaturing conditions
- Robotic sample loader: automated injection of prepared samples
- Compute workstation: basecalling software, trace interpretation
```

Read length: 600–1000 bp. Accuracy: 99.99%. Throughput: very low (~1 Mb/day per instrument). Cost: ~$1/bp initially.

**Next-Generation Sequencing — Illumina (2000s–present)**

Massively parallel sequencing by synthesis. Millions of DNA clusters on a flow cell read simultaneously.

Hardware stack (HiSeq/NovaSeq class):
```
Physical systems:
- Flow cell: glass slide with patterned nanowells; DNA clusters form by bridge amplification
- Fluidics system: 16+ reagent bottles, precision pumps, valves, tubing
- Temperature control: ±0.1°C across entire flow cell
- Four-laser system: 532nm, 638nm, 658nm, 785nm (for 4-channel sequencing)
- Scientific CMOS cameras: 2–4, 100 megapixel class, for simultaneous imaging all clusters
- Vibration isolation: active damping table required
- Compute servers: real-time image processing, basecalling, quality scoring
- Cooling system: chilled water or refrigerated air for electronics
- UPS: power conditioning, prevents data loss during sequencing run
```

Run time: 1–3 days. Output: 200 Gb–6 Tb per run. Read length: 2×150 bp (paired end). Accuracy: 99.9%+. Cost: $0.001/bp and falling.

Why these machines are huge: optical imaging requires vibration isolation, precision optics, multiple lasers, large-format cameras, and cooling. Every run generates terabytes of raw image data.

**Third-Generation Sequencing — Oxford Nanopore MinION (2015–present)**

Revolutionary removal of the optical detection stack. DNA translocates through protein nanopores; ionic current changes are measured electrically.

Core physics:
```
- Engineered protein nanopore (MspA or CsgG variant) inserted into lipid bilayer membrane
- Applied voltage: ~120–180 mV across membrane
- Open-pore current: ~100–300 pA (depends on pore species)
- DNA translocates at ~400 bases/second (motor protein controlled)
- Each k-mer (group of ~5 bases) creates characteristic current signature
- Current deviation from open pore: ~10–20 pA per k-mer context
- Signal digitized at 3–5 kHz, then downsampled
- Deep learning basecaller (Guppy → Dorado) converts raw current trace to sequence
```

Hardware stack (MinION):
```
Flow cell (consumable, $500–900 each):
- Lipid bilayer membrane: synthetic lipid mixture, cast across array
- 512 individually addressable nanopore wells (R9/R10 series)
- Electrode grid: silver chloride, per well
- Microfluidics: top reservoir for sample loading
- Protein nanopores: CsgG octamers or MspA pores inserted into bilayer
- Motor enzyme: helicase controls DNA threading speed

MinION reader (reusable):
- ASIC: Oxford Nanopore custom chip (Mk1C has integrated FPGA+ARM)
- Analog front end: per-channel low-noise transimpedance amplifier
- ADC: 12-bit, 25kHz sampling per channel (512 channels parallel)
- Digital multiplexer: reads all 512 channels
- USB 3.0 controller: streams data to laptop
- LED indicators
- Dimensions: 10.5 × 3.3 × 2.3 cm, 87g
- Power: 5V via USB, peak 500mA
```

Signal chain:
```
DNA in library prep buffer
→ motor enzyme attaches, controls threading speed
→ single-stranded DNA enters nanopore
→ each base position modulates ionic current
→ analog amplifier (per channel)
→ 12-bit ADC
→ raw squiggle signal streamed over USB
→ Dorado neural network basecaller (LSTM/transformer architecture)
→ FASTQ sequence output with quality scores
→ Minimap2 alignment to reference genome
→ variant calling (medaka or PEPPER-DeepVariant)
```

Advantages over Illumina:
- No optical components → portable, pocket-sized reader
- Ultra-long reads (N50 >50kb, up to Mb for ultra-long reads) → whole genome phasing, structural variant detection, repeat regions
- Direct RNA sequencing (no cDNA conversion) → true transcript reading, native modifications
- Direct DNA methylation detection → epigenomics without bisulfite treatment
- Real-time streaming → results in hours not days
- Cost: $1000 device, $500–900 per flow cell

Limitations:
- Raw accuracy lower than Illumina (Q20 per read, improving with R10 pore)
- Flow cell consumables expensive
- Sensitive to pore degradation, membrane rupture
- Computationally intensive basecalling
- Library prep still complex (though improving toward simpler native prep)

Why MinION is not fully open-source:
- Pore protein engineering (MspA, CsgG variants) — proprietary, patented
- ASIC design — proprietary
- Motor enzyme selection and coupling chemistry — trade secret
- Basecaller neural network weights — partially closed
- Flow cell manufacturing (bilayer casting at scale) — proprietary process

**NanoFlowSIM derivative: NFSIM-SEQ-01 (open nanopore sequencer)** — addresses each of these gaps with open alternatives.

**LAMP (Loop-Mediated Isothermal Amplification):**
Isothermal alternative to PCR — amplifies DNA at constant 65°C using 4–6 primers. Extremely fast (15–30 min) and sensitive. Works with simple heat block, no thermal cycling. LAMP-compatible colorimetric or turbidity readout eliminates need for optical detection in some applications.

**RPA (Recombinase Polymerase Amplification):**
Room-temperature isothermal amplification (37–42°C, or even ambient). Uses recombinase enzymes to thread primers onto target, then extends. Results in 10–20 min. Even simpler hardware requirements than LAMP. Lateral flow strip readout possible.

**CRISPR Diagnostics (SHERLOCK, DETECTR):**
CRISPR Cas12/Cas13 proteins have collateral cleavage activity — after detecting target nucleic acid, they non-specifically cleave fluorescent reporter molecules. Readout: fluorescence or lateral flow strip. Extreme sensitivity (attomolar detection). Can be combined with LAMP or RPA for sample pre-amplification.

### 7.2 Domain: Structural / Anatomical Imaging

**What It Measures:** Physical anatomy — tissue density, organ geometry, vascular structure, lesion morphology, bone integrity, internal motion.

**Why It Matters for NanoFlowSIM:** DICOM imaging data defines the physical map of the patient — where the tumor is, its geometry, vascular supply, tissue characteristics. This directly parameterizes the tissue-layer simulation model and the 3D body map at Level 2 resolution.

#### X-Ray (1895)
Röntgen discovered X-rays November 8, 1895. Within months, radiographs were being taken in hospitals worldwide.

Core physics: Bremsstrahlung radiation. Electrons accelerated through 40–150 kV strike tungsten anode → rapid deceleration → X-ray photon emission. Photon energy spectrum: 30–150 keV.

Hardware stack:
```
X-ray tube:
- Cathode: tungsten filament, ~2–4mm effective focal spot
- Rotating anode: tungsten-rhenium alloy disk, 90–200mm diameter, 3000–9000 RPM
- Vacuum: <10⁻⁶ torr
- High voltage generator: DC inverter, 50–150 kVp, 100–1000 mA capability
- Beam collimator: lead shutters defining field size
- Glass/beryllium window: X-ray exit

Detector (modern):
- Flat-panel detector (FPD): 43×43 cm cesium iodide (CsI) scintillator + amorphous silicon TFT array
- Spatial resolution: 2–4 line pairs/mm
- DQE (Detective Quantum Efficiency): 60–70%
- Digital output: 14-bit DICOM image
```

**CT Scanner (1970s):**

Rotating X-ray source + curved detector array. Hundreds of projections per revolution → filtered back projection or iterative reconstruction → volumetric data.

Hardware stack:
```
Gantry:
- Rotating assembly: X-ray tube + detector, 400–700 kg, rotation speed 0.25–0.5s/rev
- Slip rings: allow continuous rotation while passing high voltage + data
- Counterweights and precision bearings

X-ray system:
- 60–140 kVp, 50–800 mA, rotating anode tube
- Bowtie filter: compensates for patient shape (more filtration at periphery)
- Beam collimator: defines slice thickness

Detector array:
- Solid-state scintillator: GOS (gadolinium oxysulfide), 64–320 rows
- Photodiode array bonded to scintillator
- 800–1000 individual elements per row
- 64–320 parallel data acquisition channels

Data acquisition:
- ADC: 20-bit per channel
- DAS (Data Acquisition System): ~10 Gb/s raw data rate
- Gantry-to-workstation data transfer via fiber optical slip ring or wireless

Compute:
- Reconstruction: GPU cluster, FBP + MBIR algorithms
- CT dose modulation: real-time tube current adjustment
- AI reconstruction: vendor-specific deep learning (GE TrueFidelity, Siemens ClearIQ)
```

Typical CT: 16-, 64-, 128-, 256-, 320-slice systems. Each slice: 0.5–1.25mm thickness.

**MRI (1970s–present):**

No ionizing radiation. Nuclear magnetic resonance of hydrogen protons.

Core physics:
```
- Main magnet aligns proton spins (parallel or antiparallel to B0)
- Net magnetization M0 along B0 field direction
- 90° RF pulse tips M0 into transverse plane
- Protons precess at Larmor frequency: f = γ × B0
  (for ¹H: f = 42.58 MHz/T)
- Gradient coils spatially encode precession frequency/phase
- Protons relax: T1 (longitudinal), T2 (transverse)
- FID (Free Induction Decay) signal detected in RF coil
- 2D/3D Fourier transform → spatial image
```

Hardware stack:
```
Superconducting magnet:
- Niobium-titanium (NbTi) wire coils cooled by liquid helium to 4K
- Field strength: 1.5T (clinical standard), 3T (high-field), 7T (research)
- Homogeneity: <2 ppm over 50cm DSV (diameter of spherical volume)
- Fringe field: 5 Gauss line extends several meters
- Weight: 4,000–10,000 kg

Gradient coils:
- X, Y, Z gradient: up to 80 mT/m amplitude, 200 T/m/s slew rate
- Creates loud acoustic noise (up to 130 dB SPL) from Lorentz forces
- Actively shielded to reduce eddy currents in magnet bore

RF system:
- Body coil: built into bore, transmit + receive
- Surface coils: 4–32 channel arrays for specific anatomy
- Digital receivers: direct digitization, 10–100 MHz bandwidth per channel

Shimming:
- Passive shims: iron pieces placed inside bore for coarse correction
- Active shims: additional coils for fine correction

Compute:
- k-space reconstruction: FFT-based, GPU-accelerated
- Parallel imaging: GRAPPA, SENSE for undersampled k-space
- Compressed sensing: randomized k-space sampling + iterative reconstruction
- AI super-resolution: vendor-specific (GE AIR, Siemens Deep Resolve)
```

**Portable/Low-Field MRI (emerging):**

Key innovations enabling portable MRI:
- Permanent magnet arrays (Halbach configuration): no cryogenics, 50–100 mT field
- AI reconstruction compensates for lower SNR at reduced field
- Shielding not required at low fields (no 5-Gauss line problem)
- Power: runs on standard outlet, or battery for point-of-care

**Ultrasound (1950s–present):**

Core physics: piezoelectric elements generate pressure waves at 1–40 MHz. Waves reflect at tissue interfaces (impedance mismatches). Round-trip time → depth. Amplitude → tissue reflectivity.

Why ultrasound became most portable:
- No ionizing radiation
- No large magnets
- Acoustic power levels safe at standard diagnostic levels (ISPTA < 720 mW/cm²)
- Electronic beam steering eliminates mechanical scanning
- Digital beamforming → fits on ASIC

Hardware stack (modern portable):
```
Transducer:
- Piezoelectric element array: 128–256 elements, PZT or cMUT (capacitive micromachined)
- Matching layers: quarter-wave acoustic matching to tissue impedance
- Backing material: tungsten-loaded epoxy (acoustic attenuation)
- Lens: acoustic focusing lens for fixed focus or electronic focus
- Frequencies: 2–5 MHz (abdominal), 7–15 MHz (superficial), 20–40 MHz (high-res)

Electronics:
- TX beamformer: nanosecond timing, high-voltage pulsers (50–100V) per element
- RX beamformer: low-noise amplifiers, dynamic receive focusing
- ADC: 10–14 bit, 50–100 MSPS per channel
- DSP: envelope detection, log compression, scan conversion
- Doppler processing: FFT-based for spectral Doppler, autocorrelation for color Doppler
- Wireless: WiFi 802.11ac or USB-C to phone/tablet for display

Power: 1–10W depending on mode (B-mode vs. color Doppler vs. 3D)
```

**OCT (Optical Coherence Tomography):**

Near-infrared interferometry. Resolution: 1–15 μm axial, 5–20 μm lateral. Penetration: 1–3 mm in tissue. Widely used in ophthalmology (retinal imaging), cardiology (coronary OCT), and dermatology.

Physics: Michelson interferometer with broadband light source. Interference between reference arm and sample arm light creates interference pattern. Fourier transform → depth-resolved image.

**NanoFlowSIM derivatives: NFSIM-US-01 through US-09, NFSIM-MRI-01, NFSIM-XRAY-01, NFSIM-OCT-01, NFSIM-MICRO-01**

### 7.3 Domain: Chemical / Metabolic Sensing

**What It Measures:** Dissolved molecules — ions, metabolites, dissolved gases, hormones, enzymes, neurotransmitters, drugs. The real-time biochemical state of the body.

**Why It Matters for NanoFlowSIM:** Metabolic state modulates nanoparticle behavior. pH affects payload release. Protein corona composition depends on blood chemistry. Glucose level affects cancer cell metabolism modeling. Continuous chemistry is the most actionable real-time data layer.

#### Pre-Electronic Era (1800s–mid 1900s)
Chemical sensing was visual and manual. Fehling's test (1848) for glucose: blue copper complex turned brick-red in the presence of glucose. Litmus paper for pH. Biuret test for protein. These were slow, qualitative, batch-only.

#### Electrochemical Revolution (mid 1900s)
Key realization: chemical reactions involve electron transfer → can be measured electrically.

**Three electrochemical modalities:**

**1. Potentiometry** (measuring equilibrium voltage):
```
Reference electrode | Solution | Ion-selective membrane | Working electrode
                                   ↑
                   Nernst equation: E = E₀ + (RT/nF) × ln([ion])

Hardware:
- Ion-selective electrode (ISE): pH glass electrode, Na+ glass, K+ valinomycin
- Reference electrode: Ag/AgCl in saturated KCl
- High-input-impedance amplifier: >10¹² Ω input (glass electrode source impedance huge)
- ADC: 16–24 bit (need <0.1 mV resolution)
Applications: pH, Na+, K+, Ca2+, Li+, pCO2
```

**2. Amperometry** (measuring reaction current):
```
Working electrode maintained at fixed potential vs. reference
Analyte oxidizes/reduces at electrode → current proportional to concentration
i = n × F × A × D × (∂C/∂x) at electrode surface

Hardware:
- 3-electrode cell: working (Pt, Au, carbon), counter (Pt), reference (Ag/AgCl)
- Potentiostat: controls working electrode potential
- Transimpedance amplifier: converts pA–μA current to measurable voltage
- ADC: 16–24 bit
Applications: glucose (glucose oxidase), H2O2, O2, dopamine, acetaminophen
```

**3. Conductometry** (measuring solution conductance):
```
AC measurement (avoids electrode polarization)
Conductance proportional to total ion concentration
Applications: total electrolyte concentration, bacterial growth detection
```

**Glucose Sensing Evolution:**

Phase 1 — Chemical strips (1965): Dextrostix. Reflectance photometry. Glucose oxidase on paper strip → colorimetric. Estimated by eye. Inaccurate.

Phase 2 — First-generation glucometers (1970s): Electrochemical. Glucose oxidase reaction:
```
Glucose + O₂ → Gluconolactone + H₂O₂   (glucose oxidase catalysis)
H₂O₂ → 2H⁺ + O₂ + 2e⁻                  (electrode oxidation at +0.6V vs Ag/AgCl)
Current ∝ glucose concentration
```

Phase 3 — Second-generation CGM (2006+): Subcutaneous sensor. Challenges overcome:
- Biofouling: polyurethane outer membrane limits glucose diffusion rate, stabilizes signal
- Enzyme stability: crosslinked GOx in hydrogel matrix survives 10–14 days
- Calibration drift: factory calibration algorithms, optional fingerstick calibration
- BLE transmission: NFC (FreeStyle Libre style passive readout) or active BLE (Dexcom G7)

**Pulse Oximetry:**
Beer-Lambert law applied to tissue. Oxygenated hemoglobin (HbO2) and deoxygenated hemoglobin (Hb) have different extinction coefficients at 660nm (red) and 940nm (near-IR).

```
SpO2 = HbO2 / (HbO2 + Hb) × 100%

Ratio of ratios (R):
R = (AC660/DC660) / (AC940/DC940)

SpO2 ≈ 110 - 25R  (empirical, calibrated against SaO2)

Hardware:
- Red LED: 660nm, 2–3mA drive
- IR LED: 940nm, 5–8mA drive
- Photodiode: silicon, broadband
- Analog front end: transimpedance amp, synchronous demodulation (lock-in)
- ADC: 18–22 bit
- DSP: adaptive filtering, motion artifact removal (accelerometer-based)
```

**NIRS (Near-Infrared Spectroscopy):**
Extended pulse oximetry concept. Multiple wavelengths (700–900nm) at multiple distances from source → depth-resolved tissue oxygenation. Detects oxy-Hb, deoxy-Hb, and cytochrome c oxidase. Used for cerebral oximetry, muscle oxygenation monitoring during exercise.

**NanoFlowSIM derivatives: NFSIM-CGM-01, NFSIM-SWEAT-01, NFSIM-CHEM-01 through CHEM-08, NFSIM-OXY-01, NFSIM-BREATH-01**

### 7.4 Domain: Electrical / Bioelectric Sensing

**What It Measures:** Bioelectric signals generated by ion flux across cell membranes — cardiac rhythm (ECG), brain activity (EEG), muscle activation (EMG), eye movement (EOG), skin conductance (EDA/GSR), nerve conduction.

**Why It Matters for NanoFlowSIM:** Cardiac status informs vascular simulation. Neural activity relates to CNS-targeting therapies. ECG arrhythmias may correlate with drug toxicity from simulated therapeutics.

#### Core Physics of Bioelectricity

Action potential: Cell membrane at rest maintains -70 mV (neurons) to -90 mV (cardiac) via Na+/K+ ATPase pump. Depolarization opens voltage-gated Na+ channels → rapid influx → +30 mV overshoot. K+ channels repolarize membrane. This spike propagates cell-to-cell.

Body as volume conductor: The body is a conductive medium. Bioelectric dipoles within the heart, brain, or muscles create potential fields that spread through tissue and appear (attenuated) at skin surface.

Signal amplitudes at skin:
```
ECG: 1–3 mV (heart, strong)
EMG: 0.1–10 mV (muscle, strong)
EOG: 0.1–5 mV (eye movement)
EEG: 10–100 μV (brain, weak)
ERG: 5–20 μV (retina)
```

**ECG Hardware Stack:**
```
Electrodes:
- Ag/AgCl wet gel: lowest impedance, best signal, requires gel
- Dry electrodes: carbon composite or conductive fabric, higher impedance, no prep
- Textile electrodes: conductive yarn woven into fabric

Analog front end:
- Instrumentation amplifier: 3-op-amp topology, CMRR >80 dB (to reject 50/60Hz)
- Input impedance: >100 MΩ (to preserve signal despite electrode impedance)
- Gain: 250–1000× (to bring mV signals to ADC range)
- Right-leg drive (RLD) circuit: drives patient to virtual ground, improves CMRR
- High-pass filter: 0.05 Hz cutoff (removes baseline wander)
- Low-pass filter: 150 Hz cutoff (anti-alias, removes EMG artifact)
- Notch filter: 50 or 60 Hz (power line interference)

ADC:
- Resolution: 16–24 bit (to resolve 10 μV LSB)
- Sample rate: 250–500 Hz standard; 8000 Hz for high-freq analysis

MCU/DSP:
- R-peak detection: Pan-Tompkins algorithm (bandpass → derivative → squaring → moving window integration)
- HRV analysis: SDNN, RMSSD, pNN50, frequency domain (LF/HF ratio)
- Arrhythmia detection: AI classifier (AFib, PVC, SVT) - TinyML on device or cloud

Power:
- Supply: 3.3V or 5V from battery
- Quiescent current: 1–10 mA (ultra-low-power IC options: ADS1291, MAX30003)
- Battery life: 14–30 days (CR2032 to 180mAh LiPo depending on duty cycle)

ECG ICs used in NFS devices:
- Texas Instruments ADS1291: 1-channel, 8-lead capable, ultra-low noise (4 μV_RMS)
- Texas Instruments ADS1298: 8-channel, 24-bit, SPI interface
- Maxim MAX30003: dedicated cardiac monitor AFE with R-R detection
- Nordic nRF5340 (MCU + BLE combo)
```

**EEG Hardware Stack:**
```
Challenges vs ECG:
- Signals 10–100× weaker (μV vs mV)
- Skull attenuates high frequencies (above 40 Hz severely attenuated)
- More electrodes needed for spatial resolution (8–256 channels)
- Dry electrodes have much higher impedance → more noise

Amplifier requirements:
- Noise floor: <1 μV_RMS (vs ~5 μV for ECG)
- Input impedance: >1 GΩ (dry electrodes have skin-electrode impedance of 50–500 kΩ)
- CMRR: >100 dB
- Gain: 1000–10000×

Key IC: Texas Instruments ADS1299 (8-channel, 24-bit, specifically designed for EEG)
- Noise: 1 μV_RMS input-referred
- Input impedance: 1 GΩ
- Programmable gain: 1–24×

Frequency analysis:
- Delta: 0.5–4 Hz (deep sleep)
- Theta: 4–8 Hz (drowsiness, meditation)
- Alpha: 8–13 Hz (relaxed wakefulness, eyes closed)
- Beta: 13–30 Hz (active thinking, focus)
- Gamma: 30–100 Hz (cognitive processing, attention)
```

**EMG Hardware Stack:**
```
Surface EMG (sEMG):
- Electrodes: Ag/AgCl pairs 20–30mm apart, aligned with muscle fiber direction
- Differential amplification: rejects common-mode noise
- Bandpass: 10–500 Hz (motor unit action potentials)
- Sampling: 1000–4000 Hz
- Rectification + envelope detection → muscle activation level
- Pattern recognition: gesture classification via ML (NFSIM-EMG-01)

Needle EMG:
- Concentric needle electrode inserted into muscle
- 50–500 μm diameter
- Recording: individual motor unit action potentials (MUAPs)
- Signal: 0.1–5 mV amplitude, 5–15 ms duration
- Requires clinical operation
```

**EDA (Electrodermal Activity / GSR):**
```
Measures sweat gland activity (eccrine glands, under sympathetic nervous control)
Skin conductance rises during arousal/stress
Two components:
- SCL (Skin Conductance Level): tonic baseline
- SCR (Skin Conductance Response): phasic response to stimuli

Measurement:
- 500 mV AC voltage at 20 Hz applied to skin electrodes
- Measure resulting current → skin conductance (0.1–30 μS)
- Palmar sites (thenar/hypothenar eminence) most sensitive
```

**NanoFlowSIM derivatives: NFSIM-ECG-01, ECG-02, EEG-01, EMG-01, NEURAL-01, EOG-01, EDA-01**

### 7.5 Domain: Implantable / Closed-Loop Systems

**What It Measures + Does:** Combines continuous sensing with automatic intervention. Pacemakers, cochlear implants, deep brain stimulators, continuous glucose monitors with insulin delivery, BCIs.

**Why It Matters for NanoFlowSIM:** Implantable sensors provide the highest-quality continuous data streams (direct tissue contact, no motion artifact, no transdermal attenuation). Nanoparticle systems may eventually be implant-compatible or delivered via implant.

Historical arc:
```
1950s: External cardiac pacemakers (wall-powered, patient tethered)
1958: First implantable pacemaker (Åke Senning/Rune Elmqvist, Sweden)
1960s: Mercury-zinc batteries, transistor circuits (replaced vacuum tubes)
1970s: Lithium iodide batteries → 5–10 year longevity
1980s: Programmable pacemakers (external radio programming)
1990s: ICDs (Implantable Cardioverter-Defibrillators) — sense + shock
2000s: Biventricular pacing (cardiac resynchronization therapy)
2010s: Leadless pacemakers (Medtronic Micra), MRI-conditional devices
2020s: Subcutaneous ICDs, remote monitoring, adaptive algorithms

Cochlear implants:
1972: House single-channel implant
1985: Nucleus multi-electrode (Cochlear Ltd, 22 electrodes)
1990s-present: Digital signal processing, 22+ channel, speech coding strategies
Future: optical cochlear implants, higher channel count, neural prosthetics

Deep Brain Stimulation:
1987: Alim-Louis Benabid discovers DBS for Parkinson tremor
1997: FDA approval for tremor
2000s: Bilateral STN stimulation for motor Parkinson symptoms
2010s: DBS for depression, OCD, Tourette (investigational)
Future: Adaptive DBS (sensing + stimulating simultaneously), closed-loop
```

**Key engineering challenges that apply to all NFS implant-adjacent devices:**

| Challenge | Description | NFS Approach |
|---|---|---|
| Biocompatibility | Body attacks foreign materials | Parylene-C coating, titanium casing |
| Power | Continuous sensing drains battery | Ultra-low-power ASICs, energy harvesting |
| Data transmission | Wireless through tissue | BLE/MICS band radio, inductive telemetry |
| Hermeticity | Body fluids destroy electronics | Titanium or ceramic hermetic packages |
| Long-term stability | Tissue changes around device | Flexible electrodes, anti-inflammatory coatings |
| Safety | Heating, RF interference | SAR limits, MRI compatibility testing |

---

## 8. Open-Source Hardware Ecosystem — All Devices

### Design Philosophy

Every NanoFlowSIM hardware device follows these universal mandates:

1. **Fully open hardware:** KiCad source files, no proprietary EDA required
2. **JLCPCB-compatible BOM:** All components available from LCSC/JLCPCB for one-stop PCB + assembly
3. **Open firmware:** FreeRTOS or Zephyr RTOS, MIT license
4. **Open software:** Python SDK + Node.js SDK + Rust client library
5. **NFS Protocol:** Universal JSON packet over BLE GATT or USB-C
6. **Battery operable:** USB-C charging, minimum 8h continuous operation on internal battery
7. **UBERON-tagged output:** All data tagged with anatomical codes
8. **Sub-$500 BOM** target for most devices (exceptions noted)
9. **Research Use Only (RUO) status** — not cleared as medical devices

### Device Naming Convention

```
NFSIM-[DOMAIN]-[NUMBER]

DOMAIN codes:
PCR    = Polymerase Chain Reaction / isothermal amplification
SEQ    = DNA/RNA Sequencing
CRISPR = CRISPR-based diagnostics
GELEC  = Gel electrophoresis
dPCR   = Digital PCR
US     = Ultrasound
MRI    = Magnetic Resonance Imaging
XRAY   = X-ray
OCT    = Optical Coherence Tomography
MICRO  = Microscopy
CGM    = Continuous Glucose Monitor
SWEAT  = Sweat/interstitial chemistry
CHEM   = Blood/chemical analysis
OXY    = Oxygenation (NIRS/SpO2)
BREATH = Breath analysis
ECG    = Electrocardiography
EEG    = Electroencephalography
EMG    = Electromyography
NEURAL = Neural recording
EOG    = Electrooculography
EDA    = Electrodermal activity
CAP    = Ingestible capsule
FLOW   = Flow cytometry
ENV    = Environmental sensing
```

---

### Domain A: Molecular / Genomic

---

#### NFSIM-PCR-01 — Portable Individual PCR Thermocycler

**Concept:** A single-strip (8-tube) PCR thermocycler designed for individual field use. Smaller than a paperback book. Peltier-based thermal cycling, BLE connectivity, TFT display, battery powered.

**What problem it solves vs OpenPCR:** OpenPCR was a 96-well desktop unit at ~1.5 kg. NFSIM-PCR-01 targets individual 0.2mL strip tubes at <300g, runs on a 3000 mAh LiPo for 40+ PCR cycles without USB power.

**Specifications:**
```
Sample format: 8-tube 0.2 mL PCR strip
Sample volume: 5–50 μL per tube
Thermal range: 4°C – 99°C
Temperature accuracy: ±0.2°C block-to-block, ±0.5°C well-to-well
Ramp rate heating: 5°C/second minimum
Ramp rate cooling: 3°C/second minimum (Peltier-limited)
Maximum cycles: 60 cycles
Lid temperature: 105°C (heated lid prevents evaporation)
Dimensions: 120 × 80 × 60 mm
Weight: ~280g with battery
Display: 2.4" IPS TFT 240×320 (ST7789 controller)
MCU: STM32G474 (Cortex-M4, 170 MHz, with math co-processor for PID)
Wireless: nRF52840 (BLE 5.0) on daughter module
USB: USB-C for charging and data (USB-CDC serial for firmware update + protocol control)
Battery: 3000 mAh LiPo, USB-C PD charging
Charging time: 2h to full
Runtime: ~8–12 PCR runs (35 cycles each) per charge
Power supply for Peltier: 5V 3A from battery via boost converter
```

**Hardware Stack — PCB Design:**
```
Primary MCU board (PCB-A, 80×50mm, 4-layer):
- STM32G474RET6 (LQFP64, main controller)
- nRF52840-QIAA (QFN73, BLE SoC)
- DS18B20 or PT1000 RTD (temperature reference)
- MAX4238 (precision op-amp for RTD readout)
- 24C256 EEPROM (protocol storage, calibration)
- USB-C connector + CH552 USB bridge or STM32 internal USB
- SWD debug header (TC2030-CTX-NL)
- LDO: TPS7A85 3.3V 2A for logic
- Status LEDs: 3× WS2812B (RGB addressable)

Thermal block board (PCB-B, 80×50mm, 2-layer, aluminum-core):
- Aluminum PCB substrate for thermal conductivity
- Peltier module footprints: 2× TEC1-12706 (40×40mm, 6A, 12W max)
- Thermistors: 2× NTC 10kΩ B=3950 (block and heat sink)
- Current sense: INA219 (measures Peltier drive current)
- MOSFET H-bridge: 2× IRLZ44N (for Peltier polarity switching — heating vs cooling)
- Gate drivers: IR2104 half-bridge driver
- Gate resistors: 10Ω
- Bootstrap capacitors: 100nF ceramic

Heat sink assembly:
- Aluminum heat sink: 80×50×20mm, 0.5°C/W thermal resistance
- Cooling fan: 50×50×10mm, 5V, 0.1A, ball bearing
- Thermal interface: 3M 8810 thermal pad between Peltier and heat sink

Heated lid assembly:
- Kapton flexible heater: 70×30mm, 5V, 5W
- Thermistor: NTC 10kΩ embedded in lid block
- MOSFET: IRLML6344 (logic-level, N-channel)
- Silicone pressure pad: 1.5mm, compresses against tube caps

Display module:
- 2.4" IPS TFT (ST7789, SPI)
- 4 tactile buttons (protocol select, start/stop, navigate menus)
- Membrane switch or silicone rubber buttons
```

**Schematic — Critical Nets:**
```
Peltier control loop (PID):
- STM32 TIM1 → PWM at 20kHz → IR2104 gate driver → IRLZ44N H-bridge → Peltier
- Direction pin → H-bridge direction = heating or cooling
- Block temp measured via 10-bit ADC + NTC thermistor
- PID coefficients: Kp=5.0, Ki=0.3, Kd=0.8 (tuned for 5°C/s ramp)

BLE communication (nRF52840 to STM32):
- SPI interface (4-wire) at 8 MHz
- INT line from nRF52840 to STM32 (data ready)
- 3.3V logic compatible

Power tree:
- LiPo → BQ24075 charger (USB-C PD negotiation) → protection IC → raw battery rail
- Battery → TPS61085 boost converter → 5V 3A rail (Peltier + fan + lid heater)
- Battery → TPS7A85 LDO → 3.3V rail (MCU, BLE, display, sensors)
- Battery monitoring: MAX17055 fuel gauge (I2C to STM32)
```

**Firmware Architecture:**
```
RTOS: FreeRTOS (STM32CubeMX generated)

Tasks:
1. ThermalControlTask (highest priority, 10ms tick)
   - PID loop for block temperature
   - Stage detection (denaturation/annealing/extension/hold)
   - Lid heater PID (separate controller, setpoint 105°C)
   - Cycle counter
   
2. ProtocolTask (normal priority, 100ms tick)
   - Protocol file parsing (JSON stored in EEPROM)
   - Stage progression logic
   - Protocol completion detection
   
3. BLECommTask (normal priority, 50ms tick)
   - GATT server for NFS device profile
   - Characteristic updates: temp, stage, cycle count, estimated time remaining
   - Command reception: start, stop, pause, load protocol
   
4. DisplayTask (low priority, 50ms tick)
   - TFT rendering via LVGL (Light and Versatile Graphics Library)
   - Real-time temperature plot (last 60 seconds)
   - Stage/cycle display, progress bar, ETA
   - Menu system for protocol selection
   
5. BatteryMonitorTask (low priority, 1000ms tick)
   - MAX17055 polling
   - Low-battery warning at 10%
   - Emergency stop at 5% (preserves current cycle then halts)
   
State machine:
IDLE → RUNNING → PAUSED → COMPLETE → ERROR
                    ↕
                  RUNNING (resume)
```

**Communication Protocol — NFSIM-PCR-01 specific:**
```
BLE GATT Service: NFS Device Control (4a6e-1000-...)
Characteristics:
- 0x1001 (notify, 20 bytes): Current state packet
  [status:1][stage:1][cycle:1][block_temp_x100:2][lid_temp_x100:2][ETA_sec:2][battery_pct:1]
  
- 0x1002 (write): Command
  0x01 = Start protocol
  0x02 = Stop
  0x03 = Pause
  0x04 = Resume
  0x10 = Load protocol (followed by JSON protocol data over multiple writes)
  
NFS Universal JSON packet (on session completion):
{
  "nfs_version": "1.0",
  "device_id": "NFSIM-PCR-01-XXXXXX",
  "session_id": "uuid",
  "patient_id": "uuid",
  "timestamp_unix": 1748304000,
  "data_type": "pcr_run",
  "anatomy_region": "UBERON:0000178",  // blood or user-specified sample source
  "data": {
    "protocol_name": "COVID_Taqman",
    "cycles_completed": 40,
    "final_block_temp": 72.1,
    "thermal_profile": [
      {"stage": "denaturation", "target": 95.0, "duration": 30, "achieved": 94.8},
      ...
    ],
    "total_runtime_seconds": 2847
  },
  "quality": 0.98,
  "battery_pct": 74
}
```

**BOM (Key Components):**
```
STM32G474RET6       $3.80   Mouser 511-STM32G474RET6
nRF52840-QIAA       $4.50   Mouser 949-NRF52840-QIAA-R
TEC1-12706          $2.80×2 LCSC / Amazon
50×50 fan           $1.20   LCSC
ST7789 2.4" TFT     $4.50   AliExpress / LCSC
BQ24075             $1.20   LCSC
TPS61085            $1.80   LCSC
MAX17055            $2.10   Mouser
INA219              $1.50   LCSC
IR2104              $0.80×2 LCSC
IRLZ44N             $0.60×4 LCSC
3000mAh LiPo        $6.00   Amazon / Adafruit
PCB manufacture     $15.00  JLCPCB (4-layer, 2 boards)
PCB assembly        $40.00  JLCPCB PCBA
Enclosure           $12.00  3D printed PETG
Hardware/misc       $8.00

Total BOM estimate: ~$115–$148
```

**Mechanical:**
```
Enclosure: Two-part PETG shell (top lid + base)
Lid hinged: 3mm stainless steel hinge pin
Tube well access: 8-position opening in top shell
Display window: polycarbonate inset
Button cutouts: 4 positions
USB-C cutout: bottom edge
Vent holes: fan intake (bottom) + exhaust (side)
Silicone gasket: around tube block area (prevents condensation damage)
Dimensions: 120 × 80 × 60 mm
```

---

#### NFSIM-PCR-02 — Gel-Slip Strip Reader

**Concept:** Portable gel electrophoresis via pre-cast disposable gel strips. Think MinION-style consumable design applied to gel electrophoresis. Instead of casting agarose gels in a lab, users receive pre-cast gel strips (or cast them using the provided mold kit). The reader provides high voltage, UV LED illumination, and CMOS imaging.

**What problem it solves:** Traditional gel electrophoresis requires: agarose weighing, microwave melting, casting, solidification, buffer preparation, UV transilluminator (heavy, UV hazard), gel documentation station. Total setup time: 45+ minutes. NFSIM-PCR-02 reduces this to: insert gel strip + load samples + press run = 25 min total.

**Gel strip design:**
```
Strip dimensions: 70 × 20 × 2mm
Material: 1.5% agarose pre-cast in TBE buffer
Wells: 8 wells + 1 ladder well (10μL capacity each)
Loading dye: pre-mixed into loading buffer vials (supplied)
Storage: sealed foil pouches with preservative buffer
Shelf life: 6 months refrigerated
Cost target: $30/10 strips
Ladder: pre-loaded in well 1 (50bp–3kb) or 1kb ladder option
```

**Reader Hardware Stack:**
```
High-voltage system:
- HV power supply: 300V DC at up to 30mA
- Step-up transformer or charge pump (Cockroft-Walton multiplier)
  IC: EMCO Q101-5 (0–300V adjustable DC-DC module) or custom
- HV connectors: platinum wire contacts that contact gel strip end electrodes
- Safety interlock: door switch cuts HV when opened
- Current limiting: 30mA max (current sense + comparator shutdown)
- LED indicator: HV active warning

UV LED illumination:
- 365nm UV LED array: 8× 1W UV LEDs (SMD LED365-08)
- LED driver: AL8860 constant current (100–300mA per LED)
- LED arrangement: under-illumination through clear gel strip holder
- Safety interlock: UV LED off when door open

CMOS imaging:
- Camera module: OV5640 (5MP, 1/4" CMOS, 30fps at 1080p)
- Lens: fixed focus f/2.0, 10cm working distance
- Filter: orange cutoff filter (550nm longpass) to block UV, pass ethidium bromide emission (590nm)
- Image processor: STM32H743 (Cortex-M7, 480 MHz) for JPEG compression

Microcontroller:
- STM32H743 (main controller + image processing)
- nRF52840 (BLE)

Display:
- 3.5" TFT IPS 480×320 (ILI9488, SPI)
- Gel image display with brightness/contrast adjustment

USB:
- USB-C: image transfer (USB-MSC mass storage + NFS protocol)
- Storage: 16GB eMMC for image archive

Power:
- 5000 mAh LiPo
- USB-C PD charging
- HV generation from 5V rail (boost to 300V)

Safety:
- Interlocked door mechanism (requires latching)
- Automatic UV + HV cutoff when door unlatched
- Timer auto-shutoff (HV max 60 min)
```

**BOM Estimate: ~$83 reader + $30/10 gel strips**

---

#### NFSIM-PCR-03 — LAMP Isothermal Reader

**Concept:** Loop-mediated isothermal amplification reader. Fixed 65°C block. No thermal cycling required. Faster than PCR for pathogen detection. Suitable for LAMP primers available for COVID-19, influenza, HIV, malaria, Zika, dengue, TB.

**Key advantage over NFSIM-PCR-01:** Simpler thermal system (no cycling, just hold 65°C), faster results (15–30 min), potentially lower cost and smaller form factor. Fluorescence readout (LAMP with fluorescent dye like SYTO-9, or turbidity via LED/photodiode).

**Hardware Stack:**
```
Thermal block:
- Single-temperature Peltier + aluminum block, 8-tube strip
- Setpoint: 65°C (fixed for LAMP, user-adjustable 60–70°C)
- Temperature uniformity: ±0.5°C
- No ramp rate requirement (just hold temperature)

Optical detection system:
- Excitation LED: 470nm (blue, for SYBR Green/SYTO-9)
- Emission filter: 520nm bandpass (25nm FWHM)
- Photodiode: OPT101 (with integrated amplifier)
- One photodetector per tube well (8 channels)
- ADC: ADS1115 (16-bit, 4-channel, I2C) × 2 (for 8 channels)
- Real-time fluorescence monitoring every 30 seconds

Turbidity option:
- OD600 LED + photodiode alternative
- No fluorescent dye needed (LAMP produces visible turbidity)
- Lateral flow strip slot (alternative to optical readout)

MCU: STM32G0 (simpler than PCR-01, no complex PID needed)
BLE: nRF52840
Display: 2.8" TFT
Battery: 2000mAh LiPo
```

**BOM Estimate: ~$65**

---

#### NFSIM-PCR-04 — RPA Room-Temperature Amplification Reader

**Concept:** Recombinase Polymerase Amplification works at ambient temperature (25–42°C). Minimal heating required — just maintaining 37–42°C body temperature range. Enables truly ultra-portable molecular diagnostics with minimal power consumption.

**Hardware Stack:**
```
Thermal management:
- Minimalist: single small 40×40mm Peltier module OR
- Passive warming: body heat pocket incubator concept (no active electronics)
- For electronic version: resistance heater only (no cooling needed), setpoint 37°C
- NTC thermistor + PID with simple PWM heater

Readout:
- Lateral flow strip reader (optical reflectance)
  - White LED illumination
  - OPT3001 or TSL2591 ambient light sensor
  - Band-specific line reading (control line, test line)
  - Line intensity → positive/negative/invalid result
  
- OR: Fluorescence reader (same as LAMP unit but at lower temp)

MCU: STM32L0 (ultra-low power)
BLE: nRF52840
No display option (BLE only, phone shows result)
Battery: 1000mAh LiPo (days of standby, hours of active operation)
```

**Target use cases:** HIV viral load screening, malaria diagnosis, antibiotic resistance gene detection. Compatible with standard RPA kits (TwistAmp by TwistDx or equivalents).

**BOM Estimate: ~$45**

---

#### NFSIM-SEQ-01 — Open Nanopore Sequencer

**Concept:** The most technically ambitious device in the NanoFlowSIM ecosystem. An open-source nanopore sequencer using biological pores, open-source FPGA signal processing, and open-source basecalling. Addresses everything MinION got right (portability, electrical detection) while opening what it kept closed (pore, ASIC, basecalling, flow cell design).

**Why this is possible now:**
- Alpha-hemolysin pore protein: published structure (1996), expressible in E. coli, available commercially from Sigma-Aldrich
- MspA pore: published (2010, Bhanu Bhanu lab), expressible and available
- Phi29 DNA polymerase (motor enzyme): commercially available (NEB, Lucigen)
- FPGA boards (Xilinx Artix-7, Lattice ECP5): accessible to makers
- Open-source basecalling: Bonito (Oxford Nanopore open-sourced training pipeline), Caduceus, community models
- Lipid bilayer techniques: published protocols, achievable with off-the-shelf lipids (DPhPC)

**Technical Challenges (honest assessment):**
1. Lipid bilayer formation: fragile, requires practice, not trivially reproducible
2. Pore insertion: probabilistic, requires optimization
3. Picoamp signal measurement: requires careful PCB layout, shielding
4. FPGA real-time processing: significant firmware development
5. Basecalling: computationally intensive, GPU recommended for real-time

**This device is firmly research/laboratory grade, not consumer grade.**

**Flow Cell Design (open):**
```
Membrane chamber:
- Two PDMS chambers separated by 25μm polyimide film with 50μm aperture
- cis chamber: contains DNA sample + buffer
- trans chamber: contains buffer
- Ag/AgCl electrodes: in each chamber (3mm diameter, chlorided by electrolysis)
- Lipid bilayer forms across aperture spontaneously
  (DPhPC in n-decane: 5 mg/mL solution painted across aperture)

Pore insertion:
- Alpha-hemolysin (α-HL): added to cis chamber at 1–10 μg/mL
- Self-inserts into bilayer spontaneously
- Monitoring: watch current for step from 0 pA → ~100 pA (one pore insertion)
- Target: single pore (disconnect after first insertion, or tolerate 1–4 pores)

Applied voltage:
- 120–180 mV DC, cis negative vs trans positive (drives DNA translocation)
- Voltage source: precision DAC + low-noise buffer op-amp

Signal detection:
- Transimpedance amplifier (TIA): 100 MΩ feedback, bandwidth 10 kHz
  - Op-amp: OPA637 or AD8067 (ultra-low noise, FET input)
  - Feedback resistor: 100 MΩ 0.1% (Vishay or Ohmite)
  - Feedback capacitor: 0.1 pF (limits bandwidth, sets noise)
- Anti-aliasing filter: 4th order Butterworth, cutoff 5 kHz
- ADC: ADS8900 (18-bit, 1MSPS) or AD7173 (24-bit, 31.25kSPS) 
  (higher precision than speed needed here)

FPGA processing:
- Board: Digilent Nexys Video (Artix-7 XC7A200T) or Lattice ECP5 Evaluation board
- Functions:
  - ADC interface (SPI/LVDS)
  - Real-time event detection (current level changes)
  - Segmentation: identify individual k-mer events
  - Streaming to laptop via USB 3.0 (UART at 12 Mbps or USB FX3)
  - Optional: on-FPGA pre-processing (signal normalization, segmentation)

Host computer:
- Receives raw signal stream (squiggles)
- Basecaller: Bonito (PyTorch-based, Oxford Nanopore open-source basecaller)
  or Caduceus (community fork)
- GPU: NVIDIA GPU recommended for real-time basecalling
  (CPU-only works for post-run basecalling)
- Alignment: minimap2 against reference genome
- Variant calling: medaka or PEPPER-DeepVariant
```

**Library Preparation (open protocol):**
```
Rapid library prep (no PCR):
1. DNA extraction: DNeasy Blood & Tissue Kit or CTAB method
2. End-repair and dA-tailing: NEBNext Ultra II End Repair module
3. Adapter ligation: custom hairpin adapter (motor enzyme pre-loaded)
   - Motor enzyme: Phi29 DNAP (NEB M0269) or commercially pre-coupled adapters
4. Bead cleanup: SPRI beads (AMPure XP or home-made: 0.22μm SPRI protocol)
5. Load onto flow cell

Amplicon library (with PCR):
1. PCR amplification of target region (NFSIM-PCR-01 output)
2. PCR cleanup (column or beads)
3. End-repair + adapter ligation (same as above)
4. Load
```

**BOM (Major Items):**
```
Artix-7 FPGA board (Digilent Cmod A7)    $65
OPA637 precision op-amp                   $12
AD8067 backup option                      $8
ADS8900 18-bit ADC                        $15
PDMS flow cell mold (silicone)           $20
Ag/AgCl electrodes (×10)                $8
DPhPC lipid (1mg, Avanti Polar Lipids)  $45
Alpha-hemolysin (50μg, Sigma)            $180
PCB design (4-layer, shielded)           $30
Enclosure (aluminum, Faraday cage)       $35
Assorted electronics                     $60

Total BOM estimate: ~$478–$536
```

**Note on pore alternatives:**
- Alpha-hemolysin (α-HL): most published, easiest to source, larger pore (~1.4nm) — suitable for ssDNA
- MspA: narrower reading head, better signal discrimination — harder to source but expressible from published sequence
- Aerolysin: emerging for DNA sensing — commercially available

---

#### NFSIM-SEQ-02 — Solid-State Nanopore Research Board

**Concept:** Instead of biological pores in lipid bilayers (fragile, requires biological handling), uses fabricated solid-state nanopores in SiN or MoS₂ membranes. More stable than biological pores, reusable, manufacturable. Requires cleanroom fabrication or purchase of commercial nanopore chips.

**Hardware Stack:**
```
Nanopore chip:
- SiN membrane: 20–50nm thick, 10–30nm pore (TEM or FIB drilled)
  Commercial source: IRSPEC, Norcada, or DIY via cleanroom access
- OR: MoS₂ monolayer membrane with sub-2nm pore (research grade)
- Chip holder: PDMS gasket, clamped between two fluid chambers

Signal detection:
- Same TIA circuit as NFSIM-SEQ-01 but with wider bandwidth (50kHz+)
- Faster ADC: ADS8861 (16-bit, 1MSPS) 
- FPGA: higher bandwidth processing

PCB layout:
- 4-layer, microstrip controlled impedance
- Ground plane isolation around TIA
- Shielded Faraday cage enclosure (aluminum)
- Guard ring around TIA input
- Low-noise 3.3V LDO: MAX6126 (reference) + TPS7A4901 (supply)

Advantages over biological pore:
- Reusable (clean between experiments)
- No lipid bilayer manipulation
- Stable for weeks
- Higher bandwidth possible

Disadvantages:
- Pore requires fabrication (TEM or FIB — expensive, specialized)
- Less selective than engineered biological pores
- Commercial chips: $50–500 each

BOM estimate (excluding chips): ~$180
```

---

#### NFSIM-CRISPR-01 — Portable CRISPR Diagnostic Reader

**Concept:** Implements SHERLOCK (CRISPR-Cas13a) or DETECTR (CRISPR-Cas12a) diagnostic assay in a portable, room-temperature device with fluorescence readout and optional lateral flow strip output. Can detect specific DNA/RNA targets at attomolar sensitivity when combined with LAMP pre-amplification.

**SHERLOCK assay workflow:**
```
1. Sample RNA/DNA extracted (quick lysis kit or NFSIM-PCR-03 LAMP amplification)
2. T7 transcription (if DNA target): converts amplified DNA to RNA target
3. CRISPR-Cas13a + crRNA added:
   - crRNA guides Cas13a to target RNA sequence
   - Cas13a binds target → activates collateral cleavage activity
   - Collateral cleavage destroys fluorescent RNA reporter molecules
   - Reporter: quenched RNA with FAM fluorophore (e.g., FAM-AAAA-Biotin, Iowa Black quencher)
4. Read fluorescence: target present → high fluorescence (reporters cleaved = dequenched)
   Wait, actually: in SHERLOCK with clamped crRNA, presence of target INCREASES cleaveage
   → cleaved reporters = INCREASED fluorescence (quencher separated from fluorophore)
5. OR: lateral flow: biotinylated reporter captured at test line when intact; cleaved reporter runs through

Incubation: 37°C for 1 hour (or 45°C for 30 min accelerated)
```

**Hardware Stack:**
```
Heating system:
- Single 40×40mm Peltier module (only heating needed, 37–42°C)
- Aluminum block with 8-tube strip format
- Temperature uniformity: ±1°C (less critical than PCR)
- Setpoint: 37°C (SHERLOCK/DETECTR), 65°C if combined with LAMP pre-amp

Fluorescence detection:
- Excitation: 470nm LED (FAM excitation) + 530nm LED (HEX/VIC excitation)
- Emission filter: 520nm bandpass (FAM), 570nm bandpass (HEX)
- Per-well detector: OPT101 photodiode × 8
- ADC: ADS1115 × 2 (8 channels total)
- Measurement: end-point fluorescence (single read at assay completion) OR
  Real-time kinetic monitoring (every 5 min during incubation)

Lateral flow strip reader:
- White LED transilluminator
- CMOS camera (OV2640 2MP) images lateral flow strip
- AI model on-device classifies positive/negative/invalid (ResNet-8, INT8 TFLite)

MCU: STM32G474
BLE: nRF52840
Display: 2.4" TFT (same as PCR-01)
Battery: 2000mAh LiPo

Consumables (per test):
- SHERLOCK master mix (freeze-dried): Cas13a protein, crRNA, reporter RNA, buffer
  Reconstituted with nuclease-free water per test
- LwCas13a protein: commercially available (GenScript, Sigma-Aldrich)
  Cost: ~$5–20 per test depending on supplier and batch size
- Lateral flow strips (Milenia HybriDetect format): ~$2 each

Design priority for open-source: 
  crRNA synthesis is published/open (can order from any oligo synthesis service)
  Cas protein expression protocols are published
  Full open-source SHERLOCK protocol published by Broad Institute/MIT
```

**BOM Estimate: ~$96 reader + $5–20/test reagents**

---

#### NFSIM-dPCR-01 — Digital Droplet PCR System

**Concept:** Digital PCR by oil-water emulsion partitioning. Sample partitioned into ~20,000 nanoliter droplets. After PCR amplification, each droplet is either positive or negative. Poisson counting gives absolute molecule quantification without standard curves. Critical for liquid biopsy ctDNA detection at 0.01% VAF.

**Hardware Stack:**
```
Droplet generation (microfluidic chip):
- PDMS chip with T-junction or flow-focusing channel geometry
- Channel dimensions: 50–100μm width × 30–50μm depth
- Oil phase: Droplet Generation Oil (Bio-Rad compatible formulation or open alternative)
- Aqueous phase: PCR master mix + sample
- Flow control: precision syringe pumps (stepper motor driven)
  - Aqueous: 0.2–1 μL/min
  - Oil: 2–10 μL/min
- Droplet size: 1–5 nL (20,000 droplets from 20 μL sample)

Chip fabrication (open):
- Soft lithography from SU-8 master mold (photolithography required, OR)
- Commercial PDMS chips (Dolomite, Micralyne — specify open design)
- 3D printed mold (Formlabs Clear V4 resin, post-cured, PDMS cast)

Thermal cycling:
- Chip placed in flat-block thermocycler
- 40 cycles PCR at standard temperatures
- Chip sealed with adhesive film before cycling

Fluorescence readout station:
- Droplets flow through serpentine channel past detector
- Two-color detection: FAM (blue excitation) + HEX (green excitation)
- Detector: photomultiplier tube (R7400P, Hamamatsu) or avalanche photodiode
- Excitation lasers: 488nm (10mW) + 532nm (5mW)
- Dichroic + bandpass filters: standard epifluorescence configuration
- Flow rate: 1–2 μL/min during readout
- Data: amplitude histogram → threshold → count positives/negatives

Data analysis:
- Poisson statistics: concentration = -ln(1 - positives/total) × (dilution/droplet_volume)
- 2D clustering (Ch1 vs Ch2 amplitude) → mutation discrimination
- Software: open-source DropViz or Python ddPCR analysis library

MCU: STM32H7 (high-speed ADC + image processing)
Laser control: dedicated driver ICs
Pumps: TMC2209 stepper motor driver
```

**BOM Estimate: ~$285 (excludes laser sources if salvaged)**

---

#### NFSIM-GELEC-01 — Portable Complete Gel Electrophoresis System

**Concept:** Full portable gel electrophoresis with real agarose casting, UV LED safe visualization, and CMOS gel documentation. Self-contained in a lunchbox-sized unit. Uses standard laboratory gel electrophoresis technique but miniaturized and battery-powered.

**What makes this different from NFSIM-PCR-02:** PCR-02 uses pre-cast disposable gel strips optimized for consumer use. GELEC-01 supports casting any agarose concentration from powder, using standard molecular biology protocols, for research applications.

**Hardware Stack:**
```
Gel tank:
- Internal tank: 80×65mm casting area
- Accepts: standard 0.7–2.5% agarose gels
- Includes: casting tray, comb set (6 or 12 teeth)
- Buffer: TBE or TAE (user prepared)

High-voltage power supply:
- Output: 10–200V DC adjustable
- Current: 0–500mA
- Safety: current limiting, HV interlock with lid
- HV generation: flyback converter (UC3845 PWM controller)
- Voltage feedback: resistive divider + TL431 reference
- Current measurement: INA219

Gel visualization:
- UV LED array: 12× 365nm UV LEDs (1W each) in lightbox below gel tray
- Safety interlock: UV LEDs off when viewing window is open
- Viewing window: Orange UV-blocking acrylic (>500nm cutoff)
- CMOS camera: OV5640 5MP, positioned above gel through orange filter
- Exposure: auto-exposure via OV5640 driver

Safety:
- UV protective orange goggle included
- Gel stain: SYBR Safe instead of ethidium bromide (non-mutagenic, UV-visible)
  Alternative: GelGreen (excites at 254nm, 302nm, or 491nm)
  Note: if EtBr used, treat waste as hazardous (outside scope of this design)

Documentation:
- Images saved to microSD card (JPEG, 5MP)
- Wi-Fi (ESP32 module) for wireless image transfer to phone/PC
- NFS Protocol: metadata packet with run parameters + image attachment reference

MCU: STM32G474 (main) + ESP32 (WiFi)
Display: 3.5" TFT (gel image preview)
Battery: 5000mAh LiPo (longer runtime needed for 45min runs + UV)
```

**BOM Estimate: ~$110**

---

### Domain B: Structural / Anatomical Imaging

---

#### NFSIM-US-01 — USB-C Handheld Ultrasound Probe (B/M/Doppler)

**Concept:** A handheld ultrasound probe that connects via USB-C to a smartphone or laptop. Opens ultrasound to the NanoFlowSIM ecosystem as a direct DICOM-generating, UBERON-tagging sensor. Inspired by commercial USB probes (Clarius, Butterfly IQ) but with open hardware design.

**Core physics implementation:**
```
Transducer array:
- 64-element linear array (or convex for abdominal)
- Element pitch: 0.25mm (linear) or 0.3mm (convex)
- Frequency: 7.5 MHz center (broadband 4–12 MHz usable)
- Element impedance: ~100Ω (PZT5H matching to electronics)
- Acoustic stack: 2× matching layers (quarter-wave PVA + polyurethane)
- Backing: 1-part epoxy + tungsten powder, ~5dB/cm acoustic attenuation

TX beamformer:
- 64 independent TX channels
- Pulser IC: HV748 (Supertex/Microchip) — 64-channel multiplexed high-voltage pulser
  - Peak voltage: ±100V
  - Rise time: <5ns
- TX timing: FPGA-controlled (sub-nanosecond precision)
- Apodization: Hanning window applied across aperture
- Focusing: delay-and-sum with programmable focus depth

RX signal chain (per channel):
- T/R switch: MOSFET or dedicated T/R switch IC (MD2012, Texas Instruments)
- LNA: AD8432 or LM6172 (low noise, high input impedance)
  Noise figure: <5dB at 7.5MHz
- TGC (Time Gain Compensation): programmable amplifier, 0–80dB range
  IC: AD9275 (8-channel LNA + TGC + ADC)
- ADC: AD9275 integrated 12-bit, 50MSPS (or external AD9634)

Digital beamformer:
- FPGA: Xilinx Artix-7 (XC7A100T on-board in small module)
- Receive delay calculation: pre-computed LUT for focus depths
- Dynamic receive focusing: updates focus delay every 0.5mm depth
- IQ demodulation: quadrature mixing at carrier frequency
- Envelope detection: complex magnitude
- Log compression: 40dB dynamic range compression
- Scan conversion: polar to Cartesian interpolation

Signal processing pipeline:
- B-mode: envelope → log compress → scan convert → render
- M-mode: single line repeated at PRF, time vs depth display
- Color Doppler: autocorrelation, velocity map overlay on B-mode
- Spectral Doppler: FFT, velocity spectrum vs time

Interface:
- USB-C (USB 3.1 Gen1): streams IQ data or rendered frames to host
  Bandwidth: 400MB/s available, typical usage 50–150 MB/s
- OR: Wi-Fi 802.11ac: 100–200 Mbps for wireless operation
- Power: from USB-C (5V/3A profile negotiated via USB-PD)

Processing options:
- On-probe beamforming (FPGA): streams DICOM-compatible frames
- Host-side processing: stream raw RF data to PC for software beamforming

Display: processed images rendered on phone app or desktop viewer
DICOM output: probe generates standard DICOM US format, NFS metadata header added
```

**NFS Data Packet:**
```json
{
  "data_type": "ultrasound_b_mode",
  "anatomy_region": "UBERON:0000948",
  "data": {
    "frames": "base64-JPEG array or DICOM reference",
    "depth_cm": 15,
    "frequency_mhz": 7.5,
    "mode": "B",
    "probe_type": "linear"
  }
}
```

**BOM (Key Items):**
```
PZT transducer array (custom, 64-element)    $120
Artix-7 XC7A100T module                      $65
HV748 64-channel pulser                      $35
AD9275 LNA+ADC (×8, 8ch each)               $180
USB 3.0 controller (FX3)                     $12
Enclosure + housing                          $35
Misc components                              $24

Total BOM estimate: ~$471
```

---

#### NFSIM-US-02 — Wearable Ultrasound Patch

**Concept:** A flexible, wearable ultrasound array that adheres to skin for continuous structural monitoring. Applications: continuous cardiac monitoring, blood flow monitoring, diaphragm mechanics during respiratory disease, muscle deformation analysis.

**Core innovation vs handheld probe:**
- Flexible PVDF piezoelectric film array instead of rigid PZT
- Serpentine interconnects allow bending without cracking
- Miniaturized beamformer ASIC or FPGA on rigid island
- Wireless BLE transmission (no tether)

**Hardware Stack:**
```
Transducer array:
- PVDF (polyvinylidene fluoride) film, 52μm thickness
- Array: 64 elements in 8×8 or 16×4 configuration
- Element size: 2×2mm
- Flexible PCB substrate: polyimide (Kapton), 25μm
- Serpentine copper interconnects: 100μm trace width, 50μm space

ASIC requirements (custom or FPGA-based):
- 64-channel TX/RX switching
- Miniaturized beamformer
- Low-power operation: <100mW total
- Key challenge: custom ASIC needed for production; FPGA for prototype

Coupling gel layer:
- Hydrogel adhesive: medical-grade polyacrylamide hydrogel
- Acoustic impedance: ~1.5 MRayl (matches tissue)
- Sticks to skin without irritation, reusable × 100 applications
- Replacement hydrogel pads: disposable, ~$0.50 each

Wireless:
- nRF52840 BLE 5.0 on rigid island
- Streaming: compressed envelope data, not raw RF
- Power: flexible lithium polymer battery (10×80mm, 150mAh)
- Duty cycle: 30 min on / 30 min off → 24h operation

Imaging parameters:
- Frequency: 3–7 MHz (optimized for depth vs. resolution tradeoff for continuous monitoring)
- Frame rate: 5–30 fps (application dependent)
- Depth: 3–8 cm (cardiac, diaphragm) or 1–3 cm (superficial)

UBERON tags: UBERON:0000948 (heart), UBERON:0001062 (internal structure per anatomy)

Clinical targets:
- Cardiac: continuous EF monitoring, wall motion, pericardial effusion tracking
- Respiratory: diaphragm excursion, lung sliding (pneumothorax detection)
- Vascular: carotid intima-media thickness over time, DVT surveillance
- Muscle: fascicle length, pennation angle during rehabilitation

Wearable duration: 24–72 hours
```

---

#### NFSIM-US-03 — Ingestible GI Ultrasound Capsule

**Concept:** A swallowable capsule containing a miniaturized ultrasound transducer array for 360° GI tract imaging during transit. Ultrasound penetrates into the GI wall and nearby organs from the inside — unlike standard capsule endoscopy which only sees the mucosal surface.

**Design:**
```
Dimensions: 26×11mm (slightly larger than standard capsule endoscope)
Total weight: <4g
Biocompatibility: Parylene-C coated exterior, medical-grade ABS housing

Transducer:
- CMUT (Capacitive Micromachined Ultrasound Transducer) ring array
  CMUT preferred over PZT for this application: thinner, silicon-based, integrates with ASIC
- Ring configuration: 64 elements arranged circumferentially (360° coverage)
- Frequency: 12–20 MHz (higher frequency for better resolution at short range)
- Imaging depth: 0–5 cm (GI wall + immediately surrounding structures)

Imaging modes:
- B-mode: real-time cross-sectional ultrasound image
- Radial: 360° radial scan = complete GI wall cross-section
- Doppler (limited): blood flow in mesenteric vessels if adjacent

RF electronics:
- Miniaturized ASIC or application-specific FPGA-in-package
- TX pulser: miniature HV pulsers (custom)
- RX: direct-conversion IQ demodulation
- Power budget: <25mW for electronics

Communication:
- 434 MHz FSK radio (body penetration superior to BLE at this range)
- Data rate: 1–10 Mbps (compressed envelope data, not raw RF)
- External receiver: wearable belt patch with 434MHz antenna and BLE bridge to phone

Power:
- Primary battery: silver oxide (SR927W equivalent, 2× in series = 3V)
- Expected runtime: 8–12 hours (sufficient for complete GI transit from swallow to excretion)
- No recharging (single-use capsule)

Capsule position tracking:
- Method 1: Pressure signature pattern — stomach entry (high pressure peristalsis), pylorus crossing (characteristic pressure spike), ileocecal valve crossing
- Method 2: IMU — 6-axis IMU, orientation and motion during peristalsis
- Method 3: Transit time — calibrated average transit rates per GI segment
- Method 4: 434 MHz signal strength triangulation with external antenna array on body surface
- Combined: Bayesian position estimator integrating all methods
- Output: anatomical zone probability (esophagus / stomach / small intestine / colon)
- UBERON tagging: automatic per zone
```

---

#### NFSIM-US-04 — High-Frequency Dermal Ultrasound Scanner

**Concept:** High-frequency (20–50 MHz) contact ultrasound for skin imaging. Resolves epidermal thickness (0.05–0.2mm), dermis layers, subcutaneous structures. Useful for monitoring skin tumors, wound healing, dermatological conditions, nanoparticle delivery to skin.

```
Transducer: single-element 40MHz focused transducer
Mechanical scanning: X-Y piezo stage, 20×20mm scan area
Axial resolution: 35–50 μm at 40 MHz
Lateral resolution: 0.2mm
Depth: 3–8mm (penetration limited at high frequency)
Display: 2D cross-sectional B-mode + en-face C-mode
```

---

#### NFSIM-US-05 — Doppler Wristband (Radial Artery)

**Concept:** Wrist-worn continuous Doppler ultrasound for radial artery blood flow monitoring. More specific than optical PPG (pulse oximeter wristband) — measures actual blood velocity waveform, enabling beat-to-beat stroke volume estimation and continuous blood pressure waveform (via pulse wave analysis).

```
Transducer: dual-element 8MHz pulsed-wave Doppler
Location: radial artery at wrist
Coupling: ultrasound gel-impregnated silicone coupling layer
Signal: Doppler velocity spectrum + envelope = blood pressure waveform
Continuous operation: 8–12h per charge
Output: beat-to-beat BP estimate, HR, stroke volume estimate, arterial stiffness index
```

---

#### NFSIM-US-06 — Transcranial Doppler Headband (TCD)

**Concept:** Wearable transcranial Doppler for cerebral blood flow velocity monitoring. Measures flow in middle cerebral artery (MCA) through temporal bone window. Applications: stroke monitoring, cerebral autoregulation, intracranial pressure estimation.

```
Transducer array: 4× 2MHz probes positioned over bilateral temporal windows
Depth: 25–65mm (MCA, ACA, PCA)
Mode: pulsed-wave Doppler
Output: flow velocity, pulsatility index, Lindegaard ratio, auto-regulation index
Headband: adjustable, maintains probe position and coupling gel contact
```

---

#### NFSIM-US-07 — Endocavity Ultrasound Probe

**Concept:** Transvaginal or transrectal ultrasound probe for endocavity imaging. Connects to NFSIM-US-01 electronics module. Specific probe head geometry for endocavity insertion.

```
Probe head: 12×60mm cylindrical (transvaginal) or 15×80mm (transrectal)
Array: 128-element curved array, 5–9 MHz
Field of view: 150° sector
Applications: uterus/ovary imaging, prostate imaging, early pregnancy monitoring
Connection: proprietary probe port on NFSIM-US-01 reader
```

---

#### NFSIM-US-08 — Fetal Doppler Wristband

**Concept:** Wearable fetal heartbeat Doppler for continuous fetal monitoring at home during pregnancy (3rd trimester). Detects fetal heart motion via Doppler shift.

```
Transducer: 2–3 MHz continuous-wave Doppler
Location: maternal abdomen (adjustable band, 7–9 positions)
Output: fetal HR (continuous), fetal movement detection
Display: wristwatch-sized display
Alert: notification if FHR outside 110–160 bpm range
```

---

#### NFSIM-US-09 — Ultrasound Needle Guide

**Concept:** Clip-on ultrasound transducer that mounts to a syringe or needle guide, providing real-time needle visualization during injections or aspirations. Reduces procedure risk (prevents inadvertent vessel puncture during joint injections, spinal taps, etc.).

```
Clip mount: fits standard 3–5mL syringe
Transducer: 10MHz linear array, 20mm aperture
Needle visualization: beam-steer for needle angle display
Output: connects to phone via USB-C for real-time B-mode display
```

---

#### NFSIM-MRI-01 — Low-Field Portable MRI System

**Concept:** A 64 mT permanent magnet MRI system using a Halbach cylinder or similar permanent magnet array arrangement. No cryogenics. AI reconstruction compensates for reduced SNR at low field. Primarily for structural brain or extremity imaging.

**This is the most ambitious structural imaging device and requires significant development effort.**

```
Magnet design (Halbach cylinder):
- Array of N50 grade NdFeB permanent magnets
- Halbach arrangement: produces dipole field internally, near-zero external field
- Target field: 50–100 mT (Larmor frequency: 2.13–4.26 MHz for ¹H)
- Bore diameter: 15–25 cm (head-only, extremity, or small animal)
- Field uniformity: <100 ppm over 10cm DSV (shimming required)
- Passive shimming: additional magnet pieces, iteratively placed
- Weight: 30–80 kg depending on bore size

RF system:
- TX/RX coil: surface coil or single-channel solenoid/birdcage
- RF frequency: 2.13–4.26 MHz (much lower than clinical 64/128 MHz)
- RF power: 10–50W (much less than clinical systems)
- Pre-amplifier: low-noise JFET or GaAs FET (noise figure <0.5dB at 2–4 MHz)
- Quadrature detection: two orthogonal receivers for SNR improvement

Gradient system:
- Three gradient coils: Gx, Gy, Gz
- Amplitude: 10–50 mT/m (weaker than clinical but adequate for 64mT)
- Slew rate: 2–10 T/m/s
- Gradient amplifiers: Class-D audio amplifiers (100–300W)
  H-bridge: IRFS7430 + IR2010 gate driver
  Commercial option: Kepco BOP 20-20 analog amplifier

Shimming:
- Passive: NdFeB shim pieces in dedicated shim tray
- Active (optional): second-order shim coils, resistive
- Mapping: 3D field map scan + iterative algorithm

Reconstruction:
- Standard: Fourier-based (FFT) — same as clinical MRI in concept
- AI enhancement: U-Net or diffusion model trained on low-field images
  Trained to recover resolution from noisy low-field acquisition
  Open-source models available from FastMRI challenge datasets

Sequence library (open):
- Spin echo (SE): T1, T2 weighted
- Gradient echo (GRE): fast acquisition, susceptibility contrast
- Inversion recovery (IR): T1 mapping
- EPI (Echo Planar Imaging): fast (but challenging at low field due to B0 inhomogeneity)

Hardware controller:
- MRI console: custom or open-source (MaRCoS — Magnetic Resonance Control System)
  MaRCoS is an open-source MRI console project (GitHub: vnegnev/marcos_server)
  Runs on Xilinx Red Pitaya FPGA platform
  Generates RF pulses, gradient waveforms, acquisition triggers

Power:
- Gradient amplifiers: 3× 200W Class-D amps
- RF amplifier: 50W
- Total: ~700W from standard AC outlet

Shielding:
- 64mT fringe field is minimal — far less shielding needed than clinical
- Basic copper mesh Faraday cage for RF shielding (prevents pickup interference)
- No 5-Gauss line safety perimeter required

BOM estimate: $2,000–$8,000 depending on magnet design and bore size
```

---

#### NFSIM-XRAY-01 — Portable X-ray System

**Concept:** A battery-powered portable X-ray generator paired with a wireless flat-panel detector. Enables point-of-care radiography in field settings, remote clinics, or disaster relief.

**⚠ REGULATORY NOTE:** X-ray devices emit ionizing radiation. Operator training required. Regulatory approval varies by jurisdiction. This is RUO designation but real radiation hazards exist.

```
X-ray generator:
- Tube: mini rotating anode (Varian M111 or stationary Dunlee series)
  Or: fixed anode miniature tube (Newton Scientific MINI-X2)
- kVp range: 40–120 kVp
- mAs range: 0.5–320 mAs
- High-voltage generator: resonant inverter (DC-DC, target 120kV peak)
- Input power: Li battery 24V, 10Ah (for portable operation)
- Weight: 3–5 kg (tube + HV generator)
- Collimator: adjustable lead shutters with light field indicator

Detector (wireless FPD):
- Size: 35×43 cm or 30×35 cm
- Scintillator: CsI (thallium-doped), structured
- Active matrix: amorphous silicon TFT array
- Pixel size: 139–148 μm
- DQE: 60–70% at 70 kVp
- Wireless: 802.11ac dual-band
- Battery: built-in 6000mAh
- Commercial options (to repurpose into open system): iRay or Rayence OEM FPDs

Processing:
- Flatfield correction (dark field, air flat field calibration)
- Bone/soft tissue processing algorithms
- DICOM output (DR SOP Class)
- NFS metadata header addition
- Grid artifact removal (anti-scatter grid correction)

Safety features:
- Radiation indicator light
- Dead-man switch (exposure only when button held)
- Timer circuit limits max exposure time
- Exposure counter and cumulative dose tracker

BOM estimate: ~$3,500–$6,000 (FPD cost dominates)
```

---

#### NFSIM-OCT-01 — Portable Spectral Domain OCT Probe

**Concept:** A portable SD-OCT probe for dermatology, ophthalmology, and wound assessment. Generates cross-sectional tissue images at 1–15 μm axial resolution without contact. The ultrasound of light.

```
Light source:
- SLD (Superluminescent Diode): 840nm center, 50nm FWHM bandwidth
  Manufacturer: Superlum, Thorlabs
  Output power: 10–20mW
- Axial resolution: Δz = 0.44λ²/Δλ = 0.44×840²/50 = 6.2 μm (in tissue)

Interferometer:
- Fiber Michelson interferometer
- 2×2 50/50 fiber coupler (SMF-28e fiber)
- Reference arm: mirror on translation stage (for path length matching)
- Sample arm: galvanometric scanner + objective lens

Spectrometer:
- Diffraction grating: 1200 lines/mm transmission grating
- Collimating + focusing optics
- Line-scan camera: e2v Aviiva (1024 or 2048 pixels, InGaAs or Si)
- Camera interface: Camera Link or GigE Vision

Lateral scanning:
- Galvo mirrors: Cambridge Technology 6mm aperture
- Scan angle: ±10° mechanical = ±20° optical
- Scan speed: up to 100 A-scans/second for real-time B-mode

Processing:
- FPGA or GPU: FFT of spectral interferogram → A-scan
- Frame rate: 30 fps B-mode (500 A-scans per frame × 30 fps = 15,000 A-scans/s)
- Display: 3D rendering (en-face + cross-section)
- DICOM output: OCT SOP class

Handheld probe:
- Portable ophthalmoscope form factor
- Optional slit lamp adapter
- Patient fixation target (internal LED)
```

---

#### NFSIM-MICRO-01 — Portable Digital Pathology Microscope

**Concept:** A portable transmission microscope with motorized stage, LED illumination, and automated slide scanning for digital pathology. Supports fluorescence imaging with UV/blue excitation. AI-based cell classification on-device.

```
Optics:
- Objective: 10×, 20×, 40× (switchable, or turret)
- Illumination: LED Köhler (white for brightfield, 365nm UV + 470nm blue for fluorescence)
- Camera: 12MP IMX477 (Sony, for Raspberry Pi CM4 integration)
- Motorized XY stage: stepper motors, 50×25mm travel, 1μm step resolution
- Focus: piezo Z axis, 100μm range, 0.1μm resolution

Processing:
- Compute: Raspberry Pi CM4 (quad-core Cortex-A72, 8GB RAM)
- Whole-slide imaging: automated tiling, stitching (OpenSlide compatible output)
- AI cell classification: custom TFLite model for H&E-stained slides
  - Cell type: normal vs. abnormal morphology detection
  - Mitosis detection (cancer diagnosis support)
  - RBC/WBC counting for blood smears

Output:
- SVS/TIFF whole-slide images
- Cell count reports (JSON)
- UBERON-tagged NFS packets
- Wi-Fi or USB-C connection

Dimensions: 300×200×250mm (desktop portable, not handheld)
Power: 12V 3A adapter or 10,000mAh power bank
```

---

### Domain C: Chemical / Metabolic

---

#### NFSIM-CGM-01 — Open Continuous Glucose Monitor

**Concept:** A completely open-source CGM platform. Open hardware sensor with glucose oxidase chemistry, NFC passive readout + active BLE, 14-day wear target, OpenAPS/Loop compatible data output.

```
Sensor design:
- Working electrode: platinum wire 127μm diameter, 5mm insertion depth
- Enzyme layer: glucose oxidase (GOx) crosslinked with BSA + glutaraldehyde
- Polymer membrane: polyurethane outer (glucose diffusion limiter, biocompatibility)
  + Nafion inner (H2O2 selectivity, blocks interfering species)
- Reference electrode: Ag/AgCl (3mm disk on sensor housing)
- Counter electrode: platinum ring on housing

Electrochemistry:
- Applied potential: +0.6V vs Ag/AgCl (oxidizes H2O2 from GOx reaction)
- Current range: 1–30 nA (glucose 40–400 mg/dL)
- Interferents blocked by Nafion membrane: ascorbic acid, acetaminophen, uric acid
- Calibration: factory calibration (50 sensors calibrated at 3 glucose concentrations)
  OR fingerstick-based in-vivo calibration (1× per wear period)

Electronics:
- ASIC: custom low-power AFE OR
  Texas Instruments LMP91000 (potentiostat IC, programmable)
  + Current-to-voltage: transimpedance amplifier (gain 1 MΩ → 1nA = 1mV)
- ADC: 16-bit, 1 sample/minute (glucose changes slowly)
- MCU: nRF52840 (BLE + NFC)
- NFC: ISO 15693 (13.56 MHz passive readout, compatible with phone NFC)
  Range: 2–3 cm through clothing
- BLE: active connection every 5 minutes for alert-capable streaming
- Battery: 25mAh coin cell (CR1616 equivalent) for 14-day operation
  Ultra-low power design: 5–15 μA average current drain

Transmitter unit:
- PCB: 12mm × 12mm (miniaturized to fit within sensor housing)
- Housing: epoxy-filled ABS, IPX7 water resistant
- Adhesive: medical-grade acrylic adhesive, skin patch
- Applicator: spring-loaded needle applicator (inserts filament, then retracts needle)

Data output (NFS protocol):
- UBERON: UBERON:0000178 (blood) / UBERON:0004537 (interstitial fluid)
- Update rate: every 5 minutes
- Units: mg/dL or mmol/L (user configurable)
- Trend: rate of change (mg/dL/min), directional arrows
- OpenAPS compatibility: Nightscout endpoint or local REST API

Factory calibration vs user calibration:
- Factory: each sensor batch calibrated in vitro against reference analyzer
  Calibration coefficients stored in NFC memory on sensor
- User: optional fingerstick at 6h and 12h for improved accuracy
- Accuracy target: MARD < 10% vs. reference analyzer

```

---

#### NFSIM-SWEAT-01 — Sweat Chemistry Patch

**Concept:** A flexible microfluidic wearable patch that analyzes sweat chemistry in real time. Measures sodium, potassium, pH, lactate, and sweat rate. Attached to skin like a large bandage, worn during exercise or continuously.

```
Microfluidics layer:
- Material: PDMS or laser-cut adhesive microfluidic tape
- Channels: serpentine sweat collector → individual ISE chambers
- Sweat inlet: laser-drilled pores through skin-adhesive layer
- Flow control: capillary pressure-driven (no pump needed)
- Volume: 5–20 μL total volume triggers sensors

Sensor array:
- Na+ ISE: PEDOT-based ion-selective membrane
- K+ ISE: valinomycin ionophore membrane
- pH ISE: polyaniline or iridium oxide film
- Lactate: lactate oxidase amperometric sensor
- Sweat rate: galvanic cell measuring skin conductance at inlet

Electronics:
- Multiplexed potentiostat: LMP91000 × 2 (for 4 ISE channels)
- Reference electrode: shared Ag/AgCl
- ADC: ADS1115 (16-bit, 4-channel)
- MCU: nRF52840
- BLE: 5-minute update interval
- Flexible PCB: polyimide, conductive polymer electrodes
- Power: thin-film battery (Enfucell SoftBattery, 50mAh)

Calibration:
- Factory: calibration sweat buffer pre-loaded in sealed chamber adjacent to sensor
  On first sweat contact: buffer releases → 2-minute calibration sequence
- Drift correction: continuous drift model (Na+ ISE drifts ~1mV/h)

Data interpretation:
- Na+ 20–80 mM (hyponatremia indicator if very low)
- K+ 3–8 mM
- pH 4.5–7.5
- Lactate 1–25 mM (exercise intensity marker)
- Sweat rate: nl/min/cm²

UBERON: UBERON:0001416 (skin surface, sweat gland region)
Note: sweat values ≠ blood values directly, correlation models provided
```

---

#### NFSIM-CHEM-01 — Portable Blood Chemistry Analyzer

**Concept:** A portable point-of-care blood chemistry analyzer using microfluidic test cartridges. A small fingerstick blood sample runs through a disposable cartridge containing dried reagents. Results in 2–4 minutes.

```
Analyzer unit (reusable):
- Microfluidic cartridge slot: accepts credit-card-sized cartridge
- Optical reader: LED-photodiode pairs at 4 wavelengths (415, 540, 575, 625nm)
  Measure colorimetric reactions (absorbance)
- Electrochemical reader: potentiostat for ISE-based cartridge tests
- Barcode scanner: reads cartridge type, lot, expiry
- LCD display: 2.4" TFT (same as PCR-01)
- MCU: STM32G474
- BLE: nRF52840
- Battery: 3000mAh LiPo
- USB-C: data export + charging

Disposable cartridge (15-analyte panel):
- 15 microfluidic lanes, each with specific reagent
- Dried reagent beads (rehydrated on sample addition)
- Wicking membrane controls flow
- Reaction windows: optically transparent

Analytes measured (example 15-panel):
Colorimetric:
- Total protein (biuret, 540nm)
- Albumin (BCG dye, 625nm)
- Total bilirubin (diazo, 540nm)
- ALT / AST (NADH oxidation, 340nm UV — LED)
- Alkaline phosphatase (4-NPP substrate, 405nm)
- Creatinine (Jaffe method, 510nm)
- BUN (urease + Berthelot, 625nm)
- Cholesterol (oxidase-peroxidase, 540nm)
- Triglycerides (GPO method, 540nm)
- Glucose (GOx-POD, 540nm)

Electrochemical (ISE):
- Na+ (sodium glass ISE)
- K+ (valinomycin ISE)
- Cl- (chloride ISE)
- CO2/bicarbonate (pCO2 electrode)
- Lactate (amperometric, lactate oxidase)

Accuracy targets (vs reference lab): within 5% MARD for most analytes
Cost per cartridge target: $8–15

UBERON: UBERON:0000178 (blood sample)
```

---

#### NFSIM-OXY-01 — Multi-Site NIRS Tissue Oxygenation Array

**Concept:** A wearable NIRS (Near-Infrared Spectroscopy) array with multiple source-detector pairs for continuous multi-site tissue oxygenation monitoring. Extends pulse oximetry to muscle oxygenation, cerebral oxygenation, and organ perfusion monitoring.

```
Principle:
- Modified Beer-Lambert law applied at multiple wavelengths
- Wavelengths: 730nm (sensitive to deoxy-Hb), 850nm (sensitive to oxy-Hb)
  Optional: 780nm (cytochrome c oxidase sensitive)
- Multiple source-detector distances: short (<15mm for superficial tissue correction)
  and long (30–45mm for deep tissue)
- Spatial resolution: ~1cm × 1cm per detector pair

Hardware:
- Optical sources: 730nm + 850nm + optional 780nm LED (Osram SFH series)
- Detectors: silicon photodiodes (Hamamatsu S2387-33R)
  or avalanche photodiodes (for better SNR at long separations)
- Source-detector geometry: flexible PCB, multiple source positions (4–8)
  and multiple detector positions (4–8) = 4–16 independent channels
- Modulation: 1kHz frequency division multiplexing (different frequencies per source)
  or time-division multiplexing (sequential source activation)
- Lock-in detection: synchronous demodulation to extract signal per source

Signal processing:
- Modified Beer-Lambert: calculate ΔHbO2, ΔHHb from ΔOD at two wavelengths
- Differential pathlength factor (DPF): age and tissue-specific correction
- Short-channel regression: remove superficial tissue contribution
- CBSI (corrected Beer-Lambert): motion artifact correction

Applications:
- Cerebral oxygenation (forehead placement): StO2, HbO2, HHb
  UBERON: UBERON:0001017 (brain)
- Muscle oxygenation (quadriceps, biceps during exercise):
  UBERON: specific muscle UBERON code
- Peripheral perfusion (forearm, calf): vascular health monitoring
- Tumor perfusion monitoring (if placed over accessible superficial tumor)

BLE: nRF52840, 1-minute averaged data updates (or 1-second for high-resolution)
Battery: 2000mAh, 8h continuous
Array size: 8×4cm flexible patch per site
```

---

#### NFSIM-BREATH-01 — Breath Metabolomics Device

**Concept:** An exhaled breath analyzer that measures metabolite signatures in breath. Breath contains >800 volatile organic compounds (VOCs). Several are disease biomarkers: acetone (diabetes, ketoacidosis), isoprene (cholesterol metabolism, liver disease), ammonia (renal failure), hydrogen sulfide (gut microbiome), CO (inflammation, anemia).

```
Two sensing technologies combined:

1. Photoacoustic sensor (for targeted molecules):
   - Quantum cascade laser: 7–9 μm mid-IR, tunable over absorption fingerprint region
     (or cheaper DFB IR laser for specific molecule)
   - Photoacoustic cell: Helmholtz resonator, microphone detection
   - Target molecules: CO2 (respiration rate), CO (1–10 ppm), NO (1–100 ppb — asthma)
   - Sensitivity: ppb range for CO/NO

2. Metal oxide semiconductor (MOX) e-nose array:
   - Array of 6–12 MOX sensors (Sensirion SGP40 or SGP41, or MQ series)
   - Each sensor responds differently to different VOC classes
   - Pattern: multivariate response vector → ML classification
   - Targets: acetone (>1.8 ppm: possible diabetes/ketosis), isoprene (<0.1 ppm: healthy range)
     ammonia (>1 ppm: possible renal failure)
   - Cross-validation: temperature cycling improves selectivity
   - Training data: breath samples from known conditions

Breath collection:
- Flow meter: integrated, detects exhalation flow
- Breath sampling valve: excludes dead space air (first 30% of breath)
  Collects alveolar air (late-exhaled, 150–200 mL)
- Condenser trap: removes water vapor (prevents MOX sensor saturation)
- One-way check valves ensure correct flow direction

MCU: STM32G474 (laser driver PWM + ADC for MOX + I2S for microphone)
BLE: nRF52840
Battery: 2000mAh (photoacoustic laser = highest power draw)
Use: blow through mouthpiece for 10 seconds → 90-second analysis → result
Disposable mouthpiece: standard medical mouthpiece, ~$0.30 each

UBERON: UBERON:0001707 (lung air, exhaled breath)
```

---

#### NFSIM-CHEM-02 — Saliva Chemistry Analyzer

**Concept:** Cartridge-based saliva analyzer. Saliva is accessible, non-invasive, and contains diagnostically relevant analytes: cortisol, alpha-amylase (stress markers), glucose, uric acid, nitrites (oral health), DNA (for rapid PCR prep), SARS-CoV-2 antigen.

```
Sample: passive drool into sample cup (1mL)
Cartridge: single-use, 8-analyte panel
Analytes: cortisol (ELISA immunoassay), alpha-amylase (enzymatic), glucose, uric acid,
          nitrite (Griess reagent), pH, sodium, total protein
Reader: same base unit as NFSIM-CHEM-01 (compatible cartridge slot)
UBERON: UBERON:0001836 (saliva)
```

---

#### NFSIM-CHEM-03 — Urine Dipstick Smart Reader

**Concept:** AI-powered digital urine dipstick reader. Standard commercial dipstick strips provide 10–14 parameters. This reader eliminates visual interpretation error with a CMOS camera + calibrated color analysis.

```
Hardware:
- Standard dipstick slot (accepts all major brands: Combur, Multistix)
- LED illumination: controlled intensity, 6500K color temperature
- Camera: OV5640 5MP
- Calibration target: integrated white balance + color calibration card
- MCU: STM32H743 (camera interface + color processing)
- BLE: nRF52840

Analysis:
- Each reagent pad photographed: RGB → HSV → compare to reference LUT
- Parameters: glucose, protein, ketones, blood, bilirubin, urobilinogen, nitrite,
              leukocytes, pH, specific gravity, creatinine (some strips)
- AI quality check: detects invalid/expired strip, insufficient dip time

UBERON: UBERON:0001088 (urine)
```

---

#### NFSIM-CHEM-04 — Portable Lipid Panel Analyzer

**Concept:** Fingerstick whole blood cholesterol panel. Total cholesterol, LDL, HDL, triglycerides in 3 minutes using enzymatic colorimetric cartridge.

```
Sample: 40μL whole blood (fingerstick)
Analytes: TC, LDL-C (Friedewald calculated or direct), HDL-C, TG, non-HDL-C
Cartridge: single-use, enzymatic reagent embedded
Reader: optical (same base as CHEM-01) with cholesterol-specific calibration
Accuracy: NCEP guidelines compliance target (CV < 3%, bias < 3%)
UBERON: UBERON:0000178 (blood) + UBERON:0004537 (systemic)
```

---

#### NFSIM-CHEM-05 — Portable Lactate Meter (Point-of-Care)

**Concept:** Handheld fingerstick lactate analyzer for sports performance, critical care triage, and metabolic monitoring. Similar to glucose meter but measuring blood lactate.

```
Chemistry: amperometric lactate oxidase sensor on disposable strip
Sample: 1.5μL whole blood (fingerstick)
Range: 0.5–30 mmol/L
Accuracy: ±2 standard deviation = ±0.3 mmol/L at low values, ±5% at high
Time to result: 15 seconds
Strips: 25-strip cartridge
UBERON: UBERON:0000178
```

---

#### NFSIM-CHEM-06 — Ketone + Beta-hydroxybutyrate Sensor

Blood ketone monitoring for ketogenic diet tracking, diabetic ketoacidosis screening, fasting monitoring.

```
Chemistry: amperometric beta-hydroxybutyrate dehydrogenase
Sample: 0.8μL whole blood
Range: 0–8 mmol/L BHB
UBERON: UBERON:0000178
```

---

#### NFSIM-CHEM-07 — Cortisol / Stress Hormone Sensor

Saliva cortisol immunoassay for diurnal cortisol monitoring (morning cortisol, evening cortisol, 4-point daily curve). Adrenal function assessment.

```
Method: competitive ELISA on microfluidic cartridge
Sample: 50μL saliva
Time: 15 minutes
Range: 0.5–60 nmol/L (covers physiological diurnal variation)
UBERON: UBERON:0001836 (saliva) → linked to UBERON:0001186 (adrenal gland)
```

---

#### NFSIM-CHEM-08 — Continuous Lactate Subcutaneous Sensor

**Concept:** Extension of CGM technology to lactate monitoring. Subcutaneous enzyme sensor for continuous lactate measurement. Research-grade; real-world continuous lactate sensing is technically harder than glucose due to enzyme sensitivity.

```
Working electrode: gold or platinum
Enzyme: lactate oxidase (LOx) crosslinked with polyurethane membrane
Applied potential: +0.5V vs Ag/AgCl (oxidizes pyruvate intermediate)
Current: 1–20 nA for 1–25 mmol/L lactate
Wear: 3–7 days target (shorter than glucose due to enzyme stability)
Electronics: same as NFSIM-CGM-01 (LMP91000 + nRF52840)
Applications: exercise physiology, ICU metabolic monitoring, sepsis screening
UBERON: UBERON:0001175 (interstitial fluid)
```

---

### Domain D: Electrical / Bioelectric

---

#### NFSIM-ECG-01 — Single-Lead ECG Patch (30-Day Continuous)

**Concept:** A credit card-sized ECG patch worn on the chest for up to 30 days. Captures single-lead ECG continuously. On-device AI detects AFib, PVC, pause events. Waterproof (IPX7). Equivalent to a Zio Patch but fully open.

```
Hardware:
- Electrodes: two dry Ag/AgCl electrodes, 35mm spacing, on device face
  OR gel electrode pads (disposable, snap-on)
- AFE: Texas Instruments ADS1291
  - 1 channel, 24-bit ADC
  - Noise: 4 μV RMS (≤150 Hz bandwidth)
  - Built-in 1-pole RC + internal programmable filter
  - Input impedance: >1 GΩ
  - CMRR: >105 dB
  - RLD output: reduces common-mode interference
- MCU: STM32L4 (ultra-low-power, Cortex-M4)
  - Active ECG recording: 2.5 mA
  - Sleep between acquisitions: 5 μA
  - Duty cycle: record 10s every 30s = 75% sleep → effective ~700μA average
- Storage: 32GB eMMC (stores 30 days of 250Hz single-lead ECG)
- BLE: nRF52840 (weekly summary uploads, alert transmission)
- Battery: 200 mAh LiPo sealed in device (non-user-replaceable, 30-day design)
- Waterproofing: conformal coating + silicone gasket around button, IPX7

On-device AI (TinyML):
- Model: custom LSTM-based ECG classifier (AFib, PVC, pause, normal)
- Size: ~20 KB INT8 quantized TensorFlow Lite Micro
- Inference: runs on 10-second windows every 5 minutes
- Power: 5 mW during inference on Cortex-M4, 0.1ms per inference
- Sensitivity/specificity: AFib detection >99%/>97% (target, trained on PhysioNet AF database)

Alert system:
- BLE alert when phone in range: detected arrhythmia type + timestamp
- Alerts also stored in local memory for next sync
- At sync (weekly BLE download), all arrhythmia events + 2min context ECG windows uploaded

Physical:
- Dimensions: 65×35×6mm (credit-card-ish)
- Weight: 12g
- Adhesive: proprietary breathable waterproof adhesive (compatible with Tegaderm)
  Replaceable: adhesive pad + outer sticker changed at 14 days for 30-day wear
- IPX7: tested 30 min at 1m submersion

Data flow:
- 250 Hz, 24-bit → compressed (delta encoding): ~300 KB/day raw
- 32GB @ 300 KB/day = 30,000 day capacity (far exceeds 30-day design)
- DICOM ECG SOP class output on sync
- NFS packet: continuous session, 5-minute summary segments

UBERON: UBERON:0000948 (heart)
BOM estimate: ~$35–$45 per unit (target production cost)
```

---

#### NFSIM-ECG-02 — 12-Lead ECG Vest (24–48h Holter)

**Concept:** Textile-based ECG recording vest with 10 electrode positions (standard 12-lead configuration), dry textile electrodes, continuous 24–48h recording at 1000 Hz for professional Holter monitoring.

```
Hardware:
- Electrodes: 10× conductive silver yarn electrode patches on inside of vest
  Positions: RA, LA, RL, LL (limb leads), V1–V6 (precordial leads)
  Electrode size: 30×30mm conductive fabric islands
  Impedance: 10–50 kΩ (dry skin contact)
- AFE: Texas Instruments ADS1298 (8-channel, 24-bit, SPI)
  - 8 simultaneous channels at up to 32,000 SPS per channel
  - Noise: 8 μVpp at 1000 Hz bandwidth
  - Runs at 1000 SPS per channel (standard Holter rate)
  - Two ICs in daisy-chain → 12 simultaneously sampled leads + 4 extra channels
- MCU: STM32H743 (processes all channels, manages storage)
- Storage: 32GB eMMC (stores 48h × 12 leads × 1000 Hz × 24-bit ≈ 26 GB)
- BLE: nRF52840
- Battery: 800 mAh LiPo (48h life at 20mA average draw)
- Electronics housing: rigid unit sewn into vest pocket, removable for washing

Vest:
- Material: performance fabric (polyester/spandex, moisture-wicking)
- Size range: XS–3XL (or custom/adjustable straps)
- Washable: remove electronics unit before washing
- Electrode contacts: snap connectors (gold-plated, spring-loaded)

Analysis:
- On-device: basic arrhythmia detection (AF, VT screening)
- Full analysis: export to PC for professional Holter analysis software
  Compatible: Mortara MARS (professional), or open-source WFDB tools
- Output: DICOM Holter ECG SOP, EDF+ format, NFS protocol

UBERON: UBERON:0000948 (heart)
```

---

#### NFSIM-EEG-01 — Dry-Electrode EEG Headset (8–16 Channels)

**Concept:** Open-source dry-electrode EEG headset compatible with OpenBCI Cyton board or custom ADS1299-based board. 8 or 16 channels. Applications: sleep staging, neurofeedback, BCI research, seizure monitoring.

```
Hardware:
- Electrodes: dry comb or cup electrodes (gold-plated spring-loaded)
  Array: 8-channel minimum (Fp1, Fp2, F3, F4, C3, C4, P3, P4)
  Optional 16-channel expansion (international 10-20 system)
  Reference: CMS/DRL electrodes (Active Reference)
- AFE: ADS1299 (Texas Instruments)
  - 8-channel simultaneously sampled
  - 24-bit ADC
  - Noise: 1 μVRMS input-referred
  - Input impedance: 1 GΩ
  - Gain: 24× (programmable 1–24)
  - CMRR: >110 dB
  - SPI interface
- MCU: STM32H743 (for processing) + nRF52840 (BLE)
  - Sampling: 250 Hz standard (up to 16 kSPS per channel)
  - Data streaming: BLE 5.0 (250 Hz × 8ch × 24-bit = 6kB/s, within BLE PHY 2M bandwidth)
- Power: 1200 mAh LiPo (8h continuous recording)
- Mechanical: adjustable headband, soft-touch silicone ear clips

Signal quality monitoring:
- Electrode impedance check: brief injected current at 1 kHz, measure voltage
  Per-electrode impedance: displayed as green (<10kΩ), yellow (10–50kΩ), red (>50kΩ)
- User-guided electrode placement with impedance feedback

Analysis (on-device or host):
- On-device: band power calculation (delta, theta, alpha, beta, gamma)
  Sleep stage classification (TFLite model, ~40KB)
  SSVEP detection (for BCI)
- Host: MNE-Python, EEGLAB, OpenViBE compatible output
- Output: EDF+ format, NFS protocol continuous session

OpenBCI compatibility: firmware mode that mimics OpenBCI Cyton SPI protocol
→ Works with OpenBCI GUI, BrainFlow, Neurosity SDK

UBERON: UBERON:0001017 (brain/central nervous system)
```

---

#### NFSIM-EMG-01 — 8-Channel EMG Armband

**Concept:** An 8-channel surface EMG armband for gesture recognition, prosthetic control, rehabilitation monitoring, and muscle activation mapping. Inspired by the Myo armband (discontinued) but fully open-source.

```
Hardware:
- Electrode configuration: 8 electrode pairs (16 total) arranged circumferentially
  Pairs spaced evenly around forearm circumference
  Inter-electrode spacing: 20mm within pair, ~45° arc between pairs
- Dry electrodes: conductive silicone with silver coating
  Contact area: 10×10mm per electrode
- AFE: ADS1298 (8-channel, 24-bit)
  - 8 simultaneous differential EMG channels
  - Bandwidth: 10–500 Hz (bandpass filter)
  - Sample rate: 2000 SPS (captures individual MUAPs and spectral content)
  - Gain: 12× (programmable)
- IMU: ICM-42688-P (6-axis, accelerometer + gyroscope)
  - 3-axis ACC ±16g, 3-axis GYR ±2000°/s
  - ODR 100Hz
  - For orientation, motion artifact removal, and gesture context
- MCU: STM32H7 (real-time EMG processing)
- BLE: nRF52840 (streaming at 2kHz × 8ch × 16-bit = 32kB/s, needs BLE 5.0 2M PHY)
- Battery: 500 mAh LiPo (6h continuous streaming, 12h with duty cycling)
- Mechanical: elastic adjustable band (22–35cm circumference range)

On-device gesture recognition (TinyML):
- Features: MAV (Mean Absolute Value), WL (Waveform Length), ZC (Zero Crossings)
  per 200ms window
- Classifier: MLP or SVM, INT8 quantized, ~50KB model
- Gestures: open, close, pinch, supination, pronation, point, grip, wrist flex/extend
  Accuracy: >90% on trained user
  Cross-user: ~70% (personalization training recommended)
- Inference latency: <10ms for real-time prosthetic control

Research mode: raw 2000 Hz data stream via BLE for full signal analysis

UBERON: UBERON code for specific muscle group (user-specified on placement)
```

---

#### NFSIM-NEURAL-01 — High-Density ECoG Research Array

**Concept:** A 64-channel to 256-channel electrocorticography (ECoG) research electrode array with flexible Parylene-C substrate and Intan RHD2000 series acquisition front end. Designed to interface with open-source acquisition systems (Open Ephys).

```
Electrode array:
- Substrate: Parylene-C (5μm base coat, 2μm encapsulation)
  Biocompatible, transparent, flexible, ultra-thin (8–10μm total)
- Electrode material: iridium oxide (IrOx) or PEDOT:PSS
  IrOx: high charge injection capacity, low impedance (<100kΩ at 1kHz)
  PEDOT:PSS: better biocompatibility, lower stiffness
- Array size: 4×4 (16ch), 8×8 (64ch), 16×16 (256ch)
- Electrode diameter: 200μm, pitch 400μm
- Connection: ZIF (zero insertion force) connector to PCB

Acquisition electronics:
- Intan RHD2132 (32ch) or RHD2216 (16ch) per module
  - 16-bit ADC, 20 kSPS per channel
  - On-chip bandwidth filter: 0.1 Hz – 20 kHz (configurable)
  - SPI interface, daisy-chainable
  - 0.98 μVRMS noise (300 Hz – 10 kHz)
- FPGA controller: Xilinx Artix-7 (data aggregation from multiple Intan chips)
- Open Ephys compatibility: USB interface to Open Ephys GUI
  (Open Ephys is the standard open-source neural recording software)

Data rates:
- 64ch @ 20kHz × 16-bit = 2.56 MB/s → USB 3.0 streaming
- On-system buffering: 1 GB SDRAM

Applications:
- Intraoperative seizure mapping (research only)
- BCI research (finger movement decoding, speech BCI)
- Sensory processing studies (somatosensory, auditory)

UBERON: UBERON:0001017 (central nervous system, brain surface)
NOTE: This device requires surgery for placement. Lab/research only.
```

---

#### NFSIM-EOG-01 — Electrooculography Sensor

**Concept:** Around-eye electrodes for eye movement tracking. Measures horizontal and vertical eye position via corneoretinal potential (the eye acts as a dipole — cornea positive relative to retina).

```
Hardware:
- 4 electrodes: nasal and temporal positions each eye (or 2 electrodes for horizontal only)
- AFE: ADS1299 (low noise, sufficient for EOG amplitudes of 0.5–5mV)
- Sampling: 250 Hz (EOG bandwidth <30 Hz)
- BLE streaming

Applications:
- Sleep stage detection (REM characterized by saccades)
- HCI (eye-gaze interface for mobility impaired)
- Nystagmus detection
- Driver fatigue monitoring
UBERON: UBERON:0004548 (eye)
```

---

#### NFSIM-EDA-01 — Electrodermal Activity Monitor

**Concept:** Wristband-based EDA/GSR (Galvanic Skin Response) sensor for sympathetic nervous system activity monitoring. Stress, arousal, emotion research.

```
Hardware:
- Two Ag/AgCl electrodes on volar wrist surface (thenar/hypothenar eminence preferable,
  but wrist convenient for wearable)
- 500mV AC, 30 Hz, applied between electrodes
- Skin conductance measured: 0.05–30 μS range
- ADC: 24-bit (ADS1256 for high precision)
- High-pass + synchronous demodulation: extract DC skin conductance level
  + phasic SCR (skin conductance response)
- BLE: nRF52840
- Battery: 200mAh (days of continuous monitoring at 4 Hz sample rate)
- Sampling: 4 Hz continuous, 64 Hz burst for acute response capture

Output:
- SCL: tonic baseline (μS)
- SCR: phasic event amplitude and latency
- SDSCL: standard deviation of SCL (arousal variability metric)

UBERON: UBERON:0001416 (skin, eccrine gland region)
```

---

### Domain E: Ingestible / Traversing Capsules

The ingestible capsule domain is unique in NanoFlowSIM because it represents sensors that physically traverse the body rather than being attached externally.

**Universal capsule position tracking system:**
All NanoFlowSIM capsules implement the same position estimation algorithm:

```
Position Estimator inputs:
1. Pressure sensor readings (peristaltic pressure waves)
2. IMU: acceleration + gyroscope (peristaltic motion patterns)
3. Elapsed time from swallow (calibrated transit time models)
4. Optional: pH sensor readings (stomach pH 1–3, small intestine pH 6–7, colon pH 7–8)
5. Optional: 434MHz signal strength from external antenna array

Anatomical zone output (with confidence):
- Esophagus: 5–15 seconds post-swallow (rapid transit)
- Stomach: 15 min – 4 hours (highly variable based on meal content)
- Duodenum: 20 min – 5 hours
- Small intestine (jejunum + ileum): 2–8 hours
- Ileocecal junction: identifiable by pH shift and pressure pattern change
- Colon (ascending, transverse, descending): 10–72 hours
- Rectosigmoid: terminal phase, pressure pattern change

UBERON tagging per zone:
- Esophagus: UBERON:0001043
- Stomach: UBERON:0000945
- Duodenum: UBERON:0002114
- Jejunum: UBERON:0002115
- Ileum: UBERON:0002116
- Colon: UBERON:0001155
```

**Universal capsule communication constraints:**
- 434 MHz FSK (external body-penetrating radio, better than 2.4 GHz at depth)
- Data rate: 10–100 kbps (limited by power budget)
- Power budget: <25mW for electronics (extends battery life for 8–24h transit)
- External: wearable receiver belt → BLE bridge → smartphone app

---

#### NFSIM-CAP-01 — Optical Imaging + Chemistry Capsule (GI Camera + pH/O2/Temp)

**Concept:** Standard capsule endoscopy camera PLUS real-time pH, oxygen, and temperature sensors. Maps optical images with precise chemical environment data. Provides context for interpreting mucosal findings (inflamed areas are often hypoxic, low pH).

```
Dimensions: 26×11mm
Total weight: <3.5g

Imaging system:
- Front: CMOS camera OV9726 (1MP, 60fps)
  - FOV: 160° fisheye lens
  - Illumination: 4× white LEDs (580nm warm white, oriented around lens)
  - Frame rate: 4 fps (standard capsule rate), up to 60 fps burst
  - Resolution: 640×480 @ 4fps for 8h streaming
- Rear: optional second camera (for 2-directional coverage)

Chemical sensors:
- pH: ISFET sensor (ion-sensitive field effect transistor, H+ selective)
  Range: 1–8 pH, accuracy ±0.3 pH
- Oxygen: Clark-type O2 electrode (gas-permeable membrane)
  Range: 0–100% pO2
- Temperature: NTC thermistor 10kΩ B=3950
  Range: 20–45°C, accuracy ±0.2°C

Position sensors:
- IMU: ICM-42605 (6-axis)
- Pressure: BMP581 (absolute pressure, peristaltic wave detection)

Electronics:
- MCU: STM32L4R9 (low power, camera interface, multiple sensor ADCs)
- Memory buffer: 8MB PSRAM (frame buffer + data buffer)

Communication:
- 434 MHz FSK transmitter: Si4463 (Silicon Labs)
  Transmit power: 10 dBm (regulatory limit for implantable body devices in some regions)
  Data rate: 76.8 kbps (sufficient for compressed JPEG frames + sensor data)
  JPEG compression: hardware-assisted, target 15KB/frame at 640×480

Power:
- Primary battery: 2× SR44 silver oxide batteries (3.0V, 200mAh total)
  Or: custom thin lithium battery
- Expected runtime: 8–12 hours active imaging
- Power management: sleep between frames, wake for transmission

External receiver:
- Belt-worn unit with 4-antenna diversity array (434MHz)
- STM32H7 + nRF52840 (receiver + BLE bridge)
- Records all received frames + sensor data → syncs to phone via BLE

Data volume:
- 4fps × 15KB/frame = 60KB/s × 8h = 1.7 GB total
- Compressed on receiver side: run-length encoding for similar frames
- Final: ~400-800 MB per complete GI transit study

Clinical applications:
- Small bowel Crohn's disease detection
- Occult GI bleeding (video + hemoglobin sensor)
- Barrett's esophagus surveillance
- Celiac disease (villous atrophy pattern recognition via AI)
```

---

#### NFSIM-CAP-02 — GI Ultrasound Capsule (Intraluminal US)

**Concept:** Capsule with an ultrasound transducer array for transmural GI wall imaging from the inside. Sees GI wall layers (mucosa, submucosa, muscularis propria) plus nearby structures (mesenteric lymph nodes, portal vein, pancreas from stomach/duodenum).

```
Dimensions: 32×13mm (slightly wider than CAP-01 due to US transducer ring)

Transducer:
- CMUT (Capacitive Micromachined Ultrasound Transducer) ring
- 64 elements circumferentially arranged
- Frequency: 15–20 MHz
- Imaging depth: 3cm radially (enough to see full GI wall + local lymph nodes)
- Radial 360° coverage: B-mode scan every 0.5 seconds

Electronics:
- Custom low-power TX pulsers (miniaturized, 12-channel multiplexed)
- TIA: OPA657 or similar low-noise, ultra-small package
- ADC: ADS8661 (12-bit, 10MSPS)
- FPGA: iCE40UP5K (low power, small package) for beamforming
- MCU: STM32L4 for sensor control + data management

Communication:
- 434 MHz at 250 kbps (compressed US frames)
- Frame size: 512 samples × 64 elements × 10-bit = ~41kB raw
  After beamforming + JPEG compression: ~8KB per frame

Power:
- Battery: 2× custom prismatic lithium, 180mAh total
- Runtime: 8h (us scan every 0.5s = 58,000 frames)

Position tracking:
- Pressure + IMU (same as CAP-01) + radial US can identify lumen diameter changes at transitions

Clinical applications:
- EUS (Endoscopic Ultrasound) equivalent without tethered endoscope
- Submucosal tumor assessment
- Lymph node staging in GI cancer
- Pancreatic cyst surveillance
```

---

#### NFSIM-CAP-03 — DNA / RNA Capture Capsule

**Concept:** A capsule that mechanically captures cellular material and luminal contents from the GI tract at a specific anatomical location for DNA/RNA extraction. When triggered (pH change or remote trigger), a collection chamber opens and samples surrounding fluid/cells, then seals. Patient excretes capsule, retrieves it, and processes sample for sequencing.

```
Dimensions: 28×11mm

Collection mechanism:
- Trigger: pH sensor + timer
  When pH rises above 6.5 (small intestine) → trigger opens collection door
  OR: magnetic external trigger (patient holds magnet to abdomen)
  OR: timed trigger (set for estimated transit time to target segment)
- Door mechanism: shape-memory alloy (nitinol wire, heats to 45°C → actuation)
  Or: electrochemical valve (dissolving anode releases spring-loaded door)
- Collection chamber: 50μL gold-coated chamber

Sample preservation:
- RNAlater-equivalent preservation solution pre-loaded in chamber
- Immediately stabilizes RNA upon sample contact
- Chamber seals automatically after 60 seconds (spring mechanism)

Retrieval protocol:
- Patient collects stool sample, retrieves capsule (floats or color-coded)
- Ships in provided cold pack or processes locally within 24h
- Processing: standard bead-based DNA/RNA extraction → NFSIM-SEQ-01 or commercial sequencer

Applications:
- Gut microbiome sampling at specific GI locations (not just fecal — luminal at jejunum, ileum)
- Small bowel mucosal gene expression (RNA from shed epithelial cells)
- Tumor DNA shedding detection (cfDNA from early GI tumors)
- Drug metabolism gene expression in enterocytes (CYP3A4, etc.)

Power:
- Small primary battery (only needed for sensor monitoring + actuation, not communication)
- Runtime: 24–48h standby, 1 actuation event
```

---

#### NFSIM-CAP-04 — Full Multi-Modal Research Capsule

**Concept:** The ultimate ingestible research platform combining all sensor modalities in one capsule. Larger than clinical capsules — designed for research studies where capsule size is acceptable (volunteer studies).

```
Dimensions: 36×13mm (large, borderline swallowable for some subjects)

Integrated systems:
- Dual CMOS cameras (front + rear optical)
- CMUT ultrasound ring (15MHz, 32-element)
- Chemical sensors: pH, pO2, temperature, glucose
- Bioimpedance: 4-electrode array, 1kHz–1MHz sweep (GI tissue properties)
- IMU: 6-axis
- Pressure: peristaltic detection
- DNA capture: triggered collection chamber (100μL)
- Drug delivery: micro-reservoir (optional payload, e.g., drug or nanoparticle bolus)
  Release trigger: pH + position confirmation
  Volume: 50–200μL

Communication:
- 434MHz FSK + 2.4GHz (burst mode when in stomach, external antenna strong enough)
  434MHz primary: 100kbps for sensor data
  2.4GHz secondary: for video bursts when signal permits

Power:
- 300mAh custom lithium stack
- Smart power management: activate each sensor only when in relevant GI segment
  (cameras active throughout; US active in stomach/duodenum; DNA capture in target region)
- Runtime: 12–16 hours

Applications:
- Complete GI tract characterization study
- Nanoparticle GI delivery research (dose a NP suspension, CAP-04 tracks its progression)
- Drug absorption studies (watch drug release + detect chemical changes in lumen)
```

---

#### NFSIM-CAP-05 — Core Temperature Capsule

**Concept:** Minimalist capsule for core body temperature monitoring. The simplest ingestible sensor. Core temperature measured inside GI tract is more accurate than rectal, tympanic, or axillary measurement.

```
Dimensions: 22×9mm (small, easiest to swallow)
Sensor: precision NTC thermistor, accuracy ±0.05°C
Communication: 434MHz FSK, 1 reading/minute
Power: 24h on single SR41 cell
Applications: fever monitoring, heat stroke prevention, athletic heat management
UBERON: UBERON:0002110 (lumen of GI tract, temperature of core body)
```

---

#### NFSIM-CAP-06 — pH / Pressure / Motility Capsule

**Concept:** Equivalent to commercial SmartPill (Medtronic). Monitors pH, temperature, and pressure throughout the entire GI tract. Provides complete motility profile (gastric emptying time, small bowel transit time, colonic transit time).

```
Sensors: pH (ISFET), temperature (NTC), pressure (BMP581 or equivalent)
Communication: 434MHz
Sampling: pH every 5s, pressure every 0.5s (to capture peristaltic waves)
Data: complete motility profile → gastric emptying time, GI transit time, motility index
Clinical use: gastroparesis diagnosis, chronic constipation evaluation, IBS workup
```

---

#### NFSIM-CAP-07 — Microbiome Sampling Capsule

**Concept:** Time-controlled, site-specific microbiome sampling with anaerobic preservation. The critical challenge: gut microbiome samples from stool are heavily contaminated with colonic bacteria, missing the small intestinal microbiome. CAP-07 captures true luminal samples from any GI segment.

```
Trigger: timed gelatin capsule dissolution (designed for specific GI segment based on transit time)
  Outer capsule: standard HPMC coating (dissolves at pH > 7.0 = small intestine)
  Inner capsule: custom timed release
Collection: anaerobic sealed chamber with pre-deoxygenated collection medium
  Medium: prereduced BHI (Brain-Heart Infusion) + glycerol for cryoprotection
Preservation: temperature-stable for 24h without refrigeration
Sample volume: 100μL
Downstream processing: 16S rRNA sequencing, shotgun metagenomics
UBERON: UBERON:0002115 (jejunum) or other target segment
```

---

#### NFSIM-CAP-08 — Drug Delivery Verification Capsule

**Concept:** A capsule that verifies whether an orally administered drug actually dissolves and is available for absorption in the intended GI segment, rather than passing through unabsorbed.

```
Internal sensors: UV/Vis photodetector + LED at drug's absorption wavelength
Detection: measures local drug concentration in GI lumen as drug dose capsule
  dissolves in same region
Trigger: same location trigger as target drug dose capsule
Output: drug dissolution profile (concentration vs. time at target site)
  → pharmacokinetic ground truth at absorption site
Applications: biopharmaceutics research, generic drug bioequivalence
```

---

#### NFSIM-CAP-09 — Oxygen Mapping Capsule

**Concept:** Sequential oxygen measurements throughout the GI tract. Oxygen gradient is diagnostically relevant: gut mucosal inflammation correlates with local hypoxia. Anaerobic microbial regions can be mapped.

```
Sensors: Clark-type O2 electrode (5 readings/minute)
Output: pO2 profile vs. anatomical position
Normal: stomach ~10-15 mmHg, small intestine 5-10 mmHg, colon near 0 mmHg
Pathological: IBD → extreme hypoxia at inflamed segments
```

---

#### NFSIM-CAP-10 — GI Bleeding Detection Capsule

**Concept:** Hemoglobin-sensitive capsule for detecting occult GI bleeding. Combines optical (hemoglobin absorption at 575nm and 540nm) with chemical (heme peroxidase activity detection) sensing.

```
Sensors:
- Dual-wavelength LED-photodiode pair (540nm + 575nm absorption of oxyhemoglobin)
- Guaiac reaction on micro-pad: peroxidase activity of heme → colorimetric
  Detected optically after contact with lumen

Output: hemoglobin concentration estimate at each GI segment
Sensitivity: detects 0.5mg Hb/mL (matches clinical sensitivity for occult blood)

Applications:
- Occult GI bleeding source localization (is it in small bowel vs. stomach vs. colon?)
- Iron deficiency anemia investigation
- Post-polypectomy monitoring
```

---

### Domain F: Flow Cytometry & Environmental

---

#### NFSIM-FLOW-01 — Portable Flow Cytometer

**Concept:** A portable acoustic-focusing flow cytometer for complete blood count (CBC) estimation and cell classification. Not a replacement for clinical-grade hematology analyzers but a field-deployable cell counting device.

```
Core principle:
- Blood cells flow single-file through focused laser beam
- Forward scatter (FSC): cell size
- Side scatter (SSC): cell granularity/complexity
- Fluorescence: labeled antibodies or intracellular markers (with sample prep)

Acoustic focusing:
- Acoustic focusing (not sheath flow) used to center cells in channel
- Piezoelectric actuator at resonant frequency focuses particles to channel center
- Eliminates need for precision hydrodynamic sheath fluid system
- Simplifies fluidics dramatically for portable design

Hardware:
- Laser: 488nm solid-state diode (20mW CW)
  OR: 405nm (violet) for additional fluorescence channel
- Optics: beam shaping (cylindrical lens), focusing objective
- Detection:
  - FSC: photodiode (on-axis)
  - SSC: photodiode (90°)
  - FL1: photodiode with 530/30nm bandpass (FITC, Calcein)
  - FL2: photodiode with 585/42nm bandpass (PE, PI)
  - Optional FL3: 650nm longpass (PerCP, PI dead stain)
- Transimpedance amplifiers: OPA657 per detector
- ADC: ADS8688 (8-channel, 16-bit, 500kSPS)
- FPGA: iCE40HX8K (event detection, histogram accumulation)
- MCU: STM32H743

Fluidics:
- Sample uptake: 50μL whole blood diluted 1:100 in PBS (automated diluter)
- Flow cell: quartz square capillary (250×250μm ID)
- Piezo actuator: 1MHz resonance, bulk acoustic wave focusing
- Waste collection: sealed waste bag (biohazard)
- Pump: precision peristaltic (Watson-Marlow micro)

Analysis:
- Gating: FSC/SSC scatter plot → gate populations
- CBC estimation: WBC count + 3-part differential (lymphocytes, monocytes, granulocytes)
  RBC count + hematocrit (from scatter data)
  Platelet count (small-scatter gate)
- HIV monitoring: CD4 count (with anti-CD4 FITC-labeled antibody, sample prep required)
- Malaria: fluorescent anti-parasite stain (SYBR Green in RBC)

Output: CBC panel + scatter plots (JSON + PNG)
UBERON: UBERON:0000178 (blood)
BOM estimate: ~$380
```

---

#### NFSIM-ENV-01 — Environmental Bio-Aerosol Sampler

**Concept:** A portable air sampling device that collects biological aerosols and concentrates them for analysis by LAMP (NFSIM-PCR-03) or CRISPR (NFSIM-CRISPR-01). Enables environmental pathogen surveillance.

```
Hardware:
- Cyclone collector: high-velocity air vortex concentrates bioaerosols into liquid
  Flow rate: 10–30 LPM (liters per minute)
  Collection efficiency: >90% for 1–10 μm particles
- Fan: centrifugal blower, 5V 2A
- Collection reservoir: 2mL buffer (PBS + stabilizer)
- Collection time: 30–120 minutes → sample then processed by LAMP or CRISPR

Sample processing interface:
- Cartridge connector: direct injection of 50μL of concentrated sample
  into NFSIM-CRISPR-01 or PCR-03 cartridge
- No manual pipetting required

Applications:
- Hospital airborne pathogen surveillance (COVID, influenza, MRSA)
- Indoor air quality monitoring
- Field epidemiology outbreak tracking
- BSL-2 compliant collection (most respiratory pathogens)

BOM: ~$95
```

---

## 9. Universal NFS Communication Protocol

### Overview

All NanoFlowSIM hardware devices communicate using the NFS (NanoFlowSIM) protocol. The protocol is designed to be simple, extensible, and implementable on microcontrollers with ≥32KB flash.

### Physical Layer

| Transport | Use Case | Devices |
|---|---|---|
| BLE 5.0 GATT | Primary wireless, wearables, patches | ECG, EEG, EMG, CGM, SWEAT, PCR-01–04, CRISPR |
| USB-C (USB 2.0 CDC) | Lab devices, high-bandwidth, firmware update | PCR-01, SEQ-01, GELEC-01, FLOW-01 |
| 434 MHz FSK | Ingestible capsules | CAP-01 through CAP-10 |
| NFC ISO 15693 | Passive/low-power readout | CGM-01, CAP temperature |
| Wi-Fi 802.11ac | High-bandwidth imaging | US-01, OCT-01, MICRO-01 |

### BLE GATT Service Definitions (NFS Profile)

**NFS Device Information Service (0x180A — standard BAS)**
Standard BLE Device Information Service.

**NFS Device Control Service**
UUID: `4a6e7300-1000-4a6e-b000-4a6e00000001`

Characteristics:

| UUID | Name | Properties | Size | Description |
|---|---|---|---|---|
| 4a6e...-1001 | Device State | Read+Notify | 8 bytes | Status byte + error code + battery + flags |
| 4a6e...-1002 | Command | Write | 20 bytes | Command opcode + parameters |
| 4a6e...-1003 | Configuration | Read+Write | 100 bytes | Device-specific config JSON (compressed) |
| 4a6e...-1004 | Error Log | Read | 100 bytes | Last error details |

**NFS Data Stream Service**
UUID: `4a6e7300-2000-4a6e-b000-4a6e00000002`

| UUID | Name | Properties | Size | Description |
|---|---|---|---|---|
| 4a6e...-2001 | Primary Stream | Notify | 244 bytes | Real-time data (max BLE ATT MTU) |
| 4a6e...-2002 | Batch Upload | Indicate | 512 bytes | Bulk data segments (extended MTU) |
| 4a6e...-2003 | Stream Control | Write | 4 bytes | Start/stop stream, set interval |

**NFS Metadata Service**
UUID: `4a6e7300-3000-4a6e-b000-4a6e00000003`

| UUID | Name | Properties | Size | Description |
|---|---|---|---|---|
| 4a6e...-3001 | Patient Assignment | Write | 36 bytes | Patient UUID assignment |
| 4a6e...-3002 | UBERON Tag | Read+Write | 20 bytes | Anatomical region code (ASCII) |
| 4a6e...-3003 | Session ID | Read | 36 bytes | Current session UUID |
| 4a6e...-3004 | Timestamp Sync | Write | 8 bytes | Unix timestamp (microseconds) |

### NFS Universal JSON Packet

All device data is ultimately serialized as NFS JSON packets for storage and exchange:

```json
{
  "nfs_version": "1.0.0",
  "device_id": "NFSIM-ECG-01-ABCDEF",
  "device_type": "NFSIM-ECG-01",
  "session_id": "550e8400-e29b-41d4-a716-446655440000",
  "patient_id": "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
  "timestamp_unix_us": 1748304000000000,
  "sequence": 12345,
  "anatomy_region": {
    "primary": "UBERON:0000948",
    "label": "heart",
    "secondary": ["UBERON:0000178"]
  },
  "data_type": "ecg_continuous_segment",
  "data": {
    "sample_rate_hz": 250,
    "lead": "I",
    "duration_seconds": 10,
    "samples_int16": "base64-encoded-array",
    "lsb_uV": 4.88,
    "detected_events": [
      {"type": "normal_sinus", "confidence": 0.97}
    ]
  },
  "quality": {
    "score": 0.92,
    "signal_noise_ratio_db": 28.4,
    "artifact_fraction": 0.08
  },
  "device_status": {
    "battery_pct": 74,
    "temperature_c": 36.2,
    "firmware_version": "1.2.3",
    "uptime_seconds": 86400
  }
}
```

### USB Command Protocol

For USB-connected devices (NFS-SERIAL over CDC):

```
Command format: "NFS:<COMMAND> [<PARAMS>]\r\n"
Response: "NFS:OK [<DATA>]\r\n" or "NFS:ERR <code> <message>\r\n"

Commands:
NFS:PING                          → NFS:OK PONG
NFS:STATUS                        → NFS:OK <JSON status object>
NFS:START <session_id>            → NFS:OK <session started>
NFS:STOP                          → NFS:OK <session stopped>
NFS:CONFIGURE <JSON config>       → NFS:OK <config applied>
NFS:CALIBRATE                     → NFS:OK <calibration sequence started>
NFS:DUMP <start_ts> <end_ts>      → NFS:OK <data follows as JSON lines>
NFS:UPDATE                        → NFS:OK <OTA update mode entered>
NFS:PATIENT <patient_uuid>        → NFS:OK <patient assigned>
NFS:UBERON <UBERON_code>          → NFS:OK <region assigned>
NFS:RESET                         → NFS:OK <factory reset performed>
NFS:VERSION                       → NFS:OK FW:1.2.3 HW:RevA PROTO:1.0.0
```

### 434 MHz Capsule Radio Protocol

For ingestible capsules (434 MHz FSK, sub-carrier modulation):

```
Frame structure (variable length):
[SYNC:2][DEVICE_ID:4][SEQ:2][TYPE:1][LENGTH:2][PAYLOAD:N][CRC16:2]

SYNC: 0xAA55 (synchronization word)
DEVICE_ID: Capsule serial number (4 bytes)
SEQ: Sequence number (wraps at 65535)
TYPE: 0x01=sensor, 0x02=image_header, 0x03=image_chunk, 0x04=heartbeat
LENGTH: Payload length in bytes (max 256)
PAYLOAD: Type-specific data
CRC16: CRC-CCITT polynomial 0x1021

Sensor payload (TYPE=0x01, 16 bytes max):
[TIMESTAMP:4][PH_x100:2][TEMP_x100:2][O2_x100:2][PRESSURE:2][ZONE_ESTIMATE:1][FLAGS:1]

Image header (TYPE=0x02):
[FRAME_ID:4][JPEG_SIZE:3][WIDTH:2][HEIGHT:2][FLAGS:1]

Image chunk (TYPE=0x03):
[FRAME_ID:4][CHUNK_ID:2][DATA:N] (remaining bytes = chunk data)

Retransmission:
- External receiver ACKs each image header
- Capsule retransmits missing chunks on next pass
- Sensor data: fire-and-forget (redundant transmission)
```

---

## 10. Firmware Architecture (Universal)

### Universal Patterns

Every NanoFlowSIM firmware follows these universal architectural patterns regardless of device type.

### RTOS Selection

| Device Class | RTOS | Reason |
|---|---|---|
| Most devices (STM32, nRF52840) | FreeRTOS | Mature, small footprint, excellent support |
| Complex Linux devices (MICRO-01, SEQ-01 host) | Linux + systemd | Full OS needed for camera, USB host, complex compute |
| Ultra-low-power (CGM-01, EDA-01) | Bare-metal with interrupt-driven state machine | Minimize power overhead |

### FreeRTOS Task Hierarchy

```
Priority 7 (Highest) — SensorAcquisitionTask
  - Reads sensor hardware at programmed rate
  - Time-critical interrupt service routines
  - Hardware timer callbacks
  - DMA completion handling

Priority 6 — SignalProcessingTask
  - Real-time DSP (filtering, feature extraction)
  - TinyML inference (pattern recognition, anomaly detection)
  - Quality scoring

Priority 5 — StorageTask
  - Write processed data to flash/eMMC
  - Buffer management (circular buffer → write on threshold)
  - File system operations (FatFS or LittleFS)

Priority 4 — CommunicationsTask
  - BLE GATT updates (notifications to connected phone)
  - USB CDC data streaming
  - NFS packet assembly and transmission
  - 434 MHz radio (capsule devices)

Priority 3 — DeviceControlTask
  - Command processing from BLE/USB
  - Configuration management
  - Mode switching (idle/active/calibration/OTA)

Priority 2 — PowerManagementTask
  - Battery monitoring (fuel gauge polling)
  - Sleep/wake decisions
  - Low-power mode transitions
  - Thermal management

Priority 1 (Lowest) — SystemMaintenanceTask
  - OTA firmware update management
  - Self-test routines
  - Watchdog feeding
  - Error logging
```

### Memory Map (STM32H7 example)

```
Flash layout (2MB):
0x00000000 - 0x0000FFFF: Bootloader Stage 1 (64KB)
0x00010000 - 0x0001FFFF: Bootloader Stage 2 (64KB)
0x00020000 - 0x000FFFFF: Application (896KB)
0x00100000 - 0x001EFFFF: OTA staging area (960KB)
0x001F0000 - 0x001FFFFF: Configuration + calibration (64KB, wear-leveled)

SRAM layout (1MB):
0x20000000 - 0x2001FFFF: FreeRTOS heap + stack (128KB)
0x20020000 - 0x2004FFFF: DMA buffers + sensor ring buffers (192KB)
0x20050000 - 0x200FFFFF: Signal processing workspace (704KB)

DTCM (128KB): Time-critical ISR data, DMA descriptors
ITCM (64KB): Time-critical ISR code (copied from flash on boot)
```

### Two-Phase Initialization

```
Phase 1 (Pre-RTOS, bare-metal):
1. System clock configuration (PLL, peripheral clocks)
2. Flash/SRAM initialization
3. Watchdog configuration
4. Battery check (abort if critically low)
5. SPI/I2C/UART peripheral initialization
6. Sensor hardware reset and register initialization
7. Load calibration coefficients from flash
8. Patient ID and UBERON tag load from NFC/flash
9. BLE/radio initialization (if power allows)
10. RTOS heap and task creation
11. FreeRTOS scheduler start → Phase 2

Phase 2 (RTOS tasks):
- All tasks start in SUSPENDED state
- System task determines operational mode based on config
- Wakes appropriate tasks based on mode
```

### TinyML Models Per Device

| Device | Model Purpose | Architecture | Size (INT8) | Inference Time |
|---|---|---|---|---|
| NFSIM-ECG-01 | AFib + arrhythmia classification | LSTM + FC | 20 KB | 0.5ms @ 170MHz |
| NFSIM-EEG-01 | Sleep stage classification | Conv1D + GRU | 40 KB | 2ms @ 480MHz |
| NFSIM-EMG-01 | Gesture recognition | MLP | 50 KB | 0.2ms @ 480MHz |
| NFSIM-BREATH-01 | VOC pattern classification | Gradient boosted tree | 30 KB | 5ms |
| NFSIM-CRISPR-01 | Amplification curve classification | CNN 1D | 15 KB | 1ms |
| NFSIM-MICRO-01 | Cell morphology classification | MobileNetV3 small | 2.1 MB | 80ms on RPi CM4 |
| NFSIM-FLOW-01 | Cell population gating | Gaussian Mixture | 10 KB | 0.5ms |
| NFSIM-CAP-01 | Mucosal pathology detection | MobileNetV2 INT8 | 3.4 MB | runs on external host |

### OTA Firmware Update

```
Trigger: NFS:UPDATE command over USB or BLE + user confirmation

Protocol (BLE):
1. Client sends UPDATE_INIT {fw_size, fw_hash_sha256, target_version}
2. Device responds: UPDATE_READY or UPDATE_REJECTED (insufficient space, battery too low)
3. Client sends firmware in 244-byte chunks (BLE ATT MTU)
4. Device: receives → writes to OTA staging area → CRC check per 4KB block
5. After all chunks: device verifies SHA-256 of complete image
6. If valid: device sets boot flag → reboot → bootloader validates → swaps to new firmware
7. If invalid: OTA partition cleared, old firmware continues

Rollback: if new firmware fails to start (watchdog), bootloader reverts
```

### Calibration Architecture

```
Every NFS device stores calibration in a 4KB calibration sector:

CalibrationRecord {
  magic: 0xNF5CA1 (identifies valid calibration)
  version: u16
  device_serial: [u8; 8]
  calibration_date_unix: u32
  calibration_expiry_unix: u32  (some sensors require periodic recalibration)
  coefficients: [f32; 32]       (device-specific cal coefficients)
  reference_values: [f32; 16]   (values used during calibration)
  checksum: u32                 (CRC32 of above)
}

Calibration types:
- Factory: performed once before shipping (stored, never cleared by user)
- Field: performed by user before use (stored, overwrites field cal only)
- Auto: continuous drift correction algorithms (applied in real-time, not stored)
```

---

## 11. Software Stack

### Desktop Application

**Technology:** Electron 28 + React 18 + TypeScript + Tailwind CSS

**Key Libraries:**
```
Three.js: 3D body map rendering
@react-three/fiber: React Three.js integration
@react-three/drei: Three.js helpers
noble: BLE (Bluetooth Low Energy) via Node.js
cornerstone.js: DICOM viewer
cornerstoneDICOMImageLoader: DICOM file loading
cornerstoneWADOImageLoader: WADO server support
better-sqlite3: Local SQLite database (synchronous, fast)
electron-store: Persistent settings
electron-updater: Auto-update (Squirrel-based)
zustand: Lightweight state management
react-query: Server state + data fetching
date-fns: Date manipulation
recharts: 2D charts (glucose AGP, ECG statistics)
fhirclient: FHIR OAuth2 client
```

**Architecture:**
```
main process (Node.js):
- BLE management (noble)
- SQLite queries (better-sqlite3)
- File system (DICOM, FASTQ storage)
- USB device management
- Protocol handler: nanoflowsim:// deep links

renderer process (React + TypeScript):
- Body map 3D scene (Three.js)
- Region detail panel
- Timeline component
- Data entry forms
- DICOM viewer (cornerstone)
- Simulation launcher
- Settings

preload.js (contextBridge IPC):
- Typed API bridge: renderer → main
- Exposed: db operations, BLE control, file I/O, NFS protocol commands
- All IPC calls typed with TypeScript interfaces

IPC channels:
- ble:scan, ble:connect, ble:disconnect, ble:send-command
- db:query, db:insert, db:update, db:delete
- file:import-dicom, file:export-records
- sim:start, sim:status, sim:results
- patient:create, patient:switch, patient:export
```

### Mobile Application

**Technology:** React Native 0.73 + Expo SDK 50

**Key Libraries:**
```
expo-router: File-based routing
react-native-ble-plx: BLE (Bluetooth Low Energy)
expo-nfc: NFC (CGM readout)
expo-secure-store: Encrypted local storage
expo-camera: Camera for document scanning
expo-notifications: Push notifications + local alerts
expo-health: Apple Health / Google Health Connect
react-native-vision-camera: High-performance camera
expo-file-system: File management
```

**Architecture:**
```
app/
  (tabs)/
    index.tsx          3D body map (WebGL via expo-gl + Three.js)
    timeline.tsx       Chronological data view
    devices.tsx        Connected NFS devices
    simulate.tsx       Simulation launcher
    settings.tsx       Profile, sync, preferences
  
  _layout.tsx         Root navigation + authentication
  modals/
    region-detail/    Body region detail sheet
    add-data/         Data entry modal
    device-connect/   BLE pairing wizard
```

### Backend Server (Optional — self-hosted or cloud)

**Technology:** Django 5 + Django REST Framework + Celery + PostgreSQL + Redis + MinIO + Django Channels

```
API:
/api/v1/auth/          DID-based authentication
/api/v1/patients/      Patient profile CRUD
/api/v1/records/       Health records CRUD + filter + paginate
/api/v1/sessions/      Continuous monitoring session management
/api/v1/simulations/   Simulation job submission + results
/api/v1/fhir/          FHIR R4 endpoint (patient + observation + diagnostic report)

WebSocket:
/ws/session/<session_id>/   Real-time data stream from NFS device (via app relay)
/ws/simulation/<run_id>/    Simulation progress updates

Storage:
- PostgreSQL: structured records, metadata, indices
- MinIO: binary data (DICOM, FASTQ, JPEG, audio)
- Redis: session cache, real-time stream buffer, Celery task queue

Celery tasks:
- UBERON tagging of imported records
- Simulation engine job execution
- FHIR import processing
- AI insight generation (periodic)
- Notification dispatch
```

### SDK

**Python SDK (`nfsim-sdk`):**
```python
from nfsim import NanoFlowSIM

nfsim = NanoFlowSIM(patient_id="uuid", local=True)

# Connect to device
device = nfsim.connect_device("NFSIM-ECG-01", method="ble")
device.start_session()

# Stream data
for packet in device.stream(duration=60):
    print(packet.data)

# Import records
nfsim.import_fhir("https://myhospital.epic.com/fhir", auth_token="...")
nfsim.import_vcf("patient_variants.vcf")
nfsim.import_dicom("/path/to/dicom/folder/")

# Run simulation
sim = nfsim.simulation()
sim.configure(
    nanoparticle={"size_nm": 100, "ligand": "anti-HER2", "payload": "doxorubicin"},
    therapy=["nanoparticle", "crispr"],
    target_region="UBERON:0009835"  # HER2+ breast tumor
)
results = sim.run()
print(results.targeting_efficiency)
```

**Node.js SDK (`@nfsim/sdk`):**
```javascript
import { NanoFlowSIM } from '@nfsim/sdk';

const nfsim = new NanoFlowSIM({ patientId: 'uuid', local: true });
const device = await nfsim.connectDevice('NFSIM-PCR-01', { method: 'ble' });
await device.loadProtocol({ name: 'COVID_LAMP', temp: 65, duration: 30 });
await device.startRun();
const result = await device.waitForCompletion();
await nfsim.saveRecord(result);
```

**Rust client library (`nfsim-client`):**
```rust
use nfsim_client::{NanoFlowSIM, DeviceType, Transport};

let nfsim = NanoFlowSIM::new("patient-uuid").await?;
let device = nfsim.connect(DeviceType::ECG01, Transport::Ble).await?;
let session = device.start_session().await?;
while let Some(packet) = session.next_packet().await {
    nfsim.store(&packet).await?;
}
```

---

## 12. Monorepo Structure

```
/nanoflowsim/
├── README.md                           ← This document
├── LICENSE                             ← MIT (software) + CERN OHL v2 (hardware)
├── CONTRIBUTING.md
├── CHANGELOG.md
│
├── /simulation/                        PILLAR 1: Rust simulation workspace
│   ├── Cargo.toml                      workspace manifest
│   ├── nfsim-core/                     shared types, physics constants, UBERON
│   ├── nfsim-molecular/                receptor-ligand, CRISPR, payload models
│   ├── nfsim-cellular/                 endocytosis, trafficking, release
│   ├── nfsim-tissue/                   permeability, TME, BBB, EPR
│   ├── nfsim-systemic/                 PK/PD, circulation, immune clearance
│   ├── nfsim-ml/                       therapy ranking, nanoparticle optimization
│   ├── nfsim-backtesting/              clinical validation framework
│   ├── nfsim-visualization/            3D trajectory + heatmap generation
│   ├── nfsim-grpc/                     gRPC server for frontend communication
│   └── nfsim-cli/                      command-line simulation runner
│
├── /platform/                          PILLAR 2 & 3: Patient data platform
│   ├── /backend/                       Django 5 server
│   │   ├── manage.py
│   │   ├── requirements.txt
│   │   ├── /nfsim_core/                Django project settings
│   │   ├── /patients/                  Patient profile app
│   │   ├── /records/                   Health record CRUD
│   │   ├── /sessions/                  Continuous session management
│   │   ├── /simulations/               Simulation job bridge
│   │   ├── /fhir/                      FHIR R4 endpoint
│   │   ├── /importers/                 VCF, DICOM, FHIR, CSV importers
│   │   └── /uberon/                    UBERON ontology service
│   │
│   ├── /desktop/                       Electron + React desktop app
│   │   ├── package.json
│   │   ├── electron/
│   │   │   ├── main.js
│   │   │   └── preload.js
│   │   └── src/
│   │       ├── App.tsx
│   │       ├── /components/
│   │       │   ├── BodyMap3D.tsx       Three.js 3D body
│   │       │   ├── RegionDetail.tsx    Region side panel
│   │       │   ├── Timeline.tsx        Horizontal time scrubber
│   │       │   ├── DicomViewer.tsx     Cornerstone DICOM
│   │       │   ├── DeviceManager.tsx   BLE device control
│   │       │   └── SimLauncher.tsx     Simulation configuration
│   │       ├── /store/                 Zustand state stores
│   │       ├── /db/                    SQLite queries (typed)
│   │       ├── /ble/                   Noble BLE integration
│   │       └── /ipc/                   Electron IPC bridge
│   │
│   ├── /mobile/                        React Native + Expo mobile app
│   │   ├── package.json
│   │   ├── app.json
│   │   └── app/
│   │       ├── _layout.tsx
│   │       ├── (tabs)/
│   │       └── modals/
│   │
│   └── /sdk/                           NanoFlowSIM SDKs
│       ├── python/                     nfsim-sdk (PyPI)
│       ├── node/                       @nfsim/sdk (npm)
│       └── rust/                       nfsim-client (crates.io)
│
├── /hardware/                          PILLAR 3: All device hardware
│   │
│   ├── /NFSIM-PCR-01/
│   │   ├── hardware/
│   │   │   ├── schematic/
│   │   │   │   ├── NFSIM-PCR-01-MCU.kicad_sch
│   │   │   │   ├── NFSIM-PCR-01-Power.kicad_sch
│   │   │   │   ├── NFSIM-PCR-01-Thermal.kicad_sch
│   │   │   │   └── NFSIM-PCR-01.kicad_pro
│   │   │   ├── pcb/
│   │   │   │   ├── NFSIM-PCR-01-Main.kicad_pcb    (4-layer main board)
│   │   │   │   └── NFSIM-PCR-01-Thermal.kicad_pcb (aluminum core thermal board)
│   │   │   ├── gerbers/
│   │   │   │   ├── NFSIM-PCR-01-Main-gerbers.zip
│   │   │   │   └── NFSIM-PCR-01-Thermal-gerbers.zip
│   │   │   ├── bom/
│   │   │   │   ├── bom_main.csv
│   │   │   │   ├── bom_thermal.csv
│   │   │   │   └── bom_consolidated.xlsx
│   │   │   ├── assembly/
│   │   │   │   ├── pick_and_place_main.csv
│   │   │   │   └── pick_and_place_thermal.csv
│   │   │   ├── simulation/
│   │   │   │   └── peltier_pid_ltspice.asc
│   │   │   ├── datasheets/
│   │   │   └── hardware_config.md      (pin map, power domains)
│   │   ├── firmware/
│   │   │   ├── CMakeLists.txt
│   │   │   ├── platformio.ini
│   │   │   ├── src/
│   │   │   │   ├── main.c
│   │   │   │   ├── drivers/
│   │   │   │   │   ├── peltier.c/h
│   │   │   │   │   ├── thermistor.c/h
│   │   │   │   │   ├── display_st7789.c/h
│   │   │   │   │   └── battery_max17055.c/h
│   │   │   │   ├── tasks/
│   │   │   │   │   ├── thermal_control.c/h
│   │   │   │   │   ├── protocol_runner.c/h
│   │   │   │   │   ├── ble_comm.c/h
│   │   │   │   │   └── display_task.c/h
│   │   │   │   ├── nfs_protocol.c/h    (universal NFS protocol layer)
│   │   │   │   └── calibration.c/h
│   │   │   ├── include/
│   │   │   └── build/
│   │   │       ├── NFSIM-PCR-01-v1.0.0.bin
│   │   │       ├── NFSIM-PCR-01-v1.0.0.elf
│   │   │       └── NFSIM-PCR-01-v1.0.0.map
│   │   ├── mechanical/
│   │   │   ├── cad/
│   │   │   │   ├── NFSIM-PCR-01-top.step
│   │   │   │   ├── NFSIM-PCR-01-bottom.step
│   │   │   │   └── NFSIM-PCR-01-assembly.step
│   │   │   ├── stl/
│   │   │   │   ├── top_shell.stl
│   │   │   │   ├── bottom_shell.stl
│   │   │   │   └── tube_block_holder.stl
│   │   │   ├── drawings/
│   │   │   └── mechanical_spec.md
│   │   ├── docs/
│   │   │   ├── getting_started.md
│   │   │   ├── theory.md
│   │   │   ├── assembly_guide.md
│   │   │   └── protocol_library.md
│   │   └── production/
│   │       ├── sop/
│   │       ├── qc_checklist.csv
│   │       └── packaging/
│   │
│   ├── /NFSIM-PCR-02/         (same structure)
│   ├── /NFSIM-PCR-03/
│   ├── /NFSIM-PCR-04/
│   ├── /NFSIM-SEQ-01/
│   ├── /NFSIM-SEQ-02/
│   ├── /NFSIM-CRISPR-01/
│   ├── /NFSIM-dPCR-01/
│   ├── /NFSIM-GELEC-01/
│   ├── /NFSIM-US-01/
│   ├── /NFSIM-US-02/
│   ├── /NFSIM-US-03/
│   ├── /NFSIM-US-04/
│   ├── /NFSIM-US-05/
│   ├── /NFSIM-US-06/
│   ├── /NFSIM-US-07/
│   ├── /NFSIM-US-08/
│   ├── /NFSIM-US-09/
│   ├── /NFSIM-MRI-01/
│   ├── /NFSIM-XRAY-01/
│   ├── /NFSIM-OCT-01/
│   ├── /NFSIM-MICRO-01/
│   ├── /NFSIM-CGM-01/
│   ├── /NFSIM-SWEAT-01/
│   ├── /NFSIM-CHEM-01/
│   ├── /NFSIM-CHEM-02/
│   ├── /NFSIM-CHEM-03/
│   ├── /NFSIM-CHEM-04/
│   ├── /NFSIM-CHEM-05/
│   ├── /NFSIM-CHEM-06/
│   ├── /NFSIM-CHEM-07/
│   ├── /NFSIM-CHEM-08/
│   ├── /NFSIM-OXY-01/
│   ├── /NFSIM-BREATH-01/
│   ├── /NFSIM-ECG-01/
│   ├── /NFSIM-ECG-02/
│   ├── /NFSIM-EEG-01/
│   ├── /NFSIM-EMG-01/
│   ├── /NFSIM-NEURAL-01/
│   ├── /NFSIM-EOG-01/
│   ├── /NFSIM-EDA-01/
│   ├── /NFSIM-CAP-01/
│   ├── /NFSIM-CAP-02/
│   ├── /NFSIM-CAP-03/
│   ├── /NFSIM-CAP-04/
│   ├── /NFSIM-CAP-05/
│   ├── /NFSIM-CAP-06/
│   ├── /NFSIM-CAP-07/
│   ├── /NFSIM-CAP-08/
│   ├── /NFSIM-CAP-09/
│   ├── /NFSIM-CAP-10/
│   ├── /NFSIM-FLOW-01/
│   └── /NFSIM-ENV-01/
│
├── /shared-firmware/                   Shared firmware components across all devices
│   ├── nfs_protocol/                   Universal NFS protocol implementation (C)
│   ├── ble_gatt_server/               Generic BLE GATT server
│   ├── power_management/              Battery + sleep management
│   ├── ota_update/                    OTA firmware update client
│   ├── calibration/                   Universal calibration framework
│   ├── tinyml_runtime/                TFLite Micro integration
│   └── uberon_tags.h                  UBERON code definitions
│
├── /docs/                              Master documentation
│   ├── /guides/
│   │   ├── getting_started.md         Complete new user guide
│   │   ├── hardware_build_guide.md    PCB assembly across all devices
│   │   ├── software_setup.md          Platform installation
│   │   └── simulation_tutorial.md     First simulation walkthrough
│   ├── /theory/
│   │   ├── nanoparticle_physics.md
│   │   ├── biological_sensing_domains.md  (this encyclopedia)
│   │   ├── uberon_mapping.md
│   │   └── fhir_integration.md
│   ├── /api/
│   │   ├── python_sdk.md
│   │   ├── rest_api.md
│   │   └── nfs_protocol.md
│   └── /hardware_config/
│       └── [DEVICE]-config.md for each device
│
├── /production/                        Manufacturing guides
│   ├── /sop/                          Assembly SOPs per device
│   ├── /quality/                      QC checklists
│   ├── /packaging/                    Box design, insert templates
│   └── batch_tracking.md
│
└── /legal/
    ├── LICENSE-SOFTWARE.md            MIT License (software, firmware)
    ├── LICENSE-HARDWARE.md            CERN OHL-W v2 (hardware)
    ├── /certifications/               FCC/CE test reports (when obtained)
    ├── /third-party-licenses/         All dependency licenses
    └── /compliance/
        ├── RoHS_declaration.pdf       Lead-free component confirmation
        └── REACH_declaration.pdf
```

---

## 13. Production, Manufacturing & Quality

### PCB Manufacturing Guidelines

**All NanoFlowSIM PCBs are designed for JLCPCB manufacturing compatibility:**

```
Standard rules:
- Minimum trace width: 0.1mm (4 mil)
- Minimum clearance: 0.1mm
- Via drill: minimum 0.3mm, pad 0.6mm
- Board thickness: 1.6mm standard (1.0mm for flex regions)
- Copper weight: 1oz outer, 0.5oz inner
- Surface finish: HASL (standard), ENIG for fine-pitch (>0.4mm BGA or QFP<80)
- Soldermask: green (standard), black (optional for consumer aesthetics)
- Silkscreen: white, all component reference designators visible

4-layer stackup (most devices):
L1: Signal + components (1oz Cu)
L2: GND plane (0.5oz Cu)
L3: Power plane (0.5oz Cu)
L4: Signal + components (1oz Cu)
Core: FR4, Tg150 standard
```

**PCBA (PCB Assembly) via JLCPCB:**
- Provide: Gerber files + BOM (with LCSC part numbers) + pick-and-place CSV
- LCSC part availability check: all components must have LCSC part numbers
- Parts without LCSC availability: customer-supplied or sourced from Mouser/Digi-Key
- SMD assembly only: through-hole components (connectors, large caps) hand-soldered

### Assembly SOP (Standard Operating Procedure) Template

```
NFSIM-[DEVICE]-[REV] ASSEMBLY SOP v1.0
Status: Draft / Review / Released

1. SAFETY
   - PPE required: safety glasses, gloves (when using solvents)
   - ESD: grounded wrist strap required for all PCB handling
   - Chemical safety: consult MSDS for all chemicals used

2. TOOLS REQUIRED
   - Soldering iron: temperature-controlled, 350°C tip, fine tip
   - Solder: 63/37 Sn/Pb or SAC305 (lead-free)
   - Flux: no-clean rosin flux pen
   - IPA isopropyl alcohol: PCB cleaning
   - Hot air rework station (if BGA or fine-pitch)
   - Multimeter, oscilloscope
   - [Device-specific tools listed here]

3. COMPONENTS
   - Verify BOM revision matches PCB revision
   - Inspect incoming components for damage

4. ASSEMBLY SEQUENCE
   4.1. Inspect bare PCB (visual, dimensional)
   4.2. PCBA boards: inspect PCBA quality (reflow quality, bridging)
   4.3. Solder through-hole components (specified sequence)
   4.4. Install cable harnesses
   4.5. Install mechanical components (display, buttons)

5. FIRMWARE PROGRAMMING
   5.1. Connect ST-Link V3 to SWD header (TC2030 connector)
   5.2. Flash bootloader: [command]
   5.3. Flash application: [command]
   5.4. Verify: [NFS:PING → NFS:OK PONG]

6. QUALITY CONTROL
   See QC checklist [DEVICE]-QC-v1.0.csv

7. PACKAGING
   [Device-specific packaging instructions]
```

### QC Checklist Template

```csv
Test ID, Test Name, Method, Expected Result, PASS/FAIL, Notes
QC-001, Visual Inspection, Visual, No solder bridges/tombstones/damage, ,
QC-002, Power Input, DMM, 5V ±5% at input connector, ,
QC-003, 3.3V Rail, DMM, 3.3V ±3% at test point TP1, ,
QC-004, 5V Rail (if applicable), DMM, 5V ±3% at TP2, ,
QC-005, MCU Boot, USB serial, NFS:PING → NFS:OK PONG within 5s, ,
QC-006, BLE Advertisement, BLE scanner, Device visible as NFSIM-[TYPE]-XXXXXX, ,
QC-007, Battery Charging, USB-C + meter, Charging current 0.5–1A within 10s, ,
QC-008, Battery Fuel Gauge, App, SOC reading ±5% of actual, ,
QC-009, Sensor Functional, App, [Device-specific sensor test], ,
QC-010, BOM Revision, Visual, BOM sticker matches PCB revision, ,
```

---

## 14. Regulatory & Legal

### Device Classifications

| Device | US FDA Classification | EU MDR Classification | Notes |
|---|---|---|---|
| NFSIM-PCR-01–04, LAMP, RPA | RUO (Research Use Only) | Not regulated as MD | Labeled RUO, not for clinical diagnosis |
| NFSIM-SEQ-01, SEQ-02 | RUO | Not regulated as MD | Labeled RUO |
| NFSIM-CRISPR-01 | RUO | Not regulated as MD | Labeled RUO (clinical use requires 510k/CE IVD) |
| NFSIM-US-01 (non-diagnostic labeling) | Class II 510k pathway if clinical | Class IIa IVD | As RUO: exempt. Clinical use: regulatory submission required |
| NFSIM-CGM-01 (RUO) | RUO | Not regulated as MD | Not interoperable with clinical CGM systems unless certified |
| NFSIM-CAP series (ingestible) | Class III (PMA pathway) for clinical | Class III EU MDR | Significant regulatory barrier; RUO only |
| NFSIM-ECG-01 (consumer wellness) | General Wellness, exempt | Not regulated | "Heart Rate Variability" wellness use avoids prescription labeling |
| NFSIM-ECG-01 (for AFib detection) | Class II De Novo / 510k | Class IIa MDR | Clinical arrhythmia detection requires clearance |
| NFSIM-XRAY-01 | Requires state/federal authorization for operation | Class IIa radiological equipment | Cannot operate without radiation safety authorization |
| NFSIM-MRI-01 | Class II 510k for clinical MRI | Class IIa | RUO research use significantly less regulated |
| NFSIM-NEURAL-01 | Class III (PMA) for clinical use | Class III | Research only; surgical implant = strict regulation |

**All NanoFlowSIM devices are labeled: "FOR RESEARCH USE ONLY. NOT FOR CLINICAL DIAGNOSTIC USE."**

### Wireless Certification

```
FCC (United States):
- BLE modules: use pre-certified nRF52840 module (e.g., Sparkfun nRF52840 Mini,
  Nordic Thingy:53 module) — FCC ID on module covers device use within spec
- 434 MHz radio: Si4463 inside body = FCC Part 15 limits apply
  If transmit power <-1 dBm conducted: Part 15B exempt
  If transmit power 10dBm: requires FCC Part 15 intentional radiator certification
- Wi-Fi: use certified Wi-Fi module (ESP32-WROOM-02 or similar)
  FCC ID: 2AC7Z-ESP32WROOM32D (covers use within module specs)
- USB-C: no wireless certification needed

CE (European Union):
- BLE: RED (Radio Equipment Directive) covered by module certification
  nRF52840 QIAA module: CE marked, RED compliant
- 434 MHz: RED certification required for 434 MHz TX regardless
- General: EN 55032 emissions, EN 55035 immunity

Canada (ISED):
- RSS-247 Issue 2 covers BLE
- Pre-certified module covers RSS-247 for BLE

Japan (MIC):
- Telec certification required for 2.4GHz/BLE if selling in Japan

Note: Using pre-certified radio modules (nRF52840, ESP32-WROOM) dramatically
simplifies regulatory burden. Always operate within module's certified parameters.
```

### Open-Source Licenses

**Hardware:** CERN Open Hardware Licence (CERN OHL-W v2)
- Weakly reciprocal: modifications must be shared, products can be sold
- Covers: schematics, PCB layouts, mechanical designs, BOMs
- Attribution required: "Based on NanoFlowSIM hardware, CERN OHL-W v2"

**Firmware:** MIT License
- Permissive: use, modify, distribute, sublicense, sell
- Attribution required in copyright notice

**Software (platform):** MIT License

**Simulation Engine:** Apache 2.0 License
- Permissive, explicit patent grant
- Attribution required

**Documentation:** CC BY 4.0
- Attribution required, derivatives allowed including commercial

### Data Privacy

NanoFlowSIM platform:
- Patient data never leaves the patient's device without explicit consent and action
- No telemetry, no analytics, no data collection by NanoFlowSIM project
- Optional cloud sync is 100% patient-controlled, patient-hosted
- FHIR imports are read-only on the patient's behalf; data stays locally
- HIPAA consideration: as RUO software, not a covered entity; however designed to HIPAA best practices
- GDPR: patient is controller of their own data; NanoFlowSIM acts as data processor only when self-hosted cloud sync is used
- Nagoya Protocol: genomic data from biological samples is stored only locally; no biological data fed to external databases without explicit patient consent

---

## 15. Roadmap

### Phase 1 — Foundation (Months 1–12)

**Simulation Engine:**
- [x] Core architecture design
- [ ] nfsim-core crate (types, UBERON ontology)
- [ ] nfsim-molecular crate (ligand-receptor kinetics)
- [ ] nfsim-cellular crate (endocytosis, trafficking)
- [ ] nfsim-cli (basic simulation runner)
- [ ] gRPC API

**Platform:**
- [ ] Django backend (patients, records, sessions APIs)
- [ ] SQLite local data model (desktop)
- [ ] Basic 3D body map (generic mesh, click to view)
- [ ] NFS BLE protocol library (Python)
- [ ] Desktop app (Electron skeleton)

**Hardware (Priority 1 devices):**
- [ ] NFSIM-PCR-01 (thermal block, BLE, prototype)
- [ ] NFSIM-ECG-01 (patch prototype)
- [ ] NFSIM-CGM-01 (sensor prototype, in vitro testing)

### Phase 2 — Core Platform (Months 6–18)

**Simulation:**
- [ ] nfsim-tissue, nfsim-systemic
- [ ] BBB model
- [ ] ML therapy ranking module
- [ ] Visualization (3D trajectory output)

**Platform:**
- [ ] DICOM import + Cornerstone viewer
- [ ] FHIR client (hospital record import)
- [ ] Consumer mode UI complete
- [ ] Mobile app (basic, BLE device management)
- [ ] Timeline scrubber
- [ ] Data entry flows (manual, import, device)

**Hardware (Priority 2):**
- [ ] NFSIM-PCR-02 (gel slip reader)
- [ ] NFSIM-CRISPR-01 (fluorescence detection)
- [ ] NFSIM-US-01 (ultrasound probe, firmware)
- [ ] NFSIM-EEG-01 (ADS1299 board)
- [ ] NFSIM-SWEAT-01 (flexible patch)

### Phase 3 — Advanced Features (Months 12–24)

**Simulation:**
- [ ] Back-testing framework
- [ ] Patient-specific simulation from DICOM mesh
- [ ] Drug combination optimizer

**Platform:**
- [ ] Level 2 body map (DICOM-derived patient-specific mesh)
- [ ] Level 3 (live sensor overlay on 3D)
- [ ] Professional mode complete
- [ ] Python + Node.js SDK release
- [ ] AR overlay (mobile)
- [ ] Pharmacogenomics drug checker

**Hardware (Advanced):**
- [ ] NFSIM-SEQ-01 (nanopore sequencer prototype)
- [ ] NFSIM-CAP-01 (ingestible capsule prototype, animal testing)
- [ ] NFSIM-MRI-01 (Halbach magnet assembly)
- [ ] NFSIM-FLOW-01 (acoustic cytometry)

### Phase 4 — Ecosystem (Months 18–36)

- [ ] All 30+ devices released to community
- [ ] CI/CD for firmware (automated build + flash testing)
- [ ] NanoFlowSIM community forum + hardware sharing
- [ ] Clinical research partnerships
- [ ] Simulation validation against published trial data
- [ ] App store release (macOS, Windows, Linux AppImage)
- [ ] Mobile app stores (iOS + Android)

### Phase 5 — Future (36+ Months)

- [ ] Continuous cfDNA monitoring interface (when technology matures)
- [ ] Neural implant interface (NFSIM-NEURAL-01 research deployment)
- [ ] Full digital twin integration (all modalities fused)
- [ ] AI-driven treatment protocol suggestion (simulation + patient data)
- [ ] Federated research network (de-identified data sharing for simulation training)
- [ ] Nanoparticle synthesis verification (connect simulation to actual NP characterization)

---

## 16. License

```
NanoFlowSIM — Open-Source Precision Medicine Ecosystem

Hardware (schematics, PCB layouts, mechanical designs, BOMs):
  Licensed under CERN Open Hardware Licence Version 2 - Weakly Reciprocal (CERN OHL-W v2)
  See /legal/LICENSE-HARDWARE.md

Firmware (embedded C/C++/Rust code):
  Licensed under MIT License
  See /legal/LICENSE-SOFTWARE.md

Platform Software (simulation engine, desktop app, mobile app, backend, SDKs):
  Licensed under MIT License
  See /legal/LICENSE-SOFTWARE.md

Documentation:
  Licensed under Creative Commons Attribution 4.0 International (CC BY 4.0)

Third-party components retain their original licenses.
See /legal/third-party-licenses/ for all dependencies.

Copyright © 2026 NanoFlowSIM Contributors
All contributors retain copyright over their specific contributions.

DISCLAIMER:
All NanoFlowSIM hardware devices are labeled FOR RESEARCH USE ONLY.
They are NOT approved or cleared as medical devices by any regulatory authority.
They are NOT intended for clinical diagnostic use.
They are NOT intended to diagnose, treat, cure, or prevent any disease or condition.
Use of these devices for clinical decision-making without appropriate regulatory clearance
is strictly prohibited and may be illegal in your jurisdiction.
```

---

*NanoFlowSIM — Democratizing access to every layer of biological sensing and nanoparticle therapy modeling.*

*Built open. Built portable. Built for everyone.*
