# NanoFlowSIM

**Integrated Precision Medicine Platform — Open-Source Portable Biosensing Ecosystem + Multi-Layered Nanoparticle Simulation + Living Patient Body Map**

> *Every measurement. Every modality. Every moment. One platform.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](legal/LICENSE-SOFTWARE.md)
[![Hardware: CERN OHL-W v2](https://img.shields.io/badge/Hardware-CERN%20OHL--W%20v2-blue.svg)](legal/LICENSE-HARDWARE.md)
[![Status: Active Development](https://img.shields.io/badge/Status-Active%20Development-green.svg)]()
[![Rust](https://img.shields.io/badge/Simulation%20Engine-Rust-orange.svg)]()
[![Platforms: Linux | Windows | macOS | Android | iOS](https://img.shields.io/badge/Platforms-Linux%20%7C%20Windows%20%7C%20macOS%20%7C%20Android%20%7C%20iOS-lightgrey.svg)]()
[![Open Science](https://img.shields.io/badge/Philosophy-Open%20Science-brightgreen.svg)]()

---

## Table of Contents

1. [Project Vision](#1-project-vision)
2. [Three Pillars of NanoFlowSIM](#2-three-pillars-of-nanoflowsim)
3. [Simulation Framework — Complete](#3-simulation-framework--complete)
   - 3.1 [Architecture](#31-architecture)
   - 3.2 [Molecular Layer](#32-molecular-layer)
   - 3.3 [Cellular Layer](#33-cellular-layer)
   - 3.4 [Tissue Layer](#34-tissue-layer)
   - 3.5 [Systemic Layer](#35-systemic-layer)
   - 3.6 [Therapy Modeling](#36-therapy-modeling)
   - 3.7 [Back-Testing and Iterative Refinement](#37-back-testing-and-iterative-refinement)
   - 3.8 [Machine Learning Integration](#38-machine-learning-integration)
   - 3.9 [Expanded Clinical Applications](#39-expanded-clinical-applications)
   - 3.10 [System Workflow](#310-system-workflow)
4. [Patient Data Architecture — The Living Body Map](#4-patient-data-architecture--the-living-body-map)
   - 4.1 [Core Design Philosophy](#41-core-design-philosophy)
   - 4.2 [UBERON Anatomical Tagging System](#42-uberon-anatomical-tagging-system)
   - 4.3 [Data Model](#43-data-model)
   - 4.4 [Data Storage Architecture](#44-data-storage-architecture)
5. [UI/UX Specification — Consumer and Professional](#5-uiux-specification--consumer-and-professional)
   - 5.1 [Design Principles](#51-design-principles)
   - 5.2 [3D Body Map System](#52-3d-body-map-system)
   - 5.3 [Consumer Mode](#53-consumer-mode)
   - 5.4 [Professional / Clinical Mode](#54-professional--clinical-mode)
   - 5.5 [Data Capture Workflows](#55-data-capture-workflows)
   - 5.6 [Live vs. Historical Mode](#56-live-vs-historical-mode)
   - 5.7 [Regional Data Interaction](#57-regional-data-interaction)
   - 5.8 [Mobile-Specific UX](#58-mobile-specific-ux)
6. [Data Integration — Full Loop (Current and Future)](#6-data-integration--full-loop-current-and-future)
   - 6.1 [Non-Continuous Data Sources](#61-non-continuous-data-sources)
   - 6.2 [Continuous Data Sources (Current)](#62-continuous-data-sources-current)
   - 6.3 [Future Continuous Systems (Pre-Built Architecture)](#63-future-continuous-systems-pre-built-architecture)
   - 6.4 [Data Pipeline Architecture](#64-data-pipeline-architecture)
7. [Biological Sensing Domain Encyclopedia](#7-biological-sensing-domain-encyclopedia)
   - 7.1 [Domain: Molecular / Genomic Sensing](#71-domain-molecular--genomic-sensing)
   - 7.2 [Domain: Structural / Anatomical Imaging](#72-domain-structural--anatomical-imaging)
   - 7.3 [Domain: Chemical / Metabolic Sensing](#73-domain-chemical--metabolic-sensing)
   - 7.4 [Domain: Electrical / Bioelectric Sensing](#74-domain-electrical--bioelectric-sensing)
   - 7.5 [Domain: Implantable / Closed-Loop Systems](#75-domain-implantable--closed-loop-systems)
   - 7.6 [Domain: Cellular / Microscopic Sensing](#76-domain-cellular--microscopic-sensing)
   - 7.7 [Domain: Dynamic Physiological Monitoring](#77-domain-dynamic-physiological-monitoring)
   - 7.8 [Domain: Multi-Modal Convergence Systems](#78-domain-multi-modal-convergence-systems)
8. [Open-Source Hardware Ecosystem — Philosophy and Mandate](#8-open-source-hardware-ecosystem--philosophy-and-mandate)
9. [Hardware Domain A — Molecular / Genomic](#9-hardware-domain-a--molecular--genomic)
10. [Hardware Domain B — Structural / Anatomical Imaging](#10-hardware-domain-b--structural--anatomical-imaging)
11. [Hardware Domain C — Chemical / Metabolic](#11-hardware-domain-c--chemical--metabolic)
12. [Hardware Domain D — Electrical / Bioelectric](#12-hardware-domain-d--electrical--bioelectric)
13. [Hardware Domain E — Ingestible / Traversing Capsules](#13-hardware-domain-e--ingestible--traversing-capsules)
14. [Hardware Domain F — Wearable Patches and Implants](#14-hardware-domain-f--wearable-patches-and-implants)
15. [Hardware Domain G — Flow Cytometry and Environmental](#15-hardware-domain-g--flow-cytometry-and-environmental)
16. [Hardware Domain H — Interventional and Delivery](#16-hardware-domain-h--interventional-and-delivery)
17. [Hardware Domain I — Consumables and Universal Interfaces](#17-hardware-domain-i--consumables-and-universal-interfaces)
18. [Full Device Specifications — All 50+ Devices](#18-full-device-specifications--all-50-devices)
19. [Universal NFS Communication Protocol](#19-universal-nfs-communication-protocol)
20. [Firmware Architecture — Universal](#20-firmware-architecture--universal)
21. [Software Stack — Complete](#21-software-stack--complete)
    - 21.1 [Desktop Application](#211-desktop-application)
    - 21.2 [Mobile Application](#212-mobile-application)
    - 21.3 [Web Dashboard and Backend](#213-web-dashboard-and-backend)
    - 21.4 [SDK (Python, Node.js, Rust)](#214-sdk-python-nodejs-rust)
    - 21.5 [AI / ML Layer](#215-ai--ml-layer)
22. [Complete Monorepo Directory Structure](#22-complete-monorepo-directory-structure)
23. [Production, Manufacturing and Quality](#23-production-manufacturing-and-quality)
24. [Regulatory, Legal and Compliance](#24-regulatory-legal-and-compliance)
25. [Roadmap](#25-roadmap)
26. [Contributing](#26-contributing)
27. [Acknowledgements](#27-acknowledgements)
28. [License](#28-license)

---

## 1. Project Vision

NanoFlowSIM is a vertically integrated precision medicine ecosystem built on the belief that every layer of biological information — structural, electrical, chemical, molecular, genomic — should be simultaneously accessible, open-source, portable, continuously monitored, and unified into a single living model of each patient.

### The Problem NanoFlowSIM Solves

Modern medicine is fragmented across institutional silos:

| Domain | Typical Siloed System |
|---|---|
| Structural imaging | Hospital radiology department |
| ECG / cardiac monitoring | Cardiology clinic |
| Genomics / SNPs / sequencing | Specialized genetics laboratory |
| Continuous glucose | Endocrinology / diabetes care |
| Blood chemistry panels | Clinical laboratory |
| Neural signals (EEG, EMG) | Neurology department |
| Ingestible diagnostics | Gastroenterology |
| Environmental pathogen data | Public health agency |
| Nanoparticle therapy design | Research institution |

No single system integrates all of these into a continuous, patient-owned, portable, open-source, simulation-capable platform.

NanoFlowSIM changes this entirely.

### The Three Pillars

**Pillar 1 — Simulation Engine:**
A Rust-based computational framework that models nanoparticle behavior in biological systems at molecular, cellular, tissue, and whole-system levels. Integrates patient-specific genomic, proteomic, imaging, and physiological data. Applications span oncology, gene therapy, HIV treatment, neurological disease, autoimmune disease, antimicrobial resistance, and beyond.

**Pillar 2 — Living Patient Body Map:**
A personal health data aggregation platform where every data point from every sensing modality maps to an anatomical region of a 3D human body. Historical, episodic, and continuously streaming data coexist on the same model. The patient owns their data entirely. Individuals can import hospital records, connect wearables, and add manual entries. The 3D model updates from a generic mesh through to a patient-specific imaging-derived anatomy.

**Pillar 3 — Open-Source Portable Hardware Ecosystem:**
50+ open-source, open-hardware biological sensing devices spanning all biological sensing domains — molecular, genomic, structural, chemical, electrical, implantable, ingestible, environmental, interventional. Every device is designed to be portable, affordable, reproducible from KiCad schematics via JLCPCB, flashed with open firmware, and natively integrated into the NanoFlowSIM patient data platform.

### The Unifying Thesis

> Biological data has historically been siloed, episodic, expensive, and inaccessible. NanoFlowSIM treats the entire history of biological sensing — from gel electrophoresis to nanopore sequencing to ingestible capsule ultrasound — as a single evolving stack. It builds open-source portable versions of every layer, feeding all data into a unified living 3D patient model that directly drives nanoparticle therapy simulation.

---

## 2. Three Pillars of NanoFlowSIM

### Pillar 1: Simulation Engine (NanoFlowSIM Core)

The simulation engine is a Rust workspace that models nanoparticle therapeutics across four computational layers — molecular, cellular, tissue, and systemic — using Monte Carlo methods, agent-based modeling, pharmacokinetic compartment models, and machine learning.

**Core simulation capabilities:**
- Multi-therapy hybrid simulation (CRISPR + chemotherapy + immunotherapy simultaneously)
- Automated therapy combination screening with ML-ranked output and confidence intervals
- Back-testing against historical clinical trial data and patient outcomes
- Patient-specific customization driven by VCF variant data, proteomic profiles, and DICOM-derived tissue geometry
- Nanoparticle design parameter sweep (size, shape, surface chemistry, ligand, payload)
- Blood-brain barrier crossing simulation
- Tumor microenvironment modeling
- Immune clearance and complement activation modeling
- Pathogen reservoir targeting (HIV latent T-cell reservoirs, herpesvirus neural ganglia)
- CRISPR guide RNA efficiency and off-target risk prediction
- Visualization output: 3D nanoparticle trajectory data and tissue heatmaps

### Pillar 2: Living Patient Body Map

A persistent, patient-owned health record system that anchors every data point to an anatomical region using the UBERON cross-species anatomical ontology.

The body map exists at five progressive levels of resolution:

| Level | Description | Data Required |
|---|---|---|
| 0 | Generic anatomical mesh | None — available to any user immediately |
| 1 | Anthropometric-matched mesh | Height, weight, age, biological sex |
| 2 | Imaging-derived patient mesh | DICOM CT or MRI segmentation |
| 3 | Functional data overlay | Live continuous sensor streams |
| 4 | Molecular and simulation overlay | Genomic variants, cfDNA, nanoparticle trajectories |

### Pillar 3: Hardware Ecosystem

50+ open-source portable biosensing devices across nine sensing domains. Universal mandates for all devices:

1. **Portable:** battery-operable, fits in a bag, or wearable
2. **Open hardware:** full KiCad schematics, Gerbers, BOM, STEP files published
3. **Open firmware:** complete embedded firmware source (C/C++/Rust, FreeRTOS/Zephyr)
4. **Open protocol:** NFS universal JSON format over BLE 5.0 GATT, USB-C, 434 MHz, or NFC
5. **NanoFlowSIM-native:** data streams directly into NanoFlowSIM patient profile with UBERON tagging
6. **Reproducible:** manufacturable from commodity components, JLCPCB/PCBWay compatible
7. **Field-deployable:** operates in field conditions (0–45°C, high humidity)
8. **Affordable:** BOM cost target <$500 for most devices, <$200 for most wearables

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
PATCH  = Multi-sensor wearable patch
IMPLANT= Implantable sensor node
```

---

## 3. Simulation Framework — Complete

### 3.1 Architecture

```
nanoflowsim-simulation/           (Rust workspace)
├── nfsim-core/                   Shared types, physics constants, UBERON codes, data structures
├── nfsim-molecular/              Ligand-receptor kinetics, CRISPR modeling, payload stability
├── nfsim-cellular/               Endocytosis, endosomal escape, trafficking, release models
├── nfsim-tissue/                 Permeability, EPR, immune infiltrate, TME, BBB
├── nfsim-systemic/               PK/PD, circulation, MPS clearance, complement
├── nfsim-ml/                     Therapy combination ranking, nanoparticle optimization (Bayesian)
├── nfsim-backtesting/            Clinical data comparison, prediction validation, refinement
├── nfsim-visualization/          3D trajectory output, tissue heatmap generation (WebGL data)
├── nfsim-grpc/                   gRPC server for frontend communication
└── nfsim-cli/                    Command-line simulation runner
```

### 3.2 Molecular Layer

**Receptor-Ligand Binding Kinetics**

Uses a stochastic Gillespie algorithm for binding event simulation:

```
Key parameters:
  k_on  = Association rate constant (M⁻¹s⁻¹)
  k_off = Dissociation rate constant (s⁻¹)
  K_D   = k_off / k_on  (equilibrium dissociation constant)

Models:
  - Monovalent binding
  - Multivalent cooperative binding (avidity enhancement)
  - Surface density effects (ligand molecules per nm²)
  - Receptor internalization kinetics following binding
  - Ligand density optimization algorithm (maximizes binding while minimizing immune recognition)

Example TOML configuration:
  [ligand_config]
  ligand_type = "anti-HER2 antibody fragment"
  density_per_nm2 = 0.15
  k_on_M_per_s = 1.2e5
  k_off_per_s = 1.1e-4
  receptor_expression_level = "high"
```

**CRISPR Activation Modeling**

Supported systems: CRISPR-Cas9, CRISPR-Cas12a, CRISPR-Cas13a/b, base editors, prime editors.

```
Models:
  - Guide RNA binding efficiency per target locus
    (GC content, secondary structure, Tm, seed region mismatches)
  - Off-target site scoring from patient VCF input
    (CFD scoring, MIT specificity score, Doench 2016)
  - Cas protein expression timeline post-delivery
  - In vivo editing efficiency distribution (probabilistic, per cell type)
  - Immune recognition probability of Cas9/Cas12 proteins
    (pre-existing T-cell immunity from published epidemiology)
  - CRISPR collateral activity (Cas13 trans-cleavage for SHERLOCK diagnostic simulation)
```

**Payload Encapsulation Stability**

```
Environmental conditions tested:
  - pH range: 4.5 (lysosome) → 7.4 (blood)
  - Enzymatic: cathepsin B, MMP-2/9, furin, RNase, DNase
  - Temperature: physiological variation 36–42°C
  - Ionic strength: 150 mM NaCl
  - Oxidative: H₂O₂ gradients (tumor microenvironment)

Release mechanisms modeled:
  - pH-triggered (pore formation, protonation)
  - Enzymatic cleavage of linker
  - Thermal-responsive polymer collapse
  - Light-activated (photoactivatable caged compounds)
  - Mechanical (ultrasound-triggered)
  - Voltage-triggered (electroactive polymer)
```

**Dynamic Ligand Design**

AI algorithm generates novel ligand candidates from receptor binding pocket structure:
- Input: target receptor structure (PDB file) or sequence + homology model
- Output: ranked candidate ligand sequences/structures with predicted affinity
- Method: generative transformer model fine-tuned on protein-ligand interaction data

### 3.3 Cellular Layer

**Endocytosis Pathway Probabilities**

| Pathway | Optimal NP Size | NP Surface | Rate |
|---|---|---|---|
| Clathrin-mediated | 120–200 nm | cationic or antibody-coated | High for targeted NPs |
| Caveolae-mediated | 60–80 nm | albumin or cholesterol-modified | Bypasses lysosome (favored) |
| Macropinocytosis | >500 nm | any, especially anionic | Low, non-specific |
| Direct membrane penetration | <10 nm | cell-penetrating peptides (CPP) | High for CPP-conjugated |
| Phagocytosis (immune cells) | >500 nm, opsonized | IgG-coated | Target for immunotherapy delivery |

**Endosomal Escape Model**

```
Critical bottleneck: >90% of NPs trapped in lysosomes (degraded)

Mechanisms simulated:
  - Proton sponge effect:
      tertiary amines (PEI, PAMAM) buffer lysosomal pH
      → osmotic swelling → membrane rupture
      Modeled: buffering capacity curve vs. amine density
  - Fusogenic lipids:
      DOPE, CHEMS — phase transition at pH 5.0
      → cone-shaped lipids destabilize endosomal membrane
  - Photochemical internalization (PCI):
      light-activated reactive oxygen species (ROS) disrupt endosome
  - Pore-forming peptides:
      GALA, melittin variants — pH-triggered membrane insertion
  - Virus-like particles:
      mimicry of viral endosomal escape mechanisms

Output:
  - Escape probability (fraction of NPs per cell cycle)
  - Escape timing distribution (minutes post-internalization)
  - Payload release fraction following escape
```

**Intracellular Trafficking and Payload Release**

```
After endosomal escape:
  - Nuclear localization signal (NLS) → nucleus targeting for gene delivery
  - Mitochondria-targeting sequence (MTS) → mitochondrial delivery
  - ER targeting → secretory pathway access
  - Cytoplasmic diffusion → general cytoplasmic availability

Payload release kinetics:
  - Zero-order release (reservoir devices)
  - First-order release (membrane-diffusion limited)
  - Burst + sustained (combination profiles)
  - Triggered release profiles per mechanism

Cell viability model:
  - Dose-response curves per cell type
  - Bystander effect for radiation/chemotherapy
  - Apoptosis vs. necrosis pathway prediction
```

### 3.4 Tissue Layer

**Enhanced Permeability and Retention (EPR) Effect**

```
Parameters (patient-derived from DICOM and biopsy data):
  - Vascular pore size distribution: 200–1200 nm (tumor-specific)
  - Blood flow rate: mL/g/min per tissue zone
  - Interstitial fluid pressure (IFP): 5–40 mmHg (barrier to NP extravasation)
  - Lymphatic drainage deficiency score
  - Vessel density (from immunohistochemistry or DCE-MRI data)
  - Hypoxia zone mapping (pO2 from BOLD MRI or OPT)

Passive vs. active targeting contribution:
  - Passive (EPR): modeled as size-dependent extravasation probability
  - Active (ligand): multiplied by receptor binding probability per region
```

**Tumor Microenvironment (TME)**

```
TME zones modeled:
  - Normoxic core: standard cell physiology
  - Hypoxic rim: pO2 < 10 mmHg, reduced therapeutic efficacy
  - Necrotic core: cell death, potential drug release sink
  - Peri-vascular zone: high NP concentration immediately post-extravasation
  - Stromal barrier: CAF density, collagen content (diffusion resistance)
  - Immune infiltrate: TIL density, M1/M2 macrophage ratio, NK cells

Cytokine release modeling:
  - TNF-α, IFN-γ, IL-6, IL-10, IL-1β
  - Cytokine storm risk prediction
  - Checkpoint expression dynamics (PD-L1, CTLA-4)
```

**Blood-Brain Barrier (BBB) Model**

```
Tight junction permeability:
  - Baseline: logP prediction for small molecules
  - Receptor-mediated transcytosis pathways:
      Transferrin receptor (TfR1): anti-TfR antibody-coated NPs
      LRP1 (low-density lipoprotein receptor-related protein 1): peptides
      GLUT1: glucose-coated NPs
  - Efflux pump modeling:
      P-glycoprotein (ABCB1): substrate prediction
      BCRP (ABCG2): substrate prediction
  - Carrier-mediated transport: amino acid analogues, nucleoside analogues
  - Disruption protocols: focused ultrasound + microbubble simulation

Output:
  - CNS bioavailability fraction (Kp,uu,brain)
  - Transcytosis rate constant
  - Efflux pump clearance rate
```

**Immune Interactions**

```
Complement activation:
  - Classical pathway: anti-NP IgG (pre-existing or induced)
  - Alternative pathway: hydroxyl groups on surface
  - CARPA (complement activation-related pseudo-allergy)
  - Prevention: PEGylation, zwitterionic coating

Protein corona formation:
  - Albumin: primary component, enhances circulation
  - Fibrinogen: pro-inflammatory
  - Apolipoproteins: long circulation
  - Corona composition prediction from NP surface chemistry
  - Dynamic corona (hard vs. soft corona evolution)

Opsonization and MPS clearance:
  - Kupffer cell uptake (liver, ~50% of dose)
  - Splenic filtration (rigid particles >200 nm)
  - Bone marrow macrophage uptake
  - Stealth modification efficacy (PEG density model, brush vs. mushroom)
  - Anti-PEG antibody effect (PEG-specific IgM, second injection problem)
```

### 3.5 Systemic Layer

**Pharmacokinetic Model**

```
Two-compartment model:
  Compartment 1 (central): blood plasma + highly perfused organs
  Compartment 2 (peripheral): muscle, fat, slowly perfused tissue

  dC₁/dt = -k₁₂·C₁ + k₂₁·C₂ - k_e·C₁ + input(t)
  dC₂/dt =  k₁₂·C₁ - k₂₁·C₂

Parameters:
  - Volume of distribution (Vd): size and surface chemistry dependent
  - Clearance (CL): hepatic + renal + MPS
  - Half-life (t₁/₂): ln(2)·Vd/CL
  - AUC (area under curve): therapeutic exposure metric
  - Cmax: peak concentration prediction
  - Tmax: time to peak

PEGylation effect on circulation time:
  PEG MW 2000: t₁/₂ ≈ 2h
  PEG MW 5000: t₁/₂ ≈ 8h
  PEG MW 20000: t₁/₂ ≈ 15h
  Zwitterionic: t₁/₂ ≈ 20–30h (extended)
```

**ADMET Prediction**

```
Absorption: route-specific (IV, SC, oral NP stability, inhalation deposition)
Distribution: tissue partition coefficients per organ
Metabolism: hepatic CYP enzyme susceptibility (small molecule payloads)
Excretion: renal (size < 8nm filtered), biliary, fecal
Toxicity: hERG cardiotoxicity, hepatotoxicity, genotoxicity prediction
```

### 3.6 Therapy Modeling

**Supported Therapeutic Modalities**

| Modality | Delivery Vehicle Options | Key Metrics Computed |
|---|---|---|
| CRISPR gene editing | LNP, viral vector, NP | On-target efficiency %, off-target risk score, indel spectrum |
| siRNA / RNAi | LNP, exosome | Knockdown %, duration, off-target effects |
| mRNA therapy | LNP | Protein expression level, duration, immunogenicity |
| Chemotherapy | PEGylated NP, liposome, polymer micelle | Tumor AUC, healthy tissue AUC, therapeutic index |
| Immunotherapy | NP + checkpoint inhibitor | T-cell activation score, tumor infiltration delta, checkpoint occupancy |
| Antiviral | Lipid NP, pH-responsive polymer | Viral reservoir penetration, intracellular drug concentration |
| Antibacterial | PLGA NP, chitosan | Biofilm penetration depth, MIC achievement |
| Photodynamic therapy | Photosensitizer-loaded NP | ROS generation, singlet oxygen quantum yield |
| Sonodynamic therapy | Sonosensitizer NP | Cavitation probability, ROS yield |
| Radiotherapy enhancement | Gold NP, gadolinium NP | Dose enhancement factor (DEF), radiosensitization |
| Gene replacement | AAV-NP hybrid, lentiviral | Integration efficiency, expression cassette stability |

**Combination Therapy Synergy Models**

| Combination | Synergy Type | Interaction Modeled |
|---|---|---|
| Chemo + Immunotherapy | Immunogenic cell death | Calreticulin exposure, HMGB1 release, DC maturation |
| CRISPR + Chemo | Sensitization editing | Resistance gene knockout (BRCA2, MLH1) before chemo |
| CRISPR + Immunotherapy | Neoantigen generation | Targeted mutation → immune recognition |
| siRNA + Chemo | Synergistic anti-survival | MDR1/ABCB1 knockdown → chemo sensitization |
| RNA + Immunotherapy | Checkpoint modulation | PD-L1 siRNA knockdown + anti-CTLA-4 NP |
| Sonodynamic + CRISPR | Sequential delivery | Sonoporation-enhanced gene delivery |
| Antiviral + CRISPR (HIV) | Excision + immune activation | Latency reversal + Cas9 excision combination |

**Automated Combination Selection Algorithm**

```
1. Enumerate all feasible therapy pairings (combinatorial)
2. Filter by:
   - Patient genomic contraindications (VCF pharmacogenomics)
   - Known adverse interaction database lookup
   - Organ function constraints (renal, hepatic thresholds)
3. Pre-score using polygenic risk integration + ML ranker
4. Select top N (default 5) combinations for detailed simulation
5. Run detailed Monte Carlo simulation per combination
6. Rank by:
   - Predicted therapeutic efficacy (primary)
   - Predicted adverse event probability (secondary)
   - Synergy score (tertiary)
7. Output ranked list with confidence intervals
8. Allow manual override at any step
```

### 3.7 Back-Testing and Iterative Refinement

```
Process:
1. Load historical patient simulation run parameters
2. Import clinical outcome data (response rate, adverse events, survival)
   Formats: CSV, FHIR DiagnosticReport, clinical trial JSON
3. Re-run simulation with identical inputs
4. Compute prediction error:
   - Targeting efficiency predicted vs. estimated actual
   - Adverse event probability predicted vs. observed
5. Bayesian parameter adjustment:
   - MPS clearance rate
   - EPR efficiency coefficient
   - Endosomal escape probability
   - Protein corona composition
6. Update model weights in production pipeline
7. Cross-validation on held-out cases
8. Confidence interval reporting per output metric

Validation datasets supported:
  - ClinicalTrials.gov XML export
  - Published nanoparticle PK/PD datasets (manually curated)
  - Patient case studies (de-identified FHIR format)
  - In vitro / in vivo correlation (IVIVC) datasets
```

### 3.8 Machine Learning Integration

**On-Device (TinyML — hardware inference)**

| Device | Model | Architecture | INT8 Size | Inference Time |
|---|---|---|---|---|
| NFSIM-ECG-01 | AFib + arrhythmia classification | LSTM + FC | 20 KB | 0.5ms @ 170MHz |
| NFSIM-EEG-01 | Sleep stage classification | Conv1D + GRU | 40 KB | 2ms @ 480MHz |
| NFSIM-EMG-01 | Gesture recognition (8-class) | MLP | 50 KB | 0.2ms @ 480MHz |
| NFSIM-BREATH-01 | VOC pattern classification | PCA + Neural Net | 30 KB | 5ms |
| NFSIM-CRISPR-01 | Amplification curve classification | 1D CNN | 15 KB | 1ms |
| NFSIM-FLOW-01 | Cell population gating | Gaussian Mixture | 10 KB | 0.5ms |
| NFSIM-MICRO-01 | Cell morphology / pathology | MobileNetV3-S | 2.1 MB (RPi) | 80ms |
| NFSIM-CAP-01 | Mucosal pathology | MobileNetV2 INT8 | 3.4 MB (host) | External |

**Edge (Desktop/Local inference)**

```
Framework: PyTorch (training), ONNX Runtime (inference)
Models (up to 500 MB, on local GPU/CPU):
  - Nanopore basecaller: CRNN (LSTM + CNN), CTC decoding → FASTQ output
  - DICOM segmentation: nnU-Net architecture → organ boundary extraction
  - Genomic variant annotation: XGBoost + CADD scores
  - Low-field MRI reconstruction: U-Net super-resolution (FastMRI-trained)
  - Flow cytometry gating: GMM + SVM pipeline
```

**Cloud / Federated (privacy-preserving)**

```
Federated learning:
  - Local model training on patient data
  - Only model gradients shared (not data)
  - Differential privacy: Gaussian noise (ε=1, δ=10⁻⁵) added to gradients
  - Secure aggregation: cryptographic gradient aggregation

Cloud tasks (optional, patient-authorized):
  - Population-level therapy outcome prediction refinement
  - Nanoparticle design optimization (larger search space on cloud GPUs)
  - Rare disease cohort matching (de-identified)
```

**Simulation Engine ML (Rust backend)**

```
Bayesian Optimization for nanoparticle design:
  - Gaussian Process surrogate model
  - Expected Improvement acquisition function
  - Search space: size (10–500nm), charge (-30 to +30 mV), PEG density, ligand type

Therapy Ranking Model:
  - Gradient-boosted tree ensemble (LightGBM)
  - Input: patient VCF features, tumor transcriptomics, clinical metadata
  - Output: ordinal therapy efficacy score (0=poor, 1=intermediate, 2=good)
  - Ordinal loss: quadratic weighted kappa optimization
  - Trained on aggregated published clinical trial data + NanoFlowSIM-validated cases
```

### 3.9 Expanded Clinical Applications

**Oncology**
- Heterogeneous solid tumor treatment optimization
- Metastatic cancer multi-site simultaneous targeting
- Drug resistance evolution modeling (clonal dynamics)
- CAR-T cell nanoparticle delivery optimization
- Radioimmunotherapy (targeted radionuclide + NP)
- Tumor organoid-calibrated simulation (patient-derived organoid data import)

**HIV Treatment**
- CRISPR-Cas9-mediated HIV DNA excision from T-cell latent reservoirs
- CCR5 co-receptor gene disruption (functional cure strategy)
- Immune checkpoint modulation to reactivate latent reservoirs (shock and kill)
- Antiretroviral nanoparticle delivery optimization (brain reservoir)
- CNS reservoir penetration modeling (BBB crossing)
- Long-acting injectable NP formulation optimization

**Herpesvirus Infections (HSV-1, HSV-2, VZV, CMV, EBV)**
- CRISPR payload delivery to neural ganglia
- BBB and peripheral nerve crossing simulation
- Antiviral combination delivery optimization (acyclovir + immune modulator)
- Recurrence suppression protocol design
- Latent reservoir reactivation and elimination simulation

**Rare Genetic Diseases**
- Single-gene therapy delivery simulation (monogenic disorders)
- Tissue-specific targeting for organ-of-interest
- Off-target risk minimization for rare pediatric cases
- Patient-specific variant-to-therapy pathway mapping
- AAV serotype selection simulation (tissue tropism model)
- RNA replacement therapy (mRNA therapy for protein deficiency)

**Neurological Disorders (Parkinson's, Alzheimer's, MS, ALS, epilepsy)**
- BBB crossing NP optimization for CNS drug delivery
- Neuron-targeted gene editing simulation (SNCA, HTT, ATXN1 loci)
- Alpha-synuclein / amyloid-beta clearance nanoparticle strategies
- Anti-neuroinflammatory delivery to microglia
- Neuroprotective agent delivery timing optimization

**Autoimmune Diseases (MS, Lupus, RA, IBD, Type 1 Diabetes)**
- Regulatory T-cell targeted immunomodulation nanoparticles
- Localized immunosuppression (joint, gut, kidney) without systemic effects
- CRISPR immune tolerance restoration (antigen-specific Treg induction)
- Combination biologic + NP therapy synergy modeling

**Cardiovascular Diseases**
- Arterial plaque-targeting nanoparticle design (atherosclerosis)
- Cardiomyocyte gene therapy delivery post-myocardial infarction
- Growth factor delivery for tissue regeneration (VEGF, FGF nanoparticles)
- Clot-targeting thrombolytic delivery (fibrin-targeted NP)
- Cardiac fibrosis gene silencing (TGF-β pathway)

**Antimicrobial Resistance (AMR)**
- Phage-CRISPR hybrid system delivery simulation
- Antibiotic + NP synergistic delivery for resistant biofilms
- Biofilm penetration depth modeling (Pseudomonas, Staphylococcus)
- Efflux pump inhibitor co-delivery optimization

**Broad Infectious Diseases**
- SARS-CoV-2 and respiratory virus antiviral nanoparticles
- Malaria parasite-stage-specific targeting (hepatic, blood stage)
- Fungal biofilm penetration modeling (Candida, Aspergillus)
- Tuberculosis macrophage-targeted drug delivery
- Leishmaniasis (intracellular parasite, macrophage targeting)

### 3.10 System Workflow

**Step 1: Data Collection**

| Data Type | Format | Source |
|---|---|---|
| Genomic mutations | VCF, FASTQ | Sequencing lab, NFSIM-SEQ-01 |
| CRISPR target loci | BED, FASTA | Computational + lab |
| Proteomic profiles | mzML, CSV | Mass spectrometry |
| MRI / CT imaging | DICOM | Hospital, NFSIM-MRI-01 |
| Immune cell profiling | FCS | Flow cytometry, NFSIM-FLOW-01 |
| Continuous biosensor | JSON stream | Any NFS device |
| Microbiome | FASTQ | 16S or WGS sequencing |
| SNP panel | VCF | Array or NFSIM-SEQ-01 |
| Liquid biopsy cfDNA | BAM, VCF | Sequencing |
| Metabolomics | mzML | Mass spec or NFSIM-BREATH-01 |

**Step 2: Simulation Configuration**

```
Therapeutic goal selection:
  Mode 1 — Single Therapy: CRISPR / Chemotherapy / Immunotherapy / Gene Replacement / RNA Therapy
  Mode 2 — Combination: any multi-agent pairing
  Mode 3 — Automated: AI-ranked screening of all viable combinations

Nanoparticle design parameters:
  Size: 1–500 nm (continuous or discrete options)
  Shape: Spherical / Rod / Disc / Core-Shell / Liposomal / Polymeric / Dendrimer
  Surface coating: PEG density, ligand type, surface charge (zeta potential)
  Ligand: Antibody / Aptamer / Peptide / Small molecule / CRISPR-RNP
  Ligand density: molecules per nm²
  Payload: siRNA / mRNA / CRISPR-Cas / Chemotherapy drug / Cytokine / Radionuclide
  Payload loading: % encapsulation efficiency
  Release mechanism: pH-triggered / Enzymatic / Thermal / Light / Mechanical / Voltage

Customization options:
  - Manual parameter entry (expert mode)
  - Predefined templates for common therapeutic targets
  - Patient contraindication auto-filter
  - Prior simulation import (iterate from existing design)
```

**Step 3: Simulation Execution**

Layer execution order:
```
1. Molecular layer → binding probability, payload stability confidence
2. Cellular layer → uptake rate, escape probability, payload release profile
3. Tissue layer → extravasation, TME penetration, regional distribution
4. Systemic layer → PK curve, immune clearance, organ distribution
5. Output assembly → targeting efficiency, AUC, toxicity prediction
6. Visualization data generation → 3D trajectory coordinates, heatmap arrays
```

**Step 4: Output Analysis**

| Output | Description |
|---|---|
| Targeting Efficiency | % nanoparticles reaching target site (with 95% CI) |
| Payload Release Profile | Release % over time with compartmental PK curve |
| Off-Target Distribution | Organ-level accumulation heatmap |
| Side Effect Profile | Predicted toxicity with probability scores |
| Immune Response Curve | Predicted Ab titer and cytokine release trajectory |
| Editing Efficiency Map | CRISPR on/off-target efficiency per chromosomal locus |
| Therapy Synergy Score | Combined benefit vs. individual therapy prediction |
| Optimization Suggestions | AI-recommended design parameter adjustments |

**Step 5: Back-Testing and Validation**

```
After obtaining patient outcome data:
1. Import clinical response data (CSV / FHIR / JSON)
2. Run prediction-vs-outcome comparison
3. Auto-refine model parameters (Bayesian update)
4. Re-simulate with updated parameters
5. Track prediction accuracy improvement over iterations
6. Publish de-identified validation contributions to community dataset
```

---

## 4. Patient Data Architecture — The Living Body Map

### 4.1 Core Design Philosophy

The 3D human body is the universal anchor for all data. Not folders. Not departments. Not tables. The body itself.

When a user clicks on their kidney in the 3D model, they see simultaneously:
- Creatinine and GFR values from all blood tests ever taken (timeline)
- Continuous monitoring data if a renal function sensor is active
- DICOM imaging studies of the kidney (CT, ultrasound, MRI)
- Any genomic variants in genes expressed in the kidney (UMOD, PKD1, APOL1)
- Medications affecting renal clearance
- Any nanoparticle simulation runs targeting renal tissue
- Environmental or dietary factors tagged as relevant
- Research literature cross-referenced to their specific variants (optional)

### 4.2 UBERON Anatomical Tagging System

All data uses UBERON (Uber Anatomy Ontology) codes. UBERON is a cross-species anatomical ontology used by NIH, EBI, and major genomics databases.

| UBERON Code | Anatomical Region | Common Data Types |
|---|---|---|
| UBERON:0000948 | Heart | ECG, cardiac enzymes, echocardiography |
| UBERON:0002048 | Lung | SpO2, spirometry, chest imaging, breath |
| UBERON:0002107 | Liver | LFTs, hepatic imaging, drug metabolism SNPs |
| UBERON:0002113 | Kidney | Creatinine, GFR, renal imaging |
| UBERON:0001017 | Central nervous system | EEG, brain MRI, CSF markers |
| UBERON:0002369 | Adrenal gland | Cortisol, catecholamines |
| UBERON:0001114 | Pancreas | Glucose, insulin, pancreatic imaging |
| UBERON:0000945 | Stomach | pH capsule data, gastric imaging |
| UBERON:0002115 | Jejunum | Capsule sensor data, microbiome |
| UBERON:0001155 | Colon | Colonoscopy data, microbiome, motility |
| UBERON:0000178 | Blood | CBC, metabolic panel, genomics, cfDNA |
| UBERON:0004537 | Bloodstream (systemic) | Systemic lab values without organ specificity |
| UBERON:0001416 | Skin | Temperature, sweat sensors, dermatology |
| UBERON:0000029 | Lymph node | Immune cell profiling, PET imaging |
| UBERON:0001134 | Skeletal muscle | EMG, lactate, biopsy data |
| UBERON:0002367 | Prostate | PSA, prostate imaging |
| UBERON:0000995 | Uterus | Gynecologic imaging, hormonal data |
| UBERON:0001987 | Placenta | Maternal-fetal monitoring (pregnancy mode) |
| UBERON:0002370 | Thyroid | TSH, T3/T4, thyroid imaging |
| UBERON:0004548 | Eye | Retinal imaging, IOP, OCT |

**Systemic/Blood Data Anchoring Logic:**

Lab values without a single organ anchor (cholesterol, HbA1c, CRP) are handled as:

```
Option A: Tag to UBERON:0004537 (bloodstream/systemic) — shown as whole-body overlay
Option B: AI-suggested primary organ anchor based on clinical context:
  - Serum glucose       → UBERON:0001114 (pancreas) + UBERON:0004537
  - Creatinine          → UBERON:0002113 (kidney)
  - Troponin            → UBERON:0000948 (heart)
  - ALT/AST             → UBERON:0002107 (liver)
  - TSH                 → UBERON:0002370 (thyroid)
  - PSA                 → UBERON:0002367 (prostate)
  - HbA1c               → UBERON:0004537 (systemic glycemic control)
  - CRP                 → UBERON:0004537 + inflammatory overlay
Option C: User override (always permitted)
```

### 4.3 Data Model

```
PatientProfile {
  patient_id:        UUID  (locally generated, never server-generated)
  created_at:        ISO8601
  display_name:      string (local only)
  anthropometrics: {
    height_cm:       f32
    weight_kg:       f32
    age:             u8
    biological_sex:  enum { Male, Female, Intersex }
    ethnicity:       string  (optional, used for pharmacogenomics adjustments)
  }
  body_map_level:    0..4

  data_records: [DataRecord]
  active_sessions: [MonitoringSession]
  simulation_runs: [SimulationRun]
  consents: [ConsentRecord]
}

DataRecord {
  record_id:            UUID
  timestamp:            ISO8601 (when measurement was taken)
  ingested_at:          ISO8601 (when added to NanoFlowSIM)
  source: enum {
    NFSDevice { device_id: String, session_id: UUID },
    HospitalImport { institution: String, fhir_id: String },
    ManualEntry,
    WearableSync { platform: String },
    LabImport,
    ImagingImport
  }
  data_type:           enum DataType  (ECG, Glucose, MRI, VCF, ...)
  uberon_primary:      UBERON code
  uberon_secondary:    [UBERON codes]
  is_continuous:       bool
  continuous_session:  UUID | null
  raw_data:            JSON | BinaryRef (MinIO object key)
  processed_data:      JSON
  quality_score:       f32  (0.0 to 1.0)
  notes:               String
  attachments:         [FileRef]
  simulation_linked:   [UUID]
  fhir_id:             String | null  (for hospital-imported records)
  dicom_uid:           String | null  (for imaging)
}

MonitoringSession {
  session_id:          UUID
  device_id:           String
  device_type:         enum NFSDeviceType
  started_at:          ISO8601
  ended_at:            ISO8601 | null
  data_type:           DataType
  sampling_rate_hz:    f32
  uberon_region:       UBERON code
  record_count:        u64
  stream_endpoint:     URL | BLE characteristic UUID
}

SimulationRun {
  run_id:              UUID
  created_at:          ISO8601
  nanoparticle_config: JSON
  therapy_config:      JSON
  patient_snapshot_id: UUID
  grpc_job_id:         String
  status:              enum { Queued, Running, Complete, Failed }
  results:             JSON | null
  visualization_ref:   String | null  (MinIO object key for 3D trajectory data)
}

ConsentRecord {
  consent_id:          UUID
  scope:               String  (research sharing, institution access, etc.)
  granted_at:          ISO8601
  expires_at:          ISO8601 | null
  grantee:             String
}
```

### 4.4 Data Storage Architecture

**Client-side (local-first):**

```
SQLite database (desktop: better-sqlite3, mobile: expo-sqlite):
  - All metadata, records, session logs, simulation references
  - Encrypted at rest (SQLCipher with device keychain key)
  - Full offline read/write capability

MinIO-compatible local object storage:
  - Binary data: DICOM files, FASTQ, FCS, large images
  - Path scheme: /patient-{id}/{data-type}/{record-id}.{ext}
  - Encrypted at object level

Federated sync options:
  1. Self-hosted: patient runs Docker Compose on home server
  2. Provider-hosted: patient-authorized cloud instance
  3. DID-based: Decentralized Identity, BitTorrent-style data seeding
```

**Hospital Record Integration:**

```
Step 1: User selects "Import Medical Records" → enters institution name
Step 2: System queries FHIR directory (smart.hl7.org) for institution endpoint
Step 3: OAuth2 SMART-on-FHIR authorization with institution patient portal
Step 4: FHIR R4 resource download:
         - Patient demographics
         - Observation (lab results)
         - DiagnosticReport
         - ImagingStudy (metadata + WADO-RS DICOM fetch)
         - Condition (diagnoses, ICD-10 coded)
         - MedicationRequest
         - Procedure
         - AllergyIntolerance
         - FamilyMemberHistory
Step 5: Auto-segmentation of DICOM imaging data
Step 6: UBERON tagging of all imported records
Step 7: Conflict detection for duplicate records
Step 8: Display import summary → user approves
Step 9: All records added to local SQLite + binary files to MinIO
```

**Data Privacy Architecture:**

```
Patient data never leaves device without explicit patient-initiated action.
No telemetry, no analytics, no data collection by NanoFlowSIM project.
No cloud sync by default.
GDPR compliance: patient is controller, NanoFlowSIM is processor only.
HIPAA best practices: encryption at rest, in transit, access logging.
Genomic data: local only by default. Nagoya Protocol compliance.
Right to erasure: complete local wipe function.
Right to portability: full export as FHIR R4 bundle + JSON + CSV.
```

---

## 5. UI/UX Specification — Consumer and Professional

### 5.1 Design Principles

1. **The body is the interface.** Not menus. Not category folders. Not a table of values. The 3D human body is the primary navigation element. All data lives on the body.
2. **Data capture takes visual priority over AI insights.** Every data-entry surface is prominently accessible. AI commentary is secondary.
3. **Two modes, one data layer.** Consumer and Professional views show identical underlying data with different depth and vocabulary. No data hidden, only complexity level differs.
4. **Live and historical always coexist.** Active sensor streams pulse in real time. Historical data is accessible by scrubbing a timeline. Both are simultaneously available.
5. **Click to add, click to view.** Any body region — even with zero data — is clickable to add data. Empty regions invite entry.
6. **Plain language default, clinical toggle.** Consumer mode uses plain English. One toggle switches all labels to clinical terminology for professional use.
7. **Progressive disclosure.** Start with the most important number. Tap to expand to trend. Tap again to expand to full history. Tap again to export raw data.
8. **Every feature is actually usable.** All UI flows have been designed end-to-end, not as wireframe stubs. Every button leads somewhere. Every form submits.
9. **Fluid animations that inform.** Body map transitions, data entry overlays, and live sensor pulses use animations that convey meaning (rate of change, severity) not decoration.
10. **Accessible design.** WCAG 2.1 AA minimum. Dyslexia-friendly font options. High-contrast mode. Screen reader support for all critical interactions.

### 5.2 3D Body Map System

**Rendering Stack:**

```
Desktop/Web: Three.js scene via @react-three/fiber
  - WebGL 2.0 backend
  - PBR (Physically-Based Rendering) materials for skin
  - Subsurface scattering for realistic tissue appearance
  - Dynamic LOD (Level of Detail) — higher resolution on zoom

Mobile: React Native Three Fiber
  - Native WebGL via expo-gl
  - Simplified mesh for performance on mobile GPUs
  - Touch gesture navigation (pinch, rotate, tap)

AR Mode (mobile): ARKit (iOS) / ARCore (Android)
  - Project body map overlay on camera view
  - Patient can point camera at their own body → overlay of live sensor data
  - Annotation of real body region with data from corresponding body map region
```

**Mesh Variants:**

```
Base meshes (open-source, CC0-licensed):
  - Male reference mesh (SMPL model or MBLab export)
  - Female reference mesh
  - Intersex / non-binary option (selectable variant)
  - Pregnancy overlay mode (uterus/fetal position as separate mesh layer)
  - Pediatric scaling (age 0, 2, 5, 8, 12, 16 interpolated)
  - Geriatric variant (age-appropriate proportions)
  - BMI/body composition morphing (BMI slider 16–45 range)

Patient-specific mesh generation (Level 2+):
  - DICOM → ITK-SNAP / SimpleITK segmentation pipeline
  - Output: organ surface meshes (STL/OBJ/GLB)
  - Loaded as replacements/overlays to base mesh
  - Tumor, lesion, structural anomalies: colored separate mesh objects
  - Vascular reconstruction from contrast-enhanced CT
```

**Layer System (all individually toggleable):**

```
Layer 0: Skin surface (exterior anatomy, default ON)
Layer 1: Skeletal mesh (bones, joints, vertebrae)
Layer 2: Vascular mesh (heart, major arteries, veins, lymphatics)
Layer 3: Organ mesh (liver, lungs, kidneys, brain, stomach, intestines)
Layer 4: Neural overlay (brain lobes, spinal cord, peripheral nerves)
Layer 5: Lymphatic overlay (lymph nodes, thymus, spleen)
Layer 6: Data heatmap overlay (sensor data → color-coded regional intensity)
Layer 7: Nanoparticle trajectory overlay (simulation output as particle stream)
Layer 8: Genomic variant overlay (regions with active variants highlighted)
Layer 9: Immune activity overlay (immune cell density, inflammation zones)
Layer 10: Surgical annotation layer (clinician-drawn annotations, professional mode)
```

**Interaction Model:**

```
Hover (desktop):       Region label tooltip + data record count badge
Click:                 Open Region Detail Panel (right side overlay)
Right-click:           Context menu:
                         "Add data here"
                         "View full history"
                         "Run simulation for this region"
                         "Export region data"
                         "Annotate (professional)"
Long-press (mobile):   Context menu (same as right-click)
Pinch to zoom:         Zoom from full-body to organ-level
Orbit:                 Rotate body 360° (left-drag or touch swipe)
Slice plane tool:      Drag a cutting plane through any axis → reveals interior cross-section
Pre-set views:         Anterior / Posterior / Left lateral / Right lateral / Superior / Inferior /
                       Coronal slice / Sagittal slice / Axial slice
Cinematic flythrough:  Automated camera path through body for presentations
```

**Data Visualization on Body (Visual Language):**

| Data State | Visual Representation |
|---|---|
| Active continuous sensor (ECG) | Pulsing blue glow over heart, rhythmic with detected HR |
| Active continuous sensor (glucose) | Pulsing green → yellow → red based on value/trend |
| Active continuous sensor (SpO2) | Pulsing orange, intensity by value |
| Active continuous sensor (EEG) | Oscillating purple shimmer over brain |
| Active continuous sensor (sweat) | Cyan shimmer over skin surface |
| Recent episodic data (<30 days) | Solid region highlight, region-specific color |
| Older data (30–365 days) | Faint outline ring around region |
| Data >1 year old | Neutral mesh color, archive icon on region |
| No data for region | Neutral mesh, faint "+" icon on hover/tap |
| Alert / anomaly detected | Red pulsing animation, notification badge |
| Nanoparticle simulation active | Animated white/yellow particle stream along vascular paths |
| Simulation complete | Static colored heatmap overlaid on target tissue |
| Genomic variant in region | Small chromosome icon, color by pathogenicity |

**Timeline Scrubber:**

```
Rendered at bottom of body map:
  [============================●] Now
  2022      2023      2024      2025      2026

Behavior:
  - Drag to any historical point → body map updates to show data state at that time
  - Regions with data at that time: highlighted
  - Regions with no data at that time: dimmed
  - Live sensor data: always shown at "Now" regardless of scrubber position
  - Animated replay: press play → body evolves forward through time at selectable speed
  - Zoom timeline: scroll on timeline → expand to day or hour granularity
  - Milestone markers: hospitalizations, diagnoses, medications start/stop shown as icons

Live + Historical simultaneously:
  - Scrubber can be at any historical point while live sensor still streams
  - "Comparison mode": ghost overlay of body at historical time + current live state
```

### 5.3 Consumer Mode

**Dashboard (Home Screen Layout):**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  NanoFlowSIM                             [🔔 Alerts]  [⚙ Settings]  [👤]   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                               │
│  ┌───────────────────────┐   ┌─────────────────────────────────────────┐    │
│  │                       │   │  REGION DETAIL: Heart                    │    │
│  │   [3D BODY MAP]       │   │  ─────────────────────────────────────  │    │
│  │                       │   │  📡 LIVE: ECG Patch active               │    │
│  │  ● Heart (live ECG)   │   │  ┌────────────────────────────────────┐ │    │
│  │  ● Glucose (live CGM) │   │  │  ~~~ECG waveform animation~~~      │ │    │
│  │  ○ Liver (12 records) │   │  └────────────────────────────────────┘ │    │
│  │  ○ Brain (5 records)  │   │  HR: 68 bpm  HRV: 42ms  Rhythm: Normal │    │
│  │                       │   │                                          │    │
│  │  [Rotate: drag body]  │   │  📋 RECENT HISTORY                       │    │
│  │  [Zoom: pinch]        │   │  • 2026-05-10: 12-lead ECG — Normal     │    │
│  │                       │   │  • 2026-03-15: Echo — EF 62%            │    │
│  │                       │   │  • 2025-12-01: Troponin — <0.01 ng/mL  │    │
│  │                       │   │  • 2025-09-15: Cholesterol panel        │    │
│  │                       │   │  [View all 47 cardiac records →]        │    │
│  └───────────────────────┘   │                                          │    │
│                               │  🧬 GENOMICS (2 variants)               │    │
│  [TODAY'S SUMMARY]            │  • SCN5A rs7626962 — ↑ LQT risk         │    │
│  Glucose stable all day       │  [View full genomic report →]           │    │
│  HR normal range              │                                          │    │
│  No alerts                    │  [+ Add Data]  [🔬 Run Simulation]      │    │
│                               └─────────────────────────────────────────┘    │
├─────────────────────────────────────────────────────────────────────────────┤
│  [Timeline] ────────────────────────────────────────────────────────● Now   │
│             2022              2023              2024        2025    2026      │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Region Detail Panel — Consumer View:**

```
[Region Name and Icon]
[Last Updated timestamp] [Live status indicator if streaming]

▼ LIVE DATA (if active continuous sensor)
  [Real-time value + unit]
  [Trend sparkline — last 24h]
  [Status badge: Normal / Caution / Alert]

▼ CURRENT READINGS
  [Most recent episodic values for key metrics in plain English]
  [When taken: X days ago]

▼ HISTORY
  [List of past records, most recent first]
  [Thumbnail for imaging, waveform preview for ECG]
  [Each item: date, type, summary result, source]
  [View all → opens full timeline filtered to this region]

▼ GENETICS
  [Simplified statement: "You have a variant in gene X.
   This may affect your risk of [condition]."]
  [Learn more → opens educational overlay]

▼ MEDICATIONS
  [Drugs currently active that affect this region]
  [From hospital import or manual entry]

▼ SIMULATIONS
  [Any nanoparticle simulation runs related to this region]
  [Run date, therapy type, brief outcome summary]
  [View full results → opens simulation workspace]

[+ Add Data]
[Share with Doctor]
[Request Lab Test] (links to suggested tests for this region)
[Export Region Data]
```

**Consumer Mode Additional Features:**

```
AI Health Brief:
  Updated weekly. One paragraph in plain English.
  "Over the past 7 days, your glucose has been well-controlled with
   an average of 103 mg/dL. Your heart rate variability has improved
   slightly, which may reflect better recovery. No abnormal ECG events
   were detected."

Trend Indicators:
  Per metric: ↑ improving / → stable / ↓ declining
  Over selectable windows: 7 days / 30 days / 90 days / 1 year

Device Connection Hub:
  - List of all connected NFS devices (active / inactive)
  - Connection status, battery level, last sync
  - "Connect new device" wizard
  - Pair via BLE scan / QR code / NFC tap

Notification Center:
  - Glucose out of range (CGM)
  - Arrhythmia detected (ECG)
  - Medication reminder
  - Lab result available
  - New hospital record imported
  - Simulation complete
  - Low device battery

Emergency Data Card:
  - QR code displays emergency health summary:
    blood type, critical allergies, current medications,
    active diagnoses, emergency contacts
  - Scannable offline from lock screen
```

### 5.4 Professional / Clinical Mode

Professional mode adds to everything in Consumer mode:

**Clinical Data Browser:**

```
Tab 1 — VITALS & MONITORING
  - Full-resolution waveform viewer:
    ECG: scrollable at 25mm/s standard, 10mm/mV standard, zoom controls
    EEG: scrollable, spectrogram view, per-channel toggle, event marking
    Glucose: AGP (Ambulatory Glucose Profile) 14-day standard view
    HRV: Lorenz/Poincaré plot, frequency domain (LF/HF ratio)
  - Statistical summaries with reference ranges
  - Export selected range: EDF, CSV, DICOM, FHIR Observation

Tab 2 — LABORATORY
  - Structured table: all blood/urine/genetic lab values
  - Columns: test name, value, unit, reference range, delta from last, date, source
  - Color coding: within normal, borderline, abnormal
  - Trend chart: any lab value over time (click to expand)
  - Filter by: date range, category (metabolic, hematologic, hepatic, renal...)
  - Clinical decision support: flagged results with differential suggestion

Tab 3 — IMAGING
  - DICOM viewer (Cornerstone.js embedded)
  - Windowing controls (W/L)
  - Measurement tools (distance, area, angle, HU density)
  - Multi-planar reconstruction (MPR) for 3D DICOM
  - Linked to 3D body map: clicking an organ in viewer highlights body map region
  - AI segmentation overlay (organ boundaries, lesion detection)
  - Series comparison: side-by-side prior vs current

Tab 4 — GENOMICS
  - Variant browser (VCF viewer)
  - Filter by: pathogenicity (P/LP/VUS/LB/B), gene, chromosome, consequence type
  - Columns: gene, variant, zygosity, CADD score, gnomAD AF, classification, date
  - Pathway enrichment viewer: which biological pathways have variants
  - Pharmacogenomics table: drug-gene interactions from current variant profile
  - CRISPR target candidates: automatically identified target sites per variant
  - Copy number variation (CNV) viewer: gain/loss segments on ideogram

Tab 5 — SIMULATION
  - Full NanoFlowSIM simulation launcher
  - All nanoparticle and therapy parameters exposed
  - Batch simulation: run multiple configurations simultaneously
  - Real-time progress: per-layer completion status
  - Result comparison: side-by-side outputs from multiple runs
  - Export: PDF clinical report / JSON / CSV / 3D visualization file

Tab 6 — COHORT (institution accounts)
  - De-identified population comparisons
  - Variant frequency maps across enrolled cohort
  - Therapy outcome comparison by patient cluster
  - Clinical trial enrollment tracking
  - Aggregate body map: population data density overlaid on shared anatomy
```

**Additional Professional Tools:**

```
Annotation Layer:
  - Free-draw on 3D body map (markup tool)
  - Text annotations anchored to regions
  - Shareable with other clinicians (consent required)
  - Persistent across sessions

Multi-Patient Dashboard:
  - Grid view of multiple patients (clinic/hospital accounts)
  - Status indicators per patient: active alerts, pending imports
  - Sort by: last active, alert severity, diagnosis

API Access Panel:
  - API key generation and rotation
  - Webhook configuration for data push events
  - FHIR export endpoint configuration
  - Simulation API documentation (inline)

Audit Log:
  - Complete access log: who viewed, what data, when
  - Consent tracking per data access event
  - HIPAA-compliant audit trail export
```

### 5.5 Data Capture Workflows

**Manual Entry — Lab Value:**

```
1. User taps [+ Add Data] on body region OR global [+] button
2. Modal opens: "What type of data are you adding?"
   → [Lab Test] [Medical Image] [Symptom/Note] [Medication]
     [Device Data (manual)] [Other]
3. Select "Lab Test"
4. Searchable list: type test name or select from categories
   (Metabolic / Hematologic / Cardiac / Hepatic / Renal / Hormonal / Genomic / Imaging...)
5. Enter value and unit (auto-suggested units for selected test)
6. Enter date and source (hospital name / self-collected / pharmacy)
7. Optional: upload supporting document (PDF, image → OCR extraction)
8. System: auto-assigns UBERON codes, suggests related conditions
9. User: confirms or adjusts UBERON tags
10. Record appears immediately: body map highlight + timeline + region history
```

**Hospital Record Import:**

```
1. "Import Records" → "Connect to Hospital"
2. Enter hospital name → system searches FHIR endpoint registry
3. OR: manual FHIR URL entry (for tech-savvy users)
4. OR: upload exported file (PDF, CCR/CCD XML, FHIR JSON bundle)
5. FHIR: OAuth2 SMART-on-FHIR flow → patient portal authorization
6. Preview: list of available records by category with count
7. User selects which categories to import (all by default, opt-out)
8. Import: all records downloaded, parsed, UBERON-tagged
9. DICOM: automatically segmented and 3D-anchored to body regions
10. Conflict detection: duplicate records flagged for user resolution
11. Summary: "Imported 847 records from Memorial Hospital. Added to your body map."
```

**NFS Device Connection:**

```
1. Tap [+ Connect Device] or tap a body region and choose "Connect device here"
2. Device type selector (searchable grid of all NFS device types with icons)
3. Connection method selection: [BLE] [USB-C] [NFC tap]
4. BLE: app scans for nearby NFS devices → shows device list with signal strength
5. Select device → pair → device assigns patient ID (stored in device NVS)
6. Calibration wizard if applicable (device-specific prompts)
7. Session starts → body region glows live
8. Session ends: all data saved, processed, archived, UBERON-tagged
9. Device shows in "My Devices" panel with last-sync time and battery
```

**Device Placement Guidance (UI Overlay):**

```
When connecting an ECG patch:
  → Body map switches to anterior chest view
  → Animated placement guide shows exactly where to apply patch
  → "Place left edge of patch on left side of sternum, centered on the 4th rib"
  → Photo reference option (camera for placement verification)
  → Impedance check result shown per electrode (green/yellow/red)
  → "Good contact detected. Session starting."

When connecting EEG headset:
  → Brain anatomy view activates
  → 10-20 electrode positions highlighted with numbered placement guide
  → Per-electrode impedance shown in real-time as user adjusts
  → "All channels ready. Starting session."
```

### 5.6 Live vs. Historical Mode

**Live Mode (Active Continuous Sensor Present):**

```
Activation: automatic when any connected device streams data

Visual indicators:
  Heart region (ECG): rhythmic glow pulse synced to detected R-peaks
  Glucose region (pancreas + bloodstream): color gradient shifts:
    Green (<100 mg/dL) → Yellow (100–180) → Orange (>180) → Red (>250)
    With directional arrow: ↑↑ rapid rise, ↑ rising, → stable, ↓ falling
  SpO2 region (lungs): cyan pulse, intensity proportional to reading
  EEG region (brain): oscillating shimmer in frequency-band colors
  Temperature (skin): warm gradient, shifts from blue-green to orange-red
  EMG (muscle region): flash intensity proportional to activation amplitude

Data overlays:
  Value badges float near body region (e.g., "103 mg/dL ↑")
  Device icon floats near attachment point (wrist, chest, arm...)
  Sensor status indicator: green = good signal, yellow = check device, red = disconnected

Multi-sensor simultaneous:
  All active sensors display simultaneously
  Regional overlaps prioritized by clinical significance
  Transparency used to layer multiple data types without occlusion
```

**Historical Mode:**

```
Activation: when no active sensors, or when user pulls timeline backward

Timeline scrubber visible and prominent at screen bottom
As user scrubs backward:
  Regions light up based on data available at that moment
  Regions without data at that time dim to neutral
  The body map shows "state at that moment" across all layers

Animated Replay:
  Play button at left of timeline
  Playback speeds: 1× / 10× / 100× / 1000×
  Body evolves visually through time
  Useful for: watching glucose trend over a week, observing ECG over a month

Comparison Mode:
  Select two timepoints (A and B)
  Body map shows two ghost meshes side by side or overlaid with color difference
  Highlight regions where data changed significantly between timepoints
```

### 5.7 Regional Data Interaction

**Surface Interaction (Outer Anatomy):**

```
Click any visible skin/surface region:
  → Returns: skin sensor data, patch readings, external wound or exam findings,
             dermatology images, radiation dosimetry from imaging,
             tattoos and body markers (clinician annotation)

Example: clicking forearm
  → Shows: NFSIM-SWEAT-01 data (Na+, K+, lactate)
           NFSIM-EMG-01 armband data
           IV cannulation site annotation if marked
           Skin rash photo (uploaded from dermatology visit)
```

**Depth Interaction (Inner Anatomy):**

```
Slice plane tool exposes interior → click any internal organ or structure:
  → Returns: all data anchored to that structure including
             imaging findings, biopsy results, implant data,
             simulated nanoparticle trajectories, genomic expression data,
             blood chemistry values mapped to that organ, capsule sensor data

Example: clicking liver after DICOM import
  → Shows: 3D liver mesh from CT segmentation
           Multiple liver CT series (timeline)
           LFTs from all blood tests (ALT, AST, GGT, bilirubin timeline chart)
           Pharmacogenomics variants in CYP2D6, CYP3A4
           Any nanoparticle simulations targeting liver
           Medication metabolism data
```

**Cross-Layer Correlation:**

```
Select two or more regions → tap "Correlate"
System performs:
  1. Identify all shared data types across both regions (by timing)
  2. Statistical correlation (Pearson, Spearman depending on data type)
  3. Time-lag correlation (does change in region A predict change in region B?)
  4. Clinical significance flagging

Example: correlate heart + kidney
  → Displays: troponin vs. creatinine correlation over time
              (cardiorenal syndrome pattern detection)
              BNP vs. GFR inverse correlation
              Medication effects on both

Example: correlate glucose + EEG
  → Displays: hypoglycemia events correlated with EEG theta-band changes
```

**Pattern Recognition Overlays (Professional Mode):**

```
Gradient analysis:
  - Show rate-of-change for any metric overlaid on body map
  - "How fast is each region's key metric changing?"

Predictive heatmap:
  - AI model predictions for next 24h (e.g., glucose trajectory)
  - Displayed as translucent future state overlay

Risk overlay:
  - Polygenic risk scores displayed as color intensity per organ
  - "High cardiovascular risk" → heart region highlighted red
  - Based on combined SNP data + clinical risk factors
```

### 5.8 Mobile-Specific UX

```
Home Screen Widget (iOS/Android):
  Glanceable vitals without opening app
  Shows: current glucose, heart rate, SpO2, step count, last update time
  Tap widget → opens body map directly to most recently active region

AR Mode (iOS ARKit / Android ARCore):
  Activate via camera button in body map
  Camera feed with body overlay
  Patient points at own body → live sensor data overlaid on camera view
  Touch detected body region → region detail panel opens
  Useful for: nurse-patient education, self-monitoring guidance

Notification System:
  Priority 1 (critical): Glucose <54 or >350 mg/dL, sustained arrhythmia
    → Immediate notification with emergency action guidance
  Priority 2 (alert): Abnormal value detected, arrhythmia, SpO2 <90%
    → Alert notification with "View details"
  Priority 3 (info): Medication reminder, sync complete, simulation done
    → Silent notification with badge

Offline Mode:
  Full data viewing and manual entry works completely offline
  Background sync when connection restored
  No cloud dependency for core features

Haptic Feedback:
  - Successful data entry: light tap
  - Alert: double buzz
  - Device connected: escalating triple tap
  - Simulation complete: gentle sustained buzz

Camera Functions:
  - Photograph medical documents: OCR → structured data extraction → add to record
  - Photograph prescriptions: AI parses drug name, dose, frequency → medication record
  - Photograph lateral flow test results: AI reads test line → result recorded
  - Photograph skin lesion: date-stamped photo → linked to skin body region

Voice Entry:
  - Dictate symptoms: "I have been feeling mild chest pain since this morning, 3/10"
    → Structured symptom record with NLP-extracted metadata
  - Dictate medication change: "Stopped lisinopril, started losartan 50mg daily"
    → Medication update record
```

---

## 6. Data Integration — Full Loop (Current and Future)

### 6.1 Non-Continuous Data Sources

| Data Category | Specific Type | Format | Integration Method |
|---|---|---|---|
| Genomic | SNP array (23andMe, Ancestry, AncestryDNA) | raw .txt | Direct import + LIFTOVER to GRCh38 |
| Genomic | Whole genome sequence | FASTQ, BAM, VCF | NFSIM-SEQ-01 output or lab upload |
| Genomic | Exome sequence | FASTQ, BAM, VCF | Lab upload |
| Genomic | RNA-seq (transcriptome) | FASTQ, counts matrix | Lab upload |
| Genomic | Liquid biopsy cfDNA | BAM, VCF | Lab upload |
| Genomic | Epigenetic methylation array | IDAT | Lab upload |
| Imaging | MRI | DICOM | FHIR WADO-RS or file import |
| Imaging | CT | DICOM | FHIR or file import |
| Imaging | X-ray | DICOM | FHIR or file import |
| Imaging | PET scan | DICOM | FHIR or file import |
| Imaging | Ultrasound image | DICOM | NFSIM-US-01 output or file import |
| Imaging | OCT | DICOM | NFSIM-OCT-01 output or file import |
| Imaging | Capsule endoscopy | AVI/MP4 | NFSIM-CAP-01 output |
| Pathology | Tissue biopsy slide | SVS, TIFF | NFSIM-MICRO-01 output or lab upload |
| Pathology | Cytopathology | SVS, TIFF | Lab upload |
| Blood labs | CBC | FHIR Observation, CSV | Hospital import or manual |
| Blood labs | Comprehensive Metabolic Panel | FHIR, CSV | Hospital import or manual |
| Blood labs | Lipid panel | FHIR, CSV | Hospital import, NFSIM-CHEM-04 |
| Blood labs | Hormone panels (TSH, cortisol, etc.) | FHIR, CSV | Hospital or NFSIM-CHEM-07 |
| Blood labs | Tumor markers (CEA, PSA, CA-125) | FHIR, CSV | Hospital import |
| Blood labs | Inflammatory (CRP, ESR, IL-6) | FHIR, CSV | Hospital import |
| Blood labs | Pharmacogenomics panel | FHIR, CSV | Hospital or lab upload |
| Immune | Flow cytometry panel (CBC+diff, CD4) | FCS | NFSIM-FLOW-01 or lab |
| Proteomics | Mass spec protein panel | mzML, CSV | Lab upload |
| Metabolomics | Plasma metabolomics | mzML, CSV | Lab or NFSIM-BREATH-01 |
| Microbiology | Blood culture | FHIR | Hospital import |
| Microbiology | Gut microbiome 16S/WGS | FASTQ | Lab or NFSIM-SEQ-01 |
| Medical records | Diagnoses, procedures, allergies | FHIR R4, HL7 v2, CCR/CCD | Hospital import or PDF OCR |
| Medications | Drug list with doses | FHIR MedicationRequest | Hospital import or manual |
| Family history | Pedigree + variants | PED, JSON | Manual or genetics lab |
| Urine | Dipstick panel | Image, CSV | NFSIM-CHEM-03 or manual |
| Saliva | Hormone panel, cortisol | Image, CSV | NFSIM-CHEM-02 or CHEM-07 |
| Sweat | Electrolytes (single session) | CSV | NFSIM-SWEAT-01 session |
| Breath | Single breath VOC panel | CSV | NFSIM-BREATH-01 session |
| Environmental | Pathogen swab result | FHIR, CSV | Manual or NFSIM-ENV-01 |

### 6.2 Continuous Data Sources (Current)

| Device Type | Measurand | Update Rate | Integration |
|---|---|---|---|
| NFSIM-ECG-01 patch | Single-lead ECG | Continuous 250 Hz | BLE GATT NFS profile |
| NFSIM-ECG-02 vest | 12-lead ECG | Continuous 1000 Hz | BLE GATT NFS profile |
| NFSIM-EEG-01 headset | EEG 8–16 channels | Continuous 250 Hz | BLE GATT NFS profile |
| NFSIM-EMG-01 armband | Surface EMG 8-channel | Continuous 2000 Hz | BLE GATT NFS profile |
| NFSIM-CGM-01 | Interstitial glucose | Every 5 min | NFC + BLE NFS profile |
| NFSIM-SWEAT-01 | Na+, K+, pH, lactate | Every 10–30 min | BLE NFS profile |
| NFSIM-OXY-01 | Tissue rSO2, 4–8 sites | 1 Hz per site | BLE NFS profile |
| NFSIM-EDA-01 | Skin conductance | 4 Hz | BLE NFS profile |
| Dexcom G7 | Glucose (third-party) | Every 5 min | Dexcom OAuth REST API |
| Abbott FreeStyle Libre | Glucose (third-party) | On NFC scan | LibreView OAuth REST API |
| Apple Watch | HR, SpO2, HRV, ECG, activity | Variable | Apple HealthKit API |
| Fitbit, Garmin, Polar | HR, HRV, sleep, GPS | Variable | Brand OAuth REST APIs |
| Oura Ring | Sleep, HRV, temperature | Nightly/hourly | Oura OAuth REST API |
| WHOOP | Recovery, strain, sleep | Daily/hourly | WHOOP OAuth REST API |
| Withings monitors | Blood pressure, weight, sleep | Per measurement | Withings OAuth API |
| Generic BLE heart rate monitor | Heart rate | Continuous | BLE GATT HRS profile |
| Hospital telemetry (remote) | ECG (ICU/telemetry) | Continuous | HL7 FHIR stream (hospital-authorized) |
| Implantable cardiac device (remote) | Rhythm, therapy events | Daily upload | Manufacturer remote monitoring APIs |

### 6.3 Future Continuous Systems (Pre-Built Architecture)

Data model and storage schema are designed today to receive these without schema changes:

| Future System | Measurand | Status |
|---|---|---|
| Continuous liquid biopsy (cfDNA) monitor | Circulating tumor DNA fragments, pathogen DNA | Experimental |
| Continuous proteomics wearable patch | Cytokines, hormones, inflammatory proteins | Research |
| Continuous nanopore flow cell | Pathogen RNA/DNA, cell-free DNA | NFSIM-SEQ-01 moving direction |
| Ingestible continuous multi-modal capsule | GI chemistry, microbiome, images, motility | NFSIM-CAP series |
| Wearable NIRS metabolomics | Real-time tissue metabolite panel | NFSIM-OXY-01 direction |
| Aptamer-based hormone sensor | Cortisol, insulin, estrogen continuous | Research stage |
| Neural implant data stream | Intracortical neural firing patterns | BCI clinical trials |
| Epigenetic methylation monitor | DNA methylation state changes over time | Experimental |
| Microfluidic real-time CBC | Complete blood count with differential continuously | Research stage |
| Sweat-based cfDNA | DNA fragments recovered from sweat | Early research |
| Continuous cortisol implant | Cortisol from interstitial fluid (ISF) | Research stage |
| Smart toilet | Glucose, protein, blood, creatinine from urine | Emerging commercial |
| Continuous breath monitor | 24h VOC profile from wearable nose-clip | Research stage |

### 6.4 Data Pipeline Architecture

```
Input sources:
  [NFS Device] ──BLE/USB/434MHz──→
  [Hospital FHIR] ─────────────→
  [3rd-party Wearable API] ────→   [Ingest Layer]
  [Manual Entry] ──────────────→         │
  [File Upload] ───────────────→         │
  [OCR from document scan] ───→         │
                                          │
                                   [Format Parser]
                                   (FHIR, HL7, VCF, FASTQ,
                                    DICOM, FCS, mzML, CSV, JSON)
                                          │
                                   [UBERON Tagger]
                                   (auto-assign anatomical codes)
                                          │
                                   [Quality Scorer]
                                   (signal quality, completeness,
                                    confidence scoring)
                                          │
                                   [Deduplication Check]
                                   (hash-based record deduplication)
                                          │
                              ┌────────────────────────┐
                              │   Local Storage         │
                              │   SQLite + MinIO        │
                              └────────────────────────┘
                                          │
                          ┌───────────────┼────────────────┐
                          ▼               ▼                 ▼
                   [3D Body Map]  [Simulation Engine]  [AI Insight Layer]
                   (visualization) (Pillar 1 input)   (trend analysis,
                                                        alerts, pattern
                                                        recognition)
                                          │
                              [Optional: Cloud Sync]
                              (patient-controlled, E2E encrypted,
                               self-hosted Docker or authorized provider)
```

---

## 7. Biological Sensing Domain Encyclopedia

This section documents the complete engineering evolution of each biological sensing domain. Every evolutionary insight directly informs the design of NanoFlowSIM portable hardware devices. For each domain: what was the original technology, what were its constraints, what miniaturization path made it portable, and what does the NanoFlowSIM open-source variant achieve.

### 7.1 Domain: Molecular / Genomic Sensing

**What It Measures:** DNA, RNA, proteins, pathogens, mutations, epigenetic marks, microbial genomes, cell-free nucleic acids, CRISPR-detectable targets.

**Why It Matters for NanoFlowSIM:** Genomic data is the highest-information layer of patient biology. SNPs, somatic mutations, and gene expression profiles directly drive nanoparticle targeting parameters, CRISPR payload design, and therapy combination selection.

#### Phase 0 — Pre-Molecular Era (Pre-1950s)

Biology was purely observational. Disease was studied through external symptoms, tissue damage visible at autopsy, and cell morphology under light microscopes. The information layer — DNA sequence, gene expression — was entirely invisible. Medicine classified disease by anatomy and observation only. There was no concept of a genetic sequence being readable.

#### Phase 1 — Gel Electrophoresis (1950s–1970s)

After DNA's double-helix structure was elucidated (Watson and Crick, 1953) and the genetic code was cracked (1960s), researchers needed tools to physically handle and separate DNA. Gel electrophoresis was the first molecular diagnostic tool.

**Core physics:** DNA carries a uniform negative charge-to-mass ratio due to its phosphate backbone. In an applied electric field across a porous gel matrix, DNA fragments migrate from negative to positive electrode. Smaller fragments migrate faster through the gel's pores. Different-length fragments separate into distinct bands.

**Original hardware stack:**
```
Gel casting apparatus:
  - Borosilicate glass or acrylic casting tray (10×14 cm standard, or 20×25 cm)
  - Well-forming comb: 6, 12, or 15-tooth stainless steel
  - Gel clamps: keep glass plates sealed during agarose pouring
  - Leveling base: ensures flat gel

Electrophoresis tank:
  - Acrylic tank, 25×15×10 cm
  - Platinum or carbon electrodes (non-reactive at electrolysis potentials)
  - Buffer volume: 200–500 mL TBE or TAE
  - Lid with electrode connections

Power supply:
  - DC output: 50–200V range
  - Current: up to 500 mA
  - LED voltage indicator
  - Timer circuit

Detection:
  - Ethidium bromide (EtBr) staining: intercalates into DNA,
    fluoresces orange-red under UV (302 nm)
  - UV transilluminator: 302 nm primary UV source
  - UV protective face shield or orange goggles
  - Gel documentation system: CCD camera above transilluminator
  - Polaroid camera (original era) → digital CCD
```

**Signal chain:**
```
DNA sample mixed with loading dye (glycerol for density + bromophenol blue tracking dye)
→ pipetted into gel wells
→ 60–90 min electrophoresis at 80–120V
→ gel removed, stained in EtBr bath (20 min) or pre-stained
→ rinsed in water
→ visualized under 302 nm UV
→ fluorescent bands photographed
→ fragment sizes estimated by comparison to DNA ladder
```

**Constraints:** Slow (45–90 min setup + run), UV radiation hazard, EtBr is mutagenic (biohazard), gel preparation required, not quantitative, no sequence information. Gel-to-gel variability. Operator-dependent interpretation.

**Miniaturization path:**
- Capillary electrophoresis (1980s): glass capillaries replace gel slabs → faster, automated
- Microfluidic chip electrophoresis (Agilent Bioanalyzer, 1999): CE on chip → 1 µL samples, 30 min
- Tape-based electrophoresis (Agilent TapeStation): pre-cast polymer gel strips, fully automated
- Paper microfluidics: lateral flow electrophoresis for ultra-low-cost applications

**NanoFlowSIM derivatives:** NFSIM-GELEC-01 (portable full gel system), NFSIM-PCR-02 (gel-slip strip reader)

#### Phase 2 — PCR Revolution (1983)

Kary Mullis invented Polymerase Chain Reaction in 1983. This is arguably the most important tool invention in molecular biology. PCR enables exponential amplification of a specific DNA target region — starting from as few as 1–10 DNA molecules, 35 cycles theoretically yield 2³⁵ = 34 billion copies of the target, enough for any downstream analysis.

**Core biochemistry and thermal cycling:**

```
Reaction components:
  - Template DNA (sample — as little as 1 molecule)
  - Forward and reverse primers (short ~20 bp oligonucleotides defining the region)
  - Taq DNA polymerase (or Pfu, Phusion, Q5 for high fidelity)
  - dNTPs (deoxynucleotide triphosphates: dATP, dCTP, dGTP, dTTP)
  - MgCl₂ (cofactor for polymerase)
  - Buffer solution (pH 8.0–9.0)

Three-stage thermal cycle per PCR cycle:
  Stage 1: Denaturation — 94–98°C for 20–30 seconds
    DNA hydrogen bonds break → double-stranded separates to single-stranded
  Stage 2: Annealing — 50–65°C for 20–40 seconds (Tm of primers minus 5°C)
    Custom oligonucleotide primers bind to their complementary sequences
    Primer melting temperature (Tm) = 2°C × (A+T) + 4°C × (G+C) per primer
  Stage 3: Extension — 72°C for 30s–2 min (1 min per 1 kb product)
    DNA polymerase extends from primer 5'→3', synthesizing new strand
    → doubling of target sequence per cycle
```

**Original PCR hardware stack:**
```
Thermal block:
  - Aluminum 6061 block with drilled wells: 96×0.2 mL, 384-well, or 48×0.5 mL
  - Tight tolerance machining: well-to-well temp uniformity ±0.5°C at 95°C
  - Block thickness: 20–25 mm (thermal mass creates inertia)

Heating elements:
  - Resistive heating: nichrome wire coils embedded below block
  - Power: 300–800W for 96-well blocks
  - Ramp rate achievable: 2–5°C/s (limited by block thermal mass)

Cooling system:
  - Peltier thermoelectric coolers (TECs): 40×40 mm, 6–12A each
  - Heat sink: aluminum extrusion with forced-air fan
  - Liquid cooling option: chilled water circulation for larger instruments
  - Cooling ramp rate: 1–3°C/s

Temperature sensors:
  - Thermistor or RTD (PT1000) embedded in block center and edge
  - Accuracy: ±0.1°C
  - Uniformity mapping required at QC

Heated lid:
  - Resistive heater in lid block, setpoint 103–110°C
  - Prevents condensation on tube caps during denaturation stage
  - Spring-loaded pressure pad: compresses uniformly on tube caps

Controller:
  - Microcontroller (early: 8051 or Z80; modern: ARM Cortex-M4)
  - PID control loop (Kp, Ki, Kd tuned per block geometry)
  - Protocol storage: EEPROM or flash (up to 200 stored programs)
  - LCD display + keypad
  - RS-232 or USB-B connectivity to PC software

Power electronics:
  - MOSFET H-bridge for Peltier (bidirectional: heating/cooling)
  - Gate drivers: bootstrap for high-side
  - Current limiting resistors or soft-start
  - SMPS (Switched Mode Power Supply): 12V and 5V rails from AC mains
```

**Why early PCR machines were large (300mm × 250mm × 300mm, 5–15 kg):**
- High thermal mass aluminum block required powerful heaters (300–800W)
- 96-well capacity required large block area
- Peltier modules + heat sinks added bulk and weight
- Mains-powered only (200–800W peak — no battery option)
- Separate LCD control panel + PCB + power supply housing

**Evolution to portable PCR:**

| Generation | Example | Size | Power | Key Technology |
|---|---|---|---|---|
| Lab thermocycler (1990s) | Perkin-Elmer 9600 | Large desktop | 300–500W | Resistive + Peltier |
| Compact thermocycler (2000s) | Bio-Rad iCycler | 2–5 kg desktop | 150–250W | Better TEC efficiency |
| OpenPCR (2012) | Chai OpenPCR | 1.5 kg desktop | ~50W | Arduino, open-source |
| Portable PCR (2015+) | miniPCR | 0.5 kg | 20–40W | USB-C, simplified |
| Handheld field PCR (2020+) | USTAR Rapid PCR | <300g | 5–15W | Thin-film heaters, MEMS |
| Personal capsule PCR (future) | NFSIM-PCR-01 | ~280g | 5–12W | Single-strip, battery |

**qPCR (Quantitative PCR) — additions to standard PCR:**

Standard PCR tells you "is target present or absent." qPCR adds real-time fluorescence detection to quantify DNA amount during amplification. The cycle number at which fluorescence crosses a threshold (Ct value) correlates with starting DNA quantity.

```
Additional hardware required for qPCR:
  Excitation sources:
    - LED array (blue 470nm, green 520nm) — modern portable systems
    - Halogen lamp + monochromator — older full systems
    - Solid-state laser — high-end instruments
  
  Fluorophores detected (multiplex possible):
    - FAM (FITC): excitation 488nm, emission 520nm (most common)
    - HEX / VIC: excitation 535nm, emission 556nm
    - ROX: excitation 575nm, emission 602nm (passive reference)
    - Cy5: excitation 650nm, emission 670nm
    - SYBR Green (intercalating dye): excitation 497nm, emission 520nm

  Detection hardware:
    - Photodiodes (one per fluorescence channel per well, or shared optical path)
    - Scientific CMOS or CCD camera (imaging-based systems scan all wells at once)
    - Optical bandpass filters (one per fluorescence channel)
    - Lock-in detection (LED chopped at 1 kHz; synchronous demodulation improves SNR)
  
  Signal processing:
    - Baseline correction (subtract early cycles)
    - Threshold determination (user-set or auto)
    - Ct value calculation (cycle at threshold crossing)
    - Standard curve interpolation → copy number
```

**Digital PCR (dPCR) — absolute quantification:**

```
Principle:
  Sample diluted and partitioned into thousands of individual compartments
  (droplets: Bio-Rad Droplet Digital PCR) or wells (Thermo Fisher QuantStudio 3D)
  Each compartment contains 0 or 1 DNA template molecules on average (Poisson distribution)
  After PCR amplification: each compartment is either positive (fluorescent) or negative
  Count positive compartments → Poisson statistics → absolute molecule concentration

Hardware additions:
  Droplet generator: T-junction microfluidic chip, oil + aqueous phase
  Droplet reader: flow-through laser + 2-color photomultiplier detection
  Droplet counter: high-speed event capture (10,000–2,000,000 droplets per run)

Key advantage: no standard curve needed, absolute quantification
Key applications: liquid biopsy (ctDNA detection at 0.01% VAF), rare allele detection,
                 copy number variation, viral load in transplant monitoring

NanoFlowSIM derivative: NFSIM-dPCR-01
```

**LAMP (Loop-Mediated Isothermal Amplification):**

```
Principle: 4–6 primers designed to form stem-loop structures on target
  Amplification at constant 65°C (no thermal cycling required)
  Bst DNA polymerase (strand-displacing, no need for denaturation)
  Time to result: 15–30 minutes
  Visual readout: turbidity (LAMP produces magnesium pyrophosphate precipitate)
                  colorimetric pH indicator dye (pink → yellow when positive)
                  fluorescent intercalating dye (SYTO-9, calcein)

Key advantages over PCR:
  - Isothermal: no thermocycler needed (simple heater at 65°C)
  - Faster: 15–30 min vs 60–90 min for PCR
  - High sensitivity: similar to PCR
  - Simpler equipment requirements

Key disadvantages:
  - Complex primer design (4–6 primers per target vs 2 for PCR)
  - Higher risk of false positives from carryover contamination
  - Limited multiplexing capacity vs qPCR

NanoFlowSIM derivative: NFSIM-PCR-03
```

**RPA (Recombinase Polymerase Amplification):**

```
Principle: recombinase proteins facilitate primer binding at room temperature
  Works at 25–42°C (even body temperature in some versions)
  Results in 10–20 minutes at 37°C
  No denaturation step needed — recombinase opens dsDNA helix for primer access

Key advantages:
  - Room temperature or body-temperature operation
  - Fastest isothermal method
  - Simplest thermal requirements (just maintain 37°C)
  - Compatible with lateral flow strip readout (no optics needed)

NanoFlowSIM derivative: NFSIM-PCR-04
```

**CRISPR Diagnostics (SHERLOCK, DETECTR):**

```
SHERLOCK (Specific High-sensitivity Enzymatic Reporter UnLOCKing):
  Uses CRISPR-Cas13a, which has collateral RNA cleavage activity
  1. Sample pre-amplified (RPA or LAMP)
  2. Target RNA binds Cas13a + crRNA complex → activates Cas13a
  3. Activated Cas13a cleaves nearby reporter RNA molecules non-specifically
  4. Reporter: FAM-RNA-Quencher → cleavage separates fluorophore from quencher
  5. Fluorescence measurement → target detected

DETECTR (DNA Endonuclease-Targeted CRISPR Trans Reporter):
  Uses CRISPR-Cas12a instead
  Same collateral cleavage principle but for DNA targets
  Lateral flow: biotin-labeled reporter → captured at streptavidin line when intact
  Target present → reporter cleaved → no line at test (vice versa from conventional)

Sensitivity: attomolar (10⁻¹⁸ M) with pre-amplification
Specificity: single-base-pair discrimination possible (mismatch = no Cas activation)
Heat required: 37°C (near room temperature)
Equipment needed: heater + fluorometer OR heater + lateral flow strips (no optics)

NanoFlowSIM derivative: NFSIM-CRISPR-01 (fluorescence), NFSIM-CRISPR-02 (lateral flow only)
```

#### Phase 3 — Sanger Sequencing (1977)

**Core principle:** Chain-terminating dideoxynucleotides (ddNTPs) randomly terminate DNA synthesis. Fragments of all possible lengths are generated, each terminated at a specific base. Fragment sizes reveal sequence position; fluorescent labeling reveals base identity.

**Hardware stack:**
```
Sample preparation:
  - Cycle sequencing reaction (PCR-like but with ddNTPs)
  - 96-well thermocycler (same as PCR)
  - Precipitation cleanup: ethanol or SPRI beads

Capillary electrophoresis instrument:
  - Capillary array: 48–96 fused silica capillaries, 50–80 cm × 50 µm ID
  - Polymer fill: POP-6 or POP-7 (linear polyacrylamide)
  - Loading robot: electrokinetic injection of denatured samples
  - High-voltage power supply: 10–15 kV DC (safe design, safety interlock)
  - Thermostat oven: maintains 60°C for DNA denaturation during separation

Detection optics:
  - Argon ion laser: 488 nm, 25 mW
  - Prism or holographic diffraction grating
  - CCD detector array (one detector samples all capillaries through optical path)
  - Fluorescent dye-terminators: Big Dye Terminator v3.1
    ddATP-ROX (red), ddCTP-FAM (green), ddGTP-TAMRA (yellow), ddTTP-JOE (blue)
  - Four-color discrimination by spectral separation onto CCD

Read length: 600–1000 bp per capillary per run
Throughput: 96 samples per 3–6 hour run
Accuracy: >99.99% (Phred Q40+)
Cost: ~$4–10 per sample (reagents)
Machine cost: $80,000–$200,000

Constraints: requires elaborate optical path, capillary polymer consumables,
             expert operation, controlled environment, low throughput for WGS
```

#### Phase 4 — Next Generation Sequencing (NGS) (2005–present)

**Illumina (Sequencing by Synthesis) — core principle:**

```
1. Library preparation: DNA fragmented to ~300–500 bp, adapters ligated to ends
2. Cluster generation: bridge amplification on flow cell surface
   → each template → cluster of ~1000 identical copies (signal amplification)
3. Sequencing by synthesis:
   - One cycle: all 4 fluorescently labeled, 3'-blocked dNTPs flowed simultaneously
   - Each cluster incorporates exactly one dNTP (complementary to template)
   - Flow cell imaged: each cluster emits color indicating base
   - Chemical reversal of block + dye removal
   - Repeat for next cycle
4. Base calling: image intensity matrix → nucleotide per cycle per cluster

Read length: 75–300 bp per end (paired-end)
Throughput: 20 Gb (MiniSeq) to 6 Tb (NovaSeq X) per run
Accuracy: >99.9% (Q30) per base
Cost: ~$0.001 per base (genome scale), ~$1,000 per whole human genome (NovaSeq)
```

**Illumina hardware stack:**
```
Flow cell:
  - Glass or silicon substrate with nanowell or patterned array
  - Oligonucleotide P5/P7 capture sequences covalently bonded to surface
  - Patterned flow cells (NovaSeq): 25 nm nanowells at predetermined positions
  - 1–16 lanes (depending on instrument model)

Fluidics system:
  - 16–32 reagent positions
  - Precision peristaltic pumps (0.1 µL accuracy)
  - Multi-port valve manifold: routes reagents to specific lanes
  - Temperature-controlled reagent cart

Optical system:
  - 2 or 4 lasers: 532 nm (green), 638 nm (red), 488 nm (blue), 785 nm (near-IR)
  - TIR (Total Internal Reflection) or epifluorescence illumination
  - 2–4 scientific CMOS cameras: 100+ megapixels each
  - Objective lens: 0.75 NA, 20× magnification
  - Filter wheels: emission bandpass per laser + channel

Motion system:
  - XY stage: motorized, sub-micrometer positioning
  - Z-focus: autofocus piezo
  - Vibration isolation: pneumatic optical table

Compute:
  - Real-time image processing cluster (dedicated servers)
  - Base calling: real-time during run
  - Output: BCL files → FASTQ conversion
  - Storage: 100 TB+ per instrument lifecycle

Why these machines are large (refrigerator to room-sized):
  Precision optics require vibration isolation
  Multiple lasers require heat management
  Fluidics require robotic automation
  Real-time imaging generates terabyte data streams
  Controlled environment (temperature, humidity) for reagent stability
```

#### Phase 5 — Third Generation: Oxford Nanopore (2015–present)

**Revolutionary change:** Completely removes the optical detection stack.

**Core physics:**
```
Nanopore sensing mechanism:
  1. Artificial lipid bilayer membrane separates two chambers (cis and trans)
  2. Voltage applied across membrane: +120–180 mV
  3. Ionic current flows through membrane via protein nanopore channels
  4. Open-pore current: ~100–300 pA (baseline)
  5. DNA in cis chamber: motor protein (helicase) binds and ratchets DNA
     through nanopore at controlled speed ~400 bases/second
  6. As each DNA sequence transits the pore:
     different k-mers (groups of ~5 consecutive bases) occlude the pore differently
     → measurable current modulations: each k-mer has characteristic blockade signature
  7. Current changes: ~10–20 pA amplitude, distinguishable by ML basecaller

Protein nanopore options:
  - MspA (Mycobacterium smegmatis porin A): narrow constriction, excellent resolution
  - CsgG: latest Oxford Nanopore pore, R10.4.1 variant — best current accuracy
  - α-hemolysin (original research pore): wider, lower resolution

Motor proteins:
  - Phi29 DNA polymerase: processively reads dsDNA, controls speed
  - Helicase enzymes (Hel308 and variants): Oxford Nanopore's current commercial choice
  - Speed: ~400 bases/sec (R9/R10 pores)
```

**MinION hardware stack:**
```
Flow cell (consumable, $500–900):
  - 512 independently addressable nanopore wells in 128 groups of 4
  - R10.4.1 pore: CsgG octamer variant with dual reader head for improved accuracy
  - Lipid bilayer: synthetic lipid mixture (DPhPC or equivalent) in each well
  - Motor enzyme pre-loaded on flow cell (helicase)
  - Electrode: Ag/AgCl per well
  - Temperature control: flow cell maintained at 34–38°C
  - Lifetime: 72 hours once opened, or until ~95% of pores consumed

MinION reader (reusable, $1,000):
  - ASIC (Oxford Nanopore custom): 512 parallel analog amplifier channels
  - Each channel: low-noise transimpedance amplifier (TIA), gain = 500 MΩ
  - ADC: 12-bit, 25 kHz per channel (512 channels simultaneously)
  - FPGA (integrated in MK1C): multiplexes 512 channel data
  - USB 3.0 controller: streams data to laptop at ~300 MB/s raw rate
  - USB-C power: 5V, 0.5–1A peak
  - Dimensions: 105 × 33 × 23 mm — fits in palm
  - Weight: 87 g
  - Temperature sensor: monitors flow cell
  - LED: run status indicator

Signal chain:
  DNA in library prep buffer
  → Motor enzyme (helicase) threads DNA through nanopore channel
  → Ionic current modulation: each k-mer context = unique blockade signature
  → Analog TIA (500 MΩ feedback) → voltage signal (50 mV range)
  → Anti-aliasing filter: Bessel 4-pole, 10 kHz
  → 12-bit ADC: digitized at 25 kHz per channel
  → Raw squiggle data streamed via USB
  → Dorado neural network basecaller (LSTM/transformer architecture, GPU):
      Input: raw current trace segments
      Output: FASTQ sequence with per-base quality scores
  → Alignment: minimap2 pairwise alignment to reference genome
  → Variant calling: medaka, PEPPER-DeepVariant, Clair3

Read length capability:
  - Standard: N50 = 20–50 kb
  - Ultra-long: >1 Mb reads demonstrated (specialized extraction protocol)
  - Limited only by DNA integrity in extraction

Accuracy:
  - Q20 per read (raw): ~99% with R10.4.1 + Dorado v4+
  - Duplex mode: two complementary reads → Q30+ consensus accuracy
  - Matches Illumina accuracy for most variant types with sufficient coverage

Applications unlocked by portability:
  - Field sequencing: Amazon jungle outbreak response (2016 Zika)
  - Arctic field work: permafrost environmental DNA
  - Antarctic stations: penguin population genetics
  - International Space Station: first DNA sequencing in space (2016)
  - Field hospital: SARS-CoV-2 whole genome sequencing during pandemic

What MinION does NOT fully open-source:
  - Pore protein engineering (CsgG variant sequences and modifications): proprietary, patented
  - ASIC design: proprietary
  - Motor enzyme selection and coupling chemistry: trade secret
  - Dorado basecaller weights: partially available; training code open, weights restricted
  - Flow cell manufacturing process: proprietary (bilayer deposition at scale)

NanoFlowSIM strategy:
  NFSIM-SEQ-01: open biological pore (α-hemolysin or MspA) + open FPGA acquisition
  NFSIM-SEQ-02: solid-state nanopore (fabricated SiN) + open amplifier board
  Open basecaller: Bonito (Oxford Nanopore's own open-source training code) +
                   community models trained on published squiggle data
```

#### Phase 6 — CRISPR Diagnostics Era (2016–present) — see Phase 2 subsection above

#### Phase 7 — Future: Continuous Molecular Monitoring (Emerging)

```
Target direction:
  The ultimate goal is continuous molecular monitoring —
  analogous to what CGM is to glucose, but for nucleic acids and proteins

Technologies under development:
  Continuous nanopore: microfluidic blood sampling + continuous nanopore sequencing
    → real-time pathogen DNA/RNA in blood, cfDNA monitoring
  Aptamer electrochemical sensors: synthetic oligonucleotides that bind targets
    → conformational change → measurable current change → continuous protein monitoring
  Nanotube sensors: SWCNT functionalized with aptamers → optical signal change
  CRISPR chemical sensing: programmable molecular detection, enzymatic signal
  Programmable DNA nanostructures: molecular switches that report specific sequences

Timeline: 5–15 years to clinical deployment at scale
NanoFlowSIM architecture: pre-built to receive these data types without schema changes
```

### 7.2 Domain: Structural / Anatomical Imaging

**What It Measures:** Physical anatomy — tissue density, organ geometry, vascular structure, lesion morphology, bone integrity, internal motion, soft tissue characterization, metabolic activity distribution.

**Why It Matters for NanoFlowSIM:** DICOM imaging data defines the physical geometry of the patient — tumor location, size, vascular supply, tissue properties. This directly parameterizes the tissue-layer simulation model and drives the 3D body map Level 2 patient-specific mesh.

#### Phase 0 — Pre-Imaging Medicine (Pre-1895)

Internal anatomy visible only through surgery or autopsy. Physical examination methods: palpation (feeling lumps), percussion (listening to density), auscultation (stethoscope for heart/lung sounds). Interior of the living body was entirely inaccessible to inspection without cutting it open.

#### Phase 1 — X-Ray (1895)

Wilhelm Conrad Röntgen discovered X-rays on November 8, 1895. Within weeks, the first clinical radiographs were taken. Within months, hospitals worldwide were using X-ray systems. This is arguably the first major leap in internal medicine's history.

**Core physics:**
```
X-ray generation (Bremsstrahlung):
  - Electrons accelerated through 40–150 kV high-voltage field
  - Strike tungsten anode target
  - Rapid deceleration → emission of X-ray photons (broad spectrum)
  - Characteristic X-ray peaks from tungsten electron shell transitions

Tissue attenuation by density and atomic number:
  Air/gas:      minimal attenuation → appears BLACK on image
  Fat:          low attenuation → dark grey
  Soft tissue:  moderate attenuation → grey
  Bone:         high attenuation (calcium, phosphorus) → light grey/white
  Metal/contrast: very high attenuation → bright white

Beer-Lambert law of attenuation:
  I = I₀ × e^(−µt)
  Where: µ = linear attenuation coefficient (material + energy dependent)
         t = material thickness
```

**Original hardware stack:**
```
X-ray tube:
  - Glass or metal envelope vacuum tube (<10⁻⁷ torr)
  - Cathode filament: tungsten wire, heated to thermionic emission (~2200°C)
  - Focusing cup: shapes electron beam
  - Rotating tungsten-rhenium anode: 90–200mm disk, 3000–10000 RPM
    (rotating distributes heat across larger focal track area)
  - Focal spot size: 0.6 mm (fine) to 1.2 mm (broad)
  - Heat dissipation: anode thermal capacity 100–500 kJ, cooling by radiation/oil

High voltage generator:
  - Transformer: 40–150 kVp (kilovolt peak)
  - Current: 100–1000 mA
  - Full-wave rectification → DC output
  - Ripple: <1% for constant potential generators

Beam collimator:
  - Lead shutters defining rectangular field size
  - Light field mirror and lamp (light field = X-ray field indicator)
  - Added filtration: aluminum (removes low-energy X-rays that only add dose)

Detector (modern):
  - Flat-panel detector (FPD): amorphous silicon TFT array
  - Scintillator: CsI (thallium-doped), structured columnar crystal
  - Size: 35×43 cm (DR, digital radiography)
  - Pixel pitch: 139–200 µm
  - Bit depth: 14-bit grayscale (16,384 gray levels)
  - DQE: 60–70% (detective quantum efficiency at 70 kVp)
  - Read time: <5 seconds per image

Anti-scatter grid:
  - Lead strips aligned with X-ray beam direction
  - Grid ratio: 8:1 to 12:1
  - Removes scattered X-rays that degrade contrast

Output: DICOM DR SOP class digital image, 14-bit
```

**Portable X-ray (modern):**
```
Generator: 4.5 kg battery-powered unit, 40–90 kVp, up to 100 mA
Detector: wireless flat-panel, 802.11ac transmission
Battery: 300+ exposures per charge
Use cases: field medicine, veterinary, ICU bedside, dental portable
NanoFlowSIM derivative: NFSIM-XRAY-01
```

#### Phase 2 — Fluoroscopy (Real-Time X-Ray)

```
Principle: Continuous X-ray beam → real-time motion visualization
  Used for: catheter guidance, barium swallow, joint injection guidance,
            cardiac catheterization, orthopedic surgery guidance

Modern flat-panel fluoroscopy:
  - Pulsed X-ray (reduces dose vs continuous)
  - Frame rate: 7.5 to 30 frames/second
  - Digital fluoroscopy: each frame processed, stored as video
  - Dose rate: 1–10 mGy/min (much higher than static radiography)
  - Safety: automatic dose rate control, low-dose save modes
```

#### Phase 3 — Computed Tomography (CT) (1972)

**Core physics:** Same X-ray attenuation, acquired from hundreds of angles around the patient. Filtered back projection or iterative reconstruction algorithms compute a 3D volumetric density map from the multiple projections.

```
Hounsfield units (HU) — tissue density scale:
  Air: −1000 HU
  Fat: −50 to −100 HU
  Water: 0 HU
  Soft tissue: 30–60 HU
  Bone: 300–1000 HU
  Metal: >1000 HU (artifact)
```

**Gantry hardware:**
```
Rotating assembly (400–700 kg, rotation in 0.25–0.5 sec):
  - Slip rings: allow continuous rotation while passing kW of power + Gbps of data
  - X-ray tube: rotating anode, 60–140 kVp, 50–800 mA
  - Bowtie filter: compensates for patient shape (attenuates periphery more)
  - Detector array: 64–320 rows, GOS scintillator + photodiode, 800–1000 elements/row

Data acquisition:
  - 800–1000 detector channels × 320 rows × 1000 views/rotation
  - ADC: 20-bit per channel
  - DAS (Data Acquisition System): raw data rate ~10 Gb/s
  - Slip ring data transfer: fiber optic, wireless, or capacitive

Reconstruction:
  - FBP (Filtered Back Projection): classic, fast, some noise amplification
  - MBIR (Model-Based Iterative Reconstruction): higher dose reduction
  - AI reconstruction: deep-learning denoising (GE TrueFidelity, Siemens ClearIQ)
  - Output: 512×512 pixels per slice, 0.5–1.25 mm slice thickness, 14-bit

Patient table:
  - Motorized, isocentered ±250 mm
  - Speed: up to 100 mm/second (helical CT)
  - Weight capacity: 300 kg

Why CT machines are room-sized (2000–5000 kg):
  Gantry structure: holds 400–700 kg rotating assembly
  Radiation shielding: lead-lined walls of scan room
  High-voltage generation: 120 kVp at 800 mA = 96 kW peak
  Cooling systems: X-ray tube generates enormous heat
  Data infrastructure: real-time Gb/s data → reconstruction servers
```

**Portable CT (emerging):**
```
Mobile trauma CT: mounted on wheeled platform, push to bedside
Low-power portable head CT: NeuroLogica CereTom (8-slice, 240 kg)
AI-assisted portable: reduced kVp + AI reconstruction compensates for lower quality
NanoFlowSIM derivative: NFSIM-XRAY-01 (X-ray panel, precursor technology)
```

#### Phase 4 — MRI (1973–present)

**Core physics — nuclear magnetic resonance:**
```
Larmor precession:
  Hydrogen protons (¹H) have spin → magnetic dipole moment
  External field B₀ aligns spins (parallel: low energy, antiparallel: high energy)
  Net longitudinal magnetization M₀ along B₀

  Precession frequency (Larmor frequency):
  f₀ = γ × B₀
  γ (gyromagnetic ratio of ¹H) = 42.577 MHz/T
  At 1.5T: f₀ = 63.9 MHz
  At 3.0T: f₀ = 127.7 MHz
  At 0.064T (NFSIM-MRI-01): f₀ = 2.73 MHz

Excitation and relaxation:
  1. RF pulse at Larmor frequency: tips M₀ from z-axis into xy-plane (90° flip angle)
  2. Transverse magnetization M_xy precesses → induces EMF in receive coil (FID signal)
  3. T1 relaxation: M_z recovers (spin-lattice, tissue-specific: fat 250ms, CSF 4000ms at 1.5T)
  4. T2 relaxation: M_xy decays (spin-spin, tissue-specific: fat 60ms, CSF 1000ms at 1.5T)
  5. Gradient coils: spatially encode position by creating z, phase, frequency gradients
  6. k-space filling: RF pulses + gradient waveforms fill k-space matrix
  7. 2D/3D Fourier transform: k-space → image

Contrast mechanisms:
  T1-weighted: short TR, short TE → bright fat, dark CSF
  T2-weighted: long TR, long TE → bright CSF, bright edema
  FLAIR: T2 with CSF suppression (inversion recovery)
  DWI: diffusion-weighted → detects cell swelling (stroke, tumors)
  fMRI (BOLD): blood oxygenation changes → indirect neural activity
  Gadolinium contrast: shortens T1 → bright enhancement of vascular structures
```

**Full clinical MRI hardware stack:**
```
Superconducting magnet:
  - Wire: NbTi (niobium-titanium) multifilament superconductor
  - Operating temperature: 4.2 K (liquid helium)
  - Field strength: 1.5T (clinical standard), 3T (high-field), 7T (research)
  - Homogeneity: <1 ppm variation over 50 cm DSV (after shimming)
  - Fringe field: extends meters outside bore — controlled by active shielding
  - Weight: 4,000–10,000 kg (magnet alone)
  - Cryostat: double vacuum jacket, liquid helium fill volume 700–1500 L
  - Helium boil-off rate: <0.1 L/h (modern ZBO — zero boil-off — systems)

Gradient coils:
  - Three orthogonal sets: Gz (Maxwell coils), Gx and Gy (Golay coils)
  - Maximum gradient strength: 45–80 mT/m
  - Maximum slew rate: 150–200 T/m/s
  - Acoustic noise: 100–130 dB SPL from Lorentz forces (ear protection required)
  - Actively shielded: reduces eddy currents in magnet structure
  - Gradient amplifiers: 1000+ A, bipolar (ADC-style linear or Class-D)
  - Power: 200–400 kW peak per axis

RF transmit/receive system:
  - Body coil: birdcage resonator, built into bore liner, transmit + reference receive
  - Surface coil arrays: 8–64 receive elements (head, spine, cardiac, body, knee)
  - RF amplifiers: 15–30 kW at Larmor frequency
  - Duplexer: T/R switch for transmit-receive isolation
  - Digital receive: direct sampling at 100+ MHz (modern), quadrature detection
  - Preamplifiers: low-noise, in-bore mounting, JFET or GaAs

Shimming:
  - Passive shim: iron pieces in shim tray (placed iteratively via field map)
  - Active shim: additional resistive coils (2nd and 3rd order spherical harmonics)
  - Room-temperature shims: require separate amplifiers

Reconstruction computer:
  - k-space reconstruction: GPU-accelerated FFT (cuFFT)
  - Parallel imaging: GRAPPA, SENSE (undersampled k-space acceleration)
  - AI reconstruction: U-Net architecture (FastMRI challenge winners)
  - DICOM output: MR SOP class

Why MRI rooms are special (shielded rooms, 20–100 tonnes):
  5-Gauss line (500 µT): defined safety perimeter for pacemakers
  RF shielding room: prevents external RF interference from corrupting signals
  Faraday cage: 100+ dB RF isolation at Larmor frequency
  Structural: floor loads up to 50 tonnes (magnet weight)
  Liquid helium quench pipe: vents helium safely if magnet quenches
```

**Low-Field Portable MRI (NFSIM-MRI-01 technology basis):**
```
Key realization: removing the superconducting magnet removes 90% of the cost and complexity
At 64 mT (permanent magnet):
  - Larmor frequency: 2.7 MHz (not 64 MHz like clinical 1.5T)
  - SNR ∝ B₀^(7/4) → drastically lower SNR vs clinical
  - AI reconstruction: compensates for low SNR → clinical-quality resolution possible
  - No cryogenics: permanent NdFeB magnets, room temperature
  - No RF shielded room: 2.7 MHz RF doesn't need clinical-grade shielding
  - Power: 1.5 kW vs 1,000+ kW for clinical (cooling alone)
  - Weight: 30–80 kg vs 5,000+ kg
  - Cost: $20,000–$50,000 vs $1,500,000–$3,000,000

Halbach array magnet geometry:
  Halbach cylinder: arrangement of permanent magnets that concentrates field inside,
  cancels field outside
  → self-shielded → reduces external fringe field
  → no need for heavy iron yoke
  → lighter construction possible

Open-source MRI console (MaRCoS):
  Runs on Red Pitaya FPGA platform
  GitHub: vnegnev/marcos_server + marcos_client
  Generates RF pulses, gradient waveforms, acquisition timing
  NanoFlowSIM NFSIM-MRI-01 builds on this foundation
```

#### Phase 5 — Ultrasound (1940s–present)

```
Core physics:
  Piezoelectric crystal generates pressure waves when AC voltage applied
  Frequency: 1–40 MHz (clinical range)
  Speed of sound in tissue: ~1540 m/s
  Axial resolution: λ/2 = c/(2f)
    At 7 MHz: λ = 1540/7,000,000 = 220 µm → resolution ~110 µm axial
    At 15 MHz: resolution ~50 µm axial
  Depth: attenuated ~0.5 dB/cm/MHz
    At 7 MHz: useful depth to ~15 cm
    At 15 MHz: useful depth to ~5 cm

Tissue interface reflection (acoustic impedance mismatch):
  Reflection coefficient R = ((Z₂-Z₁)/(Z₂+Z₁))²
  High impedance difference → strong echo (bone: strong; fat-muscle: moderate; gas: near total)

Transducer types:
  Linear array (5–15 MHz): shallow imaging, flat footprint (vascular, MSK, small parts)
  Curved/convex array (2–5 MHz): abdominal imaging, wider field of view
  Phased array (1–5 MHz): small footprint, electronic beam steering (cardiac)
  Endocavitary (5–10 MHz): transvaginal, transrectal (gynecology, urology)
  IVUS (20–40 MHz): intravascular ultrasound (coronary arteries)
  CMUT arrays: capacitive micromachined — silicon-based, allows batch fabrication
```

**Traditional ultrasound hardware stack (hospital console):**
```
Transducer:
  - PZT-5H piezoelectric elements (128–512 elements per array)
  - Backing material: tungsten-epoxy (high acoustic absorption)
  - Matching layers: quarter-wave impedance matching to tissue
  - Acoustic lens: silicone lens (fixed elevation focus)
  - Ground shield: copper foil

TX beamformer:
  - Delay-and-sum: nanosecond timing per element for beam steering and focusing
  - HV pulsers: ±50–100V per element (STHV800 or HV748 ICs)
  - Frequency: center frequency ± 50% bandwidth

RX signal chain:
  - T/R switch: isolates receiver from high-voltage TX pulse
  - Low-noise amplifier (LNA): ~20 dB gain, <5 dB noise figure
  - Time Gain Compensation (TGC): programmable amplifier, 0–80 dB over depth
  - ADC: 12–14 bit, 40–100 MSPS per channel
  - Beamformer ASIC or FPGA: delay-and-sum per receive aperture
  - Envelope detection, log compression, scan conversion
  - Display: real-time B-mode at 30–60 fps

Doppler modes:
  PW Doppler: pulsed Doppler, depth-gated velocity spectrum (FFT-based)
  CW Doppler: continuous wave, all velocities along beam (high velocity)
  Color Doppler: autocorrelation algorithm, velocity map overlaid on B-mode
  Power Doppler: amplitude (not velocity), more sensitive for low flow

Why handheld ultrasound became possible:
  - Digital beamforming on ASIC: replaces analog beamformer hardware
  - CMUT transducers: semiconductor-fabricated, integrates with ASIC
  - Smartphone computing: GPU handles scan conversion and display
  - USB-C power: 5V 3A sufficient for modern digital beamformer
  - Miniaturized HV pulsers: SOT-23 package, 50V in 1mm² silicon

Commercial handheld examples:
  Butterfly IQ (2017): first CMUT + ASIC whole-body probe, smartphone-connected
  Clarius HD3 (WiFi-connected): 3 transducer options, tablet display
  Philips Lumify (USB): compact, dedicated elements, clinical quality

NanoFlowSIM derivatives: NFSIM-US-01 through US-09
```

#### Phase 6 — Optical Structural Imaging

```
OCT (Optical Coherence Tomography):
  Principle: Michelson interferometer with broadband near-IR source
  Axial resolution: 1–15 µm (100× better than clinical ultrasound)
  Penetration: 1–3 mm (shallow, optically scattering tissue)
  Dominant applications: retinal imaging, coronary OCT, skin imaging

  SD-OCT (Spectral Domain): spectrometer-based (most common modern type)
  A-scan rate: 20–100 kHz (entire depth profile per shot)
  B-scan rate: 20–60 fps
  Hardware: SLD light source + fiber coupler + galvo scanner + spectrometer

  SS-OCT (Swept Source): rapidly tuned laser sweeps wavelength
  Advantages: faster A-scan rate (400 kHz+), better depth range
  Hardware: swept-source laser (MEMS or Fourier-domain mode-locked)

Endoscopy:
  Direct optical visualization of luminal structures (GI tract, bronchi, bladder)
  White-light, NBI (Narrow Band Imaging), fluorescence, AI-augmented endoscopy
  Capsule endoscopy (PillCam): camera in pill, GI transit visualization

NanoFlowSIM derivatives: NFSIM-OCT-01, NFSIM-MICRO-01
```

### 7.3 Domain: Chemical / Metabolic Sensing

**What It Measures:** Dissolved chemistry — ions, metabolites, dissolved gases, hormones, enzymes, neurotransmitters, drugs — the real-time biochemical state of the body.

**Why It Matters for NanoFlowSIM:** Metabolic state modulates nanoparticle behavior directly. pH affects payload release. Protein corona composition depends on blood protein concentrations. Glucose level affects cancer cell metabolism modeling. Continuous chemistry is the most actionable real-time data layer for adaptive therapy.

#### Phase 0 — Pre-Electronic Chemistry (1800s)

Visual and manual methods only. Fehling's test (1848) for glucose: blue copper sulfate solution → brick-red precipitate in glucose presence. Litmus paper for acid/base. Benedict's test. All qualitative, slow, batch-only.

#### Phase 1 — Electrochemical Biosensors (1950s)

**Three core electrochemical modalities:**

```
1. Potentiometry (equilibrium voltage measurement):
   Measures ion concentration via Nernst equation:
   E = E₀ + (RT/nF) × ln([ion])
   At 37°C: RT/F = 26.7 mV → ~59 mV per decade for monovalent ions

   Ion-selective electrodes:
   pH (H⁺): glass membrane (silicon dioxide selective for H⁺)
   Na⁺: glass membrane doped with sodium-binding oxides
   K⁺: valinomycin ionophore (cyclic peptide, K⁺ selective)
   Cl⁻: silver chloride membrane
   Ca²⁺: calcium ionophore (ETH 1001 or Fluka 21192)

   Hardware:
   - Reference electrode: Ag/AgCl in saturated KCl (stable reference potential)
   - High-impedance electrometer: input impedance >10¹² Ω (glass electrode has GΩ source)
   - Differential amplifier: minimizes noise
   - ADC: 16–24 bit (resolves <0.1 mV for <0.1 pH unit resolution)

2. Amperometry (reaction current measurement):
   Fixed potential applied to working electrode (vs. reference)
   Analyte oxidizes or reduces at electrode surface → measurable current
   Current proportional to analyte concentration (mass transport limited)

   Glucose oxidase (GOx) reaction:
   Glucose + O₂ → Gluconolactone + H₂O₂   [GOx catalysis at pH 7.4, 37°C]
   H₂O₂ → 2H⁺ + O₂ + 2e⁻                  [Anodic oxidation at +0.6V vs Ag/AgCl]
   Current (nA range) ∝ glucose concentration

   Three-electrode potentiostat:
   Working electrode: Pt, Au, or carbon (reaction surface)
   Reference electrode: Ag/AgCl (stable potential)
   Counter electrode: Pt (completes current circuit)
   Potentiostat IC: holds working electrode at fixed potential, measures current

3. Conductometry (solution conductance):
   AC measurement (2-electrode, avoids polarization) at 1–10 kHz
   Total ion concentration → solution conductance
   Used for: electrolyte balance measurement, bacterial growth detection
```

#### Phase 2 — Automated Blood Chemistry Analyzers (1960s)

Large laboratory analyzers (Beckman Coulter, Abbott Architect, Roche Cobas) integrate multiple electrochemical and optical measurement modules with robotic sample handling.

```
Internal subsystems:
  ISE module: Na+, K+, Cl-, CO2, Li+ measurement
  Photometric module: white light through reaction cuvette → absorbance at specific λ
    Glucose (oxidase-peroxidase): reads at 505 nm
    Creatinine (Jaffe): reads at 510 nm
    ALT/AST: NADH oxidation reads at 340 nm (UV)
    Bilirubin: reads at 540 nm (diazo reaction)
  Immunoassay module: antibody-capture with chemiluminescent label
    Troponin, TSH, HbA1c, B-HCG, PSA — detected at attomolar range
  Hemolysis detector: sample quality check
  Cell counter (CBC): impedance counting (Coulter principle) + light scatter

Constraints: large (refrigerator-sized), expensive reagent cartridges,
             requires trained technician, turnaround 15–60 minutes,
             requires indoor AC power

Miniaturization path:
  Point-of-care analyzers (i-STAT, Piccolo): credit-card cartridge, handheld reader
  Dry chemistry strips: reagents embedded in membrane, optical reader
  Microfluidic integration: all steps on chip
  NanoFlowSIM derivative: NFSIM-CHEM-01
```

#### Phase 3 — CGM (Continuous Glucose Monitoring) (2006–present)

```
Subcutaneous enzymatic wire sensor:
  Working electrode construction:
  Core wire: Pt 127 µm diameter
  ├── GOx enzyme layer: glucose oxidase crosslinked with BSA + glutaraldehyde
  ├── Inner interference membrane: Nafion (rejects ascorbate, acetaminophen, uric acid)
  ├── Glucose-limiting outer membrane: polyurethane (controls diffusion rate)
  └── Biocompatibility outer layer: medical-grade polyurethane or silicone

  Reference electrode: Ag/AgCl (on sensor body, not filament)

  Electrochemistry:
  Applied potential: +0.6V vs Ag/AgCl
  Reaction: glucose → gluconolactone + H₂O₂ → measured current
  Sensitivity: ~0.2–1 nA per mg/dL (varies by design)
  Range: 40–400 mg/dL → 8–80 nA typical

  Signal conditioning:
  Transimpedance amplifier (TIA): converts nA current → measurable mV voltage
    Feedback resistor: 10 MΩ → 10 nA = 100 mV
  Low-pass filter: removes high-frequency noise
  ADC: 16–24 bit (resolves <1 nA current changes)
  Temperature compensation: NTC thermistor corrects for temperature effect on enzyme kinetics

  Wireless transmitter:
  MCU: nRF52840 (BLE + NFC)
  Power: CR2032 or CR2477 coin cell
  NFC (FreeStyle Libre style): passive ISO 15693, phone tap → read
  BLE (Dexcom style): active advertising every 5 min → streaming to receiver

  Challenges solved over 3 generations:
  Biofouling: protein deposition on sensor surface → calibration drift
    Solution: anti-fouling membranes (phosphorylcholine, zwitterionic coating)
  Enzyme degradation: GOx loses activity over 7–14 days
    Solution: crosslinked GOx + stabilizing additives (BSA, trehalose)
  Immune response: foreign body response → fibrous encapsulation
    Solution: dexamethasone eluting coating, flexible filament design
  Calibration: factory calibration coefficients + optional fingerstick calibration

  NanoFlowSIM derivative: NFSIM-CGM-01 (fully open design)
```

#### Phase 4 — Pulse Oximetry (1972–present)

```
Beer-Lambert law applied to tissue optics:
  Photons transmitted through finger/earlobe
  Two LEDs: 660 nm (red), 940 nm (near-IR)
  Photodiode detects transmitted light at each wavelength

  HbO₂ and Hb have different extinction coefficients:
  At 660 nm: ε(Hb) >> ε(HbO₂) — Hb absorbs much more red
  At 940 nm: ε(HbO₂) > ε(Hb) — HbO₂ absorbs more IR

  Ratio of ratios (removes tissue path length dependency):
  R = (AC₆₆₀/DC₆₆₀) / (AC₉₄₀/DC₉₄₀)
  AC component: pulsatile (arterial blood only)
  DC component: non-pulsatile (tissue + venous blood)

  SpO₂ from empirical calibration (volunteers):
  SpO₂ ≈ 110 − 25R (simplified linearization)
  True calibration: multipoint calibration curve vs. SaO₂ co-oximetry

  Hardware:
  Red LED: 660 nm, 2–5 mA drive current
  IR LED: 940 nm, 5–10 mA drive current
  LED multiplexing: alternate 1 kHz, dark measurement for ambient subtraction
  Photodiode: Si broadband
  Transimpedance amplifier: converts photodiode current to voltage
  Synchronous demodulation (lock-in): separates 660 nm and 940 nm signals
  ADC: 18–22 bit (extracts pulsatile component, <0.1% of DC)
  DSP: adaptive filtering for motion artifact

  Extended multi-wavelength oximetry (Masimo Rainbow):
  8 wavelengths → additionally measures:
  SpCO (carboxyhemoglobin), SpMet (methemoglobin), SpHb (hemoglobin)
  cpHb (non-invasive hemoglobin concentration)
  SpOC (oxygen content)
  PVi (pleth variability index → volume responsiveness)
```

#### Phase 5 — NIRS (Near-Infrared Spectroscopy) for Tissue Oxygenation

```
Extended to brain and muscle:
  Multiple source-detector distances: short (<15 mm) vs long (30–45 mm)
  Short separation: superficial signal (skin, skull)
  Long separation: deep tissue signal (brain cortex, muscle)
  Differential signal: long − (short × scaling factor) = true deep tissue signal

  Modified Beer-Lambert law:
  ΔA(λ) = ε_HbO₂(λ)·ΔCHBO₂·d·DPF + ε_HHb(λ)·ΔCHHb·d·DPF
  Where:
    d = source-detector distance
    DPF = differential pathlength factor (scatter correction, tissue-specific)
    ΔC = concentration change vs. baseline

  Measured: ΔHbO₂ and ΔHHb (changes from baseline)
  Derived: rSO₂ = HbO₂/(HbO₂+HHb) × 100%

  Clinical applications:
  Cerebral NIRS (forehead): monitor cerebral oxygenation during cardiac surgery
  Muscle NIRS (quadriceps): exercise physiology, VO₂max testing
  Tumor NIRS: detect hypoxia zones in accessible tumors

  NanoFlowSIM derivative: NFSIM-OXY-01
```

#### Phase 6 — Sweat Chemistry and Breath Analysis

```
Sweat sensing:
  Sweat contains: Na+ (10–100 mM), K+ (3–8 mM), pH (4.5–7.5), lactate (0–30 mM),
                  urea (~10 mM), glucose (<0.5 mM), cortisol (~25 nM), uric acid
  Microfluidic collection: PDMS serpentine channels fill with eccrine sweat
  ISE detection: ionophore membranes for Na+, K+; polyaniline/IrOx for pH
  Amperometric: lactate oxidase for lactate
  Challenge: sweat rate variability, dilution, skin pH contamination
  NanoFlowSIM derivative: NFSIM-SWEAT-01

Breath analysis:
  Exhaled breath contains >800 volatile organic compounds (VOCs)
  Key biomarkers in breath:
    Acetone (>1.8 ppm): ketosis, diabetic ketoacidosis, fasting
    Isoprene (<0.1 ppm): normal range; changes with cholesterol metabolism
    Ammonia (>1 ppm): possible renal failure or liver disease
    H₂ and CH₄: GI fermentation, SIBO, lactose intolerance
    NO (ppb): airway inflammation (asthma FeNO test)
    CO: anemia, smoking, hemolytic disease
    Ethanol: metabolism indicator

  Detection methods:
    Metal oxide sensor (MOX) array (e-nose): non-specific but patterned response
    Photoacoustic spectroscopy: laser + resonator + microphone → specific analyte
    Ion mobility spectrometry (IMS): drift time → molecular weight
    Proton transfer reaction MS (PTR-MS): real-time mass spec
    Selected ion flow tube MS (SIFT-MS): multiple analytes simultaneously

  NanoFlowSIM derivative: NFSIM-BREATH-01
```

### 7.4 Domain: Electrical / Bioelectric Sensing

**What It Measures:** Bioelectric signals from ion flux across cell membranes — cardiac rhythm (ECG), brain electrical activity (EEG), muscle activation (EMG), eye movement (EOG), skin conductance (EDA), peripheral nerve conduction, neural firing patterns.

**Why It Matters for NanoFlowSIM:** Cardiac status informs vascular simulation. Neural activity relates to CNS-targeting therapies. ECG arrhythmias may indicate drug toxicity from simulated therapeutics. Immune cell electrical activity reflects therapy response.

#### Core Physics of Bioelectricity

```
Cell membrane ion channels and the resting potential:
  Na+/K+ ATPase pump: maintains concentration gradients
    Intracellular: high K+ (~140 mM), low Na+ (~12 mM), low Ca²⁺
    Extracellular: low K+ (~4 mM), high Na+ (~140 mM), high Ca²⁺
  Resting membrane potential:
    Neuron: approximately −70 mV
    Cardiac muscle: approximately −90 mV
    Set primarily by K+ equilibrium (Nernst) and pump activity

Action potential (neuron):
  1. Depolarization: voltage-gated Na+ channels open → Na+ influx → −70 mV → +40 mV
     Rise time: ~1 ms
  2. Repolarization: Na+ channels inactivate; K+ channels open → K+ efflux
     Fall time: 2–5 ms
  3. Hyperpolarization: brief undershoot (~−80 mV) before return to rest
  Propagation: adjacent membrane capacitively charged → sequential activation
  Speed: 0.5–100 m/s (unmyelinated: slow; large myelinated: fast)

Body as volume conductor:
  Bioelectric dipoles (heart, brain, muscle) create potential fields
  These fields spread through conductive body tissue
  Attenuated by: resistive and capacitive body compartments
  Detectable at skin surface with appropriate amplification
```

#### ECG (1903–present)

```
Cardiac conduction system:
  SA node → AV node → Bundle of His → Left/Right bundle branches → Purkinje fibers
  → ventricular myocardium

  Waveform components:
  P wave: atrial depolarization (~100 ms, 0.1–0.3 mV amplitude)
  PR interval: AV nodal conduction delay (120–200 ms)
  QRS complex: ventricular depolarization (60–100 ms, 1–3 mV amplitude)
  ST segment: ventricular plateau phase (isoelectric normally)
  T wave: ventricular repolarization (200–400 ms)
  QT interval: total ventricular electrical systole (350–450 ms)

ECG lead system:
  Standard 12-lead ECG:
  Limb leads (I, II, III, aVR, aVL, aVF): from 4 limb electrodes
  Precordial leads (V1–V6): positioned across chest

Full hardware signal chain:
  Skin electrode:
    Ag/AgCl wet gel: lowest impedance (5–10 kΩ), best clinical standard
    Dry textile: 10–100 kΩ, wearable applications
    Contact impedance critically affects noise floor (thermal noise ∝ sqrt(R))

  Instrumentation amplifier:
    3-op-amp topology: rejects common-mode interference
    CMRR > 80–100 dB (critical — ECG ~1 mV, 50/60 Hz interference ~100 mV on body)
    Input impedance: >100 MΩ
    Gain: 250–1000× (brings mV to ADC range)
    Key IC: Texas Instruments ADS1291 (24-bit, 4 µVRMS noise, integrated filter)

  Right-leg drive (RLD) circuit:
    Actively drives patient body to virtual ground
    Dramatically improves CMRR (additional 30–40 dB)
    Uses inverting amplifier driven by common-mode signal

  Filtering:
    High-pass: 0.05 Hz (removes DC baseline wander from respiration/motion)
    Low-pass: 40–150 Hz (anti-alias; 40 Hz for rhythm, 150 Hz for HF analysis)
    Notch: 50 or 60 Hz (power line interference, or use CMRR to avoid notch artifacts)

  ADC:
    16–24 bit resolution
    Sampling rate: 250–500 Hz standard; 1–4 kHz for signal-averaged ECG

  MCU processing:
    R-peak detection: Pan-Tompkins algorithm (1985, still gold standard)
      Steps: bandpass filter (5–15 Hz) → derivative → squaring → moving window integration
      → adaptive thresholding → R-peak index
    RR interval extraction: time between successive R-peaks
    HRV metrics: SDNN, RMSSD, pNN50, LF/HF ratio (frequency domain)
    Arrhythmia detection: ML classifier (nRF52840 TFLite Micro: ADS1291 + nRF5340)

  AI ECG capabilities (modern):
    Neural network input: raw 10-second 12-lead ECG
    Detects: AFib, flutter, PVC, SVT, LVH, LBBB, RBBB, myocardial infarction (old and acute),
             ST changes, QT prolongation, hyperkalemia (serum K+ from ECG waveform)
    Reference: Stanford/Google/Mayo AI-ECG papers (published models)
    Models deployed in wearables, Apple Watch, AliveCor KardiaMobile
```

#### EEG (1924–present)

```
Neural population dynamics:
  EEG records aggregate cortical activity from millions of pyramidal neurons
  Pyramidal cell dipoles: apical dendrites (excitatory input) → sink current → source at soma
  Synchronized populations: coherent EPSPs → macroscopic field potential at scalp

  Signal amplitudes:
  At cortical surface (ECoG): 1–10 mV
  At skull inner surface: 100–500 µV
  At scalp surface: 10–100 µV (skull attenuates and smears by 40–100× factor)

  Skull attenuation properties:
  Bone conductivity ~0.02 S/m (40× lower than gray matter ~0.7 S/m)
  Acts as spatial low-pass filter: blurs high-frequency (>30 Hz) spatial information
  Source localization limited to ~5–10 cm spatial resolution (vs. mm for ECoG)

  EEG frequency bands and physiology:
  Delta (0.5–4 Hz): slow-wave deep sleep (NREM 3/4), anesthesia
  Theta (4–8 Hz): drowsiness, memory encoding, meditation, hippocampal activity
  Alpha (8–13 Hz): relaxed wakefulness with eyes closed, default mode network
  Beta (13–30 Hz): active thinking, focus, motor planning, anxious states
  Gamma (30–100 Hz): perceptual binding, working memory, cognitive engagement
  High gamma (>70 Hz): most localized neural processing, near-threshold for clinical EEG

EEG hardware stack:
  Electrode preparation (wet, clinical):
    Skin abrasion at electrode sites, alcohol cleaning
    Conductive gel (EC2 or Ten20) applied under cup electrodes
    Impedance target: <5 kΩ (wet gel contact)
    Cap or mounted headset: maintains 10-20 system positions

  Dry electrodes (NFSIM-EEG-01):
    Spring-loaded gold-tipped pins: penetrate hair, contact scalp without gel
    Impedance: 10–100 kΩ (higher but acceptable with modern high-impedance amplifiers)
    Advantage: no prep time, wearable, ambulatory monitoring possible

  Amplifier requirements vs ECG:
    Noise floor: <1 µVRMS (vs <5 µVRMS for ECG — 5× more challenging)
    Input impedance: >1 GΩ (vs >100 MΩ for ECG — 10× higher)
    CMRR: >100 dB
    Gain: 1000–10000× (vs 250–1000× for ECG)
    Key IC: TI ADS1299 (8-channel 24-bit, 1 µVRMS noise, specifically designed for EEG)

  Artifact types and mitigation:
    Eye blink: EOG artifact ~100 µV (ICA artifact removal)
    Eye movement: horizontal/vertical EOG (ICA, EOG regression)
    Muscle artifact (EMG): >30 Hz, particularly neck muscles (time-frequency masking)
    Power line: notch filter or adaptive filtering (Hampel filter)
    Movement: accelerometer-based template subtraction

  Analysis methods:
    Spectral: FFT-based power spectrum, spectrogram
    Event-Related Potential (ERP): averaging locked to stimulus onset
    ICA (Independent Component Analysis): separates source signals (MNE-Python)
    Connectivity: coherence, PLV, Granger causality
    BCI features: motor imagery (ERD/ERS), SSVEP, P300
```

#### EMG (1929–present)

```
Motor unit action potentials (MUAPs):
  Motor unit: single motor neuron + all muscle fibers it innervates
  MUAP amplitude: 0.1–5 mV (surface EMG), 100–10,000 µV (needle EMG)
  MUAP duration: 5–15 ms
  MUAP shape: diphasic or triphasic characteristic waveform

  Surface EMG (sEMG) characteristics:
  Records sum of many MUAPs
  Amplitude: 0.1–10 mV during strong contraction
  Bandwidth: 10–500 Hz (most power 50–150 Hz)
  Sampling: 1000–4000 Hz

  Applications:
  Rehabilitation: biofeedback, gait analysis, muscle fatigue monitoring
  Prosthetics: control signal for myoelectric prosthetic hand/arm
  Gesture recognition: 8-channel armband → 6–10 gesture classes (ML classification)
  Neuromuscular diagnosis: ALS, myopathy, neuropathy screening
  Sports science: muscle activation ratio, co-contraction patterns

  NFSIM-EMG-01 hardware:
  ADS1298 (8-channel 24-bit, TI): 8 simultaneous differential channels at 2 kHz
  Bandpass: 20–500 Hz hardware Butterworth filter
  ML: TFLite Micro on nRF52840, ~50 KB INT8 gesture model
  Input: MVC-normalized features (MAV, WL, ZC, SSC)
  Latency: <10 ms inference → real-time prosthetic control
```

#### Invasive Neural Sensing and BCIs

```
ECoG (Electrocorticography):
  Electrode grid on brain surface (beneath dura)
  Signal amplitude: 0.1–10 mV (100× stronger than scalp EEG)
  Bandwidth usable: DC to 500 Hz (vs <100 Hz for EEG)
  Spatial resolution: 1–5 mm (vs 3–5 cm for EEG)
  Application: surgical epilepsy mapping, BCI, research

Intracortical microelectrode arrays:
  Utah Array: 10×10 silicon shanks, 400 µm spacing, 1–1.5 mm depth
    96 electrodes, each records 1–5 neurons (extracellular unit recording)
    Impedance: 100–500 kΩ at 1 kHz (Pt-black or PEDOT coating lowers to <100 kΩ)

  Neuropixels (IMEC, 2017): 960 electrodes on single 70 µm × 10 mm silicon shank
    Records across all cortical layers simultaneously
    Inter-electrode pitch: 25 µm
    Bandwidth: 0.3 Hz – 10 kHz
    Game-changer for systems neuroscience

  Signal chain for intracortical recording:
  Extracellular spikes: 100–500 µV amplitude, 0.5–2 ms duration
  LFP (Local Field Potential): <300 Hz, 0.1–5 mV
  Headstage amplifier: Intan RHD2132 (32-channel, 16-bit, 0.98 µVRMS noise)
  Spike sorting: Kilosort2/3 (deep learning-based), MountainSort, JRClust
  Output: sorted spike times per unit → neural code

  Brain-Computer Interfaces (BCIs):
  BrainGate: Utah array recordings → cursor control, robotic arm, speech synthesis
  Stentrode (Synchron): stent-like electrode array placed endovascularly over motor cortex
    No open brain surgery → chronic BCI access
  Neuralink N1 chip: 1024 electrodes on 64 threads, fully implanted, wireless BLE
  NeuroPace RNS: detect seizure onset → electrical stimulation to abort seizure

  Current BCI challenges:
  Signal stability: glial scarring degrades signal quality over months-years
  Flexible electronics: PEDOT-coated polymer arrays reduce tissue damage
  Power delivery: inductive coupling limits bandwidth for high-channel-count systems
  Decoding: non-stationary neural code → needs adaptive decoders
  Ethics: privacy, consent, cognitive liberty for neural data

  NanoFlowSIM derivative: NFSIM-NEURAL-01 (flexible ECoG research array)
```

### 7.5 Domain: Implantable / Closed-Loop Systems

**Core Architecture Principle:**

All implantable systems share this fundamental operational loop:

```
Sense biological state
→ Condition signal (amplify, filter, digitize)
→ Interpret (algorithm or AI classification)
→ Decide (therapy needed? which parameter?)
→ Actuate (stimulate, release drug, open valve)
→ Physiological response
→ Sense again (close the loop)
```

```
Historical arc of implantable medicine:
1958: First implantable pacemaker (Åke Senning, Sweden) — mercury-zinc battery, 3-week life
1960s: Lithium iodide battery → 5–10 year pacemaker life
1970s: Programmable pacemakers (external radio reprogramming)
1980s: ICDs (defibrillation capability added), dual-chamber pacing
1990s: Biventricular (cardiac resynchronization therapy, CRT)
2000s: Remote monitoring (daily data upload via cellular)
2010s: Leadless pacemaker (Medtronic Micra — 0.8 cc capsule inside heart)
2020s: Adaptive DBS, subcutaneous ICD, endovascular BCI (Stentrode)
Future: Closed-loop multi-organ implant networks, bioresorbable sensors

Key engineering challenges all implants face:
  Power: sealed system, no external supply → battery or energy harvesting
  Hermetic sealing: body fluids destroy electronics → titanium or ceramic packages
  Biocompatibility: immune rejection, fibrosis, chronic inflammation
  Lead reliability: fatigue fracture from cardiac and respiratory motion
  Wireless communication: through tissue at safe RF power levels
  MRI compatibility: most clinical MRI restricted with pacemakers (improving)
  Longevity: minimum 5–10 years for surgically placed devices
```

**Pacemaker (detailed hardware):**
```
Sensing channel:
  Intracardiac electrogram (IEGM): 0.5–30 mV amplitude bipolar sensing from lead tip
  Sense amplifier: bandpass 10–100 Hz, blanking period after pace artifact
  Sensitivity: 0.5–10 mV programmable threshold
  Sense detection: threshold crossing → triggers timing logic

Pacing channel:
  Pulse generator: constant-voltage output
  Parameters: amplitude 0.5–5 V, pulse width 0.1–1.5 ms, rate 60–200 bpm
  Current draw: ~5 µJ per pulse
  Battery: Li-SVO (lithium silver vanadium oxide) — 2.8 V, 1–2 Ah
  Battery life: 5–15 years at standard settings

Accelerometer (rate-adaptive pacing):
  Detects physical activity → increases pacing rate
  Simple 1D piezoelectric or 3-axis MEMS accelerometer
  Algorithm: activity count → target rate mapping

Wireless telemetry:
  Inductive telemetry: 175 kHz, used for original programming
  Far-field RF: 402–405 MHz (MICS band), 60–300 kbps
  BLE 5.0: newer devices (Micra AV, Gallant XT)
  Remote monitoring: daily transmission via cell modem or home monitor

Leadless pacemaker (Micra AV, Medtronic):
  Capsule dimensions: 25.9 mm × 6.7 mm, volume 0.8 cc
  Delivered: via femoral catheter → right ventricle
  Fixation: 4 nitinol tines screwed into trabeculae
  Power: Li-MnO₂ primary cell
  Communication with Micra AV: VDD mode (sense atrial contraction via accelerometer
    detecting mechanical P wave → synchronize ventricular pacing)
```

**Cochlear Implant (hardware detail):**
```
External processor:
  Microphones: 1–3 directional MEMS microphones
  DSP: filterbank into 12–22 frequency channels
  Coding strategies: ACE (Advanced Combination Encoder), CIS, FS4
  RF transmitter coil: transcutaneous link (modulated radio at 900 MHz or 5 MHz)
  Battery: rechargeable (Z power silver-zinc or Li-Ion)

Internal implant:
  Receiver/decoder: RF receiver coil, signal demodulation
  Stimulator ASIC: 22 independent current sources
  Electrode array: 22 platinum-iridium contacts in silicone carrier
  Positioned: scala tympani of cochlea (basal turn to apex)
  Current per channel: 0–2 mA, biphasic pulses 25 µs
  Frequency mapping: tonotopic (base=high frequency, apex=low frequency)
  Stimulation rate per channel: 250–5000 Hz

Outcomes:
  Adults (post-lingual deafness): 80%+ speech understanding in quiet
  Children (pre-lingual): critical period → implant early for best language development
  Brain plasticity: auditory cortex adapts to electrical hearing pattern
```

**Deep Brain Stimulation (DBS):**
```
Target nuclei by indication:
  Parkinson's disease: STN (subthalamic nucleus) or GPi (globus pallidus interna)
  Essential tremor: Vim (ventral intermediate nucleus of thalamus)
  Epilepsy: ANT (anterior nucleus of thalamus) — Medtronic SANTE trial
  OCD: VC/VS (ventral capsule/ventral striatum) — FDA HDE approved
  Depression: SCC (subgenual cingulate cortex, Area 25) — investigational

Stimulation parameters:
  Frequency: 60–180 Hz (high-frequency stimulation disrupts pathological beta oscillations)
  Pulse width: 60–210 µs
  Amplitude: 1–5 V (voltage-controlled) or 1–5 mA (current-controlled)
  Mode: monopolar or bipolar (electrode configuration)

Adaptive DBS (sensing + stimulating):
  Sense: LFP (local field potential) from same electrodes during stimulation gaps
  Beta band (13–30 Hz): pathologically elevated beta → proportional to Parkinson symptoms
  Adaptive algorithm: beta power high → increase stimulation amplitude; beta low → decrease
  Result: 50% reduction in stimulation compared to chronic stimulation → battery savings
  + may improve therapeutic specificity

  Hardware: Medtronic Percept PC (FDA approved 2020) — first commercial sensing DBS
  NanoFlowSIM application: adaptive DBS data → neural region body map → simulation of
  nanoparticle-based neuromodulatory agents
```

**Artificial Pancreas / Closed-Loop Insulin Delivery:**
```
Components:
  1. CGM: Dexcom G7 or Abbott FreeStyle Libre 3 (or NFSIM-CGM-01)
     Glucose reading every 5 minutes → transmitted to controller

  2. Control algorithm: runs on smartphone or dedicated controller
    PID control: proportional-integral-derivative on glucose error
    MPC (Model Predictive Control): predicts glucose trajectory 30–60 min ahead
    Fuzzy logic: rule-based controller (simpler, robust)

  3. Insulin pump: Omnipod 5, MiniMed 780G, or DIY (Cozmo hacked)
    Delivery: micro-doses (0.05 U steps) every 5 minutes (automated mode)
    Basal rate modulation + correction boluses

Open-source closed-loop systems (approved in some countries, DIY in others):
  OpenAPS: Node.js algorithm on Raspberry Pi Zero
  Loop (iOS): Swift app on iPhone, Nightscout CGM bridge
  AndroidAPS: Android app, full algorithm + pump driver
  All use: CGM + pump + Nightscout data platform

These systems achieve:
  TIR (Time In Range 70–180 mg/dL): 70–85% (vs 50–60% manual)
  HbA1c reduction: 0.5–1.0% average improvement
  Hypoglycemia reduction: significant (life-saving)

NanoFlowSIM integration: NFSIM-CGM-01 → compatible with OpenAPS/Loop for DIY APS
```

### 7.6 Domain: Cellular / Microscopic Sensing

```
Flow Cytometry (1967–present):
  Principle: cells in single-file flow through laser beam
  Forward scatter (FSC): correlates with cell size
  Side scatter (SSC): correlates with granularity/complexity
  Fluorescence: antibody-conjugated fluorophores → protein expression quantification

  Applications:
  CBC with differential: WBC 5-part diff (neutrophils, lymphocytes, monocytes,
    eosinophils, basophils) + RBC + PLT count
  Immunophenotyping: CD4/CD8 ratio (HIV monitoring), B-cell, T-cell panels
  Cell cycle: propidium iodide DNA staining → G1, S, G2/M phase distribution
  Apoptosis: Annexin V (early apoptosis) + PI (late apoptosis/necrosis)
  Rare cell detection: circulating tumor cells (CTCs), fetal cells in maternal blood

  Hardware challenge for portability:
  Sheath fluid focusing: requires precision pumps + 3D flow channel geometry
  Acoustic focusing: piezo-driven bulk acoustic wave focuses cells without sheath fluid
  → eliminates complex fluidic system (NFSIM-FLOW-01 approach)
  Laser: 20 mW 488 nm solid-state diode (vs mW-class gas laser historically)

  NanoFlowSIM derivative: NFSIM-FLOW-01

Digital Pathology:
  Whole slide imaging (WSI): motorized XY stage + high-resolution camera
  → gigapixel images of complete tissue sections
  AI pathology: cell segmentation, mitosis counting, tumor grading,
    biomarker quantification, survival prediction
  NanoFlowSIM: NFSIM-MICRO-01 outputs → UBERON-tagged to biopsy site
```

### 7.7 Domain: Dynamic Physiological Monitoring

```
Cardiovascular:
  Continuous blood pressure:
    Tonometry: radial artery waveform (wrist sensor pressed against artery)
    PPG-derived: pulse wave velocity from two PPG sensors at known separation
    ABPM: automated cuff inflation (Holter-style, 24h)
  Cardiac output:
    Thermodilution (clinical): cold saline bolus + thermistor catheter → Fick principle
    Bioimpedance: 4-electrode thoracic impedance (changes with stroke volume)
    CW Doppler aortic: NFSIM-US-05 wristband variant

Respiratory:
  Capnography (EtCO2): IR absorption of CO2 in exhaled breath
    Normal ETCO2: 35–45 mmHg
    Critical in: ventilation monitoring, CPR quality assessment
  Spirometry: flow-volume loop measurement
    FEV1 (1-second forced expiratory volume): obstructive disease marker
    FVC (forced vital capacity): restrictive disease marker
    Peak expiratory flow (PEF): asthma monitoring
  Pulse oximetry SpO2: see Chemical domain
  RIP (Respiratory Inductance Plethysmography): coils around thorax + abdomen
    → respiratory rate, tidal volume, phase relationship

Body Temperature:
  Tympanic (infrared): ear canal IR emission → 0.2°C accuracy
  Temporal artery: forehead swipe IR scanner
  Core temperature: ingestible thermometer capsule (NFSIM-CAP-05)
    → most accurate continuous core temperature available
    Normal: 36.5–37.5°C, circadian variation ~0.5°C

Motion and Posture:
  IMU (Inertial Measurement Unit): 3-axis accelerometer + gyroscope + magnetometer
  Applications: step counting, activity classification, fall detection,
    tremor quantification (Parkinson's), balance assessment
  Gait analysis: multiple IMUs on limbs → full gait kinematics
  NFSIM integration: motion data UBERON-tagged to limbs/spine
```

### 7.8 Domain: Multi-Modal Convergence Systems

```
Current multimodal combinations:
  PET-CT: metabolic function (FDG uptake) co-registered with anatomical CT
    Gold standard for oncologic staging
  PET-MRI: simultaneous PET (functional metabolic) + MRI (soft tissue anatomy)
    Emerging for pediatric oncology, neuroimaging
  MRI + ECG gating: cardiac MRI synchronized to cardiac cycle
  EEG + fMRI: simultaneous brain electrical + hemodynamic signals

Future convergence (NanoFlowSIM architecture pre-built for):
  Continuous EEG + ECG + CGM + SpO2 + motion + breath VOC +
  wearable chemistry + episodic sequencing + imaging
  → AI-integrated living physiological model
  → Personalized digital twin
  → Predictive intervention triggers

Grand direction of medicine:
  FROM: symptom → diagnosis → treatment (episodic, reactive)
  TO: continuous monitoring → prediction → preventive intervention (proactive)

  The bottleneck is no longer data collection — it is interpretation.
  AI is the essential layer that transforms raw biosignals into clinical insight.
  NanoFlowSIM's simulation engine + AI layer is the interpretation infrastructure.
```

---

## 8. Open-Source Hardware Ecosystem — Philosophy and Mandate

### The Portability Revolution — Pattern Across All Domains

Every domain of biological sensing has followed the same historical pattern:

```
1. Physical sensing principle discovered/described
2. Large, expensive, centralized instrument built to exploit it
3. Biological insight gained, clinical value demonstrated
4. Years/decades of incremental improvement
5. Key enabling miniaturization technology emerges:
   (semiconductor integration, MEMS, better DSP, better batteries, better algorithms)
6. First commercial portable version released (still proprietary, expensive)
7. Open-source community replicates core function at fraction of cost
8. Accessibility expands dramatically → broader scientific and clinical use

Examples of step 7:
  OpenPCR (2012): democratized PCR thermocycling
  OpenBCI (2014): democratized EEG neural sensing
  Open Ephys (2016): democratized neuroscience recording
  AMULET / OpenHRV: open ECG / HRV platforms
  OpenMRI: academic low-field MRI efforts

NanoFlowSIM performs step 7 across ALL domains simultaneously.
```

### Design Mandates (Universal — All Devices)

1. **Portable:** Battery-operable minimum 8h. Fits in a bag, worn on body, or swallowed.
2. **Open hardware:** Full KiCad 6.0+ schematic, PCB, Gerbers, STEP files published
3. **Open firmware:** Complete C/C++/Rust embedded firmware, MIT license, FreeRTOS/Zephyr
4. **Open protocol:** NFS universal JSON over BLE 5.0 GATT / USB-C CDC / 434 MHz / NFC
5. **NanoFlowSIM-native:** All data UBERON-tagged, streams directly to NFS patient profile
6. **Reproducible:** All components available from LCSC + Mouser + Digi-Key. JLCPCB compatible.
7. **Field-deployable:** 0–45°C ambient, IPX4 minimum splash-resistance for wearables
8. **Affordable BOM:** <$500 for most research devices, <$200 for most wearables
9. **Usable UI:** Every device has a companion UI flow tested end-to-end, not wireframe stubs
10. **Calibrated:** Factory calibration protocol + coefficients stored in NVS + UBERON-anchored

### BOM Compliance Checklist (Per Device, Pre-Release)

```
□ All components have LCSC part numbers (for JLCPCB PCBA)
□ All components available from Mouser or Digi-Key (worldwide supply)
□ No end-of-life components (lifecycle status: Active on manufacturer site)
□ Bill of materials in CSV and interactive HTML BOM format
□ Pick-and-place CSV compatible with JLCPCB SMT assembly
□ Alternate part numbers listed for at least 2 sources per critical component
□ Total BOM cost calculated with current pricing (date-stamped)
□ Any custom components (machined parts, custom chemistry) have supplier listed
□ Consumable costs calculated separately per test or per month of use
```

---

## 9. Hardware Domain A — Molecular / Genomic

### Complete Device List

| Device ID | Name | Primary Technology | BOM Target |
|---|---|---|---|
| NFSIM-PCR-01 | Portable Individual PCR Thermocycler | Peltier + PID thermal cycling | ~$148 |
| NFSIM-PCR-02 | Gel-Slip Strip Reader | HV electrophoresis + CMOS imaging | ~$83 |
| NFSIM-PCR-03 | LAMP Isothermal Reader | Fixed heater + fluorescence | ~$65 |
| NFSIM-PCR-04 | RPA Room-Temperature Reader | Low-temp heater + lateral flow | ~$45 |
| NFSIM-SEQ-01 | Open Nanopore Sequencer | Biological pore + FPGA patch clamp | ~$536 |
| NFSIM-SEQ-02 | Solid-State Nanopore Board | SiN pore + multi-channel amplifier | ~$180 |
| NFSIM-CRISPR-01 | CRISPR Fluorescence Reader | SHERLOCK/DETECTR + fluorometer | ~$96 |
| NFSIM-CRISPR-02 | CRISPR Lateral Flow Reader | SHERLOCK/DETECTR + optical strip | ~$55 |
| NFSIM-CRISPR-03 | Electrochemical CRISPR Detector | No optics, electrical only | ~$40 |
| NFSIM-dPCR-01 | Digital Droplet PCR | Microfluidic partitioning + fluorescence | ~$285 |
| NFSIM-GELEC-01 | Full Portable Gel Electrophoresis | HV + UV LED + CMOS | ~$110 |
| NFSIM-GELEC-02 | Chip Capillary Electrophoresis | Microfluidic CE chip reader | ~$130 |

### NFSIM-PCR-01 — Portable Individual PCR Thermocycler

**Concept:** Single-strip (8-tube) PCR thermocycler designed for individual field use. Smaller than a paperback book. Peltier-based thermal cycling, BLE connectivity, TFT display, battery-powered. Addresses the gap left by OpenPCR (which was desktop, 96-well, mains-only).

**Full Specifications:**

| Parameter | Value |
|---|---|
| Sample format | 8 × 0.2 mL PCR strip or 1 individual tube |
| Sample volume | 5–50 µL per tube |
| Temperature range | 4°C – 99°C |
| Temperature accuracy | ±0.2°C block-to-block, ±0.5°C well-to-well |
| Ramp rate (heating) | 5°C/second minimum |
| Ramp rate (cooling) | 3°C/second minimum (Peltier limited) |
| Maximum cycles | 60 programmable |
| Run time (40 cycles) | 45–60 minutes |
| Lid temperature | 103°C (heated lid, prevents evaporation) |
| Connectivity | USB-C + BLE 5.0 |
| Power source | 3000 mAh LiPo OR USB-C PD 20W |
| Battery life | 8–12 complete 40-cycle PCR runs |
| Dimensions | 120 × 80 × 60 mm |
| Weight | ~280g with battery |
| Display | 2.4" IPS TFT 240×320, ST7789 |
| MCU | STM32G474 (Cortex-M4, 170 MHz, hardware FPU for PID) |
| Wireless | nRF52840 (BLE 5.0) on daughter module |
| IP rating | IP42 splash-limited |
| Operating temperature | 0°C – 40°C ambient |

**Hardware Architecture — PCB Design:**

```
Primary MCU board (PCB-A, 80×50mm, 4-layer FR4):
  MCU: STM32G474RET6 (LQFP64)
    - Hardware math co-processor for PID loop
    - Timer-1 → PWM for Peltier drive (20 kHz)
    - SPI1 → TFT display (10 MHz)
    - SPI2 → nRF52840 BLE (8 MHz)
    - I2C1 → MAX17055 fuel gauge, NTC thermistor readout
    - UART1 → Debug / firmware update
    - ADC1 → thermistor channels (2× NTC block, 1× NTC ambient, 1× NTC lid)

  BLE co-processor: nRF52840-QIAA (QFN73)
    - BLE 5.0 GATT server (NFS device profile)
    - Connected to STM32 via SPI (INT line for wake on BLE command)
    - Antenna: onboard PCB trace antenna (2.4 GHz, FCC pre-certified layout)

  Power tree:
    LiPo (3.7V nominal) → BQ24075 charger (USB-C PD negotiation via FUSB302)
    → Protection IC (BQ2970DSET) → battery rail
    → TPS61085 boost converter → 5V 3A (Peltier + fan + heated lid)
    → AMS1117-3.3 LDO → 3.3V (MCU, BLE, display, sensors)
    Battery monitoring: MAX17055 (fuel gauge, coulomb counter, I2C)
    USB-C PD: FUSB302MPCX (USB-C PD PHY, negotiates 20W profile)

  Display circuit:
    ST7789 TFT 2.4": SPI at 10 MHz, backlight PWM via MOSFET
    LVGL (Light and Versatile Graphics Library): real-time UI rendering
    XPT2046 touch controller (optional capacitive touch variant)

  Buttons: 4× tactile buttons (3mm travel) — START/STOP, UP, DOWN, MENU

Thermal block board (PCB-B, 80×50mm, 2oz copper, aluminum-core substrate):
  Thermal substrate: 1.6mm aluminum-core PCB (IMS board) for direct heat transfer
  Thermal block: CNC-machined 6061 aluminum, 8 conical wells for 0.2 mL format
  Peltier modules: 2× TEC1-12706 (40×40mm, 6A, 12W each — in parallel configuration)
  TEC driver: DRV8876 H-bridge (5A, 45V, TTL-compatible) × 2 (one per TEC)
    or IRLZ44N MOSFET H-bridge with IR2104 gate drivers for higher current
  Thermistors: 4× NTC 10kΩ B=3950K — 2× embedded in block wells (center, edge),
    1× on heat sink, 1× ambient
  Current sense: INA219 (I2C, measures Peltier current for PID monitoring)
  Fan: 30×30×10mm, 5V, 6 CFM (cooling heat sink beneath Peltier cold side)
  Heat sink: copper vapor chamber 60×40mm + finned aluminum extrusion
  Thermal interface: Arctic Silver 5 compound between all thermal interfaces

Heated lid assembly:
  Heater: Kapton flexible heater 70×30mm, 5V, 5W (NTC thermistor embedded)
  MOSFET: IRLML6344 (logic-level N-channel, SOT-23)
  Lid block: aluminum, spring-loaded, 1.5mm silicone pressure pad
  Setpoint: 103°C, PID controlled (separate from block PID)

Enclosure:
  2-part PETG shell printed at 0.2mm layer height
  Top: lid hinged with 3mm stainless pin, tube access opening
  Bottom: fan intake vents, USB-C cutout, rubber feet
  Window: polycarbonate lens for display
  Silicone gasket: around tube block area prevents condensation entry
  Dimensions: 120 × 80 × 60 mm
  Tripod mount: 1/4-20 threaded brass insert in bottom shell
```

**Firmware Architecture:**

```
RTOS: FreeRTOS (STM32CubeMX generated, FreeRTOS 10.4.6)

Tasks:
ThermalControlTask (priority 7, 10ms tick, 1KB stack):
  - Reads block and lid thermistors via ADC DMA
  - Block PID loop: Kp=5.0, Ki=0.3, Kd=0.8 (gain-scheduled for heat vs cool)
    Error = setpoint - measured
    P_out = Kp × error
    I_out += Ki × error × dt (anti-windup: clamp ±100)
    D_out = Kd × (error - prev_error) / dt
    Output → PWM duty cycle on TEC H-bridge (20 kHz PWM)
    Direction pin: HIGH = heat mode, LOW = cool mode
  - Lid PID: Kp=3.0, Ki=0.5, Kd=0.2 (simpler, just resistive heat)
  - Stage transitions: time-based with temperature confirmation
  - Safety: if block > 100°C or <0°C for >30s → ERROR state → full stop

ProtocolRunnerTask (priority 6, 100ms tick, 2KB stack):
  - Protocol JSON loaded from SPI flash (W25Q128)
  - Supported protocol fields:
    { "name": "...", "lid_temp": 105,
      "steps": [{"type": "denaturation", "temp": 95, "time": 30},
                {"type": "annealing", "temp": 58, "time": 20},
                {"type": "extension", "temp": 72, "time": 60},
                {"type": "cycle_repeat", "count": 35, "from_step": 0},
                {"type": "final_extension", "temp": 72, "time": 300},
                {"type": "hold", "temp": 4}] }
  - State machine: IDLE → RUNNING → PAUSED → COMPLETE → ERROR
  - Cycle counter, step timer, ETA calculation
  - On COMPLETE: log JSON result record, notify BLE task

BLECommunicationsTask (priority 5, 50ms tick, 2KB stack):
  - Manages nRF52840 via SPI command protocol
  - NFS BLE GATT characteristics updated:
    0x1001 (notify): {status, stage_name, cycle, block_temp_x100, ETA_sec, battery_pct}
    0x1002 (write): command byte → start/stop/pause/resume/load protocol
  - Protocol upload: receives JSON over BLE (fragmented over 244-byte MTU)
  - Session management: assigns session UUID, links to patient ID if set

DisplayTask (priority 4, 50ms tick, 4KB stack):
  - LVGL widgets: temperature chart, stage badge, cycle counter, progress bar, ETA
  - Real-time temperature plot: last 60 seconds ring buffer → line chart
  - Menu system: protocol selector, settings, calibration trigger
  - Color coding: blue (cooling/hold 4°C), red (denaturation), yellow (annealing),
    green (extension), white (complete)

BatteryMonitorTask (priority 2, 1000ms tick, 512B stack):
  - MAX17055 polling via I2C
  - State of charge, voltage, current, temperature
  - Low-battery warning at 10% → yellow battery icon
  - Emergency stop at 5% → save current run state, graceful shutdown

SystemMaintenanceTask (priority 1, 10000ms tick, 1KB stack):
  - Watchdog feeding
  - Error log write to flash
  - OTA check: BLE command 0x10 → enter DFU mode
  - Uptime tracking
```

**Communication Protocol:**

```
BLE Notifications (every 500ms during active run):
  Characteristic 0x1001 packet (10 bytes):
  Byte 0: status (0=idle, 1=running, 2=paused, 3=complete, 4=error)
  Byte 1: stage (0=denat, 1=anneal, 2=extend, 3=hold, 4=final)
  Byte 2: cycle number (current cycle / total cycles, encoded as current)
  Bytes 3-4: block temp × 100 (uint16, e.g., 9500 = 95.00°C)
  Bytes 5-6: lid temp × 100 (uint16)
  Bytes 7-8: ETA seconds remaining (uint16)
  Byte 9: battery % (uint8, 0–100)

NFS Session Complete JSON (streamed over BLE Batch Upload or USB):
{
  "nfs_version": "1.0.0",
  "device_id": "NFSIM-PCR-01-ABCDEF",
  "device_type": "NFSIM-PCR-01",
  "session_id": "uuid",
  "patient_id": "uuid",
  "timestamp_unix_us": 1748304000000000,
  "data_type": "pcr_run",
  "anatomy_region": { "primary": "UBERON:0000178", "label": "blood_or_sample_source" },
  "data": {
    "protocol_name": "COVID_LAMP_65C",
    "protocol_version": "2.1",
    "cycles_completed": 40,
    "total_runtime_seconds": 2847,
    "thermal_profile_summary": [
      {"stage": "initial_denaturation", "target_c": 95.0, "duration_s": 120, "achieved_c": 94.7},
      {"stage": "denaturation", "target_c": 95.0, "duration_s": 30, "achieved_c": 94.8},
      {"stage": "annealing", "target_c": 58.0, "duration_s": 20, "achieved_c": 57.9},
      {"stage": "extension", "target_c": 72.0, "duration_s": 60, "achieved_c": 72.1}
    ],
    "temperature_log_1hz": [95.1, 95.0, 94.9, ...],
    "max_ramp_rate_C_per_s": 4.8,
    "block_uniformity_delta_C": 0.3
  },
  "quality": { "score": 0.98, "thermal_consistency": 0.99, "cycles_completed_pct": 1.0 },
  "device_status": { "battery_pct": 74, "firmware_version": "1.2.0" }
}
```

**Bill of Materials (Key Components):**

| Component | Part Number | Supplier | Est. Unit Cost |
|---|---|---|---|
| STM32G474RET6 | STM32G474RET6 | Mouser | $3.80 |
| nRF52840-QIAA | nRF52840-QIAA-R | Mouser | $4.50 |
| TEC1-12706 Peltier (×2) | TEC1-12706 | LCSC | $2.80 × 2 |
| DRV8876 H-bridge (×2) | DRV8876PWPR | LCSC | $1.20 × 2 |
| MAX17055 fuel gauge | MAX17055REWL+ | Mouser | $2.10 |
| BQ24075 charger | BQ24075RGTR | LCSC | $1.20 |
| FUSB302 USB-C PD | FUSB302MPX | LCSC | $0.90 |
| TPS61085 boost converter | TPS61085DBVR | LCSC | $1.80 |
| AMS1117-3.3 LDO | AMS1117-3.3 | LCSC | $0.12 |
| INA219 current sense | INA219BIDR | LCSC | $1.50 |
| W25Q128 SPI flash | W25Q128JVSIQ | LCSC | $0.80 |
| 2.4" TFT display (ST7789) | ILI9341 2.4" module | AliExpress | $4.50 |
| 30×30mm fan 5V | FAN30×30×10 | LCSC | $1.20 |
| CNC aluminum thermal block | Custom machined 6061 | Local machine shop | $25.00 |
| Vapor chamber + heat sink | 60×40mm copper VC | AliExpress | $8.00 |
| Kapton heater (lid) | 5V 5W 70×30mm | AliExpress | $2.50 |
| NTC thermistors 10kΩ (×6) | SDNT2012X103F3950 | LCSC | $0.15 × 6 |
| Arctic Silver 5 (small) | AS5-3.5G | Amazon | $2.00 |
| 3000 mAh LiPo 4S | custom pack | Amazon/Adafruit | $6.00 |
| PCB 4-layer 2oz Cu | 2 boards | JLCPCB | $15.00 |
| SMT Assembly | — | JLCPCB PCBA | $40.00 |
| PETG enclosure | — | FDM print | $12.00 |
| Hardware, connectors, misc | — | Various | $10.00 |
| **Total** | | | **~$148** |

---

### NFSIM-PCR-02 — Gel-Slip Strip Reader

**Concept:** Pre-cast disposable polymer gel strips inserted into a compact reader. UV LED illumination, CMOS imaging. Results in 8–12 minutes with no gel preparation required.

**Gel Strip Design:**
```
Dimensions: 70 × 20 × 2 mm
Material: 1.5% agarose pre-cast in 1× TBE buffer, SYBR Safe pre-stained
Wells: 8 sample wells + 1 ladder well (10 µL capacity each)
Ladder: pre-loaded with 100 bp–10 kb ladder (Well 1)
Sealed: foil tab over each well (peel to load)
Buffer wells: pre-filled reservoirs at each end, sealed with separate tabs
Storage: sealed nitrogen-flushed foil pouches
Shelf life: 6 months refrigerated / 3 months ambient
Cost target: $30 per 10 strips

Polymer gel variants:
  Standard: 1.5% agarose (100 bp–5 kb)
  Large fragment: 0.8% agarose (1 kb–20 kb)
  Small fragment: 3.0% agarose (50 bp–1 kb)
  Each strip type labeled with distinct color-coded stripe on housing
```

**Full Specifications:**

| Parameter | Value |
|---|---|
| Gel format | Disposable polymer gel strip, 70×20mm |
| Lanes per strip | 8 sample + 1 ladder |
| Separation range | 50 bp – 10 kb |
| Resolution | ±5% fragment size |
| Run time | 8–12 min at 200V |
| Stain | SYBR Safe (pre-loaded) or SYBR Gold (compatible) |
| UV excitation | 470 nm blue LED (safe, no UV exposure) |
| Detection | OV5647 CMOS (Raspberry Pi camera, 5MP) |
| Buffer | Pre-loaded in sealed strip |
| Voltage output | 200V DC, 30 mA max |
| Power source | USB-C 5V (internal boost converter to 200V) |
| Dimensions | 120 × 60 × 40 mm |
| Weight | 200 g |
| Connectivity | USB-C, BLE 5.0 |
| IP rating | IP31 (indoor use) |

**Hardware Architecture:**

```
High-voltage system:
  DC-DC boost: MC34063 switching regulator core + external transistor + transformer
  OR: EMCO Q101-5 commercial module (5V→0–300V adjustable, 5mA max)
  Feedback: resistive divider + TL431 reference → adjustable regulation
  Safety: optocoupler-isolated crowbar circuit (>220V trips crowbar SCR)
  Current limit: 30mA max hardware fuse + software current monitoring (INA219)
  Interlock: door microswitch → cuts HV when lid opened (mechanical interlock)
  Electrodes: platinum wire 0.5mm, contacts buffer reservoirs in strip

SYBR Safe compatible imaging (blue LED excitation):
  LED: 2× 470 nm blue LEDs (1W each, Cree EZ290), under-illumination through clear strip bed
  Filter: 520 nm longpass orange acrylic sheet (absorbs blue, passes green SYBR emission)
  Camera: OV5647 5MP, fixed focus at 80mm working distance to gel
  OR: Raspberry Pi HQ Camera + 25mm C-mount lens
  Exposure: auto-exposure via OV5647 AGC
  No UV source needed → no UV safety concerns

Compute:
  Raspberry Pi Zero 2W (quad-core A53, 512MB RAM):
    - Drives OV5647 via CSI camera interface
    - Lane detection algorithm: horizontal profile → peak detection
    - Band detection: per-lane intensity profile → Gaussian peak fitting
    - Size estimation: log-linear interpolation from ladder bands
    - Output: JSON result + PNG image saved to microSD

Electronics:
  STM32G0 MCU: HV control, interlock management, front-panel buttons
  nRF52840 BLE: data transmission
  INA219: monitor HV current (safety cutoff if >30mA)
  10-second auto-shutoff: HV disabled after programmable run time

Result output JSON:
{
  "type": "gel_electrophoresis",
  "strip_type": "1.5_percent_agarose",
  "run_voltage": 200,
  "run_duration_s": 480,
  "ladder_detected": true,
  "bands": [
    {"lane": 1, "size_bp": 500, "intensity_au": 0.82, "pct_total": 45},
    {"lane": 2, "size_bp": 1000, "intensity_au": 0.71, "pct_total": 38},
    {"lane": 2, "size_bp": 300, "intensity_au": 0.45, "pct_total": 24}
  ],
  "image_ref": "gel_run_20260526_134500.png"
}
```

**BOM (Key):**

| Component | Est. Cost |
|---|---|
| EMCO Q101-5 HV module | $12 |
| Raspberry Pi Zero 2W | $15 |
| OV5647 camera module | $8 |
| 470nm LED (×2) | $2 |
| 520nm longpass filter | $5 |
| PTFE strip dock (machined) | $12 |
| STM32G030 MCU | $1 |
| nRF52840 module | $7 |
| PCB (2-layer) | $6 |
| Enclosure (SLA print) | $20 |
| Passives, connectors | $8 |
| **Electronics total** | **~$96** |
| **Gel strips (per 10)** | **~$30** |

---

### NFSIM-PCR-03 — LAMP Isothermal Reader

**Concept:** Loop-mediated isothermal amplification reader. Fixed 65°C incubation block. No thermal cycling. Fluorescence readout in real-time. Results in 15–30 minutes. Compatible with published LAMP primers for COVID-19, influenza, HIV, malaria, Zika, dengue, TB, SARS-CoV-2 variants.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Amplification method | LAMP (Loop-Mediated Isothermal Amplification) |
| Temperature setpoint | 65°C ± 0.5°C (user-adjustable 60–70°C) |
| Sample format | 8-tube 0.2 mL strip |
| Detection | 470 nm LED + 8× OPT101 photodiode (one per well) |
| Fluorescent dye | SYTO-9 / SYBR Green / Calcein / HNB colorimetric |
| Time to result | 15–30 minutes (LAMP) |
| Multiplexing | 2-color (FAM 520nm + ROX 610nm filters) |
| Connectivity | USB-C + BLE 5.0 |
| Power | USB-C 5V 1A (3W total power draw) |
| Battery | 2000 mAh LiPo |
| Battery life | 20+ runs per charge |
| Dimensions | 110 × 70 × 45 mm |
| Weight | 190 g |
| Temperature uniformity | ±0.5°C across all 8 wells |

**Hardware Architecture:**

```
Thermal system (simplified vs PCR-01 — no cooling required):
  Heating block: CNC-machined aluminum, 8 wells, 0.2 mL format
  Heater: Nichrome resistive wire embedded in block (5W, 5V)
    OR: Peltier used only in heating mode (simpler control, no cooling switch)
  Thermistor: NTC 10kΩ embedded in block center + edge
  PID: STM32G474, heating-only PID (no cooling path)
    → Achieves thermal stability ±0.5°C within 3 minutes

Optical detection system:
  Excitation: 2× 470nm LED SMD (OSRAM LT A67K), focused per well through light guide
  Emission filter: 520nm bandpass (FAM, SYBR Green, Calcein) per detector
    OR 610nm bandpass (ROX, EtBr, Calcein-Mn²⁺ orange shift)
  Detector: OPT101 monolithic photodiode + transimpedance amp (Texas Instruments)
    One OPT101 per tube well (8 detectors)
    Output voltage: 0.5–4.5V proportional to fluorescence intensity
  ADC: ADS1115 × 2 (16-bit, 4-channel I2C, two ICs = 8 channels)
  Lock-in detection: LEDs modulated at 1 kHz; software synchronous demodulation
    Improves SNR by rejecting ambient light

Colorimetric LAMP option (no optics):
  LAMP produces color change with pH indicator (phenol red: pink→yellow positive)
  Camera module: OV2640 (2MP) images all 8 wells
  AI classifier (TFLite Micro): detects color change → positive/negative/invalid
  Advantage: no LED, no photodiodes needed → even simpler hardware variant
  Disadvantage: semi-quantitative only (kinetic data lost)

MCU: STM32G474 (main controller, PID, ADC readout)
BLE: nRF52840 (GATT server, streaming amplification curves)
Display: 1.3" OLED I2C (SSD1306, 128×64) — simpler than PCR-01 TFT
```

**BOM:**

| Component | Est. Cost |
|---|---|
| Aluminum heating block (machined) | $18 |
| Nichrome heater element | $3 |
| OPT101 photodiode×8 | $1.80 × 8 = $14.40 |
| ADS1115 ADC ×2 | $1.20 × 2 = $2.40 |
| 470nm LED ×2 | $1 |
| 520nm filter ×8 | $2 × 8 = $16 |
| STM32G474 MCU | $3.80 |
| nRF52840 BLE | $4.50 |
| 1.3" OLED | $2 |
| PCB (4-layer) | $10 |
| 2000mAh LiPo | $5 |
| Enclosure (PETG) | $8 |
| Misc | $5 |
| **Total** | **~$93** |

---

### NFSIM-PCR-04 — RPA Room-Temperature Amplification Reader

**Concept:** Recombinase Polymerase Amplification reader. Works at 25–42°C — just body temperature range. No thermocycler, minimal electronics. Can be used with body heat incubation + lateral flow strip readout for zero-power field diagnostics.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Amplification method | RPA (TwistAmp kits compatible) |
| Temperature | 25–42°C (37°C optimal — body temperature range) |
| Heating | Minimal resistive heater (or body heat pouch, optional) |
| Detection | Lateral flow strip (optical camera reader) or fluorescence |
| Time to result | 10–20 minutes |
| Sample format | 8-tube strip |
| Connectivity | BLE 5.0 |
| Power | USB-C 5V 0.5A (1.5W max) |
| Battery | 1000 mAh LiPo (days of standby, hours of active) |
| Dimensions | 95 × 60 × 35 mm |
| Weight | 120 g |

**Hardware Architecture:**

```
Ultra-minimal thermal system:
  Option A (electronic): small resistance heater strip, 1W, 37°C setpoint
    NTC thermistor feedback, MOSFET driver, STM32L0 PID (very simple)
  Option B (passive): exothermic chemical hand-warmer pack (body-temperature range)
    No electronics for heating — zero power consumption during amplification

Lateral flow strip reader:
  LED: white 5mm, 100mW, illuminates strip from behind
  Camera: OV2640 2MP (compact CMOS module)
  Image analysis: line detection algorithm (horizontal scan, peak finding)
    Control line (always present if valid test)
    Test line (present if negative for DETECTR; present if positive for SHERLOCK)
  AI classifier: MobileNet-tiny INT8 (TFLite Micro) or simple threshold algorithm
    Input: 128×128 cropped strip image
    Output: {result: "positive"/"negative"/"invalid", confidence: float}

Fluorescence option (if SYTO-9 or FAM reporter used):
  Same OPT101 detectors as NFSIM-PCR-03 but only 1 channel (simplified)

MCU: STM32L0 (ultra-low power Cortex-M0+)
BLE: nRF52811 (BLE 5.0, lower cost)
Power: deep sleep between measurements (<5 µA)
```

**BOM: ~$45**

---

### NFSIM-SEQ-01 — Open Nanopore Sequencer (Biological Pore, Gel Membrane)

**Concept:** Open-source nanopore sequencing platform. Uses biological protein nanopores (α-hemolysin or MspA) reconstituted in a supported gel membrane. Open FPGA acquisition board measures picoamp currents. Open basecaller converts raw signals to DNA sequence. Targets research-grade sequencing where MinION flow cells are inaccessible.

**⚠ RESEARCH GRADE — requires laboratory technique skills for membrane formation.**

**Full Specifications:**

| Parameter | Value |
|---|---|
| Pore type | α-hemolysin (Sigma H9395) or MspA (research protein expression) |
| Membrane type | Supported gel lipid bilayer (DPhPC in agarose gel matrix) |
| Ionic current range | 0–500 pA |
| Voltage clamp range | –200 to +200 mV |
| Applied sequencing voltage | +120 to +180 mV |
| Open-pore current | ~100 pA (α-HL at 180 mV in 1M KCl) |
| Noise floor | <2 pA RMS (at 5 kHz with careful Faraday cage shielding) |
| Sampling rate | 10–50 kHz |
| ADC resolution | 16-bit minimum |
| Active channels | 1 (research), up to 16 with PCB expansion |
| Temperature control | 18–40°C (Peltier-controlled chamber base plate) |
| Motor protein | Phi29 DNA polymerase (NEB M0269S) at 50–200 nM |
| Theoretical read length | Unlimited (filament length limited) |
| Raw accuracy | ~85–92% (pre-trained community basecaller model) |
| Connectivity | USB 3.0 to host computer |
| Dimensions | 200 × 150 × 80 mm (amplifier + flow cell unit) |
| Power | USB 3.0 or 12V DC |

**Membrane Chamber Design:**

```
Flow cell body: polycarbonate CNC-machined, 2-chamber design
  Cis chamber (top): sample + buffer + pore protein
  Trans chamber (bottom): buffer only
  Partition: 25 µm Teflon (PTFE) film with laser-drilled or heat-formed 50 µm aperture
    OR: agarose gel membrane (more stable, easier to form):
        2% agarose dissolved in 1M KCl buffer
        Melted at 80°C, cooled in flow cell → gels around aperture
        DPhPC lipid (5 mg/mL in decane) applied → bilayer forms spontaneously on gel surface
        Gel membrane superior to free-standing bilayer: more robust, less fragile

Ag/AgCl electrode preparation:
  Ag wire (0.5mm diameter) electrolytically chlorided in 0.1M HCl (30 min at 1 mA)
  Resulting AgCl coating → stable reference potential in KCl solutions
  Two electrodes: one in cis (connected to headstage), one in trans (reference/ground)

Faraday shield:
  Aluminum enclosure, fully enclosed during measurement
  All cable exits through feedthroughs
  Connected to circuit ground
  Achieves: <5 pA RMS ambient noise reduction to <2 pA RMS
```

**Low-Noise Patch Clamp Amplifier:**

```
Headstage design (Rogers 4350B PCB, low dielectric loss):
  Input op-amp: OPA637 (BiFET, ultra-low noise, unity gain stable)
    Voltage noise: 4.5 nV/√Hz at 1 kHz
    Current noise: 2.5 fA/√Hz (excellent for high-impedance electrode)
  Feedback resistor: 100 MΩ precision (Vishay or Ohmite, 0.1%)
    Gain: 100 MΩ → 1 pA input = 100 µV output
  Feedback capacitor: 0.1 pF (Cf, limits bandwidth to: 1/(2π×100MΩ×0.1pF) = 16 kHz)
  Guard ring: surrounds input trace, driven at same potential as input
    Eliminates leakage current through PCB (key for pA-level measurement)

Anti-aliasing filter:
  4th-order Bessel filter (linear phase), cutoff 5 kHz
  Implemented: cascaded Sallen-Key topology with OPA2134 op-amps

Voltage clamp DAC:
  AD5791 (20-bit, ±10V output, 0.5 µV/°C drift) → precision command voltage
  Applied to trans electrode: sets trans potential relative to cis ground
  Typical sequencing voltage: 120–180 mV

ADC:
  ADS1256 (24-bit, 30 kSPS, differential input)
  OR: AD7177 (32-bit, 10 kSPS, lower noise floor)
  Sampling: 25 kHz (oversampled relative to headstage bandwidth for noise averaging)

FPGA acquisition:
  Board: Lattice iCE40HX8K evaluation board (Breadboard-friendly, open toolchain)
    OR: Digilent Cmod A7 (Artix-7, more resources)
  Functions:
    SPI interface to ADC (triggered acquisition at 25 kHz)
    Real-time event detection: threshold crossing → capture dwell time
    Signal segmentation: identify k-mer events by plateau detection
    USB streaming: FT232H (USB-FS FIFO bridge to host at 40 Mbps)
    Optional: on-FPGA pre-basecalling (simple DTW against k-mer models)
```

**Open-Source Basecaller:**

```
NFSIM Basecaller (Python + PyTorch):
  Architecture: Convolutional + LSTM (similar to Bonito Catfish model)
  Input: raw current signal (normalized, events or events-free)
  Output: FASTQ sequence with per-base Phred quality scores
  Training data: published squiggle datasets (published by academic groups)
    ENA accession: ERA000000+ (various nanopore raw data releases)
    Synthetic training: squiggles generated from known sequences + noise model
  CTC (Connectionist Temporal Classification) decoding
  Open-source basecallers compatible with NFSIM-SEQ-01:
    Bonito (Oxford Nanopore open-source, MIT license, requires trained weights)
    Caduceus (community fork, compatible with R9.4 pore models)
    Dorado (ONT official, models partially available)

Library preparation (open protocols):
  Rapid amplicon protocol (with PCR pre-amplification from NFSIM-PCR-01):
  1. PCR amplify target region (50 ng–1 µg DNA in 50 µL)
  2. SPRI bead cleanup: 0.8× beads, wash 2× 80% ethanol, elute 15 µL
  3. End-repair + dA-tailing: NEBNext Ultra II End Repair (NEB E7596)
  4. Adapter ligation: custom motor-enzyme adapter (hairpin structure)
     Motor enzyme (phi29 DNAP) pre-loaded during synthesis
  5. SPRI cleanup: 1× beads
  6. Load into cis chamber: dilute to 5–50 ng/µL in 1M KCl buffer

Direct native DNA protocol (no PCR):
  1. High-molecular-weight DNA extraction (e.g., Monarch HMW, NEB T3060)
  2. Quantify: Qubit dsDNA HS assay
  3. Fragment size check: NFSIM-GELEC-01 (1% gel)
  4. End-repair + adapter ligation (same as above)
  5. Load into cis chamber
```

**BOM:**

| Component | Source | Est. Cost |
|---|---|---|
| OPA637 precision op-amp | Mouser | $12 |
| 100 MΩ feedback resistor (Vishay) | Mouser | $15 |
| AD5791 precision DAC | Mouser | $35 |
| ADS1256 24-bit ADC | LCSC | $18 |
| Lattice iCE40HX8K FPGA board | Aliexpress/ICE40 | $45 |
| Rogers 4350B headstage PCB (2-layer) | PCBWay | $30 |
| FT232H USB bridge | LCSC | $4 |
| Polycarbonate flow cell (machined) | Local CNC | $40 |
| Teflon film 25 µm (sheet) | Amazon | $20 |
| Ag wire 0.5mm (1m) | Amazon | $10 |
| Aluminum Faraday shield (custom) | Local fabrication | $25 |
| α-hemolysin 20 µg (Sigma H9395) | Sigma-Aldrich | $80 |
| DPhPC lipid 5 mg (Avanti Polar) | Avanti | $50 |
| Phi29 DNAP 500 U (NEB M0269S) | NEB | $120 |
| Peltier temp control base | Custom PCB | $20 |
| Miscellaneous | Various | $22 |
| **Total** | | **~$546** |

---

### NFSIM-SEQ-02 — Solid-State Nanopore Research Board

**Concept:** Development platform for solid-state nanopore research. Provides electrical infrastructure (multi-channel patch clamp amplifier, voltage clamp, high-speed ADC) for testing custom-fabricated SiN or MoS₂ nanopore chips. More stable than biological pores; reusable; cleanroom-fabricated.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Membrane compatibility | SiN (10–50 nm), MoS₂, Al₂O₃, HfO₂ on Si substrate |
| Pore diameter range | 1–20 nm (varies by fabrication) |
| Chip format | 5 × 5 mm substrate with microfluidic PDMS gasket |
| Voltage clamp | ±1V, 1 mV resolution |
| Current range | 1 pA – 10 nA |
| Bandwidth | DC to 100 kHz |
| Sampling rate | 500 kHz (16-bit ADC) |
| Noise floor | <3 pA RMS at 10 kHz |
| Channels | 4 independent channels |
| Interface | USB 3.0 + SPI for FPGA extension |
| Software | Python API, real-time event detection |

**Hardware Architecture:**

```
4-Channel Patch Clamp Amplifier:
  4× independent TIA channels:
    Op-amp: AD8625 or OPA827 (ultralow bias current, FET input)
    Feedback: switchable 500 MΩ (high sensitivity) / 50 MΩ (high bandwidth)
    Per-channel voltage clamp: AD5541A (16-bit DAC) → LT1010 buffer → electrode
    Bandwidth per mode:
      500 MΩ, 0.1 pF Cf → 3.2 kHz BW (high sensitivity mode)
      50 MΩ, 0.01 pF Cf → 320 kHz BW (high speed mode, solid-state pores)
    Cross-talk isolation: >80 dB between channels (separate PCB sections)

FPGA Acquisition:
  Xilinx Artix-7 (Digilent Basys 3 or Arty A7):
    4× 16-bit ADC (ADS8860, 1 MSPS): one per channel
    Real-time event detection: threshold + hysteresis crossing detection
    Dwell time and blockade depth extraction in FPGA logic
    USB 3.0 bulk transfer: FT601 (USB 3.0 SuperSpeed FIFO, 200 MB/s)

Chip Interface:
  PDMS gasket: seals chip between two microfluidic chambers
  Spring-loaded Ag/AgCl contact pins: contact chip electrode pads
  Peltier temperature control: 10–60°C ± 0.1°C
  Integrated buffer reservoirs: 200 µL each chamber
```

**BOM: ~$280 (excluding nanopore chips, $50–500 each from commercial sources)**

---

### NFSIM-CRISPR-01 — CRISPR Fluorescence Reader

**Concept:** Portable SHERLOCK (Cas13a) or DETECTR (Cas12a) reader with real-time fluorescence monitoring. Detects specific DNA/RNA targets at attomolar sensitivity. LAMP pre-amplification stage integrated. Results in 60–90 minutes total.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Assay type | SHERLOCK (Cas13a) and/or DETECTR (Cas12a) |
| Pre-amplification | RPA at 37°C or LAMP at 65°C |
| CRISPR reaction temperature | 37°C |
| Detection | Fluorescence: FAM (520nm) + Texas Red/ROX (610nm) |
| Excitation LEDs | 470nm + 530nm SMD LEDs |
| Detection | SiPM (silicon photomultiplier) or OPT101 per channel |
| Dynamic range | 1 aM – 1 µM target (with pre-amplification) |
| Sensitivity | Single molecule (with LAMP pre-amp) |
| Time to result | 30–60 min LAMP + 30 min CRISPR = 60–90 min total |
| Sample wells | 8 (FAM + ROX duplexing per well) |
| Power | USB-C 5V 2A |
| Connectivity | USB-C + BLE 5.0 |
| Dimensions | 150 × 90 × 50 mm |
| Weight | 220g |
| Reagent format | Lyophilized tubes (room temperature stable, 6 months) |

**Hardware Architecture:**

```
Dual heating zones:
  Zone 1 (LAMP/RPA): TEC or resistive heater, 65°C ±0.5°C (for LAMP)
    OR 37°C for RPA — same zone, temperature setpoint switchable
  Zone 2 (CRISPR): Resistive heater, 37°C ±0.5°C
  Both zones: NTC thermistor feedback, STM32F4 software PID
  Physical separation: zones in aluminum block with air gap insulation

Fluorescence optical design (perpendicular excitation/emission):
  Excitation path:
    470nm LED (for FAM excitation) — SMD LED, 5mW
    530nm LED (for ROX/Texas Red excitation) — SMD LED, 5mW
    Both LEDs: square-wave modulated at 1 kHz (different frequencies per LED)
    Collimating lens: 5mm aspheric
    Bandpass excitation filter: 475/35nm and 535/30nm
  Emission path (90° to excitation):
    Bandpass emission filter: 520/35nm (FAM) and 610/40nm (ROX)
    Detector: MicroFC-10035 SiPM (silicon photomultiplier, Ontario Photon Inc.)
      Active area: 1×1 mm, Vbr ~25V, 35,000 microcells/mm²
      Gain: 10⁶ → single photon detection capability
    Transimpedance amplifier: OPA380 (high-speed, low noise)
    Lock-in demodulation: software, 1 kHz reference synchronization
  Light path: perpendicular crossing minimizes excitation bleed-through into emission path
  Dark chamber: all optical paths light-isolated within black anodized aluminum housing

Lateral flow strip reader (optional add-on module):
  White LED: 5mm diffuse, illuminates strip
  Camera: OV2640 (2MP, compact)
  Software: line detection algorithm → test/control line intensity → positive/negative
  AI model: 15 KB TFLite Micro on STM32H7 for image classification

MCU: STM32F411 (main controller, heater PID, ADC readout)
BLE: nRF52840
Display: 2.4" TFT (ILI9341, same as PCR-01)
```

**Reagent Cartridge Design:**
```
Tube format: standard 0.2 mL PCR tubes, provided pre-loaded lyophilized:
  LAMP/RPA master mix: lyophilized pellet
  Cas protein + crRNA complex: lyophilized pellet (add target-specific crRNA at prep)
  FAM-RNA reporter: lyophilized with Cas mix
  Reconstitution: add 10 µL RNase-free water + 2 µL sample → mix gently

Component sourcing:
  LwCas13a: GenScript, Sigma-Aldrich (SHERLOCK assay)
    Cost: ~$5–15 per test in research quantities
  AsCas12a: GenScript, IDT (DETECTR assay)
  crRNA: ordered from IDT or Twist Bioscience for any target
    Cost: ~$20–40 per crRNA tube (hundreds of tests)
  Reporter RNA: IDT custom oligo with FAM-3' and Iowa Black RQ quencher-5'
    Or DNA reporter for Cas12a: FAM-TTTTTTTTTT-BHQ1
```

**BOM:**

| Component | Est. Cost |
|---|---|
| STM32F411 MCU | $2.50 |
| nRF52840 BLE | $4.50 |
| MicroFC-10035 SiPM ×4 | $6 × 4 = $24 |
| OPA380 TIA ×4 | $2.50 × 4 = $10 |
| 470nm + 530nm LED | $2 |
| Bandpass filter ×4 | $5 × 4 = $20 |
| Resistive heater elements | $4 |
| NTC thermistors | $2 |
| PCB (4-layer) | $12 |
| 2.4" TFT | $4.50 |
| Enclosure (SLA resin) | $25 |
| Misc | $8 |
| **Total** | **~$118** |
| **Reagents (per 8-test kit)** | **~$40–80** |

---

### NFSIM-CRISPR-02 — Lateral Flow Only CRISPR Reader

**Concept:** Simplest possible CRISPR diagnostic reader. Camera-based lateral flow strip reading only. No fluorescence optics. Lowest cost option for binary positive/negative DETECTR results.

```
Hardware: OV2640 camera + white LED + STM32L0 + nRF52840
Display: 1" OLED (SSD1306)
Result: positive/negative/invalid per strip with confidence score
BOM: ~$35 + ~$5/strip reagents
```

---

### NFSIM-CRISPR-03 — Electrochemical CRISPR Detector

**Concept:** No optics at all. Cas12a collateral cleavage detected via electrochemical signal. Aptamer-blocked electrode surface released by Cas12a cleavage → measurable current change. Lowest power, outdoor/field-rugged.

```
Electrodes: screen-printed carbon electrode on strip (SPE)
  Working electrode modified with target-blocking aptamer + redox reporter
  Cas12a activated → cleaves aptamer → unblocks electrode → current increases
Potentiostat: LMP91000 (3-electrode, I2C)
Detection time: 20–40 min (isothermal reaction)
No LEDs, no cameras, no optical path
BOM: ~$40 reader + $3–8/test strip
```

---

### NFSIM-dPCR-01 — Digital Droplet PCR System

**Concept:** Absolute DNA quantification via droplet partitioning. Critical for liquid biopsy (ctDNA at 0.01% variant allele frequency), viral load monitoring, copy number variation.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Partition method | Oil-water droplet emulsion (T-junction microfluidics) |
| Droplet volume | ~1 nL per droplet |
| Droplets per run | 10,000–20,000 |
| Reaction volume | 20 µL per sample |
| Thermal cycling | Uses NFSIM-PCR-01 thermal block (interchangeable chip holder) |
| Detection | Endpoint fluorescence imaging of settled droplets |
| Dynamic range | 1–100,000 copies/µL |
| Sensitivity | 1 copy per 20 µL reaction |
| Duplexing | 2-color (FAM 520nm + HEX/VIC 556nm) |
| Run time | 90–120 min (PCR cycling + imaging) |
| Connectivity | USB-C + BLE |
| Power | 12V DC or battery |
| Dimensions | 200 × 150 × 80 mm |

**Hardware Architecture:**

```
Droplet generation chip:
  Material: PDMS soft-lithography (master: SU-8 photolithography on silicon)
    OR: injection-molded polycarbonate (production scale)
    OR: 3D printed microfluidic (Formlabs Clear V4 or Form 3+ BioMed Clear)
  Geometry: T-junction or flow-focusing
    Channel dimensions: 100 µm × 50 µm cross-section
  Aqueous channel: sample (PCR master mix + template + primers + probe)
  Oil channel: Mineral oil + 1% Span-80 + 0.05% Tween-20 (HFE-7500 commercial)
  Droplet size: set by aqueous:oil flow rate ratio (1:4 → ~1 nL droplets)

Flow control:
  Syringe pumps: 2× stepper motor-driven micro-syringe (250 µL Hamilton syringe)
    Motor: NEMA8 stepper, 200 step/rev
    Driver: TMC2209 stepper driver (quiet, precise)
    Resolution: 10 nL/step (fine enough for stable droplet generation)
  OR: Pneumatic pressure control (smaller footprint):
    Diaphragm micro-pump (5V) pressurizes sealed aqueous reservoir
    Regulator: proportional valve (MP6 micropump by Bartels)

Chip → PCR cycling:
  Chip sealed with adhesive thermal film after droplet generation
  Placed in NFSIM-PCR-01 (chip holder adapter replaces tube strip holder)
  Standard PCR cycling program (40–50 cycles)
  Droplets: stable through 95°C cycling (mineral oil + Span-80 maintains emulsion)

Droplet imaging station (separate module):
  After cycling, chip placed in imaging station:
  Droplets: gravity-settle into flat monolayer in imaging channel
  LED: 470nm (FAM) + 530nm (HEX) illumination
  Camera: IMX477 (12.3 MP Sony, Pi HQ Camera) with 50mm macro lens
  Filter wheel: 2-position (FAM filter / HEX filter)
  Image: full chip area imaged at 12 MP → each droplet ~5 pixels diameter

Image analysis software:
  OpenCV watershed segmentation: identifies individual droplets
  Per-droplet: intensity in each fluorescence channel
  Threshold classification: positive (bright) vs negative (dim)
  Poisson statistics: concentration = −ln(1 − P_pos) / V_droplet
  2D scatter plot: Ch1 vs Ch2 → 4 populations (neg/neg, pos/neg, neg/pos, pos/pos)
  Export: concentration in copies/µL with Poisson 95% CI

BOM: ~$285
```

---

### NFSIM-GELEC-01 — Full Portable Gel Electrophoresis System

**Concept:** A complete portable agarose gel electrophoresis system supporting real agarose gels, UV-safe SYBR Safe imaging, and gel documentation. Self-contained in a lunchbox-sized unit. Supports any agarose concentration for research applications.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Gel dimensions | 70 × 60 mm (mini gel format) |
| Lanes | 6–12 depending on comb |
| Voltage output | 50–200V DC adjustable |
| Current limit | 500 mA max |
| Run time | 20–45 min |
| Stain | SYBR Safe pre-stained or post-staining |
| UV excitation | 365 nm UV LED (OR 470 nm blue for SYBR Safe) |
| Emission filter | 520nm longpass acrylic |
| Camera | OV5647 or Pi HQ Camera 8MP |
| Buffer capacity | 400 mL internal |
| Power | USB-C (internal HV boost) or 12V DC |
| Dimensions | 200 × 160 × 90 mm |
| Weight | 800 g |
| Safety | HV interlock on lid, UV auto-cutoff |

**Hardware Architecture:**

```
Gel tank:
  UV-transparent polycarbonate body
  Carbon rod electrodes (non-reactive at electrolysis potentials)
  Buffer volume: 400 mL (1× TAE or TBE)
  Gel tray: UV-transparent polycarbonate, 70×60mm
  Comb options: 6-tooth (wide lanes), 12-tooth (standard), 15-tooth (narrow)

HV power supply:
  Flyback converter design:
    Primary: UC3845 PWM controller, FDS8958A MOSFET, custom transformer
    Secondary: rectified + filtered → 0–300V DC
    Voltage regulation: feedback via 1:100 voltage divider + TL431
    Current monitoring: INA219 on secondary side
    Short-circuit protection: primary current limit + secondary fuse
  Polarity: DPDT relay (buffer wells reversible if needed)
  User control: PWM setpoint via STM32 DAC → voltage control

Imaging system:
  UV LED array (365nm): 12× 1W LEDs in grid, under gel tray
    UV energy: 36W total (requires good image contrast)
  OR: Blue LED array (470nm) for SYBR Safe (no UV exposure)
  Emission filter: 520nm longpass acrylic sheet above gel
  Orange goggles: included for UV variant
  Camera: OV5640 5MP + Pi Zero 2W
  Captures: JPEG + PNG, 5MP, auto-exposure
  Wi-Fi: Pi Zero streams images to phone/laptop

Safety:
  Lid microswitch: mechanical interlock → HV disabled when lid open
  UV interlock: UV LEDs off when camera window open
  Timer: HV auto-shutoff after set time (15–60 min programmable)
  Grounded chassis: PE connection via USB-C GND
```

**BOM: ~$110**

---

### NFSIM-GELEC-02 — Chip Capillary Electrophoresis Reader

**Concept:** Microfluidic chip-based capillary electrophoresis. More sensitive and faster than agarose gels. Uses commercially available or custom-fabricated glass/PDMS CE chips. Laser-induced fluorescence detection.

```
CE chip: glass microfluidic chip (Micralyne, Microfab, or custom)
  Channel: 10 cm effective separation length, 50 µm width
HV: 300–1000V for CE fields
Laser: 488nm diode (1mW) for LIF detection
Detector: avalanche photodiode (APD)
Applications: DNA sizing, protein SDS-PAGE on chip, SNP genotyping
BOM: ~$280
```

---

## 10. Hardware Domain B — Structural / Anatomical Imaging

### Complete Device List

| Device ID | Name | Technology | BOM Target |
|---|---|---|---|
| NFSIM-US-01 | USB-C Handheld Ultrasound (B/M/Doppler) | Linear PZT array + FPGA beamformer | ~$471 |
| NFSIM-US-02 | Wearable Ultrasound Patch | Flexible PVDF array | ~$320 |
| NFSIM-US-03 | Ingestible GI Ultrasound Capsule | CMUT ring array, 434 MHz | ~$580 |
| NFSIM-US-04 | High-Frequency Dermal Scanner | 40 MHz single element | ~$180 |
| NFSIM-US-05 | Radial Artery Doppler Wristband | 8 MHz CW Doppler | ~$95 |
| NFSIM-US-06 | Transcranial Doppler Headband (TCD) | 2 MHz bilateral probes | ~$220 |
| NFSIM-US-07 | Endocavity Ultrasound Probe | 5–9 MHz curved array | ~$310 |
| NFSIM-US-08 | Fetal Doppler Wearable | 2–3 MHz CW Doppler | ~$65 |
| NFSIM-US-09 | Ultrasound Needle Guide | 10 MHz clip-on | ~$145 |
| NFSIM-MRI-01 | Low-Field Portable MRI (Permanent Magnet) | 64 mT Halbach, AI recon | ~$4,500 |
| NFSIM-XRAY-01 | Portable X-Ray System | Battery generator + wireless FPD | ~$4,200 |
| NFSIM-OCT-01 | Portable SD-OCT Probe | 840nm SLD interferometry | ~$680 |
| NFSIM-MICRO-01 | Portable Digital Pathology Microscope | 40× objective, IMX477, RPi CM4 | ~$520 |

### NFSIM-US-01 — USB-C Handheld Ultrasound Probe

**Concept:** Open-source handheld ultrasound probe connecting via USB-C to smartphone or laptop. B-mode, M-mode, Color Doppler. Complete open KiCad design, open firmware, open software rendering library.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Transducer type | Linear PZT-5H array, 64 elements |
| Element pitch | 0.25 mm (λ/2 at 7.5 MHz center frequency) |
| Frequency | 4–12 MHz software-selectable (broadband: 3.5 MHz bandwidth) |
| Imaging modes | B-mode, M-mode, PW Doppler, Color Doppler |
| Field of view | 38 mm × 80 mm depth (linear) |
| Frame rate | 30–60 fps (B-mode) |
| Axial resolution | 0.2–0.5 mm (frequency dependent) |
| Lateral resolution | 1–3 mm (focus depth dependent) |
| Interface | USB-C 3.1 Gen1 (power + data, 5V 3A) |
| Power draw | 5V, 2.5A peak (12.5W) |
| Probe body dimensions | 28 mm × 155 mm |
| Weight | 180 g |
| IP rating | IPX7 |
| On-probe processing | Digital beamformer on FPGA |
| DICOM output | Yes (US SOP class) |

**Hardware Architecture:**

```
Transducer Array (PZT-5H variant):
  64 PZT-5H elements, 0.25mm pitch, 15mm elevation aperture
  Acoustic stack construction (from front to back):
    - Matching layer 1: PVA (polyvinyl alcohol) + glass, λ/4 at center frequency
    - Matching layer 2: Polyurethane, λ/4
    - PZT-5H element (0.5 mm thick for 3 MHz quarter-wave resonance)
    - Backing material: 10% Al₂O₃ + epoxy (high acoustic attenuation, 5 dB/mm)
  Flex PCB interconnect: 64-conductor, 100 µm traces, 150 µm pitch
  Acoustic lens: silicone (3:1 silicone:catalyst ratio), 30 mm focal depth (fixed elevation)

TX Beamformer:
  HV pulsers: 8× STHV800 (Texas Instruments)
    Each STHV800: 8-channel, ±100V peak, 4 ns rise time
    8 × 8 = 64 channels total
  Timing: FPGA generates delay profile for each transmit event
    Sub-ns delay precision (clocked at 4 GHz → 250 ps resolution via PLL)
  Apodization: Hanning window across aperture (reduces grating lobes)
  Modes: focused beam (single focal zone), plane wave (compounding for 60fps)
  Plane wave compounding: 9 angles (−4° to +4°) → coherent compound B-mode
    Trades temporal resolution for improved SNR and resolution vs single focus

T/R Switch:
  TX810 (Texas Instruments): 8-channel T/R switch, −100V capable
  8 TX810 ICs = 64 channels
  Switching time: 100 ns (clears transmit artifact before receive)

RX Signal Chain:
  LNA: AD8432 (dual, 26 dB gain, 0.8 dB noise figure)
    32 dual-channel = 64 channels
  TGC: AD9275 (8-channel LNA + TGC + 12-bit ADC, 40 MSPS)
    TGC range: 0–40 dB, 0.5 dB step
    Integrated ADC: 12-bit, 40 MSPS per channel
    8 × AD9275 = 64 channels
  Clocking: 80 MHz crystal → distribution to all AD9275

FPGA (Digital Beamformer):
  Xilinx Artix-7 XC7A100T (Trenz TE0712 or Digilent Arty A7 form factor)
  Receive delay: lookup table per focus depth and angle
  Dynamic receive focusing: delay updated every sample (λ/2 depth increment)
  IQ demodulation: numerically controlled oscillator at carrier frequency
  Envelope detection: complex magnitude of I + jQ
  Log compression: 40 dB range → 8-bit log scale
  Scan conversion: linear scan → rectangular image (GPU preferred, FPGA possible)

USB Interface:
  FT601Q (FTDI, USB 3.0 SuperSpeed, 200 MB/s): transfers beamformed IQ data
  OR: processed envelope data (lower bandwidth)
  Bandwidth requirement:
    IQ data: 64ch × 40 MSPS × 12-bit = 3.84 Gbps (need compression or FPGA beamformer first)
    Envelope data: 256 pixels × 512 lines × 60 fps × 8-bit = 630 Mbps (USB 3.0 capable)

Host Software:
  Desktop (Electron + OpenGL/WebGL):
    Real-time B-mode rendering (scan-converted image)
    M-mode: time vs depth display
    Color Doppler overlay: autocorrelation, velocity colormap
    PW Doppler: FFT spectrum, velocity scale
    DICOM export: US SOP class (frame capture)
  UBERON tagging: user tags imaged anatomy during scan
    Prompt: "What region are you imaging?" → body map click → tag applied
  NFS output packet includes: DICOM reference, UBERON code, probe orientation metadata
```

**BOM:**

| Component | Qty | Est. Cost |
|---|---|---|
| PZT-5H transducer array (custom fabrication) | 1 | $80 |
| STHV800 HV pulser | 8 | $8 × 8 = $64 |
| TX810 T/R switch | 8 | $3 × 8 = $24 |
| AD9275 LNA+TGC+ADC | 8 | $6 × 8 = $48 |
| Artix-7 XC7A100T module | 1 | $90 |
| FT601Q USB 3.0 | 1 | $12 |
| 64-conductor flex PCB | 1 | $35 |
| Probe housing (machined Al) | 1 | $45 |
| Silicone acoustic lens | 1 | $15 |
| PCB (4-layer, ENIG) | 1 | $28 |
| USB-C connector + PD | 1 | $5 |
| Cables, connectors, misc | — | $25 |
| **Total** | | **~$471** |

---

### NFSIM-US-02 — Wearable Ultrasound Patch

**Concept:** Flexible adhesive ultrasound patch for continuous structural monitoring. PVDF array conforms to skin. Applications: continuous cardiac monitoring (parasternal view), lung sliding detection, blood flow monitoring.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Patch dimensions | 60 × 60 mm active area |
| Transducer | PVDF piezo-polymer, 8×8 = 64 elements |
| Element size | 2×2 mm per element |
| Frequency | 2–7 MHz |
| Imaging mode | B-mode, M-mode, limited Color Doppler |
| Penetration depth | 10–150 mm (application-dependent) |
| Frame rate | 5–15 fps |
| Wear duration | 24–72 hours |
| Connectivity | BLE 5.0 (image data compressed + streamed) |
| Power | 300 mAh flexible LiPo |
| Battery life | 12–24 hours continuous |
| IP rating | IPX4 |
| Thickness | <5 mm (electronics pod) + 0.5 mm array |
| Coupling | Medical hydrogel adhesive pad |

**Hardware Architecture:**

```
Flexible Transducer Array:
  PVDF (polyvinylidene fluoride) piezoelectric film:
    Thickness: 52 µm (resonant frequency ~20 MHz; operated at lower harmonics)
    Polarization: in-plane (flex-compatible vs brittle PZT)
    Array: screen-printed silver electrodes on PVDF film
    Individual element addressing: row-column matrix (8 rows + 8 columns = 64 elements)
    Acoustic coupling layer: medical hydrogel (polyacrylamide-based)
      - Acoustic impedance: 1.5 MRayl (matching tissue)
      - Adhesive: dual-sided, medical-grade acrylate

Flexible interconnect:
  Polyimide (Kapton) flex PCB substrate: 25 µm base, 100 µm copper traces
  Serpentine interconnect geometry: allows ±15% stretch without trace fracture
  Snap connector: rigid electronics module clips to flexible array (removable)

Electronics (rigid pod, reusable):
  Beamformer: miniaturized ASIC (custom for production) OR small FPGA
    Prototype option: iCE40UP5K (ultra-small FPGA, low power)
  Low-voltage pulsers: 40V (PVDF requires lower voltage than PZT due to lower impedance)
  ADC: 4× ADS5242 (dual 12-bit 65 MSPS) = 8 channels simultaneous
  Compression: JPEG-2000 hardware encoder for envelope images
  BLE: nRF5340 (dual-core, BLE 5.3, 200 MHz Cortex-M33 + 64 MHz M0)
  Wireless charging: Qi receiver coil (5W)
  Battery: 300 mAh flexible LiPo
  Dimensions of rigid pod: 35×25×4 mm

Continuous monitoring AI:
  On-device (nRF5340 Cortex-M33):
    Cardiac: ejection fraction estimation from M-mode tracings (TFLite, 45 KB model)
    Lung: B-line counting per frame → pulmonary edema score
    Output: physiological metrics (not raw images) → much lower BLE bandwidth
    Streaming: one update per 30 seconds for clinical parameters
    Alert: immediate BLE notification if pericardial effusion pattern detected
```

**BOM: ~$320 (per unit, includes electronics module + 3 disposable hydrogel patches)**

---

### NFSIM-US-03 — Ingestible GI Ultrasound Capsule

**Concept:** Swallowable capsule with 360° radial CMUT ultrasound array. Images GI wall cross-sections during natural transit. Finds tumors, wall thickening, adjacent lymph nodes from inside.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Capsule dimensions | 32 × 13 mm |
| Transducer | CMUT ring array, 64 elements, circumferential |
| Frequency | 12–20 MHz |
| Imaging geometry | 360° radial cross-section of GI lumen |
| Wall penetration | 0–30 mm |
| Axial resolution | 75–150 µm |
| Frame rate | 1 frame per 0.5–2 seconds (triggered by motion) |
| Acoustic coupling | Saline-filled silicone balloon (inflated on swallowing) |
| Wireless | 434 MHz FSK, compressed scan data |
| Battery | Li-MnO₂ primary, 300 mAh |
| Battery life | 24 hours (full GI transit + margin) |
| Biocompatibility | ISO 10993 compliant, Parylene-C coated |
| Position tracking | Pressure + IMU + pH sensor + RF triangulation from external belt |
| Retrieval | Natural passage (24–36 hours), color-coded capsule visible in stool |
| Regulatory | Class III pathway for clinical use; RUO designation for research |

**Hardware Architecture:**

```
CMUT Ring Array (Ultrasound Transducer):
  CMUT technology advantages for capsule:
    Thin (silicon-based, batch MEMS fabrication)
    Integrates directly with ASIC (same silicon process)
    Lower voltage operation vs PZT (5–30V vs 50–100V)
    Broadband response (>100% bandwidth)
  Ring configuration:
    64 elements, circumferentially arranged around capsule circumference
    Element width: ~0.5mm, height: 3mm, gap: 0.1mm
    Radial imaging: elements fired sequentially or in groups
    Coverage: full 360° → complete lumen cross-section per frame
  Acoustic coupling:
    Internal saline reservoir: capsule has thin silicone balloon
    Balloon inflates as patient swallows water after capsule
    Saline inside balloon: acoustic impedance 1.5 MRayl (matches GI wall)
    Capsule shell transmits US through thin polycarbonate (<0.5mm)

Ultrasound Electronics:
  Miniaturized ASIC (custom Si CMOS):
    TX: 64-channel high-voltage pulser (30V, 0.5A peak per channel)
    RX: 64-channel low-noise amplifier + TGC + multiplexer
    ADC: 12-bit, 100 MSPS (one ADC shared via multiplexer)
    Beamforming: delay-and-sum in hardware for radial reconstruction
    Power: 15mW for US subsystem (duty-cycled imaging)
  Image compression:
    JPEG hardware encoder (on ASIC or separate)
    Target: each 512×512 radial image → 8–15 KB compressed
    Frame rate constraint: 434MHz radio bandwidth limits to ~1 frame/2s

Position Tracking System:
  Pressure sensor: BMP581 (Bosch, 6Pa resolution, I2C)
    Peristaltic pressure signatures per GI zone:
    Esophagus: high amplitude rapid waves (50–200 mmHg)
    Stomach: irregular high-pressure contractions (30–60 mmHg)
    Pylorus: characteristic high-pressure sphincter zone
    Small intestine: regular peristaltic waves 10–30 mmHg, 3/min
    Ileocecal valve: pressure signature on crossing
    Colon: haustral contractions, lower amplitude
  IMU: BMA456 + BMI088 (6-axis accel + gyro)
    Capsule orientation, peristaltic motion pattern
    Distinguishes tumbling in stomach vs smooth intestinal transit
  pH sensor: ISFET (H+ selective)
    Stomach: pH 1.5–3.5
    Duodenum: pH 5.5–7.5 (rapid rise from bicarbonate)
    Jejunum/Ileum: pH 6.5–7.5
    Colon: pH 7.0–8.0
    pH step at pylorus → confirms gastric-to-duodenal transition
  Bayesian position estimator:
    Input: pressure signature + IMU motion + pH + elapsed time + RF signal strength
    Output: P(zone) probability distribution over anatomical zones
    UBERON zone mapping:
      Esophagus (UBERON:0001043): 0–15s post-swallow
      Stomach (UBERON:0000945): pressure + pH 1.5–3.5
      Duodenum (UBERON:0002114): pH jump >5.0 + pressure pattern
      Jejunum (UBERON:0002115): smooth peristalsis + elapsed time 2–6h
      Ileum (UBERON:0002116): elapsed time 6–8h
      Colon (UBERON:0001155): elapsed time 8–36h + haustral pattern

Communication (434 MHz FSK):
  Radio IC: Si4463 (Silicon Labs, 10 dBm TX, −121 dBm sensitivity)
  Antenna: meandered PCB trace, circumferential on capsule PCB
  Modulation: 2FSK, deviation ±38 kHz, data rate 76.8 kbps
  Protocol: NFS capsule frame format (see Section 19)
  External belt: 6× patch antennas, diversity reception
  Through-body range: >1m with diversity antenna combining

Battery and Power:
  Primary battery: 2× SR44 silver oxide (1.55V, 200mAh each) in series = 3.1V
    OR: custom thin lithium battery 3.0V 250mAh
  Capacity: 300mAh total
  Power budget breakdown:
    US electronics (active, 1 frame/2s): 15mW × 0.5s = 7.5 mJ/frame
    434MHz radio TX (10dBm): 100mW × 20ms = 2 mJ/frame
    Position sensors: 1mW continuous = 86.4 J/day → negligible vs cap
    MCU sleep: 5µA standby
  Runtime calculation:
    Assume 1 US frame every 2s + radio TX: ~5mW average = 300mAh / 5mA = 60h
    Well exceeds 24–36h GI transit → margin of safety confirmed

External Receiver Belt Hardware:
  6× receiving patch antenna, 434 MHz, positioned around abdomen
  SDR frontend: CC1101 (Silicon Labs) per antenna × 6
  Diversity combiner: maximum ratio combining in firmware
  Bridge processor: STM32H7 (aggregates 6 SDR channels)
  BLE relay: nRF52840 (sends received data to phone app in real time)
  Belt power: 1000mAh LiPo, USB-C charging
  Disposable patches: adhesive-backed antenna, 1-day use, ~$0.50 each
  Reusable module: electronics housing, snap-connects to patches
```

**BOM (Capsule): ~$580 (includes capsule + external belt receiver system)**

---

### NFSIM-US-04 — High-Frequency Dermal Ultrasound Scanner

**Concept:** High-frequency (20–50 MHz) contact ultrasound for skin layer imaging. Resolves epidermis, dermis, subcutaneous fat, and muscle fascia. Applications: skin cancer depth assessment, wound healing monitoring, nanoparticle delivery verification to skin layers.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Transducer | Single-element focused, 40 MHz |
| Mechanical scan | Motorized X-Y linear stage, 20×20 mm area |
| Axial resolution | 35–50 µm at 40 MHz |
| Lateral resolution | 0.2 mm |
| Penetration depth | 3–8 mm |
| Frame rate | 1 frame per 3 seconds (mechanical scan time) |
| Imaging modes | B-mode cross-section, en-face C-mode |
| Connectivity | USB-C + BLE |
| Power | USB-C 5V 1A |
| Dimensions | 80 × 60 × 40 mm (handheld scanner head) |
| UBERON | UBERON:0001416 (skin), UBERON:0004588 (dermis) |

**Hardware Architecture:**

```
Single-element transducer:
  Material: PZT-5H or PVDF (broadband at 40 MHz)
  Focal length: 6 mm (fixed focus, best lateral resolution at 6mm depth)
  Housing: stainless steel, waterproof (submersible for water bath coupling)
  Frequency: 40 MHz center, 50% bandwidth (20–60 MHz usable)

Mechanical scanning:
  X-Y linear stage: 20×20 mm travel, 25 µm resolution
  Stepper motors: NEMA11, 200 step/rev, 0.5mm lead screw
  Position encoder: optical quadrature (sub-step accuracy)
  Scan time: 20×20mm at 0.2mm step = 100×100 = 10,000 A-scans
    A-scan rate: 10,000/3s = 3,333 A-scans/sec → achievable with 40 MHz pulsing

Electronics:
  HV pulser: 100V spike, <5ns rise time (SiGe custom or MAX4163)
  TIA receive amplifier: OPA847 (low noise at 40 MHz)
  ADC: AD9234 (12-bit, 1 GSPS) for 40 MHz digitization
  FPGA: iCE40HX8K (envelope detection, scan conversion)
  MCU: STM32H7 (stage control + data management)

Acoustic coupling:
  Option A: ultrasound gel applied to skin surface
  Option B: water bath (capsule probe submerged, positioned above skin through water)
```

**BOM: ~$180**

---

### NFSIM-US-05 — Radial Artery Doppler Wristband

**Concept:** Wrist-worn continuous pulsed-wave Doppler for radial artery blood flow velocity. Enables beat-to-beat stroke volume estimation and non-invasive blood pressure waveform analysis.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Transducer | Dual-element, 8 MHz PW Doppler |
| Target | Radial artery (wrist) |
| Coupling | Gel-impregnated silicone pad, spring-loaded |
| Signal | Doppler velocity spectrum + pulse waveform |
| Output metrics | Beat-to-beat BP estimate, HR, stroke volume, arterial stiffness index |
| Connectivity | BLE 5.0 |
| Battery | 500 mAh LiPo |
| Battery life | 8–12 h continuous |
| UBERON | UBERON:0001614 (radial artery) |

**Hardware Architecture:**

```
Doppler transducer:
  Dual element: transmit + receive (2 MHz separation, 1cm element size each)
  Angle to artery: 45–60° for Doppler angle correction
  Spring mechanism: ensures consistent coupling pressure (20–30 g force)

Electronics:
  CW Doppler mode: continuous transmit + continuous receive
  PW Doppler: gated at specific depth (set by user tapping artery position)
  Mixer: quadrature demodulation (I + Q)
  FFT processor: 10ms windows → velocity spectrum
  Output: max velocity envelope = non-invasive BP surrogate waveform
  MCU: STM32L4 (low power, sufficient for Doppler FFT)
  BLE: nRF52833

Beat-to-beat BP estimation:
  Pulse wave velocity (PWV) method: requires two sites (wrist + finger or wrist + arm)
  Single-site: diastolic pressure from dicrotic notch timing
  Calibration: initial cuff BP → algorithm coefficients
  Accuracy target: ±10 mmHg systolic (research grade)
```

**BOM: ~$95**

---

### NFSIM-US-06 — Transcranial Doppler Headband

**Concept:** Wearable TCD headband for bilateral middle cerebral artery (MCA) blood flow velocity monitoring. Applications: stroke monitoring, cerebral autoregulation, ICP estimation, sickle cell disease screening.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Transducer positions | 4× probes: bilateral temporal windows (2 per side) |
| Frequency | 2 MHz PW Doppler |
| Depth range | 25–65 mm (covering MCA, ACA, PCA, basilar artery) |
| Gate depth | Programmable 1 mm steps |
| Output | Peak systolic velocity, end-diastolic velocity, mean velocity, PI, RI |
| Connectivity | BLE 5.0 |
| Battery | 800 mAh |
| Battery life | 4 h continuous monitoring |
| UBERON | UBERON:0001637 (middle cerebral artery) |

**Hardware Architecture:**

```
Probe design:
  4× 2 MHz single-element transducers (15mm diameter for temporal window)
  Mounted on adjustable headband with lateral positioning screws
  Angle adjustment: ±30° gimballed mount per probe
  Coupling: ultrasound gel applied in well around probe face

Electronics per probe pair:
  PW Doppler mode: burst transmit + depth-gated receive
  Burst: 8-cycle sinusoid at 2 MHz, 20V peak
  Gate delay: adjustable (depth × 2 / speed_of_sound)
  Gate duration: 3–10 µs (1–5 mm gate length)
  Quadrature mixer: 2 MHz reference oscillator
  Low-pass filter: 0–3 kHz bandwidth (blood velocity range)
  ADC: 16-bit, 8 kSPS per channel
  FFT: 256-point per 32ms window → velocity spectrum

Central hub:
  STM32H7 (processes 4 probe channels)
  BLE: nRF52840 (streams velocity waveforms at 1 Hz summary + 10 Hz detail)
  Battery + charger
```

**BOM: ~$220**

---

### NFSIM-US-07 — Endocavity Ultrasound Probe

**Concept:** Transvaginal or transrectal ultrasound probe for gynecologic and urologic imaging. Connects to NFSIM-US-01 electronics module via probe port. Open probe head design.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Probe head dimensions | 12 × 60 mm (transvaginal) or 15 × 80 mm (transrectal) |
| Array type | 128-element curved, 5–9 MHz |
| Field of view | 160° sector |
| Focal range | 2–10 cm |
| Resolution | 0.3 mm axial at 7 MHz |
| Interface | Proprietary probe port on NFSIM-US-01 reader |
| Cable length | 1.5 m |
| UBERON | UBERON:0000995 (uterus), UBERON:0002367 (prostate) |

**Hardware Architecture:**

```
Curved transducer array:
  128 PZT-5H elements, 0.3mm pitch, 20mm radius of curvature
  Sector angle: 160° (mechanical + electronic combination)
  Elevation focus: fixed at 40mm (acoustic lens)

Probe connector:
  Custom 128-pin locking connector (keyed to prevent incorrect insertion)
  Compatible with NFSIM-US-01 64-channel beamformer (interleaved connection)
  Cable: shielded 128-conductor, 1.5m, 5mm OD
  IPX7 probe housing (washable, autoclave-safe up to 134°C)
```

**BOM: ~$310**

---

### NFSIM-US-08 — Fetal Doppler Wearable Band

**Concept:** Wearable fetal heartbeat Doppler for continuous fetal monitoring at home during 3rd trimester. Multiple transducer positions across adjustable abdomen band.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Transducer | 2–3 MHz CW Doppler, 4 positions across band |
| Band coverage | Adjustable, 70–120 cm circumference |
| Auto-search | AI scans 4 positions → selects best signal |
| Output | Fetal HR continuous, fetal movement detection |
| Alert | FHR outside 110–160 bpm for >60 seconds |
| Display | 1.3" OLED wristwatch remote display |
| Connectivity | BLE 5.0 |
| Battery | 600 mAh |
| Battery life | 8 h continuous |
| UBERON | UBERON:0001987 (placenta region), UBERON:0000922 (embryo/fetus) |

**BOM: ~$65**

---

### NFSIM-US-09 — Ultrasound Needle Guide Clip

**Concept:** Clip-on ultrasound transducer mounting to syringe barrel. Provides real-time needle visualization during injections, joint aspirations, or nerve blocks.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Mount | Clips to 3–5 mL syringe barrel |
| Transducer | 10 MHz linear array, 20mm aperture, 32 elements |
| Needle visualization | Real-time B-mode, 30 fps |
| Needle angle | Adjustable clip: 15–45° insonation angle |
| Interface | USB-C to phone (iOS Lightning adapter included) |
| Display | Phone screen via NFS Ultrasound app |
| Power | Phone USB-C (no battery) |
| UBERON | Region user-selects before procedure |

**BOM: ~$145**

---

### NFSIM-MRI-01 — Low-Field Portable MRI (Permanent Magnet, Halbach Array)

**Concept:** Open-source benchtop MRI using permanent NdFeB magnets in Halbach configuration. 64 mT field. AI reconstruction compensates for reduced SNR. Targets brain (head) and extremity imaging. Based on MaRCoS open-source MRI console platform.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Field strength | 64 mT (0.064 T) |
| Magnet type | NdFeB N52 Halbach cylinder array |
| Bore diameter | 320 mm (head variant) / 120 mm (extremity variant) |
| Larmor frequency | 2.73 MHz (64 mT × 42.577 MHz/T) |
| Field homogeneity | <100 ppm over 10 cm DSV (after shimming) |
| Gradient strength | 10–30 mT/m |
| Gradient slew rate | 10–50 T/m/s |
| RF frequency | 2.73 MHz |
| SNR vs 1.5T | ~1/600 (field^7/4 ratio) — compensated by AI |
| AI-enhanced resolution | 1.5 mm isotropic (brain) |
| Scan time | 5–15 min (depending on sequence and SNR) |
| Weight (head system) | 35–50 kg (magnet assembly) |
| Power | 120/240V, 1.5 kW peak |
| MRI console | MaRCoS (open-source, Red Pitaya FPGA) |
| Shielding | Passive aluminum cage (sufficient at 2.73 MHz) |
| Sequences | SE, GRE, FLAIR, DWI (simplified) |

**Hardware Architecture:**

```
Permanent Magnet System (Halbach Cylinder):
  Magnet material: NdFeB grade N52 (Br = 1.45 T, BHmax = 414 kJ/m³)
  Halbach arrangement:
    Dipole field inside cylinder → uniform B0 field in bore
    Near-zero external field → inherently self-shielded
    Magnet blocks: 20×20×20 mm cubes, arranged with progressive angular rotation
    Formulas:
      Number of blocks N = 16 (per ring, spacing 22.5° each)
      Magnetization angle: θ_n = 2φ_n where φ_n = 360n/N (dipole Halbach)
    Rings: 6–8 rings along bore axis for field homogeneity
    Material cost: ~$1,500–2,500 for magnets alone
    
  Field homogeneity (before shimming):
    Raw Halbach: ±1000 ppm typical over imaging volume
    Target: <100 ppm over 10 cm DSV for usable images
    
  Passive shimming:
    Iron shim plates: placed in shim tray inside bore
    Iterative process: 3D field map acquisition → calculate shim positions → place → repeat
    Tools: Gaussmeter 3D probe, shim calculation software (open Python code)
    Target: <50 ppm after shimming → good image quality
    
  Temperature management:
    NdFeB temperature coefficient: −0.12%/°C (field changes with temperature)
    Active temperature compensation: NTC sensor + small room-temperature shim coil
    OR: operate in temperature-controlled room (±2°C)
    Field drift: ≤2 ppm/°C × ΔT → monitor and correct in software

Gradient Coil System:
  All air-core (no iron yoke at low field):
  Z-gradient (Maxwell pair): two opposing circular coils, field linearity along bore axis
    Material: 10 AWG magnet wire, copper
    Coil dimensions: 200mm radius, 150mm separation for bore 320mm
    Maximum gradient: 25 mT/m at 30A
  X,Y-gradients (Golay saddle coils): two pairs of saddle coils, 90° rotated
    More complex winding geometry → published formulas and MATLAB code
    Maximum gradient: 20 mT/m at 30A
  Gradient amplifiers:
    Commercial option: Crown XLS2502 (Class-D audio amplifier, 2×2500W, repurposed)
    Custom option: H-bridge using IXYS FMM300-0075X IGBT modules
    Current monitoring: 3× Hall-effect current sensors (one per axis)
  Acoustic noise: 70–90 dB SPL (much quieter than clinical MRI — lower slew rates)
  Gradient switching: gradient echo sequence requires <1 ms switching time
    → feasible with Class-D amplifiers and optimized waveforms

RF System:
  Transmit power: <100 W (low field = low power) — standard RF amplifiers work
  RF amplifier: MiniCircuits ZHL-100W-52+ (2–50 MHz, 100W CW)
    OR: homebrew MOSFET RF amplifier (BLF177 or similar, published designs)
  Duplexer (T/R switch): LC-based passive T/R switch (fast passive design at 2.73 MHz)
    Diode bridge network: PIN diodes (MA4P7446-287, Macom) for fast switching
  
  Volume coil (birdcage resonator):
    Resonant at 2.73 MHz, 200 mm diameter, 200 mm length (head coil)
    Number of rungs: 16 (standard for uniformity)
    Low-pass birdcage configuration
    Q factor: 100–200 (higher Q = better sensitivity but narrower bandwidth)
    Bench measurement tools: VNA (NanoVNA is sufficient at 2.73 MHz)
    
  Receive preamplifier:
    Low-noise JFET or GaAs preamplifier
    Noise figure target: <0.5 dB at 2.73 MHz
    Gain: 20–30 dB
    Input matching: tunable LC network for coil impedance matching
    Limiter: PIN diode circuit protects receive chain during RF transmit

MRI Console (MaRCoS — Magnetic Resonance Control System):
  Open-source project: github.com/vnegnev/marcos_server
  Hardware: Red Pitaya STEMlab 125-14 (Xilinx ZYNQ SoC)
    14-bit DAC (125 MSPS): generates RF pulses at 2.73 MHz
    14-bit ADC (125 MSPS): digitizes receive signal
    FPGA fabric: implements real-time pulse sequence engine
    Linux CPU: runs marcos_server Python/C daemon
  Client: Python marcos_client (Jupyter Notebook or custom script)
  Pulse sequences supported:
    Spin echo, gradient echo, inversion recovery
    EPI (echo planar): challenging at low field due to B0 inhomogeneity
  Output: raw k-space data → NumPy array → FFT → magnitude image
  
Reconstruction Software (open):
  BART (Berkeley Advanced Reconstruction Toolbox):
    Iterative reconstruction, parallel imaging, compressed sensing
    Installed on connected laptop (Ubuntu 24.04)
  AI super-resolution (FastMRI-trained models):
    Repository: github.com/facebookresearch/fastMRI
    Pre-trained models: U-Net trained on paired high/low-field data
    Input: low-SNR reconstruction → Output: AI-enhanced higher resolution image
    Improvement: visually equivalent to 3–5× SNR increase
  Output: NIfTI or DICOM format → import to NanoFlowSIM body map (Level 2)

Safety:
  No 5-Gauss line requirement: 64 mT system fringe field drops to 0.5 mT
    within 0.5 m from bore — no room exclusion zone required
  RF SAR (Specific Absorption Rate): trivially low at <100W, 2.73 MHz
    SAR = 0.001 W/kg at 100W total power → orders of magnitude below 4 W/kg limit
  Magnet handling: NdFeB N52 — strong magnetic force near ferromagnetic objects
    Metal tools: never bring within 0.5 m of unshielded magnet assembly
    Halbach self-shielding reduces external field significantly
```

**BOM (head system estimate):**

| Component | Est. Cost |
|---|---|
| NdFeB N52 magnet blocks (assembly) | $2,000 |
| Gradient coil materials (wire, frame) | $400 |
| Class-D gradient amplifiers (×3, Crown XLS) | $600 |
| RF amplifier (MiniCircuits ZHL-100W-52+) | $350 |
| Red Pitaya STEMlab 125-14 | $320 |
| Birdcage coil materials + PCB | $200 |
| PIN diode T/R switch components | $80 |
| Low-noise preamplifier | $120 |
| Shim coil materials | $150 |
| Structure, enclosure, bore tube | $300 |
| **Total estimate** | **~$4,520** |

---

### NFSIM-XRAY-01 — Portable X-Ray System

**⚠ REGULATORY NOTE: X-ray devices emit ionizing radiation. Operator training required by law in most jurisdictions. This design is for research use only. All applicable radiation safety regulations must be followed.**

**Concept:** Battery-powered portable X-ray generator + wireless flat-panel detector. Targets field medicine, veterinary, point-of-care bone/chest imaging, and research applications requiring portable radiography.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Generator kVp | 40–90 kVp adjustable |
| Generator mA | 1–100 mA |
| Exposure time | 1–500 ms |
| Focal spot | 0.6/1.2 mm (fine/broad) |
| Detector size | 35 × 43 cm wireless FPD |
| Scintillator | CsI:Tl structured columnar |
| Pixel pitch | 139 µm |
| DQE | 60–70% at 70 kVp |
| Image bit depth | 14-bit DICOM |
| Wireless | 802.11ac detector to acquisition laptop |
| Generator battery | 300 exposures per charge |
| Generator weight | 4.5 kg |
| Detector weight | 2.8 kg |
| UBERON | Region user-selects before exposure |

**Hardware Architecture:**

```
X-Ray Generator:
  HV module: resonant inverter (LLC topology)
    Input: 48V Li-Ion battery
    Output: 40–90 kVp DC, ±1% regulation
    Control: FPGA-based timing (1 ms resolution exposure timer)
    mA control: filament current PID
  X-ray tube options:
    Research: Newton Scientific MINI-X2 (miniature fixed anode, 40 kVp, 100 µA)
      Low output → suitable for phantoms and small objects
    Clinical: Varian M-113 (rotating anode, mini focal spot)
      Higher output → chest radiography possible
  Collimator: adjustable lead shutters, laser alignment cross
  Battery: 48V Li-Ion, 15 Ah (720 Wh)
  Radiation indicator: audible tone + LED active during exposure

Flat Panel Detector:
  OEM FPD options (to integrate into open system):
    iRay MARS series (OEM, Wi-Fi capable)
    Rayence XMARU series (direct digital, WLAN)
  Custom option: CsI scintillator + amorphous silicon TFT panel (Perkin Elmer)
    + custom readout electronics (FPGA + GigE Vision interface)
  Wireless: 802.11ac dual-band (5 GHz channel for image transfer, <5 sec per image)
  Battery: integrated 6000 mAh Li-Ion
  DICOM output: DR storage SOP class (DICOM 3.0)
  NanoFlowSIM processing:
    DICOM received → auto-detection of body part from DICOM header
    UBERON assigned → user confirms
    3D body map updated at Level 0–1 (imaging confirmation)

Software:
  DICOM receiver: Orthanc (open-source PACS, embedded)
  AI processing: BoneView (long bone fracture AI) or custom model
  NanoFlowSIM NFS exporter: DICOM → NFS JSON metadata + object reference
  Radiation dose tracking: DAP (dose area product) logged per exposure
```

**BOM: ~$4,200 (FPD cost ~$2,500 dominates)**

---

### NFSIM-OCT-01 — Portable Spectral-Domain OCT Probe

**Concept:** Portable SD-OCT probe providing micron-scale cross-sectional tissue images. Applications: retinal imaging, skin cancer depth assessment, wound healing monitoring, intraoperative margin assessment.

**Full Specifications:**

| Parameter | Value |
|---|---|
| OCT type | Spectral-Domain (SD-OCT) |
| Light source | SLD, 840 nm center, 50 nm FWHM |
| Axial resolution | 6–7 µm in tissue |
| Lateral resolution | 15–25 µm |
| Scan depth | 1.5–2 mm |
| A-scan rate | 20,000–70,000 A-scans/sec |
| Field of view | 6 × 6 mm (retinal) / 10 × 10 mm (skin) |
| Spectrometer | 2048-pixel line-scan CMOS |
| Output | 3D volume OCT (DICOM Enhanced OCT) |
| Connectivity | USB 3.0 to laptop |
| Electronics box | 200 × 150 × 80 mm |
| Probe | 120 × 30 mm handheld |
| UBERON | UBERON:0004548 (eye), UBERON:0001416 (skin) |

**Hardware Architecture:**

```
Optical Engine:
  SLD light source: Superlum SLD-MS-271-HP2-DIL-SM-PD
    Center: 840 nm, Bandwidth: 50 nm FWHM
    Coherence length: ~6.3 µm in tissue (lc = 2ln2/π × λ²/Δλ)
    Output power: 15 mW (single-mode fiber pigtail, FC/APC)

  Fiber interferometer:
    2×2 50:50 fiber coupler (Thorlabs FC850-50B-FC, SMF-28e fiber)
    Reference arm: retroreflector (silver mirror on kinematic mount)
      Dispersion compensation: BK7 glass block matched to sample arm glass
    Sample arm: MEMS galvo scanner probe (handheld)
    Dual-balanced detection: both output ports of coupler → differential detection
      Improves SNR by 3 dB, removes common-mode RIN noise

  Spectrometer:
    Collimating lens: f = 75 mm achromatic doublet
    Diffraction grating: 1200 lines/mm transmission holographic grating
    Focusing lens: F-theta lens, f = 150 mm, focused onto line sensor
    Line-scan camera: Basler spL4096-140km (4096 pixels, 140 kHz line rate)
      OR budget option: Thorlabs LC100-USB (1024 pixel, 18 kHz)
      Spectral range coverage: 810–870 nm (50 nm centered at 840 nm)
      Pixel size: 7 µm × 7 µm (Basler)
    Interface: Camera Link or USB 3.0

  Handheld probe head:
    MEMS galvo mirrors (Mirrorcle MEMS): ±10° optical scan, 2-axis
    Collimating optic from fiber: aspheric lens
    Scan lens: achromatic doublet, f = 50 mm (retinal mode) or f = 25 mm (skin)
    Working distance: 25–30 mm from probe face
    Protective glass window: fused silica, AR coated

Electronics:
  Galvo driver: custom DAC + current driver (±5V, 100 mA per axis)
  Scan waveforms: sawtooth (fast axis) + step (slow axis), synchronized to A-scan trigger
  Trigger generator: FPGA (iCE40 or STM32 timer) → camera line trigger
  GPU workstation: processes raw interferograms in real time
    FFT: cuFFT (CUDA) on NVIDIA GPU (GTX 1650 min)
    Processing pipeline: spectrum resampling → dispersion correction → FFT → magnitude → dB
  Display: real-time OpenGL B-scan rendering (30 fps at 512 A-scans per frame)

Reconstruction Output:
  DICOM Enhanced OCT SOP class
  En-face projection images
  3D rendering (Amira or open-source: 3D Slicer + OsiriX compatible)
  NanoFlowSIM: UBERON-tagged DICOM → Level 2 body map update
```

**BOM: ~$680**

---

### NFSIM-MICRO-01 — Portable Digital Pathology Microscope

**Concept:** Portable compound microscope with motorized stage, LED illumination, fluorescence capability, AI cell classification, and whole-slide imaging. Designed for field pathology, blood smear analysis, and tissue biopsy assessment.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Magnification | 10×, 20×, 40× objectives (switchable) |
| Sensor | Sony IMX477 12.3 MP, 1/2.3" |
| Effective resolution | 0.25 µm/pixel at 40× |
| FOV at 40× | 0.5 × 0.4 mm |
| Illumination | LED Köhler (brightfield) + 365/470 nm (fluorescence) |
| Filter positions | 4-position turret: BF, FITC, TRITC, empty |
| Focus drive | Motorized stepper, 0.1 µm step |
| Stage travel | 120 × 80 mm, motorized |
| AI functions | Cell counting, WBC differential, mitosis detection, parasite ID |
| Connectivity | USB-C 3.1 to laptop |
| Power | USB-C or 12V DC adapter |
| Dimensions | 280 × 180 × 350 mm |
| Weight | 3.5 kg |
| Output | SVS whole-slide images, DICOM Microscopic Image |
| UBERON | UBERON:0000178 (blood smear), tissue UBERON per biopsy site |

**Hardware Architecture:**

```
Optical Design:
  Objective turret: manual 3-position (10×/0.25NA, 20×/0.4NA, 40×/0.65NA)
    Objectives: Olympus or Nikon RMS-threaded compatible (UIS2 standard)
    Parfocal: objectives pre-parfocalized, minimal Z re-focusing on switch
  Condenser: Abbe condenser, NA 0.9, with iris diaphragm (Köhler setup)
  Stage: motorized XY, 120×80mm travel
    Steppers: 2× NEMA11, 200 step/rev, 1mm lead screw (0.005 mm per step)
    Drivers: 2× A4988 stepper drivers
    Encoders: optical quadrature (sub-step verification)

Illumination:
  Brightfield: white LED, 3000K color temperature
    Current-controlled: constant current driver (LM3409, PWM dimming)
    Köhler alignment: adjustable condenser centration
  Fluorescence (epi-illumination):
    UV LED: 365 nm, 1W (DAPI excitation)
    Blue LED: 470 nm, 3W (FITC/Alexa488 excitation)
    LED drivers: constant current, TTL-triggered for exposure control
    Filter cube turret (4-position):
      BF cube: empty (white light through)
      DAPI cube: 365/10 excitation, 400 LP dichroic, 450/50 emission
      FITC cube: 475/35 excitation, 505 LP dichroic, 530/30 emission
      TRITC cube: 535/30 excitation, 565 LP dichroic, 610/40 emission

Camera System:
  Sony IMX477: 12.3 MP BSI CMOS, 1.55 µm pixels, 1/2.3"
    Raspberry Pi HQ camera module (breakout using Sony IMX477)
  Compute: Raspberry Pi Compute Module 4 (CM4)
    Quad-core A72, 8 GB RAM, 32 GB eMMC
    Camera interface: CSI-2 4-lane at 4.1 Gbps
    GPU: VideoCore VI for JPEG compression during scanning
  Z-focus: piezo actuator (Piezosystems PD050.31) OR motorized:
    NEMA8 stepper + 0.5 mm pitch lead screw = 2.5 µm/step
    Driver: TMC2209 (silent, StealthChop mode)

Whole-Slide Imaging:
  Automated tiling: scan entire 15×15 mm tissue section
    At 0.25 µm/pixel (40×): 60,000 × 60,000 pixels = 3.6 Gpixel
    JPEG 2000 compression → ~300 MB per slide
    Scan time: ~15 min at 1 fps with automated focus
  Focus map: pre-scan at 10× to build Z-focus map → playback at 40×
  Stitch: Microsoft Image Composite Editor (ICE) or VIPS (open source)
  Output: SVS (Aperio format, OpenSlide compatible)

AI Layer (Raspberry Pi CM4 + cloud option):
  Blood smear WBC differential (on-device):
    Training dataset: Kaggle Blood Cell Detection Dataset (12,500 images)
    Model: MobileNetV3-Small (INT8, 2.1 MB) → 5-class WBC differential
    Accuracy: >95% on held-out test set
    Output: WBC count per class + morphology flags (blast cells, hypersegmented)
  Malaria detection:
    Giemsa-stained thin smear → parasite detection
    Dataset: NIH Malaria Cell Images (27,558 images)
    Model: EfficientNet-B0 → positive/negative + parasite stage
  Mitosis counting (pathology):
    H&E stained tissue → mitotic figure identification
    Dataset: TUPAC16 challenge dataset (open)
  Cell counting (general): watershed segmentation → nuclei count per FOV
```

**BOM: ~$520**

---

## 11. Hardware Domain C — Chemical / Metabolic

### Complete Device List

| Device ID | Name | Technology | BOM Target |
|---|---|---|---|
| NFSIM-CGM-01 | Open Continuous Glucose Monitor | Enzymatic amperometric subcutaneous | ~$38 |
| NFSIM-SWEAT-01 | Sweat Chemistry Patch | Microfluidic ISE + amperometric | ~$95 |
| NFSIM-CHEM-01 | Portable Blood Chemistry Analyzer | Multi-modal cartridge reader | ~$185 |
| NFSIM-CHEM-02 | Saliva Chemistry Analyzer | Lateral flow + electrochemical | ~$80 |
| NFSIM-CHEM-03 | Urine Dipstick Smart Reader | Camera-based strip analysis | ~$55 |
| NFSIM-CHEM-04 | Portable Lipid Panel Analyzer | Enzymatic microfluidic chip | ~$120 |
| NFSIM-CHEM-05 | Portable Lactate Meter | Amperometric enzymatic strip | ~$45 |
| NFSIM-CHEM-06 | Ketone / BHB Monitor | Amperometric strip | ~$35 |
| NFSIM-CHEM-07 | Cortisol / Stress Hormone Sensor | Competitive ELISA cartridge | ~$90 |
| NFSIM-CHEM-08 | Continuous Lactate Implant | Subcutaneous enzymatic wire | ~$55 |
| NFSIM-OXY-01 | Multi-Site NIRS Oxygenation Array | 730/850nm NIRS optodes | ~$180 |
| NFSIM-BREATH-01 | Breath Metabolomics Device | MOX e-nose + photoacoustic | ~$210 |

### NFSIM-CGM-01 — Open Continuous Glucose Monitor

**Concept:** Fully open-source CGM platform. Open hardware sensor design with glucose oxidase chemistry. NFC passive readout + active BLE. 14-day target wear. OpenAPS/Loop compatible. Enables DIYbio modification of CGM sensor chemistry for research into non-glucose analytes.

**Full Specifications:**

| Parameter | Value |
|---|---|
| Sensing method | Enzymatic amperometric (glucose oxidase, GOx) |
| Insertion depth | 8–10 mm subcutaneous |
| Filament diameter | 280 µm (25 G equivalent) |
| Wear duration | 10–14 days target |
| Measurement range | 40–400 mg/dL (2.2–22.2 mmol/L) |
| MARD accuracy target | <10% vs reference analyzer |
| Sampling rate | Every 5 minutes |
| Warm-up time | 60–120 minutes |
| Connectivity | NFC (ISO 15693) + BLE 5.0 |
| Alert capability | High/low glucose, rapid rate-of-change |
| Waterproof | IPX8 (1 m, 30 min) |
| Transmitter dimensions | 38 × 28 × 8 mm |
| UBERON | UBERON:0001175 (interstitial fluid of subcutaneous tissue) |

**Sensor Filament Construction:**

```
Cross-section (inside to outside):
  Layer 1 — Core wire: Pt wire, 127 µm diameter
    Medical-grade platinum (99.99% purity)
    Drawn to 127 µm by wire drawing process
    Electrochemical role: working electrode (cathode)
    Applied potential: +0.6V vs Ag/AgCl reference

  Layer 2 — GOx enzyme coating:
    Glucose oxidase from Aspergillus niger (70–140 U/mg, Sigma G7141)
    Crosslinked matrix:
      BSA (bovine serum albumin): 10 mg/mL
      GOx: 10 mg/mL
      Glutaraldehyde: 2.5% v/v (crosslinks BSA + GOx via amine groups)
    Coating method: dip-coating platinum wire 3× into GOx solution → air dry
    Thickness: ~2–5 µm per coat
    Enzyme activity retained: >80% after crosslinking (critical metric)

  Layer 3 — Interference rejection membrane:
    Nafion (DuPont, 5% solution in lower aliphatic alcohols)
    Electrostatically repels: ascorbic acid (−), uric acid (−), acetaminophen (−)
    Molecular sieve: blocks proteins larger than H₂O₂
    Coating: dip-coat 2× → bake at 120°C for 30 min
    Thickness: 50–200 nm

  Layer 4 — Glucose diffusion limiting membrane:
    Medical-grade polyurethane (Cardiomat 510, Polymer Technology Group)
    Controls glucose flux to enzyme layer (prevents saturation at high glucose)
    Coating: dip-coat from 2% PU solution in DMF → air dry
    Thickness: 5–10 µm
    Critical: determines linear range (40–400 mg/dL)

  Reference electrode (on sensor housing):
    Ag wire (0.5mm), electrolytically chlorided: Ag + Cl⁻ → AgCl
    Stable reference: E = +0.197V vs SHE (in physiological chloride)
    Positioned adjacent to Pt working electrode tip

Transmitter Electronics:
  PCB dimensions: 12×12mm (miniaturized to fit within transmitter housing)
  
  Potentiostat ASIC / discrete:
    Texas Instruments LMP91000 (programmable potentiostat AFE)
      3-electrode mode: WE (Pt), RE (Ag/AgCl), CE (Pt ring)
      Applied potential: 0.6V vs RE (software configurable via I2C)
      Transimpedance gain: 1 MΩ (1nA = 1mV output, selectable)
      Current range: 1–400 nA (covers 40–400 mg/dL glucose range)
      Output: voltage proportional to glucose current
    OR: discrete potentiostat:
      OPA2333 (zero-drift op-amp for RE sense)
      OPA333 (TIA for WE current measurement)
      DAC: MCP4716 (10-bit I2C DAC, controls WE potential)
  
  ADC: Built into LMP91000 path OR ADS1115 (16-bit I2C) for higher precision
  MCU: nRF52840 (BLE 5.0, NFC, 64 MHz Cortex-M4F)
    BLE service: Blood Glucose Measurement Profile (GLP) + NFS extension
    NFC: ISO 15693 (13.56 MHz) — passive readout: tap phone → read current glucose
    NFS GATT extension characteristic: meal tags, insulin events, sensor metadata
  Temperature compensation: NTC thermistor (10kΩ) on sensor housing
    Algorithm: correct sensitivity for temperature (GOx activity ∝ temperature)
  
  Battery options:
    NFC-only mode: harvests power from phone NFC (no battery needed, tap-to-read)
    Active BLE mode: CR2477 (3V, 1000 mAh), supports 14-day life at 5 min intervals
  Flash memory: W25Q40 (4 Mbit): 14-day data log at 5-min intervals (2016 readings)
  Enclosure: medical silicone overmold, IPX8

Applicator:
  Single-use spring-loaded inserter
  Insertion needle: 25G (0.52mm OD), beveled tip, retracts after filament placed
  Sensor housing: self-adhesive base plate (3M 1520N medical tape)
  Operation:
    1. Peel backing → place on skin (upper arm or abdomen)
    2. Press button → spring fires needle + deposits filament → needle retracts
    3. Filament remains subcutaneously → transmitter snaps to base plate

Calibration:
  Factory calibration coefficients stored in NFC memory on transmitter:
    [sensitivity_nA_per_mgdL, offset_nA, batch_lot, expiry_date]
  Optional field calibration: enter fingerstick glucose value → recalculate offset
  Temperature correction: −2%/°C sensitivity change compensated

OpenAPS / Loop Integration:
  GATT CGM Profile: standard BLE glucose measurement characteristic (0x2A18)
  Nightscout compatible: share data to Nightscout server via phone app bridge
  AAPS (Android): direct AAPS support via NFS CGM plugin (planned)
```

**BOM (transmitter unit, per unit):**

| Component | Est. Cost |
|---|---|
| nRF52840-QIAA | $4.50 |
| LMP91000 potentiostat | $2.80 |
| CR2477 battery (included) | $1.20 |
| NTC thermistor | $0.20 |
| W25Q40 flash | $0.35 |
| PCB (2-layer, flex-rigid) | $6.00 |
| Silicone overmold | $8.00 |
| Ag/AgCl electrode | $0.50 |
| Misc passives | $1.00 |
| Applicator (plastic, spring, needle) | $8.00 |
| Sensor filament + chemistry | $5.00 |
| **Total per unit** | **~$37.55** |

---

### NFSIM-SWEAT-01 — Sweat Chemistry Patch

**Full Specifications:**

| Parameter | Value |
|---|---|
| Analytes | Na⁺, K⁺, pH, lactate, glucose (optional), cortisol (optional) |
| Sweat collection | Passive microfluidic, 5–20 µL/h fill rate |
| Detection | Potentiometric ISE (Na⁺, K⁺, pH) + amperometric (lactate, glucose) |
| Na⁺ range | 10–200 mmol/L |
| K⁺ range | 1–30 mmol/L |
| Lactate range | 0–30 mmol/L |
| pH range | 4.5–8.0 |
| Wireless | BLE 5.0 |
| Battery | 20 mAh thin-film LiPo |
| Battery life | 6–12 hours continuous |
| Patch wear time | Single-use, 24h max |
| Waterproof | IPX5 |
| Dimensions | 60 × 40 × 3 mm |
| UBERON | UBERON:0001416 (skin) |

**Hardware Architecture:**

```
PDMS Microfluidic Layer:
  Fabrication: PDMS soft lithography (SU-8 master) OR laser-cut adhesive microfluidics
  Channels: serpentine collector (inlet pores → sensor chambers → waste)
  Inlet pores: 200 µm diameter holes through adhesive layer (align to eccrine glands)
  Priming: capillary pressure drives initial sweat fill (no pump required)
  Volume: 5 µL active sensor chamber, 50 µL total channel volume
  Air-displacement vent: allows channel priming without bubble trapping

Sensor Array (Flexible PCB, polyimide substrate):
  Na⁺ ISE:
    Working: PEDOT-based Na⁺ ionophore (Sodium Ionophore X in PVC membrane)
    Polyaniline coating: provides ionic-to-electronic transduction
    Response: ~58 mV/decade Na⁺ (Nernstian slope)
  K⁺ ISE:
    Working: valinomycin ionophore in PVC matrix
    Response: ~58 mV/decade K⁺
  pH electrode:
    Material: polyaniline (PANI) electrodeposited on Au electrode
      OR: iridium oxide (IrOx) sputtered film
    Response: ~59 mV/pH unit (Nernstian at physiological range)
  Reference electrode:
    Ag/AgCl printed with conductive Ag ink + KCl-saturated gel
    Shared reference for all ISEs
  Lactate amperometric:
    Lactate oxidase (LOx) crosslinked on carbon paste electrode
    Ferrocene mediator (electron shuttle, avoids O₂ dependence)
    Applied potential: +0.4V vs Ag/AgCl
  Glucose amperometric (optional):
    GOx on carbon paste, Prussian Blue mediator
    Applied potential: +0.2V vs Ag/AgCl

Electronics (reusable module):
  Potentiostat array:
    LMP91000 × 2 (for amperometric channels: lactate + glucose)
    Multiplexed ISE readout: ADG708 8-channel mux → single ADC
    ADC: ADS1220 (24-bit, SPI, 4-channel differential, 2 kSPS)
  MCU: nRF52833 (BLE 5.0, compact version of nRF52840)
  Thin-film battery: 20 mAh flexible LiPo (EFC batteries)
    OR: Qi wireless charging from smartwatch
  Connector: 8-pin magnetic pogo-pin (to disposable patch)

Calibration:
  Factory: each patch batch calibrated against NaCl + KCl + lactate standards
    Calibration coefficients stored in NFC tag on patch (ISO 15693)
  In-sweat recalibration: algorithm accounts for sweat rate effects
    Using short-channel reference electrode closer to skin surface

Interpretation model:
  Sweat ≠ blood (direct correlation not possible)
  Mapping relationships used:
    Sweat Na⁺ > 60 mM → possible CF (cystic fibrosis screening threshold)
    Lactate > 20 mM → high exercise intensity / anaerobic threshold crossing
    K⁺ trend → hydration status proxy
    pH < 5.0 → high sweat rate, acidic output
    Cortisol elevation → stress event correlation (immunoassay add-on variant)
```

**BOM: ~$95 (reader module ~$65 + 3-pack disposable patches ~$30)**

---

### NFSIM-CHEM-01 — Portable Blood Chemistry Analyzer

**Full Specifications:**

| Parameter | Value |
|---|---|
| Sample type | Capillary whole blood (fingerstick) |
| Sample volume | 15–50 µL |
| Cartridge type | Single-use disposable, bar-coded (1D barcode) |
| Analyte panels | Basic Metabolic (10 analytes), Liver (8), Renal (6), Lipid (5) |
| Time to result | 2–4 minutes |
| Accuracy target | ±10% CV vs reference laboratory |
| Detection methods | ISE (ions) + amperometric (enzymes) + photometric (bilirubin, Hgb) |
| Display | 3.5" color TFT |
| Connectivity | BLE 5.0 + USB-C |
| Battery | 3000 mAh |
| Battery life | 100+ tests per charge |
| Dimensions | 140 × 70 × 30 mm |
| Weight | 350 g |
| UBERON | UBERON:0000178 (blood) |

**Cartridge Design:**

```
Physical format: polycarbonate card, 85×54×2 mm (credit card size)
  Sample inlet: 15 µL capillary blood applied to inlet well
  Capillary distribution: passive wicking to all reagent zones
  Separate lanes per analyte (15 parallel microfluidic channels)
  
  Electrochemical zones (ISE):
    Sodium: glass membrane ISE (printed)
    Potassium: valinomycin ionophore membrane (screen-printed)
    Chloride: AgCl membrane
    CO₂/HCO₃⁻: pCO₂ electrode (gas-permeable membrane + pH sensing)
    Electrode contacts: carbon + Ag/AgCl screen-printed traces
    
  Enzymatic amperometric zones:
    Glucose: GOx + Prussian Blue on carbon
    Creatinine: creatinine iminase + glutamate dehydrogenase (GLDH) cascade
    Lactate: LOx + ferrocene mediator
    BUN/urea: urease + NH₃ detection amperometric
    
  Photometric zones:
    Bilirubin: diazo reagent dried pad, read at 540 nm
    Hemoglobin: hemoglobin-specific chromogen, read at 540 nm
    Total protein: biuret reagent, read at 545 nm
    ALT / AST: NADH consumption, UV read at 340 nm (LED)
    Cholesterol: oxidase-peroxidase colorimetric, 540 nm
    Triglycerides: GPO-POD method, 540 nm
    
  Barcode: Code 128, encodes: cartridge type, lot number, calibration coefficients
    Reader: linear CCD barcode scanner (integrated in reader unit)
  
  Storage: hermetically sealed foil pouch with silica desiccant
  Shelf life: 12 months at 2–8°C / 3 months at room temperature
  Cost target per cartridge: $8–15 (basic metabolic panel)

Reader Electronics:
  Cartridge slot: edge connector (32-pin) contacts electrochemical zones
  Optical module: 
    LEDs: white + UV (375 nm) LED array, 6 wavelengths
    Photodiode array: OPT3001 ambient-corrected + Si photodiode per lane
    Bandpass filters: 6× per photometric lane
  Potentiostat array: 8× LMP91000 in parallel (8 electrochemical channels)
    Multiplexer: ADG1414 (8-channel, SPI-controlled) for sequential ISE readout
  Incubation heater: aluminum block with embedded resistive heater, 37°C ± 0.5°C
  MCU: STM32H743 (main computation, result processing)
  BLE: nRF52840
  Display: ILI9486 3.5" TFT (320×480)
```

**BOM: ~$185 reader + $8–15/cartridge**

---

### NFSIM-CHEM-02 through NFSIM-CHEM-08 Summary Specifications

**NFSIM-CHEM-02 — Saliva Chemistry Analyzer**
```
Sample: passive drool, 1 mL into sample cup
Analytes: cortisol, alpha-amylase, glucose, uric acid, nitrite, pH, Na⁺, total protein
Method: competitive ELISA (cortisol) + enzymatic (amylase) + ISE (Na⁺, pH)
Reader: same base unit as NFSIM-CHEM-01 (compatible cartridge slot)
UBERON: UBERON:0001836 (saliva)
BOM: ~$80 reader + $6–12/cartridge
```

**NFSIM-CHEM-03 — Urine Dipstick Smart Reader**
```
Hardware: OV5640 5MP camera + white LED + calibration card + STM32H7
Compatible strips: Combur-Test, Multistix 10, Siemens Clinitek strips
Parameters: glucose, protein, ketones, blood, bilirubin, urobilinogen, nitrite, WBC, pH, SG, creatinine
AI: per-pad color analysis (HSV space → LUT comparison) with quality check
Output: 14-parameter panel + invalid/expired strip detection
UBERON: UBERON:0001088 (urine)
BOM: ~$55 reader (strips from pharmacy, $0.30–1.50 each)
```

**NFSIM-CHEM-04 — Portable Lipid Panel Analyzer**
```
Sample: 40 µL whole blood (fingerstick)
Analytes: TC, LDL-C (direct or Friedewald), HDL-C, TG, non-HDL-C
Method: enzymatic colorimetric microfluidic cartridge
Accuracy: NCEP guidelines (<3% CV, <3% bias)
Time: 3 minutes
UBERON: UBERON:0000178 (blood) + UBERON:0004537 (systemic lipid)
BOM: ~$120 reader + $4–8/cartridge
```

**NFSIM-CHEM-05 — Portable Lactate Meter**
```
Chemistry: amperometric LOx on disposable strip (same principle as glucose meter)
Sample: 1.5 µL capillary blood (fingerstick)
Range: 0.5–30 mmol/L
Accuracy: ±0.3 mmol/L at <5 mmol/L; ±5% above 5 mmol/L
Time to result: 15 seconds
Display: OLED 0.96" + BLE output
UBERON: UBERON:0000178
BOM: ~$45 meter + $0.50/strip (in packs of 25)
```

**NFSIM-CHEM-06 — Ketone / BHB Monitor**
```
Chemistry: amperometric beta-hydroxybutyrate dehydrogenase (BHB-DH)
Sample: 0.8 µL capillary blood
Range: 0.1–8.0 mmol/L BHB
Time: 10 seconds
UBERON: UBERON:0000178
BOM: ~$35 meter + $0.60/strip
```

**NFSIM-CHEM-07 — Cortisol / Stress Hormone Sensor**
```
Method: competitive ELISA on microfluidic cartridge
Sample: 50 µL saliva (unstimulated)
Range: 0.5–60 nmol/L (covers physiological diurnal variation)
Time: 15 minutes (antibody incubation)
UBERON: UBERON:0001836 (saliva) → UBERON:0002369 (adrenal cortex)
Diurnal protocol: measure at wake + noon + 4pm + bedtime → 4-point cortisol curve
BOM: ~$90 reader + $10/cartridge
```

**NFSIM-CHEM-08 — Continuous Subcutaneous Lactate Sensor**
```
Working electrode: platinum 127 µm wire (same as CGM-01 core)
Enzyme: LOx (lactate oxidase) crosslinked with BSA + glutaraldehyde
Membrane stack: polyurethane outer + Nafion inner (same design as CGM-01)
Applied potential: +0.5V vs Ag/AgCl
Sensitivity: 0.5–1 nA per mmol/L (calibrated vs plasma lactate)
Range: 0.5–25 mmol/L
Wear: 3–7 days target (shorter than glucose — enzyme instability)
Transmitter: nRF52840 + LMP91000 (same as CGM-01 PCB with revised calibration)
Applications: exercise physiology, ICU critical care, sepsis monitoring
UBERON: UBERON:0001175 (subcutaneous interstitial fluid)
BOM: ~$55 (sensor + transmitter unit)
```

---

### NFSIM-OXY-01 — Multi-Site NIRS Tissue Oxygenation Array

**Full Specifications:**

| Parameter | Value |
|---|---|
| Optode count | 4–8 independent modules |
| Wavelengths | 730 nm + 850 nm (±2 nm) |
| Depth sensitivity | 10–25 mm |
| Source-detector distance | 30–40 mm (deep) + 12–15 mm (shallow reference) |
| Output metrics | rSO₂ %, ΔHbO₂ (µM·mm), ΔHHb (µM·mm), HbDiff |
| Sampling rate | 1 Hz per module |
| Wireless | BLE 5.0 per module |
| Battery per module | 1000 mAh |
| Battery life | 8 h per charge |
| Module dimensions | 35 × 15 mm |
| IP rating | IPX4 |
| UBERON | Application-specific (brain, muscle, tumor) |

**Hardware Architecture:**

```
Optode Module (per site):
  Light sources:
    730 nm LED: Osram SFH4544 (5 mW, ±15° half-angle, SMD)
    850 nm LED: Osram SFH4547 (5 mW, SMD)
    LED modulation: square wave, 1 kHz (for lock-in detection)
    Two LEDs per source position → both wavelengths from same point
  Detector:
    Si photodiode: Hamamatsu S2387-33R (3×3 mm active area)
      OR: OPT101 (monolithic photodiode + amplifier, integrated)
    Transimpedance amplifier: OPA2134 (10 MΩ feedback, low noise)
    Two detector positions:
      Short (12 mm from source): captures superficial signal (skin + skull)
      Long (35 mm from source): captures deep signal (brain cortex or muscle)
  
  Signal processing:
    ADC: ADS1220 (24-bit, SPI, 4-channel differential, 2 kSPS)
    Lock-in demodulation (software):
      Synchronous demodulation at 1 kHz reference frequency
      Extracts signal at modulation frequency → removes ambient light contribution
    Modified Beer-Lambert computation:
      ΔOD(λ) = OD_long(λ) − k × OD_short(λ)  [short-channel regression]
      ΔHbO₂ = [ε_HHb(850)·ΔOD(730) − ε_HHb(730)·ΔOD(850)] / Δ_det
      ΔHHb  = [ε_HbO₂(730)·ΔOD(850) − ε_HbO₂(850)·ΔOD(730)] / Δ_det
      Where: Δ_det = ε_HbO₂(730)·ε_HHb(850) − ε_HbO₂(850)·ε_HHb(730)
      DPF (Differential Pathlength Factor): brain = 6.26, muscle = 4.16
      rSO₂ = HbO₂/(HbO₂+HHb) × 100%

  MCU: STM32L4R5 (low power, 120 MHz Cortex-M4)
  BLE: nRF52811 (small, BLE 5.0)
  Battery: 1000 mAh LiPo
  Wireless charging: Qi 5W receiver coil

Adhesive base:
  Dual-layer foam pad: outer black (light-blocking) + inner skin-contact foam
  LED and detector positioned precisely in foam (4 mm from foam face)
  Pre-applied hydrogel coupling (improves optical contact)

Multi-site hub (optional):
  Central device aggregates 4–8 optode modules
  Displays all sites simultaneously with color-coded body map overlay
  Triggers synchronized measurement across all modules
```

**BOM: ~$180 (for 4-module system)**

---

### NFSIM-BREATH-01 — Portable Breath Metabolomics Device

**Full Specifications:**

| Parameter | Value |
|---|---|
| Primary analytes | Acetone, isoprene, ethanol, ammonia, H₂, CO, NO, H₂S |
| Detection technologies | MOX e-nose array (broad) + photoacoustic cell (specific) |
| Acetone detection range | 0.1–1000 ppm |
| Isoprene range | 10–2000 ppb |
| NH₃ range | 0.1–100 ppm |
| NO range | 1–500 ppb (photoacoustic, asthma FeNO) |
| H₂ range | 1–1000 ppm |
| Sampling mode | Single forced exhale (5–10 sec through mouthpiece) |
| Warm-up time | 30 seconds |
| Connectivity | BLE 5.0 + USB-C |
| Battery | 1200 mAh |
| Battery life | 200 tests per charge |
| Dimensions | 100 × 55 × 30 mm |
| Weight | 180 g |
| UBERON | UBERON:0001707 (lung/exhaled air) |

**Hardware Architecture:**

```
Breath Collection System:
  Mouthpiece: single-use disposable, standard 22mm ID connector
  Breath valve: one-way valve (exhale in → inhale prevented)
  Sample chamber: 10 mL Teflon-coated collection cell
  Flow meter: MEMS differential pressure sensor (SDP810 by Sensirion)
    Detects breath flow, triggers sampling at alveolar fraction (discard first 30%)
    Alveolar sample: last 150–200 mL of exhale (true alveolar air)
  Dehumidifier: Nafion tube (permselective water membrane)
    Removes water vapor (interferes heavily with MOX sensors)
    H₂O removal: >95% at 0.5 L/min flow rate
  Micro-pump: diaphragm pump (KPV14 Schwarzer, 50 mL/min)
    Pulls dehumidified breath sample through sensor array
  Calibration capsule: sealed CO₂/N₂ reference gas capsule (1000 uses lifespan)
    Baseline correction: sample reference gas before each test

Metal Oxide Sensor (MOX) Array:
  8 sensors with different metal oxide compositions and operating temperatures:
  1. SnO₂ pure (350°C): general VOC, alcohols
  2. SnO₂ + Pd dopant (350°C): H₂ selective
  3. SnO₂ + Pt dopant (300°C): CO selective
  4. ZnO (400°C): H₂S sensitive
  5. WO₃ (400°C): NO₂ / NO sensitive
  6. In₂O₃ (300°C): ozone / oxidizers
  7. TiO₂ (500°C): broad spectrum, high-temperature stability
  8. SnO₂ + Cr₂O₃ (300°C): ethanol vs. acetone discriminator
  Commercial option: Sensirion SGP41 (MOX array, 4-channel, built-in H₂/VOC sensing)
  Heater control: PWM temperature regulation per sensor (MOSFET per sensor)
  ADC: ADS1115 × 2 (16-bit, 8 channels, I2C)
  Response time: 5–30 sec to stable reading

Photoacoustic Spectroscopy (Acetone / NO specific):
  Light source: 3.3 µm Quantum Cascade Laser (acetone C=O stretch absorption)
    OR: 5.3 µm for NO (N=O stretch)
    OR: broadband mid-IR LED (less specific, less sensitive)
    Compact QCL module: Alpes Lasers (5mm × 5mm × 3mm package, 1mW CW)
  Acoustic cell: Helmholtz resonator (cylindrical, Q=50)
    Resonant frequency: 1 kHz (laser modulated at Helmholtz resonance)
    Cell volume: 1 mL, gold-lined reflective walls
  Microphone: MEMS (Vesper VM1010 or Knowles SPH0641LU4H-1)
    Placed in Helmholtz neck → maximum sensitivity at resonant frequency
  Lock-in detection: software, reference = laser modulation frequency
  Sensitivity: acetone <0.5 ppm; NO <5 ppb

Signal Interpretation AI (on-device, STM32H7):
  MOX 8-sensor vector → PCA → 2D feature space
  Pre-trained classifier (TFLite Micro, 30 KB INT8):
    Classes: normal_breath, high_acetone (>1.8 ppm, ketosis), high_isoprene,
      high_H2 (SIBO), high_NH3 (possible renal), high_ethanol, infection_pattern
  Confidence score output per class
  Photoacoustic: quantitative ppm reading (independent of MOX array)
  
Mouthpiece hygiene:
  Disposable cardboard/plastic mouthpiece (standard ISO 23747 compatible)
  Anti-bacterial filter: 0.22 µm HEPA pre-filter in breath inlet
  Device self-cleaning: purge with clean air 60s after test
```

**BOM: ~$210**

---

## 12. Hardware Domain D — Electrical / Bioelectric

### Complete Device List

| Device ID | Name | Technology | BOM Target |
|---|---|---|---|
| NFSIM-ECG-01 | Single-Lead ECG Patch (30-day) | ADS1291 + nRF52840, dry electrodes | ~$38 |
| NFSIM-ECG-02 | 12-Lead ECG Vest (24-48h) | ADS1298 × 2, textile electrodes | ~$145 |
| NFSIM-ECG-03 | 3-Lead Holter Patch (30-day) | ADS1294, 30-day recording | ~$52 |
| NFSIM-EEG-01 | Dry-Electrode EEG Headset (8–16ch) | ADS1299 × 2, spring-pin dry | ~$180 |
| NFSIM-EEG-02 | 64-Channel Wet EEG Research System | ADS1299 × 8, clinical cap | ~$420 |
| NFSIM-EEG-03 | Around-Ear EEG (cEEGrid style) | ADS1299, discreet behind-ear | ~$95 |
| NFSIM-EMG-01 | 8-Channel Surface EMG Armband | ADS1298, gesture recognition | ~$115 |
| NFSIM-EMG-02 | Single-Channel EMG Patch | ADS1291, muscle fatigue | ~$35 |
| NFSIM-NEURAL-01 | High-Density ECoG Research Array | Parylene-C, Intan RHD2132 × 8 | ~$650 |
| NFSIM-NEURAL-02 | Intracortical Recording Headstage | Intan RHD2132, Open Ephys compatible | ~$380 |
| NFSIM-EOG-01 | Electrooculography Sensor Glasses | ADS1299, periorbital electrodes | ~$88 |
| NFSIM-EDA-01 | Electrodermal Activity Wrist Sensor | ADS1256, 500mV AC, wristband | ~$42 |

### NFSIM-ECG-01 — Single-Lead ECG Patch (30-Day Continuous)

**Full Specifications:**

| Parameter | Value |
|---|---|
| Lead configuration | Single-lead (modified Lead II equivalent) |
| Electrode type | Dual dry Ag/AgCl + optional gel pad (snap-on) |
| ADC resolution | 24-bit |
| Sampling rate | 256 Hz (or 512 Hz, configurable) |
| Bandwidth | 0.05–150 Hz |
| CMRR | >105 dB |
| Input impedance | >1 GΩ (ADS1291 specification) |
| Noise floor | 4 µVRMS input-referred (0.5–150 Hz) |
| Wear duration | 14–30 days |
| Battery | 200 mAh LiPo (sealed) |
| Battery life | 21 days continuous at 256 Hz, 5-min BLE advertising |
| Connectivity | BLE 5.0 (alert streaming) + 8 GB flash (local log) |
| Dimensions | 65 × 35 × 7 mm |
| Weight | 12 g |
| IP rating | IPX7 (30 min at 1 m submersion) |
| AI on-device | AFib detection >99% sensitivity, pause, brady/tachy |
| UBERON | UBERON:0000948 (heart) |

**Hardware Architecture:**

```
Electrode Design:
  Primary electrodes: integrated into device bottom face
    Material: AgZn sintered (commercial) or Au-coated PCB pads
    Dimension: 10 × 5 mm pads, 35 mm inter-electrode spacing
    Dry contact: suitable for chest placement through shirt fabric at rest
  Gel electrode pads (accessory): Ag/AgCl hydrogel snap-on pads
    Snap connector: 3.5 mm male snap (standard electrode snap)
    Improves impedance from ~100 kΩ dry → ~5 kΩ with gel
    Disposable after 14 days

ECG AFE (Analog Front End):
  Texas Instruments ADS1291:
    1-channel ECG AFE, 24-bit sigma-delta ADC
    Input-referred noise: 4 µVRMS (0.5–150 Hz bandwidth)
    CMRR: >105 dB (typ)
    Input impedance: >1 GΩ
    Programmable gain: 1–12×
    Integrated Wilson Central Terminal (WCT) for virtual lead reference
    Right Leg Drive (RLD): outputs amplified common-mode → drives body to virtual ground
    SPI interface to MCU
    Lead-off detection: AC current injection method (detects electrode detachment)
    Power down modes: <0.7 µA in shutdown
    Power consumption: 300 µA in full active mode

MCU:
  Nordic nRF52840 (Cortex-M4F, 64 MHz, BLE 5.0):
    On-device DSP: hardware FPU for filtering algorithms
    R-peak detection: Pan-Tompkins algorithm (350 µs computation per sample)
    HRV: RMSSD, pNN50 computed per 5-minute segment
    QRS morphology: template matching for beat classification
    TFLite Micro (AFib classifier):
      Input: 60-second RR-interval sequence → 17 features
      Architecture: LSTM × 2 + Dense, INT8 quantized
      Model size: 20 KB
      Inference: every 5 minutes
      Outputs: {normal_sinus, afib, flutter, pvcs, artifact} with confidence
    BLE GATT server:
      NFS ECG streaming characteristic (notify, 244 bytes)
      Sends compressed: RR-interval sequence + AFib probability per 30s segment
    Power management:
      Sleep between samples (250 µA → 5 µA between ADC reads)
      Effective average: ~700 µA (continuous recording + 5-min BLE intervals)

Storage:
  W25Q64JV (8 MB NOR flash):
    Stores 30 days × 250 Hz × 24-bit = 30 × 86400 × 3 bytes = 7.78 GB
    Requires: delta encoding (ECG baseline subtraction → <50% of raw size)
    Effective storage: 8 MB stores ~14 days at 256 Hz with delta encoding
    Extended option: 128 MB flash (ISSI IS25LP128) for 30-day storage

Battery and Charging:
  200 mAh LiPo (3.7V), hermetically sealed inside device
  Non-user-replaceable: designed for 30-day disposable lifecycle
  Charge circuit: MCP73831 (USB-C, 100 mA charge rate → 2h to full)
  Fuel gauge: MAX17048 (I2C, SOC + low-battery alert)
  Energy calculations:
    700 µA × 3.7V = 2.59 mW average
    200 mAh / 0.70 mA = 286 hours = 11.9 days at full recording + continuous BLE
    Power down BLE to advertise only every 5 min → extends to ~21 days
    Alert mode: wakes BLE immediately on arrhythmia detection (event-driven)

Housing:
  TPU (thermoplastic polyurethane) overmold: flexible, skin-comfortable
  IPX7: sealed with silicone gaskets around USB-C port
  Adhesive: 3M 1585N (breathable, extended-wear medical tape)
    Pre-applied: peel-and-stick application (no gel prep)
    Additional adhesive patch replaceable at 14 days for 30-day wear

Sync Protocol:
  Weekly sync: user holds phone near patch → BLE connection → bulk data dump
  Full waveform download: all stored ECG → DICOM Holter ECG export
  Alert: immediate BLE advertising when arrhythmia detected
    Alert range: standard BLE 10m → phone app receives notification
  NFS JSON output per session end (or weekly dump):
    {data_type: "ecg_continuous", duration_days, arrhythmia_events[], hrv_summary, raw_data_ref}
```

**BOM:**

| Component | Cost |
|---|---|
| nRF52840-QIAA | $4.50 |
| ADS1291IPWR | $5.80 |
| MAX17048G+T | $2.10 |
| MCP73831T-2ATI | $0.55 |
| W25Q64JV (8MB) | $0.55 |
| PCB (4-layer, ENIG) | $8.00 |
| 200mAh LiPo | $4.50 |
| TPU overmold (mold amortized) | $3.00 |
| Adhesive (3M 1585N, per device) | $1.50 |
| NFC tag (NXP NTAG213) | $0.35 |
| Passives, connectors | $2.50 |
| Dry electrode material | $1.50 |
| USB-C + charging components | $1.50 |
| **Total** | **~$36.35** |

---

### NFSIM-ECG-02 — 12-Lead ECG Vest (24–48h)

**Full Specifications:**

| Parameter | Value |
|---|---|
| Lead count | 12-lead equivalent (Wilson Central Terminal reference) |
| Electrode count | 10 positions (RA, LA, RL, LL, V1–V6) |
| Electrode material | Silver-coated conductive textile (Shieldex) |
| ADC resolution | 24-bit, 8-channel |
| Sampling rate | 1000 Hz per lead |
| Recording module | Detachable electronics pod (waist-mounted) |
| Storage | 32 GB microSD |
| Battery life | 24–48h continuous |
| Connectivity | BLE 5.0 + USB-C data export |
| Garment washable | Yes (remove electronics pod) |
| Sizes | XS–4XL, male/female anatomical variants |
| UBERON | UBERON:0000948 (heart) |

**Hardware Architecture:**

```
Garment Design:
  Base fabric: medical-grade compression fabric (polyester 80% + spandex 20%)
    Choose: Ambiance or equivalent breathable medical textile
    Compression: 15–25 mmHg for secure electrode contact
  
  Electrode pads: 10 positions per 12-lead system
    Material: Shieldex 130 silver-plated nylon (50 dB shielding at 1 MHz)
    Size: 30×30 mm (limb leads), 20×20 mm (precordial V1–V6)
    Conductive sewing: Shieldex thread connecting electrode pads to snap connectors
    Snap connectors: gold-plated 3.5mm snaps at waist level → connect to electronics
  
  V1–V6 precordial positions: anatomically marked in garment
    V1: Right of sternum, 4th ICS (intercostal space)
    V2: Left of sternum, 4th ICS
    V3: Between V2 and V4
    V4: 5th ICS, midclavicular line
    V5: 5th ICS, anterior axillary line
    V6: 5th ICS, midaxillary line
  
  Lead routing: conductive textile traces within fabric channels → waist snap array
    Trace resistance target: <5 Ω per electrode-to-connector path

Electronics Pod:
  ADS1298 (Texas Instruments, 8-channel 24-bit ECG AFE):
    8 channels: simultaneously samples all 8 differential lead pairs
    CMRR: >80 dB
    Noise: 8 µVpp at 1000 Hz bandwidth
    SPI interface, 1000 SPS per channel (1000 Hz output data rate)
    Wilson Central Terminal (WCT): configured in firmware using RA, LA, LL averages
    Right Leg Drive (RLD): driven from WCT to reduce common-mode
    Two ADS1298 in daisy-chain → 16 total channels (12 ECG + 4 spare)
    
  STM32H743 MCU:
    Cortex-M7, 480 MHz, 1MB flash
    Processes all 12 leads simultaneously
    12-lead ECG analysis: Rhythm classification + ST deviation + QRS morphology
    AI: LightGBM or neural network for arrhythmia detection across all 12 leads
    
  microSD (32 GB):
    48h × 12 leads × 1000 Hz × 24-bit = 48 × 3600 × 12 × 1000 × 3 bytes = 6.2 TB
    Compressed with delta-encoding: ~90% compression for ECG → ~620 GB → too large
    Solution: record at 500 Hz → 310 GB → still large
    Practical: record at 250 Hz per lead → 78 GB for 48h → manageable at 32GB for 24h
    OR: store only RR intervals + arrhythmia events + hourly template → full replay mode
    
  Connectivity: BLE for real-time alert + USB-C for full data download post-wear
  Battery: 800 mAh LiPo (48h @ ~18 mA average draw)
```

**BOM: ~$145 electronics + $35 garment (per size) = ~$180 system**

---

### NFSIM-ECG-03 — 3-Lead Holter Patch (30-Day)

```
Similar to NFSIM-ECG-01 but with 3 electrodes (Lead I, II, III triangulation)
  → More information than single-lead: can detect axis deviation
AFE: ADS1294 (4-channel, 24-bit, enables 3-lead + RLD)
Storage: 32 GB eMMC (30 days × 3 leads × 512 Hz × 24-bit = 14.2 GB → fits with encoding)
UBERON: UBERON:0000948
BOM: ~$52
```

---

### NFSIM-EEG-01 — Dry-Electrode EEG Headset (8–16 Channel)

**Full Specifications:**

| Parameter | Value |
|---|---|
| Electrode count | 8 channels (expandable to 16 via Daisy board) |
| Electrode type | Spring-loaded gold-tipped dry pins |
| Electrode positions | 10-20 system subset: Fp1, Fp2, F3, F4, C3, C4, P3, P4 |
| Reference | CMS/DRL (Common Mode Sense / Driven Right Leg) ear clips |
| ADC resolution | 24-bit |
| Sampling rate | 250 Hz (up to 16 kSPS per channel) |
| Input impedance | >1 GΩ (ADS1299) |
| Noise floor | 1 µVRMS (0.5–100 Hz) |
| CMRR | >110 dB |
| Wireless | BLE 5.0 + 2.4 GHz proprietary (OpenBCI dongle compatible) |
| Battery | 1200 mAh |
| Battery life | 8 h |
| Compatible software | OpenBCI GUI, BrainFlow SDK, MNE-Python, EEGLAB |
| Dimensions | Adjustable headset, 54–60 cm head circumference |
| Weight | 180 g |
| UBERON | UBERON:0001017 (brain, CNS) |

**Hardware Architecture:**

```
Dry Electrode Design:
  Gold-tipped spring-loaded pin electrodes:
    Core: 3mm diameter stainless steel shaft, 20mm length
    Tip: electrodeposited gold (30 µm thickness, ISO biocompatible)
    Spring: stainless steel coil, 15N/m stiffness (appropriate scalp contact force)
    Comb tip: 5-point gold star (penetrates hair, contacts scalp)
    Impedance with hair: 50–200 kΩ (acceptable for ADS1299 >1 GΩ input impedance)
  
  Headset frame:
    Adjustable plastic arc (polycarbonate)
    Electrode arms: spring-loaded, position-adjustable (10-20 positions marked)
    Ear clip reference: Ag/AgCl coated, spring-loaded
    Cable routing: shielded wire from each electrode to PCB

EEG AFE:
  Texas Instruments ADS1299-8 (8-channel 24-bit EEG SoC):
    8 fully differential inputs → 8 EEG channels
    On-chip PGA: 1–24× gain (set to 24× for µV signals)
    Noise: 1 µVRMS input-referred (3 nV/√Hz at 24× gain)
    Input impedance: 1 GΩ (critical for dry electrode compatibility)
    CMRR: >110 dB with SRB (Single-ended Right Bias) reference scheme
    Bias drive (Driven Right Leg): feeds amplified common-mode → scalp
      Dramatically improves CMRR: additional 30–40 dB
    Integrated Wilson Central Terminal output
    SPI interface: 32 MHz clock compatible
    Multi-readback rate: 250 SPS (configured) up to 16,000 SPS
    Daisy chain: 2× ADS1299 → 16 channels (Daisy board add-on)

  OpenBCI Cyton compatibility mode:
    Firmware mode: mimics OpenBCI Cyton SPI protocol
    Enables use with: OpenBCI GUI, Neurosity SDK, BrainFlow library
    Maintains open-source compatibility across all major EEG software platforms

  MCU: STM32H743 (main processing + SPI interface to ADS1299)
  BLE: nRF52840 (streaming to phone/PC)
    BLE 5.0, PHY 2M mode: 2 Mbps → sufficient for 16ch × 250 Hz × 24-bit = 96 kbps
  USB: USB-C → USB-CDC → stream raw data to PC (for wired high-bandwidth operation)

Impedance monitoring:
  Injected AC current (5 nA, 31 Hz) into each electrode channel
  Measure resulting voltage → calculate impedance
  ADS1299 built-in impedance measurement feature
  Display: smartphone app shows per-electrode impedance
    Green <10 kΩ (excellent), Yellow 10–50 kΩ (acceptable), Red >50 kΩ (reposition)
  Critical for dry electrode usability: guides user to adjust electrode position

AI/BCI features (on phone or PC, not on device):
  MNE-Python: preprocessing, ICA artifact removal
  Sleep staging: SleepTransformer model (open-source, GitHub)
  Motor imagery BCI: ERD/ERS (Event-Related Desynchronization/Synchronization)
  SSVEP BCI: 6 Hz, 8 Hz visual flicker detection
  P300 speller: single-trial detection using LDA or XDAWN
```

**BOM: ~$180**

---

### NFSIM-EEG-02 — 64-Channel Wet EEG Research System

```
Electrodes: 64× Ag/AgCl cup electrodes + conductive gel (same as clinical systems)
Cap: standard EEG cap (Easycap or Brain Products compatible sizing)
AFE: 8× ADS1299-8 (8 chips × 8 channels = 64 channels, SPI daisy chain)
Sampling: 1000 Hz per channel (research standard)
Amplifier box: 120×80×30mm, battery-powered, USB-C data + power
Isolation: patient-isolated (IEC 60601-1 compliant design)
Software: Open Ephys compatible (NFSIM custom plugin)
BOM: ~$420 amplifier + $85 cap
```

---

### NFSIM-EEG-03 — Around-Ear EEG (cEEGrid Style)

```
Concept: Discreet behind-ear electrode arrays for continuous ambulatory EEG
Electrode array: 10 electrodes per ear (cEEGrid layout), flexible polyimide substrate
AFE: ADS1299 (4 channels per ear = 8 total)
Worn like earphones: rigid behind-ear housing, flexible electrode array rests on mastoid
Resolution: lower than full EEG, but suitable for sleep staging, alertness monitoring
BOM: ~$95
```

---

### NFSIM-EMG-01 — 8-Channel Surface EMG Armband

**Full Specifications:**

| Parameter | Value |
|---|---|
| Channels | 8 bipolar surface EMG channels |
| Electrode spacing | 45° radial intervals around forearm |
| Electrode type | Dry AgZn or conductive silicone |
| ADC resolution | 16-bit |
| Sampling rate | 2000 Hz |
| Bandwidth | 20–500 Hz |
| Gain | 60–80 dB |
| IMU | 9-axis (3-axis accel + gyro + mag) — ICM-42688-P |
| Wireless | BLE 5.0 |
| Battery | 500 mAh |
| Battery life | 6–8 h streaming |
| Gesture recognition | 8-class, on-device TFLite, <10ms latency |
| Circumference range | 200–400 mm (adjustable elastic band) |
| Weight | 90 g |
| UBERON | UBERON:0001134 (skeletal muscle, forearm) |

**Hardware Architecture:**

```
Electrode Array:
  8 bipolar electrode pairs (16 electrodes total):
    Each pair: 2 electrodes 20mm apart, aligned with forearm axis
    Electrode pods: 8 rigid pods, each 15×20mm, containing electrode pair
    Material: conductive silicone (carbon-loaded) or sintered AgZn
    Contact area: 10×10 mm per electrode (good current distribution)
    Common reference: 9th electrode (optional, at wrist bony prominence)

Electronics:
  ADS1298 (8-channel 24-bit, TI):
    8 simultaneous differential EMG channels at 2000 SPS
    Input bandwidth: 20–500 Hz (set via on-chip digital filter)
    Programmable gain: 12× (default for EMG amplitude range)
    Noise: 8 µVpp input-referred (20–500 Hz)
    SPI interface: 32 MHz
  IMU: ICM-42688-P (TDK InvenSense, 6-axis)
    Accelerometer: ±16g, 100 Hz
    Gyroscope: ±2000°/s, 100 Hz
    SPI interface
  MCU: nRF52840 (STM32H7 for production-level processing)
    Real-time EMG processing: RMS per channel (200ms window, updated every 50ms)
    Feature extraction: MAV, WL, ZC, SSC per window
    TFLite Micro inference: 8-class gesture model (50 KB INT8)
      Gestures: open hand, closed fist, wrist extension, wrist flexion,
                radial deviation, ulnar deviation, pinch (index+thumb), point
      Accuracy: >90% on trained user, ~70% cross-user without personalization
    Personalization mode: 10 reps per gesture → fine-tune softmax layer on-device
  BLE: nRF52840 integrated
    Streaming raw: 2000 Hz × 8ch × 16-bit = 256 kbps (BLE 2M PHY can handle)
    Streaming features: 20 Hz update with gesture + confidence + raw RMS per ch

Prosthetic control interface:
  Output via BLE → prosthetic limb controller receives gesture class
  Latency: EMG → classification → BLE TX = <10ms (critical for natural control)
  Compatible: Open Bionics Hero Arm (custom BLE receiver), Ottobock BeBionic (via adapter)
```

**BOM: ~$115**

---

### NFSIM-EMG-02 — Single-Channel EMG Patch

```
Single bipolar EMG channel, dry electrodes
AFE: ADS1291 (1-channel, 24-bit)
Target: chronic muscle fatigue monitoring, prosthetic control input
Adhesive patch format: 50×25mm, IPX7
BOM: ~$35
```

---

### NFSIM-NEURAL-01 — High-Density ECoG Research Array

**Full Specifications:**

| Parameter | Value |
|---|---|
| Electrode count | 64–256 |
| Geometry | 8×8 (64ch) or custom 16×16 (256ch) grid |
| Electrode material | Iridium oxide (IrOx) or PEDOT:PSS coated Pt-Ir |
| Electrode diameter | 200 µm active area |
| Inter-electrode spacing | 400 µm (dense) or 1 mm (standard) |
| Substrate | Parylene-C, 8–10 µm total thickness |
| Trace material | Gold, 2 µm thick, 100 µm wide |
| ADC resolution | 16-bit |
| Sampling rate | 30,000 Hz (spike band) or 1000 Hz (LFP) |
| Bandwidth | 0.1 Hz – 15 kHz |
| Input noise | 0.98 µVRMS (300 Hz – 10 kHz) |
| Acquisition system | Open Ephys compatible (Intan RHD2132) |
| Sterilization | EtO or autoclave (array) |
| UBERON | UBERON:0001017 (brain surface, neocortex) |

**Hardware Architecture:**

```
Flexible Array Fabrication:
  Substrate: Parylene-C deposition (CVD process, PDS2010)
    Base coat: 5 µm Parylene-C
    Metal layer: Ti adhesion (20 nm) + Au electrode (2 µm), patterned via photolithography
    Insulation: 3 µm Parylene-C
    Via etch: O₂ plasma through insulation at electrode sites
    Electrode coating: IrOx electrodeposition (50 mC/cm² charge) OR
      PEDOT:PSS: electropolymerization from 10 mM EDOT + 0.1M NaPSS
        Reduces impedance from ~1 MΩ → <100 kΩ at 1 kHz
    Connector: ZIF (Zero Insertion Force), 256-pin, 0.3 mm pitch
  
  Alternative (lower cost): Kapton PCB flex array
    Substrate: Kapton (polyimide), 25 µm
    Electrodes: Pt-Ir electrodeposited on gold pads
    Trace: copper (1 oz, etched)
    Insulation: PI coverlay
    Suitable for acute (non-chronic) use

Acquisition Headstage:
  Intan RHD2132 amplifier chips:
    32 channels per chip (16-bit, 0.98 µVRMS, 0.1–10,000 Hz)
    SPI interface (daisy-chainable up to 16 chips = 512 channels)
    Integrated impedance measurement (1 kHz injected current)
    Power: 3.3V, ~1.5 mA per chip (48 mW for 32-channel chip)
  For 256-channel array: 8× RHD2132 chips
    All connected in SPI daisy chain → single FPGA interface
  
  FPGA controller (Open Ephys compatible):
    Xilinx Artix-7 (Digilent Genesys 2 or Nexys Video)
    Open Ephys FPGA firmware (GitHub: open-ephys/rhythm)
    USB 3.0: 256ch × 30 kHz × 16-bit = 122 Mbps → USB 3.0 capable
    Real-time data stream → Open Ephys GUI acquisition software

Open Ephys GUI:
  Python-based open-source neural data acquisition
  Plugins: spike detector, LFP viewer, event detector, online spike sorter
  Export: binary NWB 2.0 (Neurodata Without Borders) format
  Post-processing: Kilosort 2/3 (spike sorting), Phy (manual curation)
  NanoFlowSIM integration: UBERON tag applied to neural data
    Body map shows: [UBERON:0001017 brain] → [region: right motor cortex per electrode map]
```

**BOM: ~$650 (for 64-channel system with FPGA acquisition)**

---

### NFSIM-NEURAL-02 — Intracortical Recording Headstage

```
Purpose: Interface with Utah Array or custom silicon microelectrode arrays
Headstage: Intan RHD2132 (32ch) × 3 = 96 channels (Utah Array standard)
Connector: compatible with Cereport (Blackrock standard) via adapter
FPGA: Artix-7 (Open Ephys rhythm firmware)
Wireless option: nRF5340 BLE for artifact-free low-bandwidth LFP streaming
BOM: ~$380 (headstage only, excluding array)
```

---

### NFSIM-EOG-01 — Electrooculography Sensor Glasses

```
Electrodes: 4× Ag/AgCl around eye (nasal L, temporal L, nasal R, temporal R)
  Positioned in eyeglass frame arms
AFE: ADS1299 (2-channel differential minimum)
Sampling: 250 Hz (EOG bandwidth <30 Hz — well sampled)
Output: horizontal gaze angle, vertical gaze angle, blink rate, fixation duration
Applications: sleep REM detection, HCI gaze interface, driver fatigue
BOM: ~$88
```

---

### NFSIM-EDA-01 — Electrodermal Activity Wrist Sensor

**Full Specifications:**

| Parameter | Value |
|---|---|
| Electrode positions | Two Ag/AgCl pads, volar wrist surface (thenar/hypothenar) |
| Measurement signal | 500 mV AC, 30 Hz |
| Range | 0.05–30 µS skin conductance |
| Resolution | 0.01 µS |
| Sampling rate | 4 Hz continuous, 64 Hz burst |
| Outputs | SCL (tonic), SCR amplitude + latency, SDSCL |
| Wireless | BLE 5.0 |
| Battery | 200 mAh |
| Battery life | 5 days at 4 Hz |
| UBERON | UBERON:0001416 (skin, eccrine gland region) |

**Hardware Architecture:**

```
Measurement principle:
  AC Wheatstone bridge: 500 mV, 30 Hz sine wave applied across electrodes
  Lock-in detection extracts skin conductance at 30 Hz
    Avoids electrode polarization (AC vs DC)
    In-phase component: skin conductance (G)
    Quadrature: skin capacitance (C) — usually ignored

Electronics:
  Sine wave generation: nRF52840 DAC output filtered to 500 mV, 30 Hz
  Differential amplifier: measures voltage across electrodes
  Lock-in amplifier (software): multiply by reference sine + cosine → I, Q components
  ADC: ADS1256 (24-bit, 30 kSPS, overkill but ensures resolution)
  Conductance range: 0–30 µS → signal voltage range 0–1.5 mV across 50Ω sense resistor
  Filters: 4th order Butterworth LPF 1Hz (tonic SCL) + 0.05–3Hz BPF (phasic SCR)

Output parameters:
  SCL: mean skin conductance over 60s window
  SCR: individual responses (peak amplitude, rise time, recovery half-time)
  Event-related SCR: synchronized with external event markers from BLE
  SDSCL: standard deviation of SCL → arousal variability
  nSCR: number of spontaneous SCR per minute → stress indicator
```

**BOM: ~$42**

---

## 13. Hardware Domain E — Ingestible / Traversing Capsules

### Universal Capsule Position Tracking (Applies to All CAP Devices)

```
Position estimation algorithm (Bayesian multi-sensor fusion):

Inputs:
  1. Pressure waveform (BMP581 or equivalent):
     Esophagus:        high-amplitude rapid peristalsis (50–200 mmHg, 5–8/min)
     Stomach:          irregular high-pressure contractions, churning (30–80 mmHg)
     Pyloric sphincter: characteristic high-pressure event on transit
     Small intestine:  regular peristaltic waves (10–30 mmHg, 3/min)
     Ileocecal valve:  pressure signature change on crossing
     Colon:            haustral contractions (lower, irregular, 1–2/min)
  
  2. IMU motion signature (BMA456 + BMI088):
     Stomach: chaotic tumbling, high-energy churning motions
     Small intestine: rhythmic smooth peristaltic oscillation
     Colon: longer intervals, different motion pattern
  
  3. pH (ISFET sensor, where equipped):
     Esophagus:        variable (5–7 normally, 1–3 during reflux)
     Stomach:          1.5–3.5 (strongly acidic)
     Duodenal entry:   rapid rise to 5.5–7.5 (bicarbonate neutralization)
     Small intestine:  6.5–7.5
     Colon:            7.0–8.0
     pH transition at pylorus: most reliable anatomical landmark
  
  4. Elapsed time (calibrated population-average transit times):
     Esophageal transit:   0.5–30 seconds
     Gastric emptying:     15 min – 4 hours (highly variable, meal-dependent)
     Small bowel transit:  2–8 hours
     Colonic transit:      10–72 hours
  
  5. RF signal strength (RSSI from external belt antennas):
     Triangulation from 6 antenna positions → 3D position estimate
     Accuracy: ±5 cm in abdomen (insufficient alone, improves Bayesian estimate)
  
  6. Body temperature (validates capsule inside vs. outside body)

Bayesian estimator:
  P(zone_k | observations) ∝ P(observations | zone_k) × P(zone_k | prior)
  Updated every 60 seconds
  Output: probability distribution across 8 GI zones
  Committed zone: zone with P > 0.85 (otherwise: "transitioning")

UBERON zone assignments:
  Esophagus:   UBERON:0001043
  Stomach:     UBERON:0000945
  Duodenum:    UBERON:0002114
  Jejunum:     UBERON:0002115
  Ileum:       UBERON:0002116
  Cecum:       UBERON:0001153
  Colon:       UBERON:0001155
  Rectum:      UBERON:0001052
```

### Complete Capsule Device List

| Device ID | Name | Primary Sensing | BOM Target |
|---|---|---|---|
| NFSIM-CAP-01 | Optical Imaging + Chemistry (GI Camera) | Camera + pH + O₂ + Temp | ~$390 |
| NFSIM-CAP-02 | GI Ultrasound Capsule | CMUT 360° radial US | ~$580 |
| NFSIM-CAP-03 | DNA/RNA Capture Capsule | pH-triggered collection | ~$95 |
| NFSIM-CAP-04 | Full Multi-Modal Research Capsule | All modalities combined | ~$780 |
| NFSIM-CAP-05 | Core Temperature Capsule | NTC thermistor | ~$25 |
| NFSIM-CAP-06 | pH / Pressure / Motility Capsule | SmartPill equivalent | ~$185 |
| NFSIM-CAP-07 | Microbiome Sampling Capsule | Sterile anaerobic capture | ~$45 |
| NFSIM-CAP-08 | Drug Delivery Verification Capsule | UV/Vis + position | ~$110 |
| NFSIM-CAP-09 | Oxygen Mapping Capsule | Clark-type O₂ electrode | ~$135 |
| NFSIM-CAP-10 | GI Bleeding Detection Capsule | Dual-wavelength Hb | ~$120 |

All capsule specifications and hardware architecture details for NFSIM-CAP-01 through NFSIM-CAP-04 are fully documented in Section 7 (Biological Sensing Domain Encyclopedia, Domain: Implantable/Ingestible) and Section 8. The following provides targeted addenda for CAP-05 through CAP-10.

### NFSIM-CAP-05 — Core Temperature Capsule (Detail)

```
Dimensions: 22×9mm (smallest capsule in ecosystem — easiest to swallow)
Shell: medical-grade HPMC (hydroxypropyl methylcellulose) outer coating
  → dissolves in ~5 min in stomach; inner ABS capsule body persists
  
Sensor: precision NTC thermistor (Murata NXFT15XH103, ±0.1°C accuracy)
ADC: ADS1220 (24-bit, oversampled for thermal precision)
MCU: STM32L0 (ultra-low power, 32 kHz clock for standby)
Radio: 434 MHz FSK (Si4463), 1 reading per minute
  → battery extends to 60+ hours at 1-min intervals
Battery: SR927W (1.55V, 56 mAh) × 1
  → calculated life: 56 mAh / (avg 200 µA active) = 280h → more than enough
  → OR: SR41 (1.55V, 45 mAh) still sufficient

Clinical applications:
  Fever monitoring in ICU (more accurate than axillary/tympanic)
  Core temperature tracking during hypothermia treatment
  Athletic heat stroke prevention (sustained core >40°C alert)
  Diurnal temperature rhythm studies
  Drug effects on thermoregulation research

UBERON: UBERON:0001869 (core body temperature, systemic)
BOM: ~$25 per capsule
```

### NFSIM-CAP-06 — pH / Pressure / Motility Capsule (Detail)

```
SmartPill functional equivalent (Medtronic SmartPill = $500+ per capsule commercial)
NFSIM-CAP-06 target: <$185 per capsule

Sensors:
  pH: ISFET (Honeywell FWRE-6003 or custom Si ISFET)
    Range: 1–9 pH, ±0.3 pH
    Sampling: every 5 seconds
  Pressure: BMP581 (Bosch)
    Range: 300–1100 hPa absolute
    Effectively: 0–200 mmHg gauge (after baseline subtraction)
    Sampling: 2 Hz continuous
  Temperature: NTC 10kΩ embedded
    ±0.2°C accuracy

MCU: STM32L4 (main controller, adequate processing power at low power)
Radio: 434 MHz FSK (Si4463)
Battery: 2× SR44 silver oxide (3.0V total, 200 mAh)
  Expected runtime: 120 hours (5 days) >> 72h maximum GI transit
  Design margin: >1.5× buffer

Transit time measurements:
  Gastric emptying time (GET): pH rise from <4 to >4 at pylorus → GET confirmed
    Clinical normal: <5h (solid meal)
  Small bowel transit time (SBTT): pylorus to ileocecal (pH 6.5 + pressure pattern)
    Clinical normal: 3–6h
  Colon transit time (CTT): ileocecal to rectum (pressure pattern + elapsed time)
    Clinical normal: 10–59h

Analysis software:
  Automatic motility report generation (Python analysis package released open-source)
  Compare to published normal ranges (Saad 2010, SmartPill normative data)
  UBERON-timestamped full transit pH + pressure profile export → NanoFlowSIM

UBERON: UBERON:0000945 (stomach) → UBERON:0002115 (jejunum) → UBERON:0001155 (colon)
  [continuous UBERON tag updates as capsule traverses GI tract]
BOM: ~$185
```

### NFSIM-CAP-07 — Microbiome Sampling Capsule (Detail)

```
Critical challenge solved: true luminal microbiome sampling (not just stool)
Stool sampling provides: colonic microbiome only (terminal end, post-colonic mixing)
CAP-07 provides: site-specific sampling at ANY GI segment

Capsule trigger mechanism:
  Outer coating: pH-enteric coating (Eudragit L100-55, dissolves pH >5.5)
    → protects inner capsule from stomach acid
    → dissolves in proximal small intestine → triggers collection
  Inner trigger: timer-based OR explicit remote trigger (RF command from belt)

Collection mechanism:
  Spring-loaded door: nitinol wire actuator (one-time use, 30ms actuation)
    Nitinol transition temperature: 45°C (triggered by passing body-temperature current)
    Current: 100 mA for 100ms → nitinol contracts → door opens
  Sample collection: passive filling (intestinal fluid pressure drives entry)
    Collection time: 60 seconds open → spring-loaded re-sealing
    Seal: PTFE plug compressed by sealing spring

Preservation chemistry:
  Pre-loaded preservation solution: RNAlater (Ambion) or homemade DMSO buffer
    Volume: 200 µL pre-loaded, dried (reconstitutes with ~200 µL luminal fluid on entry)
    Stabilization: RNA stability maintained >24h at room temperature post-collection
  Collection chamber: gold-coated PEEK, 300 µL total volume
    Gold coating: prevents oxidative degradation of nucleic acids

Position confirmation:
  pH sensor (ISFET) confirms pH > 6.0 before triggering (small intestine confirmed)
  Timer: backup trigger at elapsed time = 4h (average gastric emptying)
  Priority: pH-based trigger preferred for anatomical precision

Retrieval:
  Natural passage: 24–48h transit to excretion
  Visual ID: outer capsule coated with fluorescent pink dye → visible in stool
  Retrieval kit: provided (peel-and-see bag, return envelope with cold pack)
  Capsule shipment: return via standard mail (ambient temperature, RNA stabilized)

Downstream analysis:
  DNA extraction: Qiagen PowerSoil DNA Isolation Kit (standard)
  16S rRNA amplicon sequencing: V4 region, standard primers (515F/806R)
  Shotgun metagenomics: NFSIM-SEQ-01 or commercial sequencer
  Analysis: QIIME2, MetaPhlAn4, HUMAnN3 (open-source pipelines)

UBERON: UBERON:0002115 (jejunum, primary target) or as determined by pH/timer
BOM: ~$45 per capsule (excludes downstream sequencing cost)
```

### NFSIM-CAP-08 — Drug Delivery Verification Capsule (Detail)

```
Purpose: verifies that an orally administered drug actually reaches and dissolves
  in the intended GI segment at therapeutic concentration

Sensing approach:
  UV/Vis absorbance detector inside capsule:
    White LED: broad spectrum illumination of luminal fluid
    Spectrometer chip: Hamamatsu C12666MA (micro spectrometer, 340–780 nm)
      Resolution: 15 nm FWHM
      Size: 20.1×22.4×10.5mm → fits in 32mm capsule
    Measures: absorbance spectrum of luminal fluid
    Drug detection: correlate spectral signature to drug standard curve
  
  Position tracking: pH + IMU + elapsed time (standard CAP position estimator)
  
  Co-dosing protocol:
    Patient takes drug dose + CAP-08 simultaneously
    CAP-08 traverses GI tract → measures drug concentration at each zone
    Provides: luminal drug concentration profile vs. anatomical position + time
  
  Applications:
    Biopharmaceutics research: in vivo dissolution testing
    Generic drug equivalence: compare dissolution to innovator product in vivo
    pH-dependent formulation: verify enteric coating releases at correct pH
    GI disease effect: see if patient's GI disease affects drug dissolution
    
UBERON: [tracked continuously as capsule moves]
BOM: ~$110 (Hamamatsu spectrometer chip cost ~$80 dominates)
```

### NFSIM-CAP-09 — Oxygen Mapping Capsule (Detail)

```
Sensors: Clark-type electrochemical O₂ electrode
  Working: platinum wire
  Electrolyte: KOH gel
  Gas-permeable membrane: PTFE (20 µm, allows O₂ diffusion)
  Applied potential: −0.65V vs Ag/AgCl (reduction of O₂)
  Current ∝ pO₂ (linear 0–150 mmHg)

Normal GI O₂ gradient (clinically relevant):
  Duodenum: ~10 mmHg (mildly hypoxic)
  Jejunum: 5–8 mmHg
  Ileum: 3–5 mmHg
  Colon (lumen): <1 mmHg (near-anaerobic → supports anaerobic microbiome)
  Mucosal surface: 2–5 mmHg (epithelial O₂ for cell function)

Pathological:
  IBD (Crohn's, UC): severe hypoxia at inflamed segments (<1 mmHg in mucosa)
  Bowel ischemia: zero O₂ in ischemic segment → diagnostic
  GI cancer: tumor microenvironment hypoxia mapping

Sampling: 2× per minute (5s reading cycle, wake-sleep duty cycle)
UBERON: zone-tracked continuously
BOM: ~$135
```

### NFSIM-CAP-10 — GI Bleeding Detection Capsule (Detail)

```
Hemoglobin detection strategy:
  Method 1 — Optical (primary):
    540nm LED + 575nm LED: HbO₂ absorption peaks (Soret band)
    Photodiode: measures transmitted/reflected light through luminal fluid
    Ratio of 540/575nm absorbance → hemoglobin concentration
    Sensitivity: detects >0.5 mg Hb/mL (clinical relevance threshold)
  
  Method 2 — Chemical (confirmatory):
    Guaiac-type peroxidase reaction pad:
      Guaiac resin + H₂O₂ → heme peroxidase catalysis → blue color
      Read optically by LED+photodiode at 625nm
      Provides qualitative confirmation
  
  Output per zone:
    Hb concentration estimate (mg/mL) at each anatomical zone
    Active bleeding detection: Hb >2 mg/mL + location identified
    Occult bleeding: Hb 0.5–2 mg/mL at specific segment

Clinical impact:
  Iron deficiency anemia workup: localizes bleeding to specific GI segment
    → Avoids full upper + lower endoscopy if bleeding source identified
  Post-polypectomy monitoring: verify no delayed bleeding 24h post-procedure
  Hereditary hemorrhagic telangiectasia (HHT): map GI angiodysplasia sites

UBERON: zone-tracked continuously
BOM: ~$120
```

---

## 14. Hardware Domain F — Wearable Patches and Implants

### Complete Device List

| Device ID | Name | Technology | BOM Target |
|---|---|---|---|
| NFSIM-PATCH-01 | Biopotential + Motion Multi-Sensor Patch | ECG + accel + temperature | ~$48 |
| NFSIM-PATCH-02 | Wound Healing Monitor Patch | O₂ + pH + temperature + exudate | ~$85 |
| NFSIM-PATCH-03 | Transdermal Drug Delivery Controller | Iontophoresis + BLE control | ~$110 |
| NFSIM-IMPLANT-01 | Open Subcutaneous Sensor Node | Titanium capsule, NFC-powered, modular | ~$280 |
| NFSIM-IMPLANT-02 | Neural Stimulation Research Platform | 16-channel biphasic, wireless | ~$450 |

### NFSIM-PATCH-01 — Biopotential + Motion Multi-Sensor Patch

```
Sensors integrated in single adhesive patch (75×50×8mm):
  ECG: ADS1291 (single-lead, same as ECG-01 but integrated with multi-sensor)
  3-axis accelerometer: BMA456 (motion, steps, fall detection)
  Skin temperature: NTC thermistor (±0.1°C)
  Skin galvanic response: basic EDA measurement (2-electrode, 500mV, 30Hz)

Combined outputs:
  ECG waveform + R-peaks + HRV
  Activity classification: rest, walk, run, sleep
  Temperature trend
  Basic stress indicator (EDA)
  
MCU: nRF52840 (all sensors share one MCU)
BLE: integrated nRF52840
Battery: 300mAh LiPo
IPX7, 14-day wear
UBERON: UBERON:0000948 (heart ECG) + UBERON:0001416 (skin temp/EDA)
BOM: ~$48
```

### NFSIM-PATCH-02 — Wound Healing Monitor Patch

```
Applied over wound dressing (measures wound microenvironment through dressing or at wound edge)

Sensors:
  Oxygen: optical luminescence quenching (ruthenium dye, NO O₂ → max phosphorescence)
    Range: 0–21% pO₂ (full hypoxic to normoxic)
    Critical: chronic wound healing requires pO₂ >20 mmHg at wound surface
  pH: polyaniline ISE printed on flexible substrate
    Range: 4.0–9.0 (wound pH 7.2–8.5 normal → >8.5 suggests infection)
  Temperature: thermistor (elevated temperature → infection flag)
  Exudate volume: capacitive sensor layer (fluid accumulation detected by capacitance)
  Bacteria detection (future option): bacteriophage-based sensor (in development)

MCU: STM32L4 (main) + nRF52840 (BLE)
BLE: 1-hour update intervals (sufficient for wound monitoring)
Battery: 500mAh, 7-day life
Wound dressing compatibility: designed to apply over Mepilex Ag or similar
UBERON: UBERON:0001416 (skin wound region)
BOM: ~$85
```

### NFSIM-PATCH-03 — Transdermal Drug Delivery Controller

```
Iontophoresis principle: DC current drives charged drug molecules through skin
  Positive drugs: anodic drive (positively charged drug → repelled by + anode)
  Negative drugs: cathodic drive (negatively charged drug ← attracted to + anode)
  Current density: 0.5 mA/cm² max (safety limit for skin)
  Drug delivery rate ∝ current × time (Faraday's law)

Hardware:
  Drug reservoir: hydrogel patch (user loads prescribed drug solution)
  Active electrode: ITO or carbon electrode under drug reservoir
  Counter electrode: saline hydrogel on opposite skin site
  Current source: precision current source, 0–2mA, ±0.01mA resolution
    Current control: LT3092 (2-terminal programmable current source)
    Voltage compliance: 5–30V (enough for skin resistance 5–50 kΩ)
  Safety:
    Skin impedance monitoring (prevent overcurrent)
    Temperature monitoring (prevent local heating)
    Maximum charge limit (C/cm² limit enforced in firmware)
  
BLE control:
  Clinician prescribes: dose (mA·hours), duration, current density limit
  Patient initiates: confirms dose on app → delivery begins
  Real-time monitoring: current, charge delivered, skin impedance, temperature
  Completion notification: alert when dose delivered
  Audit log: every delivery logged with timestamp + actual parameters
  
Applications:
  Lidocaine for local anesthesia (pre-procedure pain reduction)
  Pilocarpine for sweat test (CF diagnosis)
  Anti-inflammatory (dexamethasone for tendinopathy)
  Insulin (experimental — not approved)
  
MCU: STM32L4
BLE: nRF52840
Battery: 1000mAh (2h delivery session)
UBERON: UBERON:0001416 (skin at application site)
BOM: ~$110
```

### NFSIM-IMPLANT-01 — Open Subcutaneous Sensor Node

```
Concept: A small titanium capsule containing a sensor board, NFC-powered,
  passively powered (no battery), implanted subcutaneously.
  Sensor module swappable during surgical revision or via specialized needle.
  Powers from external NFC reader (phone tap) → 2-second measurement window.

Physical design:
  Capsule: titanium grade 5, 10mm diameter × 5mm height, threaded cap
  Biocompatibility: ISO 10993 compliant, mirror-polished exterior
  O-ring seal: medical silicone O-ring, IP68 equivalent
  Parylene-C internal coating: protects electronics from any moisture ingress

NFC power and communication:
  IC: NXP NHS3100 (NFC-powered analog front end + sensor interface IC)
    Harvests power from NFC field (13.56 MHz ISO 15693)
    Provides: ADC + analog conditioning + NFC communication
    Power budget: 1–2mW during NFC read
  NFC antenna: 8×8mm coil PCB inside capsule (tuned to 13.56 MHz)
  Read range: 0.5–2 cm (through skin, phone NFC)

Sensor board (swappable 8mm diameter disk):
  Module A — Glucose: GOx enzymatic wire (same as CGM-01 filament)
  Module B — Lactate: LOx enzymatic wire
  Module C — Temperature: NTC thermistor
  Module D — pH: ISFET chip (small MEMS die)
  Module E — Oxygen: optical O₂ (fluorescence quenching, µLED inside capsule)
  
Insertion:
  Surgical: 15-gauge introducer needle, 5-minute local procedure
  Capsule deployment: trocar-style deployment through introducer
  Securing: fibrous capsule forms naturally → no suture needed
  Location: typically upper arm subcutaneous fat

UBERON: UBERON:0000175 (subcutaneous fat layer, specific region based on location)
BOM: ~$280 (titanium capsule machining dominates cost)
```

### NFSIM-IMPLANT-02 — Neural Stimulation Research Platform

```
Purpose: implantable stimulation for research into peripheral nerve modulation,
  bioelectronic medicine, vagus nerve stimulation, dorsal column stimulation

Design parameters:
  Channels: 16 independent stimulation channels (biphasic current sources)
  Current per channel: 0–5 mA, 0.01 mA resolution
  Pulse width: 50–2000 µs per phase
  Rate: 0–1000 Hz
  Waveform: symmetric biphasic rectangular (safe charge balance)
  Charge density limit: <50 µC/cm² per phase (safety limit for Pt electrodes)

Electronics:
  Stimulator ASIC / discrete:
    16× precision current sources: INA333 + H-bridge (biphasic control)
    DAC per channel: MCP4728 (12-bit, I2C, 4-channel per IC)
      → 4× MCP4728 = 16 DAC channels = 16 stimulation amplitudes
    H-bridge: DRV8876 (1 per 2 channels) = 8 DRV8876 for 16 channels
    Charge balance monitoring: integrator + comparator per channel
    Safety cutoff: MOSFET crowbar if impedance drops below 500Ω (short circuit)
  
  MCU: nRF52840 (BLE programming + stimulation timing control)
    Pulse timing: hardware timer (32 MHz resolution = 31 ns precision)
    BLE protocol: researcher programs stimulation parameters via phone/laptop
    Closed-loop option: receives signal from NFSIM-NEURAL-01 ECoG array
      → detects neural pattern → triggers stimulation (adaptive DBS paradigm)
  
  Power: inductive (Qi 5W) or surgical battery (LiMnO₂ primary, 3V, 1.5Ah)
  Enclosure: titanium, hermetically sealed, ISO 10993 biocompatibility
  Wireless: BLE 5.0 (in vivo, through skin)

Lead interface: compatible with standard neurostimulation leads
  (Medtronic 3389 DBS lead or equivalent 4-contact cylindrical)
  Connector: IS-1 standard (pacemaker lead connector)

⚠ RESEARCH USE ONLY. Neural stimulation devices require IRB approval and
  neurosurgeon involvement for any human research use.

UBERON: UBERON:0001017 (CNS) or UBERON:0001021 (peripheral nervous system)
BOM: ~$450
```

---

## 15. Hardware Domain G — Flow Cytometry and Environmental

### Complete Device List

| Device ID | Name | Technology | BOM Target |
|---|---|---|---|
| NFSIM-FLOW-01 | Portable Flow Cytometer / Cell Counter | Acoustic focusing, 3-color | ~$380 |
| NFSIM-ENV-01 | Environmental Bio-Aerosol Sampler | Cyclone concentrator + LAMP | ~$95 |
| NFSIM-ENV-02 | Water Pathogen LAMP Station | Automated water LAMP | ~$145 |
| NFSIM-ENV-03 | Soil Microbiome Sampler | DNA extraction + LAMP/sequencing | ~$85 |
| NFSIM-ENV-04 | Air Quality Biomonitor | VOC + PM2.5 + CO₂ + T/H | ~$75 |
| NFSIM-ENV-05 | Mosquito Trap + Species Genomics | Light trap + LAMP pathogen ID | ~$160 |

### NFSIM-FLOW-01 — Portable Acoustic Flow Cytometer

**Full Specifications:**

| Parameter | Value |
|---|---|
| Sample type | Whole blood (1:100 PBS dilution) or cell suspension |
| Sample volume | 50 µL diluted sample |
| Cell throughput | 1,000–5,000 cells/sec |
| Focusing method | Bulk Acoustic Wave (BAW) focusing (no sheath fluid) |
| Laser/LED excitation | 405 nm + 488 nm + 638 nm LEDs |
| Fluorescence channels | 3 (FITC 530/30, PE 585/42, APC 660/20) |
| Scatter channels | FSC + SSC |
| CBC output | WBC count + 3-part differential + RBC estimate + PLT |
| Time to result | 3–5 minutes |
| Connectivity | USB-C + BLE 5.0 |
| Battery | 2000 mAh |
| Battery life | 50 tests per charge |
| Dimensions | 150 × 80 × 60 mm |
| Weight | 400 g |
| Disposable | Microfluidic chip cartridge, single-use, $2–5 each |
| UBERON | UBERON:0000178 (blood cells) |

**Hardware Architecture:**

```
Microfluidic Chip (disposable):
  Material: polycarbonate or COC (cyclo-olefin copolymer)
  Channel dimensions: 350 µm × 350 µm square channel
  Acoustic focusing zone: 2 cm piezo actuator region upstream of detection
  Detection zone: clear optical window, 1 cm past acoustic focusing
  Flow rate: 50–200 µL/min (peristaltic pump controlled)
  Chip connector: spring-loaded fluid ports (no tubing connection needed)
  Sample input: pipette 50 µL into chip inlet well
  Waste: internal 500 µL reservoir

Acoustic Focusing (no sheath fluid):
  Piezo element (PZT): 5 × 20 mm, resonant frequency tuned to channel resonance
    For 350 µm channel width, 1st resonance ≈ c/(2×350µm) = 1540/(2×0.00035) = 2.2 MHz
  AC drive: 2.2 MHz signal, 10–50 Vpp (power tunable)
  Acoustic radiation force pushes cells to pressure node (channel center)
  Single-file alignment achieved within 2–3mm of piezo length
  Performance: centering efficiency >95% (vs hydrodynamic sheath >99% in lab systems)

Optical Detection:
  Illumination:
    488nm LED (Lumileds L1Cx, 50 mW): FITC and PE excitation (dual-use)
    638nm LED (Oclaro, 30 mW): APC / Cy5 excitation
    405nm LED (optional, Nichia, 10 mW): violet dyes (Brilliant Violet, DAPI)
    All LEDs focused to <50 µm spot at flow channel (matching cell diameter)
    Focusing optics: aspheric lens pairs per LED
  
  Collection and detection:
    Forward scatter (FSC): on-axis photodiode (Si PIN), 488nm bandpass
    Side scatter (SSC): 90° collection, Si PIN photodiode, 488nm bandpass
    FL1 (FITC, 530/30 nm): PMT or SiPM + bandpass filter
    FL2 (PE, 585/42 nm): PMT or SiPM + bandpass filter
    FL3 (APC/Cy5, 660/20 nm): PMT or SiPM + bandpass filter
    PMT options: Hamamatsu H10721 (compact PMT module, $150 each)
      OR: ON Semi MicroFC-10035 SiPM ($8 each) — lower cost, lower sensitivity
    Light collection: 0.5 NA aspheric lens → photodetector

Signal Processing:
  Pulse amplification: OPA657 (wide-bandwidth low-noise transimpedance amp)
  ADC: AD9234 (12-bit, 1 GSPS) — captures full pulse waveform at <5 µs per cell
  FPGA: Lattice iCE40HX8K — real-time pulse detection
    Threshold crossing → window open → peak height, area, width extraction
    Event rate: up to 10,000 events/sec
  MCU: STM32H743 — accumulates event data, applies gates, calculates populations

Cell Classification:
  CBC 3-part differential from FSC/SSC clustering:
    Lymphocytes: low FSC, low SSC (small, round, no granules)
    Monocytes: intermediate FSC, intermediate SSC
    Granulocytes (neutrophils, eosinophils, basophils): high FSC, high SSC
  RBC: gated from FSC/SSC (enucleate, biconcave disc morphology)
  Platelets: small FSC, dim SSC gate
  Lysing buffer protocol: Lyse RBC before loading → WBC enriched suspension
  
  Optional immunophenotyping:
    With fluorescent antibody staining:
      CD4-FITC: CD4+ T cells (HIV monitoring — CD4 count)
      CD45-FITC / CD14-PE: leukocyte gating
      Sample prep: 10 min antibody incubation → PBS wash → load chip
```

**BOM:**

| Component | Cost |
|---|---|
| Hamamatsu H10721 PMT × 3 | $150 × 3 = $450 → budget: SiPM × 3 = $24 |
| OPA657 TIA × 5 | $3.50 × 5 = $17.50 |
| 488nm LED (Lumileds) | $12 |
| 638nm LED (Oclaro) | $8 |
| Lattice iCE40HX8K FPGA | $18 |
| STM32H743 MCU | $8 |
| nRF52840 BLE | $4.50 |
| AD9234 ADC | $35 |
| Peristaltic pump (micro) | $25 |
| Piezo actuator | $15 |
| Optical filters × 5 | $12 × 5 = $60 |
| Aspheric lenses × 6 | $8 × 6 = $48 |
| PCB (4-layer) | $25 |
| Enclosure | $30 |
| Misc components | $35 |
| **Total** | **~$380** |

---

### NFSIM-ENV-01 through ENV-05 Summary Specifications

**NFSIM-ENV-01 — Environmental Bio-Aerosol Sampler**
```
Air flow: 100–300 LPM through cyclone concentrator
Collection: wet cyclone (PBS buffer) → 1–5 mL eluent per hour
Efficiency: >90% for 1–10 µm particles (respiratory pathogens)
Output: concentrated buffer → load directly into NFSIM-PCR-03 (LAMP) or NFSIM-CRISPR-01
Monitor: CO₂ + PM2.5 + VOC + temp/humidity (Sensirion SCD41 + SPS30 + SGP41 + SHT40)
Power: 12V DC (car lighter, solar panel, or wall adapter)
Battery backup: 4h at 300 LPM
MCU: STM32G474 + nRF52840 BLE
BOM: ~$95

Applications: hospital infection control, outbreak surveillance, indoor air quality genomics
UBERON: UBERON:0000948 (aerosol particles → nasal mucosa potential exposure)
```

**NFSIM-ENV-02 — Water Pathogen LAMP Station**
```
Water intake: peristaltic pump draws 100mL sample from water source
Filtration: 0.2 µm polycarbonate membrane concentrates bacteria/viruses
DNA extraction: heat lysis + bead-based extraction (automated on chip)
Detection: LAMP at 65°C (NFSIM-PCR-03 hardware reused)
Targets (switchable reagent kits): E. coli O157, Salmonella, Vibrio cholerae,
  Cryptosporidium parvum, Giardia, Legionella, SARS-CoV-2 (wastewater surveillance)
Result: positive/negative with target identification in 45 min
Power: 5V USB
MCU: STM32H7 (automates full pipeline)
UBERON: environmental sample (not anchored to body; site GPS tagged)
BOM: ~$145
```

**NFSIM-ENV-03 — Soil Microbiome Sampler**
```
Soil input: 0.5g soil in bead-beating tube
Extraction: PowerSoil-compatible bead-beating lysis (motorized bead beater included)
Eluent: 50 µL DNA → load into NFSIM-PCR-03 (LAMP) for pathogen detection
  OR: → NFSIM-SEQ-01 for full metagenomic sequencing
Applications: agricultural microbiome, infection source tracing, environmental monitoring
BOM: ~$85
```

**NFSIM-ENV-04 — Air Quality Biomonitor**
```
Sensors:
  CO₂: Sensirion SCD41 (photoacoustic NDIR, ±40 ppm)
  PM1/PM2.5/PM10: Sensirion SPS30 (laser particle counter)
  VOC index: Sensirion SGP41 (metal oxide, VOC index 0–500)
  NO₂: Sensirion SEN54 (electrochemical, integrated with above)
  Temperature + humidity: SHT40
  UV index: VEML6075
MCU: nRF52840 (low power, BLE 5.0)
Display: 2.9" e-paper (daily air quality summary, battery-friendly)
Battery: 3000mAh (30 day life at 1-min sampling)
Indoor/outdoor capable: IP54
UBERON: Environmental (GPS-tagged location, not body-anchored)
BOM: ~$75
```

**NFSIM-ENV-05 — Mosquito Trap + Vector Genomics Station**
```
Trap: UV LED light trap (390nm, attracts mosquitos)
Kill chamber: 350V grid (electrocution on entry)
Collection tray: dry collection for specimen preservation
Species ID: wing-beat frequency analysis (microphone + FFT → Anopheles vs Aedes vs Culex)
Pathogen detection: LAMP kits for dengue NS1, malaria PfHRP2, Zika E protein in mosquito lysate
Processing: operator manually processes 10–20 trapped mosquitos per run
Power: 12V (solar-compatible)
GPS: location tagging (SIM7000 module for cellular data upload)
UBERON: Environmental; links to UBERON:0002048 (lung) as inhalation risk proxy
Applications: malaria surveillance, arbovirus monitoring, One Health programs
BOM: ~$160
```

---

## 16. Hardware Domain H — Interventional and Delivery

### Complete Device List

| Device ID | Name | Technology | BOM Target |
|---|---|---|---|
| NFSIM-DEL-01 | Wearable Insulin Patch Pump | Micro-pump + BLE + CGM integration | ~$95 |
| NFSIM-DEL-02 | Subcutaneous Drug Implant | Osmotic pump, programmable | ~$185 |
| NFSIM-DEL-03 | Microneedle Drug Delivery Array | Dissolvable microneedle patch | ~$15 |
| NFSIM-ABL-01 | Handheld RF Cautery Pen | RF ablation, 400 kHz | ~$125 |
| NFSIM-ABL-02 | Portable Focused Ultrasound (pFUS) | HIFU therapeutic US | ~$340 |

### NFSIM-DEL-01 — Wearable Insulin Patch Pump

```
Reservoir: 200 IU insulin (3 mL U-100 cartridge)
Pump mechanism: piezoelectric micro-diaphragm pump
  Delivery precision: 0.01 U per stroke (0.1 µL)
  Maximum rate: 60 U/hour (fast bolus possible)
  Basal rate: 0.1–25 U/hour (programmable)
Integration: NFSIM-CGM-01 compatible (same NFS BLE protocol)
Closed-loop: optional connection to NFSIM-CGM-01 → automated insulin adjustment
  OpenAPS-compatible control algorithm running on paired phone
Cannula: 6mm, 28G angled steel or Teflon (user-inserted)
Pod size: 80×40×8mm
Battery: 1000mAh, 3-day pod
Water resistance: IPX8
MCU: nRF52840 (BLE + pump control)
UBERON: UBERON:0001416 (subcutaneous delivery site)
BOM: ~$95 per pod (disposable 3-day) + $35 controller (reusable)
```

### NFSIM-DEL-02 — Subcutaneous Osmotic Pump Implant

```
Osmotic pump principle (ALZA-type):
  Reservoir: drug solution inside semi-permeable membrane
  Driving force: osmotic pressure difference across membrane
  No electronics required for drug release (passive)
  Release rate: constant, set by membrane permeability
  Rate range: 1–100 µL/day
  Duration: 7–90 days (membrane + reservoir size determines duration)

Open-source variant adds electronics:
  Small NFC-programmable valve: allows on-demand dose modification
    NFC command from external programmer → valve opens/closes for X seconds
  Flow sensor: optical (LED + photodetector) confirms delivery
  MCU: ultra-low-power STM32L0, NFC-powered (same as CGM-01 concept)
  No battery: NFC-harvested power for programming events only

Applications: continuous antiretroviral delivery (HIV PrEP implant research)
  Anti-addiction medication (naltrexone) long-acting implant research
  UBERON: UBERON:0000175 (subcutaneous fat, implant site)
BOM: ~$185 (titanium capsule + osmotic components)
```

### NFSIM-DEL-03 — Microneedle Drug Delivery Array

```
Dissolvable microneedle patch:
  Array: 100 microneedles, 600µm height, 200µm base, tip radius <5µm
  Fabrication: PDMS mold → PLGA or PVP polymer dissolved with drug
    → cast into mold → dry → peel → patch ready
  Drug loading: up to 5 mg per patch (distributed across 100 needles)
  Application: press onto skin for 30 seconds → needles dissolve in ~5 min
  Pain: essentially painless (needles don't reach nerves at 600µm depth)
  Skin barrier: stratum corneum penetrated → drug reaches viable epidermis

Applications:
  Influenza vaccine delivery (proven in clinical trials)
  Lidocaine topical pre-procedure (15 min onset vs 45 min for EMLA cream)
  Insulin delivery (research, not FDA approved)
  Transdermal metformin (Type 2 diabetes research)

Open-source mold design: 3D printable SLA mold (needle arrays printable at 25µm resolution)
Drug loading protocol: published in literature for each drug class
UBERON: UBERON:0001416 (skin, drug penetration to UBERON:0001230 viable epidermis)
BOM: ~$15 per pack of 5 patches (excluding drug cost)
```

### NFSIM-ABL-01 — Handheld RF Cautery Pen

```
RF ablation: 400 kHz sinusoidal current → resistive heating → tissue coagulation
  Frequency: 400 kHz (monopolar) or 1 MHz (bipolar)
  Power: 5–30W adjustable
  Electrodes: sterile pencil tip (monopolar) + return plate
  Applications: field hemostasis, skin lesion removal, nerve ablation research

Safety features:
  Power only during button hold (dead-man switch)
  Current limit: hardware comparator cutoff at 500 mA
  Return plate monitoring: impedance check before activation
  Audible tone during activation

MCU: STM32L4 (power control + safety monitor)
BLE: nRF52840 (log activation events, duration, power to NFS patient record)
Battery: 2000mAh (hours of intermittent use)
⚠ Tissue ablation device: requires medical training to operate safely
UBERON: User-specified before procedure
BOM: ~$125
```

### NFSIM-ABL-02 — Portable Focused Ultrasound (pFUS)

```
Therapeutic high-intensity focused ultrasound (HIFU):
  Frequency: 1–3 MHz
  Focal zone: 1 mm × 10 mm (tight focus)
  Intensity at focus: 1000–3000 W/cm² (ablative: >1000, sub-ablative: 100–1000)
  Applications: pain relief (rheumatoid arthritis joints), focused drug delivery enhancement,
    blood-brain barrier opening research, deep tumor hyperthermia research

Transducer: concave focused piezo array (spherically focused, 60mm aperture, 70mm focal length)
Guidance: integrated B-mode imaging (same transducer in pulsed mode)
  Alternates between imaging pulse (low power) and therapeutic pulse (high power)
  Targeting: cross-hair targeting overlay on B-mode image
Power unit: high-power RF amplifier (class-D, 100W at 1 MHz)
  Powered by 48V Li-Ion battery (1.5 Ah)
Safety: thermal dose monitoring (CEM43 algorithm: thermal dose limit 240 CEM43)
MCU: STM32H7 (real-time thermal dose integration)
UBERON: User-specified target region
⚠ Therapeutic ultrasound: research use only; tissue damage possible without proper targeting
BOM: ~$340
```

---

## 17. Hardware Domain I — Consumables and Universal Interfaces

### Complete Device List

| Device ID | Name | Technology |
|---|---|---|
| NFSIM-CON-01 | Microfluidic Sample Prep Disc | Centrifuge-driven plasma separation |
| NFSIM-CON-02 | Universal Bio-Cartridge Interface | Standardized 15-analyte cartridge format |
| NFSIM-CON-03 | Transdermal Energy Transfer Mat | Qi wireless charging for implants through skin |
| NFSIM-CON-04 | NFS Universal Gateway Hub | Central BLE + USB hub for multiple devices |
| NFSIM-CON-05 | Field Sample Collection Kit | Standardized blood/swab/stool collection |

### NFSIM-CON-01 — Microfluidic Sample Prep Disc (Lab-on-Disc)

```
Centrifuge-on-a-disc approach:
  Disc: 75mm polycarbonate disc (CD-sized)
  Channels: spiral microfluidic channels, 100µm width
  Valves: capillary burst valves (open at specific centrifugal force)
  
  Plasma separation:
    Blood enters at center → centrifuge disc at 1500 RPM
    Cells pellet to outer edge, plasma migrates to inner collection chamber
    No centrifuge machine needed → battery-powered mini-centrifuge (egg-cup size)
  
  Multi-step processing:
    Step 1 (1000 RPM): plasma separation
    Step 2 (3000 RPM): burst next valve → plasma moves to reagent zone
    Step 3 (5000 RPM): burst next valve → mixed sample moves to detection zone
    Compatible downstream readers: NFSIM-CHEM-01 cartridge slot (adapter)
  
Mini-centrifuge:
  Motor: 3-phase BLDC, 5000 RPM max
  Speed control: STM32G0 + MOSFET driver
  Run time: 5-minute spin → complete plasma separation
  Power: USB-C 5V
  Weight: 120g
```

### NFSIM-CON-02 — Universal Bio-Cartridge Interface

```
Standardized cartridge format specification (open standard):
  Dimensions: 85 × 54 × 2 mm (ISO credit-card size)
  Electrical contacts: 32-pin edge connector (0.5mm pitch gold-plated)
    Pins 1–8: electrochemical working electrodes
    Pins 9–12: reference + counter electrodes
    Pins 13–16: optical reference windows
    Pins 17–24: ISE contacts
    Pins 25–28: barcode trigger + chip ID
    Pins 29–32: temperature sensor
  Optical windows: 8 × 4mm clear windows, positioned for LED/detector alignment
  Barcode: Code 128, 1D, identifies cartridge type, lot, calibration
  
Any device designed to the NFS-Cartridge-1.0 spec can read any NFS-compatible cartridge.
Published as open standard: github.com/nanoflowsim/nfs-cartridge-standard
```

### NFSIM-CON-03 — Transdermal Energy Transfer Mat

```
Wireless power delivery through skin for implantable devices (NFC/Qi principles):
  Frequency: 1 MHz (chosen for good tissue penetration vs 13.56 MHz NFC)
  Coil: 100mm diameter TX coil, 100mm × 100mm flexible pad
  Power delivered: up to 500mW through 15mm tissue depth
  Efficiency: ~40% (TX coil → implant RX coil, tissue losses)
  Use case: charge NFSIM-IMPLANT-01 (if battery-equipped variant)
    Or: power NFSIM-IMPLANT-02 stimulator during programming session
  Safety: SAR monitoring (tissue heating limit 10 W/kg local; system stays <2 W/kg)
  BOM: ~$65
```

### NFSIM-CON-04 — NFS Universal Gateway Hub

```
Central hub connecting multiple NFS devices simultaneously:
  BLE radio: nRF5340 (multi-protocol, 8 simultaneous BLE connections)
  USB host: USB 3.0 hub (4 ports, connects USB devices: NFSIM-US-01, SEQ-01)
  Wi-Fi: ESP32-S3 (streams data to local network or cloud)
  Processing: STM32H7 (aggregates all streams, runs NFS protocol arbitration)
  Display: 3.5" TFT (shows connected device status, active data rates)
  Storage: 256GB microSD (local buffer for all connected device streams)
  Power: USB-C PD 65W input → distributed to connected devices
  Output: HDMI (shows full NanoFlowSIM dashboard on external monitor)
  Dimensions: 120×80×30mm (bedside unit)
  BOM: ~$110
```

### NFSIM-CON-05 — Field Sample Collection Kit

```
Standardized collection system for all NFS-compatible sample types:
  Blood: BD Microtainer contact-activated lancets + capillary tubes
    → NFS-compatible labeled storage tube (barcode + QR = patient ID + timestamp)
  Throat/nasal swab: flocked swabs + VTM (viral transport medium) tubes
    → Direct compatibility with NFSIM-CRISPR-01 and NFSIM-PCR-03
  Stool: OMNIgene Gut-compatible stabilized tube
    → Compatible with NFSIM-SEQ-01 (16S metagenomics)
  Saliva: passive drool tube (Oragene compatible format)
    → Compatible with NFSIM-CHEM-02 (saliva panel)
  All tubes: NFC chip embedded → tap phone → auto-links to patient NFS record
  Barcode: 2D QR code, printed at collection → scanned by NanoFlowSIM mobile app
  Cold chain indicator: time-temperature indicator strip on each tube
  BOM: ~$8 per kit (pack of 10 mixed tubes)
```

---

## 18. Full Device Specifications — All 50+ Devices

All individual device full specifications are provided across Sections 9–17. The following table provides a consolidated index of all NanoFlowSIM hardware devices with cross-references to their specification sections and BOM estimates.

| Device ID | Section | Name | Domain | BOM |
|---|---|---|---|---|
| NFSIM-PCR-01 | §9 | Portable PCR Thermocycler | Molecular | ~$148 |
| NFSIM-PCR-02 | §9 | Gel-Slip Strip Reader | Molecular | ~$83 |
| NFSIM-PCR-03 | §9 | LAMP Isothermal Reader | Molecular | ~$93 |
| NFSIM-PCR-04 | §9 | RPA Room-Temperature Reader | Molecular | ~$45 |
| NFSIM-SEQ-01 | §9 | Open Nanopore Sequencer | Molecular | ~$546 |
| NFSIM-SEQ-02 | §9 | Solid-State Nanopore Board | Molecular | ~$280 |
| NFSIM-CRISPR-01 | §9 | CRISPR Fluorescence Reader | Molecular | ~$118 |
| NFSIM-CRISPR-02 | §9 | CRISPR Lateral Flow Reader | Molecular | ~$35 |
| NFSIM-CRISPR-03 | §9 | Electrochemical CRISPR | Molecular | ~$40 |
| NFSIM-dPCR-01 | §9 | Digital Droplet PCR | Molecular | ~$285 |
| NFSIM-GELEC-01 | §9 | Portable Gel Electrophoresis | Molecular | ~$110 |
| NFSIM-GELEC-02 | §9 | Chip CE Reader | Molecular | ~$280 |
| NFSIM-US-01 | §10 | USB-C Handheld Ultrasound | Imaging | ~$471 |
| NFSIM-US-02 | §10 | Wearable Ultrasound Patch | Imaging | ~$320 |
| NFSIM-US-03 | §10 | Ingestible GI Ultrasound Capsule | Imaging | ~$580 |
| NFSIM-US-04 | §10 | Dermal Ultrasound Scanner | Imaging | ~$180 |
| NFSIM-US-05 | §10 | Radial Artery Doppler Wristband | Imaging | ~$95 |
| NFSIM-US-06 | §10 | Transcranial Doppler Headband | Imaging | ~$220 |
| NFSIM-US-07 | §10 | Endocavity Ultrasound Probe | Imaging | ~$310 |
| NFSIM-US-08 | §10 | Fetal Doppler Wearable | Imaging | ~$65 |
| NFSIM-US-09 | §10 | Ultrasound Needle Guide | Imaging | ~$145 |
| NFSIM-MRI-01 | §10 | Low-Field Portable MRI | Imaging | ~$4,520 |
| NFSIM-XRAY-01 | §10 | Portable X-Ray System | Imaging | ~$4,200 |
| NFSIM-OCT-01 | §10 | Portable SD-OCT Probe | Imaging | ~$680 |
| NFSIM-MICRO-01 | §10 | Digital Pathology Microscope | Imaging | ~$520 |
| NFSIM-CGM-01 | §11 | Open CGM Sensor | Chemical | ~$38 |
| NFSIM-SWEAT-01 | §11 | Sweat Chemistry Patch | Chemical | ~$95 |
| NFSIM-CHEM-01 | §11 | Blood Chemistry Analyzer | Chemical | ~$185 |
| NFSIM-CHEM-02 | §11 | Saliva Chemistry Analyzer | Chemical | ~$80 |
| NFSIM-CHEM-03 | §11 | Urine Dipstick Reader | Chemical | ~$55 |
| NFSIM-CHEM-04 | §11 | Lipid Panel Analyzer | Chemical | ~$120 |
| NFSIM-CHEM-05 | §11 | Lactate Meter | Chemical | ~$45 |
| NFSIM-CHEM-06 | §11 | Ketone / BHB Monitor | Chemical | ~$35 |
| NFSIM-CHEM-07 | §11 | Cortisol Sensor | Chemical | ~$90 |
| NFSIM-CHEM-08 | §11 | Continuous Lactate Implant | Chemical | ~$55 |
| NFSIM-OXY-01 | §11 | NIRS Oxygenation Array | Chemical | ~$180 |
| NFSIM-BREATH-01 | §11 | Breath Metabolomics | Chemical | ~$210 |
| NFSIM-ECG-01 | §12 | 30-Day ECG Patch | Electrical | ~$38 |
| NFSIM-ECG-02 | §12 | 12-Lead ECG Vest | Electrical | ~$145 |
| NFSIM-ECG-03 | §12 | 3-Lead Holter Patch | Electrical | ~$52 |
| NFSIM-EEG-01 | §12 | Dry EEG Headset (8–16ch) | Electrical | ~$180 |
| NFSIM-EEG-02 | §12 | 64ch Wet EEG Research | Electrical | ~$420 |
| NFSIM-EEG-03 | §12 | Around-Ear EEG | Electrical | ~$95 |
| NFSIM-EMG-01 | §12 | 8ch EMG Armband | Electrical | ~$115 |
| NFSIM-EMG-02 | §12 | Single EMG Patch | Electrical | ~$35 |
| NFSIM-NEURAL-01 | §12 | High-Density ECoG Array | Electrical | ~$650 |
| NFSIM-NEURAL-02 | §12 | Intracortical Headstage | Electrical | ~$380 |
| NFSIM-EOG-01 | §12 | Electrooculography Glasses | Electrical | ~$88 |
| NFSIM-EDA-01 | §12 | Electrodermal Activity Sensor | Electrical | ~$42 |
| NFSIM-CAP-01 | §13 | GI Optical Camera + Chemistry | Capsule | ~$390 |
| NFSIM-CAP-02 | §13 | GI Ultrasound Capsule | Capsule | ~$580 |
| NFSIM-CAP-03 | §13 | DNA/RNA Capture Capsule | Capsule | ~$95 |
| NFSIM-CAP-04 | §13 | Full Multi-Modal Capsule | Capsule | ~$780 |
| NFSIM-CAP-05 | §13 | Core Temperature Capsule | Capsule | ~$25 |
| NFSIM-CAP-06 | §13 | pH/Pressure/Motility Capsule | Capsule | ~$185 |
| NFSIM-CAP-07 | §13 | Microbiome Sampling Capsule | Capsule | ~$45 |
| NFSIM-CAP-08 | §13 | Drug Delivery Verification | Capsule | ~$110 |
| NFSIM-CAP-09 | §13 | Oxygen Mapping Capsule | Capsule | ~$135 |
| NFSIM-CAP-10 | §13 | GI Bleeding Detection | Capsule | ~$120 |
| NFSIM-PATCH-01 | §14 | Biopotential + Motion Patch | Wearable | ~$48 |
| NFSIM-PATCH-02 | §14 | Wound Healing Monitor | Wearable | ~$85 |
| NFSIM-PATCH-03 | §14 | Iontophoresis Drug Controller | Wearable | ~$110 |
| NFSIM-IMPLANT-01 | §14 | Subcutaneous Sensor Node | Implant | ~$280 |
| NFSIM-IMPLANT-02 | §14 | Neural Stimulation Platform | Implant | ~$450 |
| NFSIM-FLOW-01 | §15 | Portable Flow Cytometer | Flow/Env | ~$380 |
| NFSIM-ENV-01 | §15 | Bio-Aerosol Sampler | Flow/Env | ~$95 |
| NFSIM-ENV-02 | §15 | Water Pathogen Station | Flow/Env | ~$145 |
| NFSIM-ENV-03 | §15 | Soil Microbiome Sampler | Flow/Env | ~$85 |
| NFSIM-ENV-04 | §15 | Air Quality Biomonitor | Flow/Env | ~$75 |
| NFSIM-ENV-05 | §15 | Mosquito Trap + Genomics | Flow/Env | ~$160 |
| NFSIM-DEL-01 | §16 | Insulin Patch Pump | Interventional | ~$95 |
| NFSIM-DEL-02 | §16 | Drug Implant (Osmotic) | Interventional | ~$185 |
| NFSIM-DEL-03 | §16 | Microneedle Drug Patch | Interventional | ~$15 |
| NFSIM-ABL-01 | §16 | RF Cautery Pen | Interventional | ~$125 |
| NFSIM-ABL-02 | §16 | Portable Focused Ultrasound | Interventional | ~$340 |
| NFSIM-CON-01 | §17 | Sample Prep Disc | Consumable | ~$55 |
| NFSIM-CON-02 | §17 | Universal Cartridge Interface | Consumable | Open spec |
| NFSIM-CON-03 | §17 | Transdermal Energy Mat | Consumable | ~$65 |
| NFSIM-CON-04 | §17 | Universal Gateway Hub | Consumable | ~$110 |
| NFSIM-CON-05 | §17 | Field Sample Collection Kit | Consumable | ~$8/kit |

---

## 19. Universal NFS Communication Protocol

### 19.1 Overview

All NanoFlowSIM hardware devices share the NFS (NanoFlowSIM) communication protocol. It is intentionally minimal, self-describing, and implementable on any microcontroller with ≥32 KB flash. Every packet carries enough context to be ingested by the NanoFlowSIM platform without side-channel metadata — device ID, patient ID, UBERON region, timestamp, data type, and quality score are all embedded in the packet itself.

### 19.2 Physical Transport Layer

| Transport | Frequency / Speed | Use Case | Devices |
|---|---|---|---|
| BLE 5.0 GATT | 2.4 GHz, 2 Mbps PHY | Primary wireless for wearables and portables | ECG, EEG, EMG, CGM, SWEAT, PCR-01–04, CRISPR, all patches |
| USB-C (USB 2.0 CDC-ACM) | Full Speed 12 Mbps | Lab devices, firmware update, high-volume log dump | PCR-01, SEQ-01, GELEC-01, FLOW-01, US-01, OCT-01, MICRO-01 |
| USB-C (USB 3.1 Gen1) | 5 Gbps | High-bandwidth imaging | US-01, OCT-01, MICRO-01 |
| 434 MHz FSK | MICS / ISM band, 76.8 kbps | Ingestible capsules (body-penetrating radio) | CAP-01 through CAP-10 |
| NFC ISO 15693 | 13.56 MHz, passive | Low-power implant/sensor readout | CGM-01, IMPLANT-01 |
| Wi-Fi 802.11ac | 5 GHz, 300 Mbps | High-bandwidth imaging streams | US-01 Wi-Fi option, XRAY-01 FPD |
| Qi inductive | 100–200 kHz, 5W | Implant power and data (therapeutic) | IMPLANT-01, IMPLANT-02 |

### 19.3 BLE GATT Profile Definitions (NFS Profile v1.0)

All BLE-capable NFS devices implement the following service hierarchy.

#### Device Information Service (0x180A — Standard BLE)

Standard BLE Device Information Service, implementing:
- Manufacturer Name String: "NanoFlowSIM"
- Model Number String: e.g., "NFSIM-ECG-01"
- Hardware Revision String: e.g., "RevA"
- Firmware Revision String: e.g., "1.2.3"
- Serial Number String: unique 6-char hex device serial

#### NFS Device Control Service

UUID: `4a6e7300-1000-4a6e-b000-4a6e00000001`

| UUID Suffix | Characteristic Name | Properties | Size | Description |
|---|---|---|---|---|
| -1001 | Device State | Read + Notify | 8 bytes | Status byte [0=idle,1=measuring,2=calibrating,3=complete,4=error] + error code + battery% + flags |
| -1002 | Command | Write | 20 bytes | Opcode [0x01=start,0x02=stop,0x03=pause,0x04=resume,0x05=calibrate,0x10=load_protocol,0x20=ota_start] + params |
| -1003 | Configuration | Read + Write | 244 bytes | JSON blob (device-specific parameters, fragmented over multiple writes if needed) |
| -1004 | Error Log | Read | 100 bytes | Latest error: code (u16) + timestamp (u32) + description string |
| -1005 | Calibration Status | Read + Notify | 12 bytes | Last calibration timestamp (u32) + coefficients digest (u64) |

#### NFS Data Stream Service

UUID: `4a6e7300-2000-4a6e-b000-4a6e00000002`

| UUID Suffix | Characteristic Name | Properties | Size | Description |
|---|---|---|---|---|
| -2001 | Primary Stream | Notify | 244 bytes | Real-time data payload (max BLE 5.0 ATT MTU with DLE) |
| -2002 | Secondary Stream | Notify | 244 bytes | Secondary sensor data (e.g., accelerometer when primary is ECG) |
| -2003 | Batch Upload | Indicate | 512 bytes (extended MTU) | Historical data segments on sync request |
| -2004 | Stream Control | Write | 4 bytes | [0x01=start, 0x02=stop, interval_ms(u16)] |
| -2005 | Data Available | Read + Notify | 4 bytes | Unsent record count (u32) — alerts host to initiate batch dump |

#### NFS Metadata Service

UUID: `4a6e7300-3000-4a6e-b000-4a6e00000003`

| UUID Suffix | Characteristic Name | Properties | Size | Description |
|---|---|---|---|---|
| -3001 | Patient Assignment | Write | 36 bytes | Patient UUID (16 bytes binary) + salt (8 bytes) |
| -3002 | UBERON Tag | Read + Write | 20 bytes | Primary UBERON code (ASCII, null-terminated, e.g., "UBERON:0000948") |
| -3003 | Session ID | Read | 16 bytes | Current session UUID (binary) |
| -3004 | Timestamp Sync | Write | 8 bytes | Unix timestamp microseconds (u64, big-endian) |
| -3005 | Device Location | Write | 12 bytes | GPS lat/lng float32 pair + altitude float32 (for environmental devices) |
| -3006 | Research Consent | Read + Write | 1 byte | Consent flags byte [bit0=research_share, bit1=anonymized_cloud, bit2=institution_access] |

### 19.4 Universal NFS JSON Packet (Full Specification)

All NFS devices ultimately serialize their session outputs as NFS JSON packets for archival, exchange, and ingestion by the NanoFlowSIM platform.

**Mandatory fields (all devices, all data types):**

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
    "secondary": ["UBERON:0000178"],
    "confidence": 0.99
  },
  "data_type": "ecg_continuous_segment",
  "data": { },
  "quality": {
    "score": 0.92,
    "signal_noise_ratio_db": 28.4,
    "artifact_fraction": 0.08,
    "electrode_impedance_kohm": [5.2, 6.1],
    "notes": ""
  },
  "device_status": {
    "battery_pct": 74,
    "temperature_c": 36.2,
    "firmware_version": "1.2.3",
    "hardware_revision": "RevA",
    "uptime_seconds": 86400,
    "error_code": 0
  }
}
```

**Domain-specific `data` payloads:**

*ECG Continuous Segment:*
```json
"data": {
  "lead": "II",
  "sample_rate_hz": 256,
  "duration_seconds": 30,
  "samples_int16": "base64-encoded-int16-array",
  "lsb_uV": 4.88,
  "r_peaks_sample_indices": [256, 512, 770, 1028],
  "rr_intervals_ms": [996, 1007, 1011],
  "hr_bpm": 60,
  "hrv_rmssd_ms": 42.1,
  "detected_events": [
    {"type": "normal_sinus", "start_sample": 0, "confidence": 0.97},
    {"type": "pvc", "start_sample": 770, "confidence": 0.84}
  ],
  "afib_probability": 0.02,
  "qt_interval_ms": 412,
  "qrs_duration_ms": 88
}
```

*Glucose (CGM) Segment:*
```json
"data": {
  "glucose_mg_dl": 112,
  "glucose_mmol_l": 6.22,
  "trend": "stable",
  "trend_arrow": "→",
  "rate_of_change_mg_dl_per_min": -0.2,
  "sensor_temperature_c": 36.8,
  "calibration_age_h": 2.3,
  "sensor_wear_day": 3,
  "interstitial_lag_min": 7
}
```

*PCR Run:*
```json
"data": {
  "protocol_name": "COVID_LAMP_Taqman",
  "protocol_version": "2.1",
  "assay_type": "LAMP",
  "target": "SARS-CoV-2 N-gene",
  "cycles_completed": 40,
  "total_runtime_seconds": 1800,
  "result": "positive",
  "ct_value": 28.4,
  "amplification_efficiency_pct": 94.2,
  "thermal_profile_summary": [
    {"stage": "denaturation", "target_c": 95.0, "achieved_c": 94.8, "duration_s": 30},
    {"stage": "annealing", "target_c": 58.0, "achieved_c": 57.9, "duration_s": 20}
  ],
  "fluorescence_channels": [
    {"channel": "FAM", "baseline_rfu": 104, "endpoint_rfu": 8240, "ct": 28.4}
  ]
}
```

*Nanopore Sequencing Read:*
```json
"data": {
  "run_id": "uuid",
  "read_id": "uuid",
  "channel": 142,
  "start_time_s": 1748304000.0,
  "duration_s": 4.2,
  "template_length_bp": 1680,
  "raw_signal_samples": 105000,
  "basecall_status": "complete",
  "basecall_model": "dna_r10.4.1_e8.2_400bps_sup@v4.3.0",
  "mean_qscore": 18.4,
  "sequence_fasta_ref": "minio://runs/uuid/reads/read_id.fastq",
  "alignment": {
    "reference": "GRCh38",
    "chromosome": "chr17",
    "start": 43044295,
    "end": 43045975,
    "strand": "+",
    "identity_pct": 98.2
  }
}
```

*Capsule Multi-Sensor:*
```json
"data": {
  "position_zone": "small_intestine_jejunum",
  "position_uberon": "UBERON:0002115",
  "position_confidence": 0.84,
  "transit_time_min": 185,
  "capsule_orientation_deg": {"roll": 22, "pitch": -5, "yaw": 180},
  "pH": 7.18,
  "temperature_c": 37.1,
  "dissolved_o2_pct": 8.3,
  "pressure_mmhg": 18.4,
  "image_frame_ids": ["uuid-frame-001", "uuid-frame-002"],
  "image_storage_ref": "minio://capsule-runs/session-uuid/frames/"
}
```

*NIRS Oxygenation:*
```json
"data": {
  "site": "right_prefrontal_cortex",
  "source_detector_separation_mm": 35,
  "wavelengths_nm": [730, 850],
  "rSO2_pct": 68.4,
  "delta_HbO2_uM_mm": 2.1,
  "delta_HHb_uM_mm": -0.8,
  "HbDiff_uM_mm": 2.9,
  "DPF": 6.26,
  "baseline_window_s": 60
}
```

*Ultrasound Frame:*
```json
"data": {
  "probe_type": "linear",
  "frequency_mhz": 7.5,
  "depth_cm": 8.0,
  "mode": "B",
  "frame_count": 1,
  "frame_rate_fps": 30,
  "image_width_px": 512,
  "image_height_px": 512,
  "pixel_spacing_mm": [0.075, 0.156],
  "dicom_uid": "1.2.3.4.5678",
  "frames_ref": "minio://ultrasound/session-uuid/frame-001.dcm"
}
```

*Gel Electrophoresis:*
```json
"data": {
  "gel_type": "1.5_pct_agarose",
  "run_voltage_v": 200,
  "run_duration_s": 480,
  "buffer": "TBE",
  "stain": "SYBR_Safe",
  "ladder_detected": true,
  "ladder_type": "1kb_plus",
  "lanes": [
    {
      "lane_number": 1,
      "bands": [
        {"size_bp": 500, "intensity_au": 0.82, "pct_of_lane": 55},
        {"size_bp": 250, "intensity_au": 0.44, "pct_of_lane": 29}
      ]
    }
  ],
  "image_ref": "minio://gel-runs/session-uuid/gel_image.png"
}
```

### 19.5 USB Serial Command Protocol (NFS-SERIAL v1.0)

For USB-connected devices via CDC-ACM virtual serial port (115200 baud or USB-CDC full-speed):

```
Command format: "NFS:<COMMAND> [<PARAM_JSON>]\r\n"
Response:       "NFS:OK [<RESPONSE_JSON>]\r\n"
Error:          "NFS:ERR <code> <message>\r\n"

Error codes:
  1001: Device busy (measurement in progress)
  1002: Invalid parameter value
  1003: Storage full
  1004: Calibration required before operation
  1005: Hardware fault (specific sub-code in message)
  1006: Patient ID not assigned
  2001: OTA: image integrity check failed
  2002: OTA: insufficient flash space

Command Set:
  NFS:PING
    → NFS:OK {"device":"NFSIM-PCR-01","fw":"1.2.3","hw":"RevA","proto":"1.0.0"}

  NFS:STATUS
    → NFS:OK {"state":"idle","battery_pct":74,"uptime_s":86400,"storage_used_pct":12,
               "patient_id":"uuid","uberon":"UBERON:0000178","last_session":"uuid"}

  NFS:START {"session_id":"uuid","patient_id":"uuid"}
    → NFS:OK {"session_id":"uuid","started_at":1748304000}

  NFS:STOP
    → NFS:OK {"session_id":"uuid","records_saved":3600,"storage_pct":15}

  NFS:PAUSE
    → NFS:OK

  NFS:RESUME
    → NFS:OK

  NFS:CONFIGURE {"sample_rate_hz":512,"gain":24,"alert_hr_high":150}
    → NFS:OK {"applied":{"sample_rate_hz":512,"gain":24,"alert_hr_high":150}}

  NFS:CALIBRATE {"method":"two_point","ref_values":[100,200]}
    → NFS:CALIBRATING (async, status updates via NFS:STATUS)
    ... NFS:OK {"cal_completed":true,"coefficients":[0.982,2.3],"timestamp":1748304120}

  NFS:PATIENT {"patient_id":"uuid"}
    → NFS:OK {"patient_id":"uuid","assigned":true}

  NFS:UBERON {"primary":"UBERON:0000948","secondary":["UBERON:0000178"]}
    → NFS:OK

  NFS:DUMP {"start_unix_us":1748300000000000,"end_unix_us":1748304000000000}
    → NFS:OK {"record_count":720,"data_size_bytes":1440000}
    [followed by streaming JSON-lines of NFS packets until done]
    → NFS:DUMP_COMPLETE {"records_sent":720}

  NFS:UPDATE
    → NFS:OK {"ota_mode":"active","max_image_size_bytes":917504}
    [host sends firmware binary in 512-byte chunks via subsequent writes]
    [device verifies SHA-256, reboots into new firmware]

  NFS:VERSION
    → NFS:OK {"fw":"1.2.3","hw":"RevA","proto":"1.0.0","build_date":"2026-01-15"}

  NFS:RESET {"factory":false}
    → NFS:OK (clears session data, preserves calibration and patient ID)
    NFS:RESET {"factory":true}
    → NFS:OK (full factory reset, clears everything including calibration)
```

### 19.6 Capsule 434 MHz Frame Protocol (NFS-RADIO v1.0)

Used by all NFSIM-CAP devices for body-penetrating radio communication.

```
Frame structure (variable length, max 256 bytes payload):
  [PREAMBLE:2][SYNC_WORD:2][DEVICE_ID:4][SEQUENCE:2][TYPE:1][FLAGS:1][LENGTH:2][PAYLOAD:N][CRC16:2]

Field definitions:
  PREAMBLE:    0xAA 0xAA (bit synchronization pattern)
  SYNC_WORD:   0x7E 0x5E (frame delimiter, unique to NFS-RADIO)
  DEVICE_ID:   Capsule serial number (4 bytes, factory-programmed)
  SEQUENCE:    Rolling 16-bit counter (wraps at 65535, detects dropped frames)
  TYPE:
    0x01 = Sensor data (pH, temperature, O2, pressure)
    0x02 = Image frame header (begins multi-frame image sequence)
    0x03 = Image frame chunk (continuation of image sequence)
    0x04 = Heartbeat / keepalive (no payload)
    0x05 = Position update (zone estimate + confidence)
    0x06 = Alert (battery low, sensor fault, collection triggered)
    0x07 = Acknowledgment request (reliable delivery for critical events)
  FLAGS:
    bit 0: ACK requested
    bit 1: Encrypted payload (future)
    bit 2: Compressed payload
    bits 3–7: Reserved
  LENGTH:      Payload length in bytes (u16, big-endian)
  PAYLOAD:     Type-specific data (see below)
  CRC16:       CRC-CCITT (polynomial 0x1021, initial value 0xFFFF)
               Covers: DEVICE_ID through end of PAYLOAD

Sensor payload (TYPE=0x01, 14 bytes):
  [TIMESTAMP:4][PH_X100:2][TEMP_X100:2][O2_X100:2][PRESSURE_X10:2][ZONE_ID:1][FLAGS:1]
  TIMESTAMP:    Seconds since capsule power-on (u32)
  PH_X100:      pH × 100 (u16), e.g., 718 = pH 7.18
  TEMP_X100:    Temperature °C × 100 (u16), e.g., 3712 = 37.12°C
  O2_X100:      Dissolved O2 % × 100 (u16), e.g., 830 = 8.30%
  PRESSURE_X10: Pressure mmHg × 10 (u16), e.g., 184 = 18.4 mmHg
  ZONE_ID:      Current zone estimate (1=esophagus, 2=stomach, 3=duodenum,
                4=jejunum, 5=ileum, 6=cecum, 7=colon, 8=rectum, 0=unknown)
  FLAGS:        sensor validity bits [bit0=pH_valid, bit1=temp_valid, bit2=O2_valid, bit3=pres_valid]

Image header (TYPE=0x02, 13 bytes):
  [FRAME_ID:4][CAMERA_ID:1][JPEG_SIZE:3][WIDTH:2][HEIGHT:2][QUALITY:1]
  Followed by image chunks (TYPE=0x03):
  [FRAME_ID:4][CHUNK_INDEX:2][CHUNK_COUNT:2][DATA:N]

Position update (TYPE=0x05, 10 bytes):
  [TIMESTAMP:4][ZONE_ID:1][ZONE_CONFIDENCE_X100:2][TRANSIT_MIN:2][PH_X100:1_byte_estimate]

Alert (TYPE=0x06, 5 bytes):
  [TIMESTAMP:4][ALERT_CODE:1]
  Alert codes:
    0x01: Battery < 20%
    0x02: Battery < 5% (critical)
    0x03: pH sensor fault
    0x04: Collection chamber opened (CAP-03, CAP-07)
    0x05: Collection chamber sealed
    0x06: Drug release triggered (CAP-08)
    0x07: Bleeding detected threshold crossed (CAP-10)

Retransmission:
  Image headers: external receiver sends ACK within 200ms
  Capsule retransmits header up to 3× if no ACK received
  Image chunks: receiver tracks missing chunks, requests retransmit at frame end
  Sensor data: fire-and-forget with redundant transmission (every reading sent 2×)
  Alerts: retransmitted every 30s until ACK received

External belt receiver:
  6× 434 MHz patch antennas at abdomen positions
  Each: CC1101 (Silicon Labs) front-end + STM32 SPI interface
  Diversity combining: maximal ratio combining (MRC) in firmware
  Bridge: nRF52840 → BLE → phone app
  Decoding: full NFS-RADIO parser with CRC verification
  Latency: sensor data appears on phone within 500ms of capsule transmission
```

### 19.7 Data Compression Standards (Per Data Type)

```
ECG waveforms:
  Algorithm: Delta encoding (successive-sample difference) → run-length encoding
  Typical compression: 70–80% (ECG baseline is smooth between R-peaks)
  Implementation: 16-bit delta, huffman codes for common delta values

EEG / EMG raw waveforms:
  Algorithm: LZ4 block compression (fast, hardware-feasible, ~40% compression typical)
  Alternative: wavelet thresholding (higher compression, lossy option)

Images (ultrasound, capsule):
  Algorithm: JPEG 2000 (lossless or visually lossless quality 90)
  Typical compression: 10:1 lossless, 20:1 at quality 85

Genomic data:
  Algorithm: bgzf (block gzip, BGZF standard for FASTQ/BAM)
  Standards: .fastq.gz, .bam, .vcf.gz — industry-standard compression

Chemical time-series (CGM, NIRS):
  Algorithm: Delta + zigzag encoding (small values) → LZ4
  Typical compression: 60% for smooth metabolic curves

DICOM imaging:
  Algorithm: JPEG 2000 lossless (DICOM Transfer Syntax 1.2.840.10008.1.2.4.90)
  All DICOM output is standards-compliant for downstream compatibility
```

### 19.8 Security Considerations

```
Encryption at rest:
  SQLite database: SQLCipher AES-256-CBC with key derived from device keychain
  MinIO objects: server-side AES-256 encryption at object level
  Device NVS (patient ID, calibration): AES-128 with hardware-derived key (nRF52840 CRYPTOCELL)

Encryption in transit:
  BLE: LE Secure Connections (BLE 4.2+), 128-bit AES-CCM
  USB: no encryption (local physical connection assumed trusted)
  Cloud sync: TLS 1.3 with certificate pinning
  434 MHz capsule radio: future: AES-128 CTR mode payload encryption (currently unencrypted)

Patient ID handling:
  Device stores: HMAC-SHA256(patient_uuid + device_secret) — never raw UUID
  Server-side mapping table: maintained only on patient-controlled infrastructure
  De-identification: strip patient_id before research data contribution

Device authentication:
  Device identity: RSA-2048 keypair burned at manufacture (private key in secure element)
  Certificate: signed by NanoFlowSIM root CA (for community-verified devices)
  BLE bonding: LE Secure Connections + numeric comparison (prevents MITM)

OTA security:
  Firmware images signed with ed25519 (64-byte signature, small and fast)
  Bootloader verifies signature before accepting image
  Downgrade prevention: version counter stored in OTP (one-time-programmable) memory
```

---

## 20. Firmware Architecture — Universal

### 20.1 RTOS Selection Per Device Class

| Device Class | RTOS | Justification |
|---|---|---|
| Ultra-low-power (CGM-01, EDA-01, CAP-05) | Bare-metal ISR state machine | FreeRTOS overhead (200+ µA) unacceptable at <5 µA target |
| Standard (ECG-01, PCR-01, EEG-01, EMG-01) | FreeRTOS 10.5.1 | Mature, small footprint, excellent STM32/nRF52 support |
| Complex multi-sensor (CHEM-01, US-01) | FreeRTOS + CMSIS-RTOS2 | Higher task count, memory-protected domains |
| Linux-capable (MICRO-01, MRI-01 console) | Buildroot Linux 2024.02 + systemd | Full OS needed for camera, USB host, FPGA comms, AI inference |
| Capsule (CAP-01 through CAP-10) | Bare-metal with cooperative scheduler | Power budget critical, no preemption needed |

### 20.2 Universal Task Architecture (FreeRTOS Devices)

```
┌──────────────────────────────────────────────────────────────────────┐
│                     NFS Firmware Task Hierarchy                      │
├───────────────────┬──────────────────────────────────────────────────┤
│ Priority 7 (MAX)  │ SensorAcquisitionTask                            │
│                   │  Rate: hardware-driven (ADC DMA interrupt)       │
│                   │  Stack: 2KB                                      │
│                   │  Function: raw sensor read → ring buffer         │
│                   │  ISRs handled here: ADC complete, DMA half/full  │
├───────────────────┼──────────────────────────────────────────────────┤
│ Priority 6        │ SignalProcessingTask                              │
│                   │  Rate: triggered by ring buffer threshold         │
│                   │  Stack: 4–16KB (algorithm-dependent)             │
│                   │  Function: filtering, feature extraction,         │
│                   │           on-device AI inference (TFLite Micro)  │
├───────────────────┼──────────────────────────────────────────────────┤
│ Priority 5        │ StorageTask                                       │
│                   │  Rate: triggered by processed data batch          │
│                   │  Stack: 2KB                                      │
│                   │  Function: write to flash/eMMC/SD                │
│                   │           manages file system (LittleFS or FatFS)│
├───────────────────┼──────────────────────────────────────────────────┤
│ Priority 4        │ CommunicationsTask                                │
│                   │  Rate: event-driven + periodic (100ms BLE tick)  │
│                   │  Stack: 4KB                                      │
│                   │  Function: BLE GATT updates, USB CDC I/O,        │
│                   │           NFS packet assembly and transmission    │
├───────────────────┼──────────────────────────────────────────────────┤
│ Priority 3        │ DeviceControlTask                                 │
│                   │  Rate: 50ms polling + command event queue         │
│                   │  Stack: 2KB                                      │
│                   │  Function: command processing, mode FSM,          │
│                   │           configuration management                │
├───────────────────┼──────────────────────────────────────────────────┤
│ Priority 2        │ PowerManagementTask                               │
│                   │  Rate: 1000ms                                     │
│                   │  Stack: 1KB                                      │
│                   │  Function: battery polling, thermal monitoring,  │
│                   │           sleep/wake decisions, alert thresholds  │
├───────────────────┼──────────────────────────────────────────────────┤
│ Priority 1 (MIN)  │ SystemMaintenanceTask                             │
│                   │  Rate: 10000ms                                    │
│                   │  Stack: 2KB                                      │
│                   │  Function: watchdog feed, OTA management,         │
│                   │           error log flush, uptime tracking        │
└───────────────────┴──────────────────────────────────────────────────┘

Inter-task communication:
  Ring buffers (lock-free SPSC): SensorAcq → SignalProc → Storage
  FreeRTOS queues (thread-safe): SignalProc → Comms (processed data packets)
  FreeRTOS event groups: mode changes, alert triggers, calibration events
  Shared memory with mutex: device configuration struct (accessed by Control + Comms)
  Notification values: fast task wake signals (binary semaphore equivalent)
```

### 20.3 Memory Map (STM32H743 Reference — Adapt Per MCU)

```
Flash layout (2 MB):
  0x0800_0000 – 0x0800_FFFF: Bootloader Stage 1 (64 KB) — ROM-resident, signed
  0x0801_0000 – 0x0801_FFFF: Bootloader Stage 2 (64 KB) — supports USB DFU + BLE OTA
  0x0802_0000 – 0x080F_FFFF: Application firmware (896 KB)
  0x0810_0000 – 0x081E_FFFF: OTA staging area (960 KB) — receives new firmware image
  0x081F_0000 – 0x081F_7FFF: Configuration NVS (32 KB, LittleFS wear-leveled)
  0x081F_8000 – 0x081F_FFFF: Factory calibration (32 KB, write-once after QC)

SRAM layout (1 MB total, SRAM1 + SRAM2 + SRAM3):
  0x2000_0000 – 0x2001_FFFF: FreeRTOS heap (128 KB) — configurable
  0x2002_0000 – 0x2005_FFFF: Task stacks (256 KB) — statically allocated
  0x2006_0000 – 0x200B_FFFF: Sensor ring buffers (384 KB) — DMA target
  0x200C_0000 – 0x200F_FFFF: Signal processing workspace (256 KB)

DTCM (128 KB): ISR code + critical timing data (copied from flash at boot)
ITCM (64 KB): Time-critical ISR handlers (zero wait-state access)
External SPI flash (W25Q128, 16 MB):
  Partition 0 (4 MB): Session log (rolling, newest first)
  Partition 1 (4 MB): Protocol library (JSON PCR/measurement programs)
  Partition 2 (4 MB): AI model storage (TFLite INT8 models)
  Partition 3 (4 MB): Reserve / extended session log overflow
```

### 20.4 Two-Phase Initialization (All FreeRTOS Devices)

```c
// Phase 1: Pre-RTOS bare-metal initialization
void SystemInit_Phase1(void) {
    // 1. Configure system clocks (HSE → PLL → 480 MHz HCLK)
    SystemClock_Config();
    // 2. Enable instruction cache, data cache, prefetch buffer
    SCB_EnableICache();
    SCB_EnableDCache();
    // 3. Configure IWDG (independent watchdog, 30-second timeout)
    MX_IWDG_Init();
    // 4. Initialize GPIO (all pins to known state)
    MX_GPIO_Init();
    // 5. Initialize debug UART (115200, for early boot messages)
    MX_USART1_UART_Init();
    // 6. Read battery voltage — if critically low (<3.3V), enter emergency halt
    if (Battery_ReadVoltage() < 3300) { Emergency_LowBattery_Halt(); }
    // 7. Initialize SPI flash — load configuration NVS
    SPI_Flash_Init();
    NVS_Load_Config(&device_config);
    // 8. Load calibration coefficients from factory partition
    Calibration_Load(&cal_data);
    // 9. Initialize sensor hardware (reset, configure registers)
    Sensor_HW_Init();
    // 10. Initialize BLE/radio hardware
    Radio_Init();
    // 11. Create FreeRTOS tasks and data structures
    RTOS_CreateTasks();
    // 12. Start FreeRTOS scheduler → enters Phase 2
    vTaskStartScheduler();
}

// Phase 2: RTOS task initialization (inside each task's startup block)
// Each task starts suspended, DeviceControlTask decides what to activate
// based on loaded configuration and operational mode.
```

### 20.5 Calibration Architecture

```
Calibration data structure (stored in factory flash partition):

typedef struct {
    uint32_t magic;                  // 0xNF5CA100 — identifies valid calibration
    uint16_t version;                // calibration data format version
    uint8_t  device_serial[8];       // factory-assigned serial
    uint32_t calibration_date_unix;  // when calibration was performed
    uint32_t calibration_expiry;     // 0 = no expiry, else unix timestamp
    char     calibrated_by[32];      // operator ID or "FACTORY"
    float    coefficients[32];       // device-specific cal values
    float    reference_values[16];   // reference standards used during cal
    float    residual_errors[16];    // fit residuals per calibration point
    char     notes[128];             // free text (lot number, ambient conditions)
    uint32_t checksum;               // CRC32 of all above fields
} CalibrationRecord_t;

Calibration types:
  FACTORY (0x01): Performed at manufacturing, stored in write-once sector
    Never overwritten by user or field operations
    Device will not ship without valid factory calibration
  FIELD (0x02): Performed by user pre-measurement or periodically
    Stored in writable NVS partition, overwrites previous field calibration
    Linked to patient session (which session triggered recalibration)
  AUTO (0x03): Continuous drift correction in firmware (not stored)
    Applied in real-time during measurement
    Example: baseline drift correction for ISE electrodes over time
  VERIFICATION (0x04): Post-calibration accuracy check against known standard
    Stored as metadata confirming calibration validity

Calibration workflow:
  1. NFS:CALIBRATE {"method":"two_point","ref_1":100,"ref_2":200} (USB command)
  2. Device: enters CALIBRATING state
  3. Device: measures known reference at concentration 1 → internal reading
  4. Device: measures known reference at concentration 2 → internal reading
  5. Device: computes linear fit: slope = (ref2-ref1)/(raw2-raw1), offset = ref1 - slope*raw1
  6. Device: stores new field calibration → CALIBRATING → IDLE
  7. Device: all subsequent measurements apply: value = slope * raw + offset
```

### 20.6 OTA Firmware Update (All Devices)

```
Trigger methods:
  USB: NFS:UPDATE command over USB-CDC
  BLE: Write 0x20 (OTA_START opcode) to Command characteristic (-1002)
  Physical: Hold BOOT button on power-up → enters USB DFU mode (STM32 built-in)

BLE OTA Protocol:
  1. Host writes UPDATE_INIT packet to Batch Upload characteristic:
     {cmd:"update_init", fw_size:524288, fw_sha256:"abc123...", target_version:"1.3.0"}
  2. Device checks:
     - Battery >25% (refuse if too low → would brick device)
     - Target version > current version (refuse downgrade unless forced flag set)
     - Sufficient flash space in OTA staging area
  3. Device responds: {"status":"ready","chunk_size":512,"chunks_expected":1024}
  4. Host sends firmware in 512-byte BLE Indicate chunks (reliable delivery)
     Device: receives → writes sequentially to OTA staging area → CRC check per 4KB block
     Every 64 chunks: device sends progress notification {"chunks_received":64,"crc_ok":true}
  5. After all chunks received: device verifies SHA-256 of complete image
     If valid: {"status":"image_verified","will_reboot":true}
     If invalid: {"status":"image_corrupt","error":"sha256_mismatch"} → OTA area cleared
  6. Device sets OTA boot flag in RTC backup register → resets
  7. Bootloader: reads OTA boot flag → validates image (ed25519 signature check)
     If valid: copies image to application partition → clears OTA flag → boots new firmware
     If invalid: clears OTA flag → boots old firmware (automatic safe rollback)
  8. New firmware boots: sends {"status":"ota_complete","new_version":"1.3.0"} via BLE

Rollback protection:
  If new firmware fails to reach operational state within 30 seconds (watchdog not fed):
  Bootloader detects incomplete boot → reverts application partition → boots previous firmware
  Patient data is never lost during OTA (stored in separate flash partition)
```

### 20.7 Power Management Per Device Class

```
Wearable ECG Patch (NFSIM-ECG-01) power budget:
  State: Active ECG recording at 256 Hz
    ADS1291: 300 µA
    nRF52840 MCU: 6 mA (active Cortex-M4F)
    BLE advertising only (no connection): +20 µA
    Total active: ~6.3 mA
  State: BLE connected streaming (rare — alert mode)
    Add BLE TX: +5 mA → total 11.3 mA
  State: Between samples (sleep, 1ms active / 3ms sleep at 256 Hz)
    MCU in WFI (wait for interrupt): 200 µA
    ADS1291 in standby: 2 µA
    Blended: ~250 µA effective
  Average over duty cycle:
    250 µA × 0.99 (sleep fraction) + 6.3 mA × 0.01 (active) = 311 µA average
  Battery life: 200 mAh / 0.311 mA = 643 hours = 26.8 days ✓ (exceeds 21-day spec)

Portable PCR (NFSIM-PCR-01) power budget:
  Heating phase (95°C): TEC at 6A × 5V = 30W → TEC driver efficiency 85% → 35W input
  Cooling phase (4°C): TEC reversed, similar draw
  Annealing (58°C): partial duty cycle PWM → ~15W average during ramp
  Hold (72°C, extension): ~5W to maintain temperature
  Display: 250 mW (TFT + backlight)
  MCU + BLE: 50 mW
  Battery: 3000 mAh × 3.7V = 11.1 Wh
  Per run energy: Denat 30s×30W + Anneal 20s×15W + Extension 60s×5W = [900J+300J+300J]×35cycles
    = 1500J × 35 + electronics 110s×0.3W = 52,500J + 33J = 52.5 kJ per run
    = 52.5 kJ / 3600 = 14.6 Wh per run
  Battery = 11.1 Wh → insufficient for full 35-cycle run without USB!
  Solution: requires USB-C PD 20W input for full cycles, battery extends to 6 additional
    half-power runs (LAMP-style 65°C hold only mode, no cooling)
  Documented limitation acknowledged in device datasheet.

Ingestible Capsule (NFSIM-CAP-01) power budget:
  Camera frame acquisition + compression (4 fps active):
    STM32L4R9: 10 mA active at 80 MHz
    Camera + JPEG: 8 mA (OV9726 active + MCU JPEG encode)
    434 MHz TX (10 dBm, 20ms per frame): 100 mW × 0.08 duty = 8 mW = 2.2 mA avg
    Total during imaging + TX: ~20 mA
  Chemical sensors (every 60s):
    ISFET pH: 2 mA for 100ms = 0.003 mA average
    O2 sensor: 0.5 mA for 500ms = 0.007 mA average
    IMU: 0.4 mA continuous
    Pressure: 0.003 mA average (1 Hz)
  Sleep between frames (750ms of each 1000ms):
    MCU STOP2 mode: 3 µA
    All sensors off
  Blended average:
    Imaging state (250ms/1000ms): 20 mA × 0.25 = 5 mA
    Sleep state (750ms/1000ms): 0.003 mA × 0.75 = 0.002 mA
    Sensors (duty-cycled): ~0.45 mA equivalent continuous
    Average: ~5.45 mA
  Battery: 2× SR44 = 200 mAh @ 3V
  Runtime: 200 mAh / 5.45 mA = 36.7 hours ✓ (exceeds 24–36h GI transit spec)
```

### 20.8 TinyML Deployment Guidelines (All Devices)

```
Framework: TensorFlow Lite Micro (TFLM)
  No dynamic allocation: all tensors statically allocated at compile time
  INT8 quantization: post-training quantization from float32 training models
    Quantization error: typically <1% accuracy drop vs float32 reference

Model deployment checklist:
  □ Convert with TFLite converter (quantize_weights=True, inference_type=INT8)
  □ Measure peak RAM usage via MicroInterpreter::arena_used_bytes()
  □ Verify inference latency on target MCU (ARM CMSIS-NN kernels for acceleration)
  □ Confirm INT8 accuracy on held-out test set (must be >floor from device spec)
  □ Store model in dedicated SPI flash partition (not application flash)
  □ Model update path: OTA can update AI models independently from firmware

CMSIS-NN acceleration per MCU:
  STM32H7 (Cortex-M7 with FPU + SIMD): 3–5× speedup for convolution layers
  nRF52840 (Cortex-M4F): 2–3× speedup for fully-connected layers
  STM32L4 (Cortex-M4 with FPU): 2× speedup
  STM32L0 (Cortex-M0+): no SIMD, software fallback only

Model storage and versioning:
  Models stored in SPI flash with metadata header:
    {model_version: "2.1.0", target_class: "afib_detection", min_fw_version: "1.2.0",
     sha256: "abc...", size_bytes: 20480, input_shape: [1,60,1], output_classes: 5}
  Platform can push model updates independently of firmware (lighter-weight OTA)
  A/B model switching: run shadow model in parallel → compare outputs → promote when confident
```

---

## 21. Software Stack — Complete

### 21.1 Desktop Application

**Technology stack:**

```
Runtime: Electron 28 (Chromium 118 + Node.js 20)
Frontend: React 18 + TypeScript 5.3 + Tailwind CSS 3.4
3D rendering: Three.js r159 via @react-three/fiber 8.15 + @react-three/drei 9.92
State management: Zustand 4.4 + React Query 5.0
Local database: better-sqlite3 9.2 (synchronous, no async overhead)
BLE: noble 1.9.1 (macOS/Linux) + noble-winrt 1.0.0 (Windows)
USB-Serial: serialport 12.0 (@serialport/parser-readline for NFS commands)
DICOM viewing: cornerstone3D 1.62 + cornerstoneDICOMImageLoader 4.2
FHIR client: @medplum/fhirkit 3.0
NFC: nfc-pcsc 0.7 (for desktop NFC reader peripherals)
File handling: electron-dl (file download), archiver (ZIP export)
Auto-update: electron-updater 6.1 (Squirrel protocol)
Settings: electron-store 8.1
IPC: electron contextBridge (typed, no remote module)
Charts: recharts 2.10 for 2D time-series data
AI visualization: WebGL shader-based for nanoparticle trajectory rendering
```

**Main process architecture (`/electron/main.js`):**

```javascript
// Main process responsibilities:
// 1. Native BLE management (noble lifecycle)
// 2. SQLite database (synchronous, main thread only)
// 3. USB-Serial device management
// 4. File system operations (DICOM, FASTQ import/export)
// 5. Auto-updater lifecycle
// 6. Window management + deep link protocol handler (nanoflowsim://)
// 7. Background tasks (batch FHIR import, DICOM segmentation subprocess)

const { app, BrowserWindow, ipcMain, protocol, shell } = require('electron');

// All IPC handlers typed via TypeScript interface (preload.ts)
// Communication pattern: renderer → contextBridge → IPC → main → response
// No remote module, no nodeIntegration in renderer (security)

ipcMain.handle('ble:scan', async (_, options) => BLEManager.scan(options));
ipcMain.handle('ble:connect', async (_, deviceId) => BLEManager.connect(deviceId));
ipcMain.handle('db:query', async (_, sql, params) => DB.query(sql, params));
ipcMain.handle('db:run', async (_, sql, params) => DB.run(sql, params));
ipcMain.handle('file:import-dicom', async (_, paths) => DICOMImporter.import(paths));
ipcMain.handle('fhir:connect', async (_, endpoint, token) => FHIRClient.connect(endpoint, token));
ipcMain.handle('sim:submit', async (_, config) => SimulationBridge.submit(config));
ipcMain.handle('sim:status', async (_, jobId) => SimulationBridge.status(jobId));
```

**Preload bridge (`/electron/preload.ts`):**

```typescript
import { contextBridge, ipcRenderer } from 'electron';

// Typed API exposed to renderer — no Node.js APIs in renderer context
contextBridge.exposeInMainWorld('nfsim', {
  ble: {
    scan: (options: BLEScanOptions) => ipcRenderer.invoke('ble:scan', options),
    connect: (deviceId: string) => ipcRenderer.invoke('ble:connect', deviceId),
    disconnect: (deviceId: string) => ipcRenderer.invoke('ble:disconnect', deviceId),
    sendCommand: (deviceId: string, cmd: NFSCommand) => ipcRenderer.invoke('ble:send-command', deviceId, cmd),
    onData: (callback: (packet: NFSPacket) => void) =>
      ipcRenderer.on('ble:data', (_, packet) => callback(packet)),
  },
  db: {
    query: <T>(sql: string, params?: unknown[]) =>
      ipcRenderer.invoke('db:query', sql, params) as Promise<T[]>,
    run: (sql: string, params?: unknown[]) => ipcRenderer.invoke('db:run', sql, params),
  },
  patient: {
    create: (data: PatientCreate) => ipcRenderer.invoke('patient:create', data),
    get: (id: string) => ipcRenderer.invoke('patient:get', id),
    list: () => ipcRenderer.invoke('patient:list'),
  },
  import: {
    fhir: (endpoint: string, token: string) => ipcRenderer.invoke('fhir:connect', endpoint, token),
    dicom: (paths: string[]) => ipcRenderer.invoke('file:import-dicom', paths),
    vcf: (path: string) => ipcRenderer.invoke('file:import-vcf', path),
  },
  simulation: {
    submit: (config: SimConfig) => ipcRenderer.invoke('sim:submit', config),
    status: (jobId: string) => ipcRenderer.invoke('sim:status', jobId),
    cancel: (jobId: string) => ipcRenderer.invoke('sim:cancel', jobId),
    results: (jobId: string) => ipcRenderer.invoke('sim:results', jobId),
  },
  shell: {
    openExternal: (url: string) => ipcRenderer.invoke('shell:open-external', url),
  },
});
```

**3D Body Map (`/src/renderer/components/BodyMap3D.tsx`):**

```typescript
import { Canvas, useFrame, useThree } from '@react-three/fiber';
import { useGLTF, OrbitControls, Html } from '@react-three/drei';
import { useBodyMapStore } from '../store/bodyMapStore';

// Body mesh loaded from GLTF (open-source anatomical model, CC0)
// Each named mesh group corresponds to a UBERON code
// Raycasting on click → identify UBERON region → open Region Detail Panel

const UBERON_MESH_MAP: Record<string, string> = {
  'Heart_Mesh':          'UBERON:0000948',
  'Lung_Left_Mesh':      'UBERON:0002048',
  'Lung_Right_Mesh':     'UBERON:0002048',
  'Liver_Mesh':          'UBERON:0002107',
  'Kidney_Left_Mesh':    'UBERON:0002113',
  'Kidney_Right_Mesh':   'UBERON:0002113',
  'Brain_Mesh':          'UBERON:0001017',
  'Stomach_Mesh':        'UBERON:0000945',
  'Colon_Mesh':          'UBERON:0001155',
  'Pancreas_Mesh':       'UBERON:0001114',
  'Spleen_Mesh':         'UBERON:0002106',
  'Thyroid_Mesh':        'UBERON:0002370',
  'Skin_Surface':        'UBERON:0001416',
  'Skeletal_Mesh':       'UBERON:0002481',
  'Vascular_Mesh':       'UBERON:0004537',
  // ... complete UBERON mesh map (200+ named regions)
};

export function BodyMap3D({ mode }: { mode: 'consumer' | 'professional' }) {
  const { nodes } = useGLTF('/assets/nfsim_anatomy.glb');
  const { selectedRegion, liveDevices, historicalTimestamp } = useBodyMapStore();

  // Per-region shader: base color + data overlay (color by latest sensor value)
  // Pulsing animation for live sensors (rhythm synced to detected HR for cardiac)
  // Heatmap overlay computed in WGSL compute shader (WebGPU path) or fragment shader
  // Nanoparticle trajectory: instanced mesh (up to 10,000 particles, 60fps)
  // Layer visibility controlled by bitmask from layer toggle panel

  return (
    <Canvas camera={{ position: [0, 0, 2.5], fov: 45 }} shadows>
      <ambientLight intensity={0.4} />
      <directionalLight position={[5, 10, 5]} intensity={0.8} castShadow />
      <AnatomyModel nodes={nodes} uberonMap={UBERON_MESH_MAP} />
      <DataOverlay liveDevices={liveDevices} timestamp={historicalTimestamp} />
      <NanoparticleTrajectory simulationJobId={selectedSimulation} />
      <OrbitControls enablePan enableZoom enableRotate dampingFactor={0.05} />
      <TimelineScrubber />
    </Canvas>
  );
}
```

**SQLite Schema:**

```sql
-- Core patient record
CREATE TABLE patients (
  patient_id    TEXT PRIMARY KEY,
  created_at    INTEGER NOT NULL,
  display_name  TEXT,
  height_cm     REAL,
  weight_kg     REAL,
  age           INTEGER,
  biological_sex TEXT CHECK(biological_sex IN ('male','female','intersex','unspecified')),
  body_map_level INTEGER DEFAULT 0,
  anthropic_hash TEXT  -- HMAC of patient_id for de-identification
);

-- All health data records
CREATE TABLE data_records (
  record_id       TEXT PRIMARY KEY,
  patient_id      TEXT NOT NULL REFERENCES patients(patient_id),
  timestamp_unix  INTEGER NOT NULL,
  ingested_at     INTEGER NOT NULL,
  source_type     TEXT NOT NULL,  -- 'nfs_device','hospital_fhir','manual','wearable_sync'
  source_detail   TEXT,           -- device_id or institution name
  data_type       TEXT NOT NULL,
  uberon_primary  TEXT NOT NULL,
  uberon_secondary TEXT,          -- JSON array
  is_continuous   INTEGER DEFAULT 0,
  session_id      TEXT,
  quality_score   REAL,
  notes           TEXT,
  fhir_id         TEXT,
  dicom_uid       TEXT,
  binary_ref      TEXT,           -- MinIO object key (for large binary data)
  processed_json  TEXT            -- Serialized processed data for quick display
);

CREATE INDEX idx_records_patient_region ON data_records(patient_id, uberon_primary, timestamp_unix DESC);
CREATE INDEX idx_records_session ON data_records(session_id);
CREATE INDEX idx_records_type ON data_records(patient_id, data_type, timestamp_unix DESC);

-- Active monitoring sessions
CREATE TABLE monitoring_sessions (
  session_id      TEXT PRIMARY KEY,
  patient_id      TEXT NOT NULL REFERENCES patients(patient_id),
  device_id       TEXT NOT NULL,
  device_type     TEXT NOT NULL,
  started_at      INTEGER NOT NULL,
  ended_at        INTEGER,
  uberon_region   TEXT NOT NULL,
  sample_rate_hz  REAL,
  record_count    INTEGER DEFAULT 0,
  status          TEXT DEFAULT 'active' CHECK(status IN ('active','complete','error','interrupted'))
);

-- Simulation runs
CREATE TABLE simulation_runs (
  run_id          TEXT PRIMARY KEY,
  patient_id      TEXT NOT NULL REFERENCES patients(patient_id),
  created_at      INTEGER NOT NULL,
  status          TEXT DEFAULT 'queued' CHECK(status IN ('queued','running','complete','failed')),
  nanoparticle_config TEXT,       -- JSON
  therapy_config  TEXT,           -- JSON
  results_json    TEXT,           -- Stored when complete
  visualization_ref TEXT,         -- MinIO key for 3D trajectory data
  grpc_job_id     TEXT
);

-- Consent records
CREATE TABLE consent_records (
  consent_id      TEXT PRIMARY KEY,
  patient_id      TEXT NOT NULL REFERENCES patients(patient_id),
  scope           TEXT NOT NULL,
  granted_at      INTEGER NOT NULL,
  expires_at      INTEGER,
  grantee         TEXT NOT NULL,
  revoked_at      INTEGER
);

-- Device registry
CREATE TABLE devices (
  device_id       TEXT PRIMARY KEY,
  device_type     TEXT NOT NULL,
  firmware_version TEXT,
  hardware_revision TEXT,
  last_seen_unix  INTEGER,
  battery_pct     INTEGER,
  paired_patient  TEXT REFERENCES patients(patient_id),
  calibration_date INTEGER,
  notes           TEXT
);
```

### 21.2 Mobile Application

**Technology stack:**

```
Framework: React Native 0.73 + Expo SDK 50
Navigation: Expo Router 3.4 (file-based, NativeStack)
3D body map: @react-three/fiber (via expo-gl) + simplified anatomy mesh
BLE: react-native-ble-plx 3.1 (iOS CoreBluetooth + Android BLE API)
NFC: react-native-nfc-manager 3.14
Camera: expo-camera 14 (document scanning), react-native-vision-camera 3 (AR mode)
AR: ViroReact (ARKit/ARCore wrapper) for body map AR overlay
Health sync: expo-health 5 (Apple HealthKit + Google Health Connect)
Storage: expo-secure-store 12 (encrypted, patient-sensitive data)
Notifications: expo-notifications 0.26 (local + push alerts)
File system: expo-file-system 16
Haptics: expo-haptics 12 (tactile feedback for alerts)
Sensors: expo-sensors 13 (device accelerometer for anti-shake)
Offline sync: react-query 5 with background sync (custom offline queue)
State: Zustand 4.4 (same stores as desktop, shared package)
Charts: Victory Native 40 (ECG, glucose, HRV charts)
```

**Directory structure:**

```
/mobile/
├── app/                          Expo Router file-based routes
│   ├── _layout.tsx               Root layout (auth gate, theme provider)
│   ├── (auth)/
│   │   ├── login.tsx             Patient ID entry / biometric unlock
│   │   └── setup.tsx             First-time onboarding wizard
│   ├── (tabs)/
│   │   ├── _layout.tsx           Tab bar definition
│   │   ├── index.tsx             Body map home screen
│   │   ├── timeline.tsx          Chronological data history
│   │   ├── devices.tsx           Connected NFS devices hub
│   │   ├── simulate.tsx          Simulation launcher
│   │   └── settings.tsx          Profile, sync, privacy preferences
│   └── modals/
│       ├── region-detail/[uberon].tsx   Region-specific data sheet
│       ├── add-data/index.tsx           Multi-step data entry flow
│       ├── device-connect/index.tsx     BLE pairing wizard
│       ├── alert-detail/[id].tsx        Alert context and actions
│       └── simulation-result/[id].tsx  Simulation output viewer
├── components/
│   ├── BodyMap3D.tsx             Simplified 3D body for mobile
│   ├── LiveSensorCard.tsx        Real-time value display card
│   ├── TimelineList.tsx          Virtualized record list
│   ├── WaveformChart.tsx         ECG/EEG waveform viewer
│   ├── GlucoseChart.tsx          AGP (Ambulatory Glucose Profile) chart
│   ├── DeviceBadge.tsx           Connected device status indicator
│   └── ARBodyOverlay.tsx         AR mode component
├── store/
│   ├── patientStore.ts           Active patient profile
│   ├── bodyMapStore.ts           Body map state, selected region
│   ├── deviceStore.ts            BLE device registry
│   └── sessionStore.ts           Active monitoring sessions
├── services/
│   ├── ble/                      BLE device management service
│   ├── nfc/                      NFC read service (CGM passive)
│   ├── sync/                     Background data sync service
│   ├── notifications/            Alert and reminder service
│   └── health/                   HealthKit / Health Connect bridge
├── hooks/
│   ├── useLiveDevice.ts          Subscribe to BLE device data stream
│   ├── useRegionData.ts          Load data for a UBERON region
│   ├── usePatientTimeline.ts     Paginated timeline query
│   └── useSimulation.ts          Submit + poll simulation job
└── utils/
    ├── uberon.ts                  UBERON code utilities
    ├── nfs-protocol.ts            NFS packet parser
    └── calibration.ts             Calibration data utilities
```

**Mobile-specific alert system:**

```typescript
// Priority tiers with haptic patterns and notification channels
enum AlertPriority {
  CRITICAL = 'critical',  // Glucose <54 or >400, VT/VF, SpO2 <85%
  HIGH     = 'high',      // Glucose 54–70 or 300–400, AFib, SpO2 <90%
  MEDIUM   = 'medium',    // Trend alerts, device battery <10%
  LOW      = 'low',       // Sync complete, medication reminder
}

const HAPTIC_PATTERNS: Record<AlertPriority, HapticPattern> = {
  critical: { pattern: [100, 50, 100, 50, 500], repeat: 3 },
  high:     { pattern: [200, 100, 200], repeat: 2 },
  medium:   { pattern: [200], repeat: 1 },
  low:      { pattern: [100], repeat: 1 },
};

// Emergency card accessible from lock screen without app unlock
// iOS: Siri Shortcut + HealthKit Emergency Card
// Android: Emergency widget + Medical ID integration
```

### 21.3 Web Dashboard and Backend

**Backend (Django 5 + DRF + Celery + PostgreSQL + Redis + MinIO + Django Channels):**

```python
# Project structure
nfsim_platform/
├── nfsim_core/              Django project settings (base, development, production)
├── patients/                Patient profile CRUD + data model
├── records/                 Health record ingestion, UBERON tagging, query API
├── sessions/                Continuous monitoring session management
├── devices/                 Device registry, firmware version tracking
├── simulations/             Job submission, status polling, result storage
├── fhir/                    FHIR R4 server endpoint (HAPI-compatible)
├── importers/               Async importers: VCF, DICOM, FHIR, CSV, mzML
├── uberon/                  UBERON ontology service (code lookup, hierarchy)
├── websockets/              Django Channels consumers (live device relay, sim progress)
├── ai/                      Background AI: insight generation, cohort analysis
└── auth/                    DID-based authentication, JWT, consent management

# API endpoints (all authenticated, patient-scoped)
urlpatterns = [
    # Authentication
    path('api/v1/auth/token/', views.TokenView.as_view()),
    path('api/v1/auth/did/', views.DIDAuthView.as_view()),
    
    # Patient management
    path('api/v1/patients/', views.PatientListCreateView.as_view()),
    path('api/v1/patients/<uuid:pk>/', views.PatientDetailView.as_view()),
    path('api/v1/patients/<uuid:pk>/export/', views.PatientExportView.as_view()),
    
    # Health records
    path('api/v1/patients/<uuid:pk>/records/', views.RecordListView.as_view()),
    path('api/v1/patients/<uuid:pk>/records/<uuid:rid>/', views.RecordDetailView.as_view()),
    path('api/v1/patients/<uuid:pk>/regions/', views.RegionSummaryView.as_view()),
    path('api/v1/patients/<uuid:pk>/regions/<str:uberon>/', views.RegionDetailView.as_view()),
    path('api/v1/patients/<uuid:pk>/timeline/', views.TimelineView.as_view()),
    
    # Continuous sessions
    path('api/v1/patients/<uuid:pk>/sessions/', views.SessionListView.as_view()),
    path('api/v1/patients/<uuid:pk>/sessions/<uuid:sid>/', views.SessionDetailView.as_view()),
    
    # Simulation
    path('api/v1/simulations/', views.SimulationCreateView.as_view()),
    path('api/v1/simulations/<uuid:pk>/', views.SimulationStatusView.as_view()),
    path('api/v1/simulations/<uuid:pk>/results/', views.SimulationResultsView.as_view()),
    
    # Import endpoints
    path('api/v1/import/fhir/', views.FHIRImportView.as_view()),
    path('api/v1/import/dicom/', views.DICOMImportView.as_view()),
    path('api/v1/import/vcf/', views.VCFImportView.as_view()),
    path('api/v1/import/csv/', views.CSVImportView.as_view()),
    
    # FHIR R4 server
    path('fhir/Patient/', views.FHIRPatientView.as_view()),
    path('fhir/Observation/', views.FHIRObservationView.as_view()),
    path('fhir/DiagnosticReport/', views.FHIRDiagnosticReportView.as_view()),
    
    # Research cohort (institution accounts only)
    path('api/v1/research/cohort/', views.CohortView.as_view()),
    path('api/v1/research/export/', views.DeidentifiedExportView.as_view()),
]

# WebSocket routes (Django Channels)
websocket_urlpatterns = [
    path('ws/session/<uuid:session_id>/', consumers.SessionStreamConsumer.as_asgi()),
    path('ws/simulation/<uuid:run_id>/', consumers.SimulationProgressConsumer.as_asgi()),
    path('ws/alerts/<uuid:patient_id>/', consumers.AlertConsumer.as_asgi()),
]
```

**Celery background tasks:**

```python
# Background task definitions
@shared_task(bind=True, max_retries=3)
def ingest_fhir_bundle(self, patient_id: str, fhir_bundle: dict):
    """Parse FHIR R4 bundle, UBERON-tag all resources, store in DB."""
    ...

@shared_task
def auto_tag_uberon(record_id: str):
    """AI-assisted UBERON tag suggestion for ambiguous records."""
    ...

@shared_task
def run_simulation(simulation_id: str):
    """Submit simulation job to Rust engine via gRPC, poll for completion."""
    ...

@shared_task
def segment_dicom_volume(study_uid: str, patient_id: str):
    """Run ITK-SNAP / SimpleITK segmentation on uploaded DICOM volume.
    Extracts organ surface meshes → stores as GLTF for body map Level 2."""
    ...

@shared_task
def generate_weekly_insight(patient_id: str):
    """Run AI insight model on last 7 days of data → plain-English summary."""
    ...

@shared_task
def federated_model_update(model_type: str, patient_id: str):
    """Compute gradient contribution from local patient data.
    Apply differential privacy noise. Submit to aggregation server."""
    ...
```

### 21.4 SDK (Python, Node.js, Rust)

**Python SDK (`nfsim-sdk` — PyPI):**

```python
# pip install nfsim-sdk

from nfsim import NanoFlowSIM, BLEDevice, SimulationConfig, TherapyType

# Initialize with local SQLite (no cloud required)
nfsim = NanoFlowSIM(patient_id="uuid", mode="local")

# Connect to NFS device via BLE
device = nfsim.connect_device("NFSIM-ECG-01-ABCDEF", transport="ble")
device.set_uberon("UBERON:0000948")

# Stream data with callback
session = device.start_session()
session.on_data(lambda pkt: print(f"HR: {pkt.data['hr_bpm']} bpm"))
session.wait(seconds=300)  # Record for 5 minutes
session.stop()

# Import hospital records
nfsim.import_fhir(
    endpoint="https://myhospital.epic.com/fhir/R4",
    auth_token=my_oauth_token
)

# Import genomic VCF
nfsim.import_vcf("/path/to/patient_variants.vcf.gz", genome_build="GRCh38")

# Query region data
cardiac_data = nfsim.query_region(
    uberon="UBERON:0000948",
    data_types=["ecg_continuous_segment", "lab_result"],
    start="2025-01-01",
    end="2026-01-01"
)

# Run nanoparticle simulation
sim = SimulationConfig(
    nanoparticle={
        "size_nm": 100,
        "shape": "spherical",
        "surface_coating": "peg_2000",
        "ligand_type": "anti_HER2_fab",
        "ligand_density_per_nm2": 0.15,
        "payload_type": "doxorubicin",
        "payload_loading_pct": 12.0,
        "release_mechanism": "pH_triggered",
    },
    therapies=[TherapyType.NANOPARTICLE, TherapyType.IMMUNOTHERAPY],
    target_uberon="UBERON:0009835",
    use_patient_data=True,
    patient_id="uuid",
)
job = nfsim.simulation.submit(sim)
results = nfsim.simulation.wait(job.run_id, timeout=600)
print(f"Targeting efficiency: {results.targeting_efficiency_pct:.1f}%")
print(f"Side effect probability: {results.adverse_event_probability:.2%}")

# Export all data as FHIR bundle
bundle = nfsim.export_fhir()
with open("patient_export.json", "w") as f:
    json.dump(bundle, f, indent=2)
```

**Node.js SDK (`@nfsim/sdk` — npm):**

```typescript
// npm install @nfsim/sdk

import { NanoFlowSIM, NFSDevice, SimulationConfig } from '@nfsim/sdk';

const nfsim = new NanoFlowSIM({ patientId: 'uuid', mode: 'local' });

// PCR workflow
const pcr = await nfsim.connectDevice('NFSIM-PCR-01-ABCDEF', { transport: 'ble' });
await pcr.loadProtocol({
  name: 'COVID_LAMP',
  steps: [
    { type: 'hold', temp: 65, duration: 1800 }
  ],
  lid_temp: 70,
});
pcr.on('progress', ({ cycle, stage, temp, eta }) => {
  console.log(`Cycle ${cycle} | ${stage} | ${temp.toFixed(1)}°C | ETA: ${eta}s`);
});
const result = await pcr.startRun();
await nfsim.saveRecord({ ...result, uberon: 'UBERON:0000178', patientId: 'uuid' });

// Simulation
const simConfig: SimulationConfig = {
  nanoparticle: { size_nm: 120, ligand_type: 'aptamer', payload: 'crispr_cas9' },
  therapies: ['crispr', 'immunotherapy'],
  targetUberon: 'UBERON:0001017',
};
const { runId } = await nfsim.simulation.submit(simConfig);
for await (const progress of nfsim.simulation.stream(runId)) {
  console.log(`Progress: ${progress.pct}% — ${progress.layer}`);
}
const results = await nfsim.simulation.results(runId);
```

**Rust client library (`nfsim-client` — crates.io):**

```rust
// Cargo.toml: nfsim-client = "1.0"

use nfsim_client::{NanoFlowSIM, Transport, DeviceType, SimulationConfig, TherapyType};

#[tokio::main]
async fn main() -> Result<(), nfsim_client::Error> {
    let nfsim = NanoFlowSIM::builder()
        .patient_id("uuid")
        .mode(nfsim_client::Mode::Local)
        .build()
        .await?;

    // Connect to CGM via BLE
    let cgm = nfsim.connect_device(DeviceType::CGM01, Transport::Ble).await?;
    cgm.set_uberon("UBERON:0001175").await?;
    
    let mut session = cgm.start_session().await?;
    while let Some(packet) = session.next_packet().await {
        let glucose_mg_dl = packet.data["glucose_mg_dl"].as_f64().unwrap();
        println!("Glucose: {:.1} mg/dL | Trend: {}", 
                 glucose_mg_dl, packet.data["trend_arrow"]);
        nfsim.store(&packet).await?;
        
        if glucose_mg_dl < 70.0 {
            nfsim.alert(nfsim_client::AlertPriority::High, 
                       "Glucose below 70 mg/dL").await?;
        }
    }

    // Submit simulation
    let config = SimulationConfig::builder()
        .nanoparticle_size_nm(100.0)
        .ligand("anti_HER2_fab", 0.15)
        .payload("doxorubicin", 12.0)
        .release(nfsim_client::Release::PHTrigggered)
        .therapies(vec![TherapyType::Nanoparticle, TherapyType::CRISPR])
        .target_uberon("UBERON:0000948")
        .use_patient_data(true)
        .build();
    
    let job = nfsim.simulation().submit(config).await?;
    let results = nfsim.simulation().wait(job.run_id, std::time::Duration::from_secs(600)).await?;
    println!("Targeting efficiency: {:.1}%", results.targeting_efficiency_pct);

    Ok(())
}
```

### 21.5 AI / ML Layer

**On-device TinyML pipeline (all FreeRTOS devices with AI):**

```c
// Generic on-device inference invocation (TFLM pattern)
#include "tensorflow/lite/micro/all_ops_resolver.h"
#include "tensorflow/lite/micro/micro_interpreter.h"

// Model binary: stored in SPI flash, loaded into RAM at startup
// Arena: statically allocated tensor arena
static uint8_t tensor_arena[MODEL_ARENA_SIZE] __attribute__((aligned(16)));

// Initialize once at startup
tflite::AllOpsResolver resolver;
const tflite::Model* model = tflite::GetModel(g_model_data);
tflite::MicroInterpreter interpreter(model, resolver, tensor_arena, MODEL_ARENA_SIZE);
interpreter.AllocateTensors();
TfLiteTensor* input = interpreter.input(0);
TfLiteTensor* output = interpreter.output(0);

// Per-inference call (called from SignalProcessingTask)
void RunInference(float* input_data, size_t input_size, float* output_data, size_t output_size) {
    // Quantize float input to INT8
    for (size_t i = 0; i < input_size; i++) {
        input->data.int8[i] = (int8_t)((input_data[i] / input->params.scale) + input->params.zero_point);
    }
    // Run inference
    interpreter.Invoke();
    // Dequantize INT8 output to float
    for (size_t i = 0; i < output_size; i++) {
        output_data[i] = (output->data.int8[i] - output->params.zero_point) * output->params.scale;
    }
}
```

**Edge inference pipeline (desktop, ONNX Runtime):**

```python
# DICOM segmentation via nnU-Net (open-source medical image segmentation)
import onnxruntime as ort
import numpy as np

class DICOMSegmenter:
    def __init__(self, model_path: str):
        self.session = ort.InferenceSession(
            model_path,
            providers=['CUDAExecutionProvider', 'CPUExecutionProvider']
        )
    
    def segment(self, volume: np.ndarray) -> dict[str, np.ndarray]:
        """Segment CT/MRI volume into organ masks.
        Returns: dict of UBERON code → binary mask array."""
        # Preprocess: normalize HU values, resample to model spacing
        preprocessed = self._preprocess(volume)
        input_name = self.session.get_inputs()[0].name
        outputs = self.session.run(None, {input_name: preprocessed[np.newaxis, np.newaxis]})
        segmentation = outputs[0][0]  # Shape: (num_classes, D, H, W)
        return {
            'UBERON:0002107': segmentation[1] > 0.5,  # liver
            'UBERON:0002113': segmentation[2] > 0.5,  # kidneys
            'UBERON:0000948': segmentation[3] > 0.5,  # heart
            'UBERON:0002048': segmentation[4] > 0.5,  # lungs
            # ... additional organs
        }

# Nanopore basecaller (open-source, Bonito-compatible)
import torch
from nfsim_basecaller import CRNNBasecaller

basecaller = CRNNBasecaller.load_pretrained('r10.4.1_400bps_sup')
fastq_records = basecaller.call(raw_signal_path='run_squiggles.pod5')
```

**Federated learning (privacy-preserving model improvement):**

```python
# Federated gradient computation (runs locally, gradient shared — not data)
from nfsim_federated import LocalTrainer, DifferentialPrivacy

trainer = LocalTrainer(
    model_type='afib_classifier',
    local_data=patient_ecg_records,  # Never leaves device
    privacy=DifferentialPrivacy(epsilon=1.0, delta=1e-5, clip_norm=1.0),
)

gradient = trainer.compute_gradient()  # INT8 gradient vector, ~50 KB
# Apply DP noise: Gaussian mechanism
private_gradient = trainer.apply_dp_noise(gradient)
# Submit gradient only (not data) to aggregation server
aggregation_server.submit_gradient(
    model_version='2.1.0',
    gradient=private_gradient,
    n_samples=len(patient_ecg_records),  # Sample count (not samples themselves)
)
```

---

## 22. Complete Monorepo Directory Structure

```
/nanoflowsim/
├── README.md                                   ← This document (complete)
├── LICENSE-SOFTWARE.md                         MIT License
├── LICENSE-HARDWARE.md                         CERN OHL-W v2
├── LICENSE-DOCS.md                             CC BY 4.0
├── CONTRIBUTING.md                             Contribution guidelines
├── CHANGELOG.md                                Full version history (HW/FW/SW)
├── SECURITY.md                                 Responsible disclosure policy
├── CODE_OF_CONDUCT.md
│
├── .github/
│   ├── workflows/
│   │   ├── ci-firmware.yml              Build + static analysis for all device firmware
│   │   ├── ci-software.yml              Lint + test + build for desktop/mobile/backend
│   │   ├── ci-simulation.yml            Rust workspace build + cargo test
│   │   ├── ci-hardware-drc.yml          KiCad DRC check on all PCB designs
│   │   ├── ci-hardware-bom.yml          LCSC part availability verification
│   │   └── release.yml                 Versioned release: binaries + Gerbers + changelog
│   ├── ISSUE_TEMPLATE/
│   │   ├── hardware_bug.yml
│   │   ├── firmware_bug.yml
│   │   ├── software_bug.yml
│   │   └── feature_request.yml
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── CODEOWNERS
│
├── /simulation/                               PILLAR 1: Rust simulation engine
│   ├── Cargo.toml                             Workspace manifest
│   ├── Cargo.lock
│   ├── /nfsim-core/
│   │   ├── Cargo.toml
│   │   └── src/
│   │       ├── types.rs                       Core data types, UBERON codes
│   │       ├── constants.rs                   Physical and biological constants
│   │       ├── patient.rs                     Patient data structures
│   │       ├── nanoparticle.rs               NP design parameter types
│   │       └── lib.rs
│   ├── /nfsim-molecular/
│   │   └── src/
│   │       ├── receptor_ligand.rs             Gillespie algorithm binding kinetics
│   │       ├── crispr.rs                      Guide RNA efficiency, off-target scoring
│   │       ├── payload_stability.rs           pH/enzymatic degradation models
│   │       ├── ligand_design.rs              AI-assisted ligand generation
│   │       └── lib.rs
│   ├── /nfsim-cellular/
│   │   └── src/
│   │       ├── endocytosis.rs                 Pathway probability models
│   │       ├── endosomal_escape.rs            Proton sponge, fusogenic models
│   │       ├── trafficking.rs                 Intracellular routing
│   │       ├── payload_release.rs             Release kinetics per mechanism
│   │       └── lib.rs
│   ├── /nfsim-tissue/
│   │   └── src/
│   │       ├── epr.rs                         EPR effect, vascular extravasation
│   │       ├── tumor_microenvironment.rs      TME modeling (hypoxia, immune)
│   │       ├── blood_brain_barrier.rs         BBB crossing models
│   │       ├── permeability.rs                Tissue-specific permeability matrices
│   │       └── lib.rs
│   ├── /nfsim-systemic/
│   │   └── src/
│   │       ├── pharmacokinetics.rs            Two-compartment PK model
│   │       ├── mps_clearance.rs               MPS, opsonization, Kupffer cells
│   │       ├── complement.rs                  Complement activation model
│   │       ├── protein_corona.rs              Hard/soft corona formation
│   │       └── lib.rs
│   ├── /nfsim-ml/
│   │   └── src/
│   │       ├── therapy_ranker.rs              LightGBM therapy combination ranking
│   │       ├── np_optimizer.rs                Bayesian optimization (nanoparticle design)
│   │       ├── patient_stratifier.rs          Patient clustering and matching
│   │       └── lib.rs
│   ├── /nfsim-backtesting/
│   │   └── src/
│   │       ├── validator.rs                   Clinical outcome comparison
│   │       ├── bayesian_updater.rs            Model parameter refinement
│   │       └── lib.rs
│   ├── /nfsim-visualization/
│   │   └── src/
│   │       ├── trajectory.rs                  3D particle trajectory data generation
│   │       ├── heatmap.rs                     Tissue concentration heatmap arrays
│   │       └── lib.rs
│   ├── /nfsim-grpc/
│   │   ├── Cargo.toml
│   │   ├── proto/
│   │   │   └── simulation.proto              gRPC service definition
│   │   └── src/
│   │       ├── server.rs                      gRPC server (tonic)
│   │       └── lib.rs
│   └── /nfsim-cli/
│       └── src/
│           └── main.rs                        CLI runner (clap argument parser)
│
├── /platform/                                 PILLAR 2 + client software
│   ├── /backend/                              Django 5 server
│   │   ├── manage.py
│   │   ├── requirements.txt
│   │   ├── requirements-dev.txt
│   │   ├── Dockerfile
│   │   ├── docker-compose.yml               (PostgreSQL + Redis + MinIO + Celery)
│   │   ├── /nfsim_core/                     Django project settings
│   │   │   ├── settings/
│   │   │   │   ├── base.py
│   │   │   │   ├── development.py
│   │   │   │   └── production.py
│   │   │   ├── urls.py
│   │   │   └── asgi.py                      ASGI (Channels + WSGI)
│   │   ├── /patients/                       Patient profile app
│   │   ├── /records/                        Health record CRUD
│   │   ├── /sessions/                       Continuous session management
│   │   ├── /simulations/                    Simulation job bridge (gRPC client)
│   │   ├── /fhir/                           FHIR R4 endpoint
│   │   ├── /importers/                      Async importers (Celery tasks)
│   │   ├── /uberon/                         Ontology service
│   │   ├── /websockets/                     Django Channels consumers
│   │   ├── /ai/                             Insight generation tasks
│   │   └── /auth/                           DID authentication, JWT
│   │
│   ├── /desktop/                            Electron + React desktop app
│   │   ├── package.json
│   │   ├── tsconfig.json
│   │   ├── electron-builder.json
│   │   ├── /electron/
│   │   │   ├── main.js
│   │   │   ├── preload.ts
│   │   │   └── /services/
│   │   │       ├── ble.ts                   Noble BLE management
│   │   │       ├── usb.ts                   USB-Serial management
│   │   │       ├── database.ts              SQLite (better-sqlite3)
│   │   │       ├── minio.ts                 Local MinIO client
│   │   │       └── simulation.ts           gRPC client to Rust engine
│   │   └── /src/
│   │       ├── App.tsx
│   │       ├── /components/
│   │       │   ├── BodyMap3D.tsx
│   │       │   ├── RegionDetail.tsx
│   │       │   ├── Timeline.tsx
│   │       │   ├── LiveFeed.tsx
│   │       │   ├── DicomViewer.tsx
│   │       │   ├── DeviceManager.tsx
│   │       │   ├── SimLauncher.tsx
│   │       │   ├── GenomicsBrowser.tsx
│   │       │   ├── AIInsightPanel.tsx
│   │       │   └── EmergencyCard.tsx
│   │       ├── /views/
│   │       │   ├── ConsumerDashboard.tsx
│   │       │   ├── ProfessionalDashboard.tsx
│   │       │   ├── CohortView.tsx
│   │       │   └── Settings.tsx
│   │       ├── /store/                      Zustand state slices
│   │       ├── /hooks/                      Custom React hooks
│   │       └── /assets/
│   │           ├── nfsim_anatomy.glb        Open-source anatomical body mesh (CC0)
│   │           ├── nfsim_anatomy_detail.glb Higher-detail mesh (organ level)
│   │           └── uberon_mesh_map.json     UBERON → mesh group name mapping
│   │
│   ├── /mobile/                             React Native + Expo mobile app
│   │   ├── package.json
│   │   ├── app.json
│   │   ├── /app/                            Expo Router file-based routes
│   │   ├── /components/
│   │   ├── /store/
│   │   ├── /services/
│   │   └── /hooks/
│   │
│   └── /sdk/                                NanoFlowSIM SDKs
│       ├── /python/                         nfsim-sdk (PyPI)
│       │   ├── setup.py
│       │   ├── nfsim/
│       │   │   ├── __init__.py
│       │   │   ├── client.py
│       │   │   ├── devices.py
│       │   │   ├── simulation.py
│       │   │   └── protocol.py
│       │   └── tests/
│       ├── /node/                           @nfsim/sdk (npm)
│       │   ├── package.json
│       │   ├── src/
│       │   │   ├── index.ts
│       │   │   ├── client.ts
│       │   │   ├── devices.ts
│       │   │   └── simulation.ts
│       │   └── tests/
│       └── /rust/                           nfsim-client (crates.io)
│           ├── Cargo.toml
│           └── src/
│               ├── lib.rs
│               ├── client.rs
│               └── protocol.rs
│
├── /hardware/                               PILLAR 3: All device hardware
│   ├── /shared/                             Shared KiCad libraries
│   │   ├── nfsim.kicad_sym                 Custom symbol library
│   │   ├── nfsim.kicad_mod                 Custom footprint library
│   │   ├── nfsim_3d.kicad_3dlib           3D model references
│   │   └── STYLE.md                        KiCad design style guide
│   │
│   ├── /NFSIM-PCR-01/                      (One directory per device — all 75+ devices)
│   │   ├── /hardware/
│   │   │   ├── /schematic/                 KiCad schematics (hierarchical)
│   │   │   │   ├── NFSIM-PCR-01.kicad_pro
│   │   │   │   ├── NFSIM-PCR-01-MCU.kicad_sch
│   │   │   │   ├── NFSIM-PCR-01-Power.kicad_sch
│   │   │   │   └── NFSIM-PCR-01-Thermal.kicad_sch
│   │   │   ├── /pcb/
│   │   │   │   ├── NFSIM-PCR-01-Main.kicad_pcb
│   │   │   │   └── NFSIM-PCR-01-Thermal.kicad_pcb
│   │   │   ├── /gerbers/
│   │   │   │   ├── NFSIM-PCR-01-Main-gerbers.zip
│   │   │   │   └── NFSIM-PCR-01-Thermal-gerbers.zip
│   │   │   ├── /bom/
│   │   │   │   ├── bom_main.csv
│   │   │   │   ├── bom_thermal.csv
│   │   │   │   └── ibom_main.html          Interactive HTML BOM
│   │   │   ├── /assembly/
│   │   │   │   ├── pick_and_place_main.csv
│   │   │   │   ├── pick_and_place_thermal.csv
│   │   │   │   └── assembly_drawing.pdf
│   │   │   ├── /simulation/
│   │   │   │   └── peltier_pid.asc         LTspice thermal simulation
│   │   │   ├── /datasheets/               Local copies of key IC datasheets
│   │   │   └── hardware_config.md          Pin map, power domains, I2C addresses
│   │   ├── /firmware/
│   │   │   ├── CMakeLists.txt
│   │   │   ├── platformio.ini
│   │   │   ├── /src/
│   │   │   │   ├── main.c
│   │   │   │   ├── /drivers/              HAL drivers
│   │   │   │   ├── /tasks/                FreeRTOS tasks
│   │   │   │   ├── nfs_protocol.c/h       NFS protocol implementation
│   │   │   │   └── calibration.c/h
│   │   │   ├── /include/
│   │   │   ├── /tests/                    Unity unit tests
│   │   │   └── /build/                    Compiled artifacts (gitignored)
│   │   │       ├── NFSIM-PCR-01-v1.0.0.bin
│   │   │       ├── NFSIM-PCR-01-v1.0.0.elf
│   │   │       └── NFSIM-PCR-01-v1.0.0.map
│   │   ├── /mechanical/
│   │   │   ├── /cad/                      Fusion 360 + STEP files
│   │   │   ├── /stl/                      FDM print-ready STLs
│   │   │   ├── /drawings/                 2D technical drawings PDF
│   │   │   └── mechanical_spec.md
│   │   ├── /docs/
│   │   │   ├── getting_started.md
│   │   │   ├── theory.md                  Circuit design rationale
│   │   │   ├── assembly_guide.md          Step-by-step build guide with photos
│   │   │   └── protocol_library.md        Pre-loaded PCR/LAMP protocols
│   │   └── /production/
│   │       ├── /sop/
│   │       ├── qc_checklist.csv
│   │       └── /packaging/
│   │
│   ├── /NFSIM-PCR-02/                     (same structure)
│   ├── /NFSIM-PCR-03/
│   ├── /NFSIM-PCR-04/
│   ├── /NFSIM-SEQ-01/
│   ├── /NFSIM-SEQ-02/
│   ├── /NFSIM-CRISPR-01/
│   ├── /NFSIM-CRISPR-02/
│   ├── /NFSIM-CRISPR-03/
│   ├── /NFSIM-dPCR-01/
│   ├── /NFSIM-GELEC-01/
│   ├── /NFSIM-GELEC-02/
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
│   ├── /NFSIM-ECG-03/
│   ├── /NFSIM-EEG-01/
│   ├── /NFSIM-EEG-02/
│   ├── /NFSIM-EEG-03/
│   ├── /NFSIM-EMG-01/
│   ├── /NFSIM-EMG-02/
│   ├── /NFSIM-NEURAL-01/
│   ├── /NFSIM-NEURAL-02/
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
│   ├── /NFSIM-PATCH-01/
│   ├── /NFSIM-PATCH-02/
│   ├── /NFSIM-PATCH-03/
│   ├── /NFSIM-IMPLANT-01/
│   ├── /NFSIM-IMPLANT-02/
│   ├── /NFSIM-FLOW-01/
│   ├── /NFSIM-ENV-01/
│   ├── /NFSIM-ENV-02/
│   ├── /NFSIM-ENV-03/
│   ├── /NFSIM-ENV-04/
│   ├── /NFSIM-ENV-05/
│   ├── /NFSIM-DEL-01/
│   ├── /NFSIM-DEL-02/
│   ├── /NFSIM-DEL-03/
│   ├── /NFSIM-ABL-01/
│   ├── /NFSIM-ABL-02/
│   ├── /NFSIM-CON-01/
│   ├── /NFSIM-CON-02/                     (open standard spec only, no KiCad PCB)
│   ├── /NFSIM-CON-03/
│   ├── /NFSIM-CON-04/
│   └── /NFSIM-CON-05/                     (consumable kit — packaging designs only)
│
├── /shared-firmware/                        Shared firmware modules (all devices)
│   ├── /nfs_protocol/                       NFS BLE + USB protocol C implementation
│   │   ├── nfs_protocol.c
│   │   ├── nfs_protocol.h
│   │   └── nfs_packet_builder.c/h
│   ├── /ble_gatt_server/                   Generic NFS GATT server (Zephyr + nRF5 SDK)
│   ├── /power_management/                   Battery + sleep management
│   ├── /ota_update/                         OTA client (BLE + USB DFU)
│   ├── /calibration/                        Calibration data storage/retrieval
│   ├── /tinyml_runtime/                     TFLite Micro integration wrappers
│   ├── /nfs_radio/                          434 MHz capsule radio protocol
│   └── uberon_tags.h                        All UBERON code definitions as C constants
│
├── /docs/                                   Master documentation
│   ├── /guides/
│   │   ├── getting_started.md              Complete new user guide (patient + developer)
│   │   ├── hardware_build_guide.md         PCB assembly across all device classes
│   │   ├── software_setup.md              Platform installation guide (Linux, Win, macOS)
│   │   ├── first_simulation.md            Step-by-step first simulation walkthrough
│   │   ├── fhir_import.md                 Hospital record import guide
│   │   ├── openaps_integration.md         Closed-loop insulin system integration
│   │   └── research_deployment.md         Multi-patient research study setup
│   ├── /theory/
│   │   ├── nanoparticle_physics.md         Simulation model derivations
│   │   ├── biological_sensing_domains.md   Full sensing domain encyclopedia (this README §7)
│   │   ├── uberon_mapping.md               UBERON usage guide + full code table
│   │   └── fhir_r4_schema.md              FHIR R4 resource usage in NanoFlowSIM
│   ├── /api/
│   │   ├── rest_api.md                    Full REST API reference
│   │   ├── nfs_protocol_spec.md           NFS-BLE + NFS-SERIAL + NFS-RADIO specs
│   │   ├── python_sdk_ref.md              Python SDK reference
│   │   ├── node_sdk_ref.md                Node.js SDK reference
│   │   └── rust_client_ref.md             Rust client library reference
│   ├── /hardware/
│   │   └── [DEVICE]-config.md             Per-device hardware config (75+ files)
│   └── /assets/                            Images and diagrams for docs
│
├── /production/                            Manufacturing guides and templates
│   ├── /sop/                               Assembly SOPs per device class
│   │   ├── pcb_assembly_general.md        General PCB handling and assembly SOP
│   │   ├── firmware_flash_sop.md          Firmware programming SOP (all devices)
│   │   ├── calibration_sop.md             Factory calibration procedure (all devices)
│   │   └── [DEVICE]-assembly.md           Per-device specific assembly SOP
│   ├── /quality/
│   │   ├── qc_checklist_template.csv      Generic QC checklist template
│   │   └── [DEVICE]-qc.csv               Per-device QC checklist
│   ├── /packaging/
│   │   ├── box_design_template.pdf        Box artwork template (Dieline)
│   │   ├── insert_template.pdf            Quick-start insert template
│   │   └── [DEVICE]-packaging.pdf         Per-device packaging specification
│   └── batch_tracking_template.md         Batch production tracking form
│
├── /legal/
│   ├── LICENSE-SOFTWARE.md                MIT License (full text)
│   ├── LICENSE-HARDWARE.md                CERN OHL-W v2 (full text)
│   ├── LICENSE-DOCS.md                    CC BY 4.0 (full text)
│   ├── /certifications/                   FCC/CE test reports (when obtained)
│   ├── /third-party-licenses/             All dependency licenses (auto-generated)
│   └── /compliance/
│       ├── RoHS_declaration_template.pdf
│       ├── REACH_declaration_template.pdf
│       └── regulatory_classification.md   Per-device regulatory analysis
│
└── /media/
    ├── /renders/                           Blender/KeyShot device renders
    ├── /photos/                            Prototype and build photos
    ├── /diagrams/                          System architecture diagrams
    ├── /video/                             Demo video assets
    └── /press/                             Press kit (logos, high-res images, one-pager)
```

---

## 23. Production, Manufacturing and Quality

### 23.1 PCB Manufacturing — JLCPCB Compliance Requirements

All NanoFlowSIM PCBs are designed to JLCPCB manufacturing design rules for maximum accessibility.

**Standard design rules (all devices):**

```
Copper traces:
  Minimum trace width:     0.1 mm (4 mil) for signal
  Recommended signal:      0.2 mm for ease of manufacture
  Power traces (≥500mA):  0.5 mm minimum, 1.0 mm preferred
  Minimum clearance:       0.1 mm between traces/pads
  
Vias:
  Minimum drill diameter:  0.3 mm
  Minimum pad diameter:    0.6 mm (0.3 mm drill + 0.15 mm annular ring × 2)
  Recommended drill:       0.4 mm (more reliable drilling)
  Via-in-pad:              Permitted (ENIG boards), add epoxy fill specification
  
Copper pour:
  Minimum copper-to-board-edge: 0.3 mm
  Thermal relief: 4-spoke, 0.3 mm spoke width, 0.2 mm clearance
  
Silkscreen:
  Minimum text height: 0.8 mm (legible at normal magnification)
  Minimum text line width: 0.15 mm
  
Soldermask:
  Minimum solder mask dam width: 0.1 mm between adjacent SMD pads
  
Board specifications:
  Standard thickness:       1.6 mm (most devices)
  Thin boards (capsule):    0.8 mm (specify in order notes)
  Aluminum-core (NFSIM-PCR-01 thermal board): specify MCPCB in order type
  Flex PCB (NFSIM-SWEAT-01 sensor layer): specify flex in order type
  
Surface finish:
  HASL (lead-free): standard, most affordable
  ENIG: required for fine-pitch ICs (QFN < 0.5mm, BGA), flex PCBs
  
Copper weight:
  Standard:     1 oz (35 µm) outer, 0.5 oz inner
  High-current: 2 oz (70 µm) outer — specify for NFSIM-PCR-01 thermal board
  
Stackup (4-layer standard):
  L1: Signal + components (1 oz Cu)
  L2: Ground plane (0.5 oz Cu)  ← critical: contiguous ground under signal traces
  L3: Power plane (0.5 oz Cu)
  L4: Signal + components (1 oz Cu)
  Prepreg: FR4 standard Tg150
  Total board thickness: 1.6 mm ± 0.15 mm
```

**PCBA (PCB Assembly via JLCPCB):**

```
Files required for PCBA submission:
  1. Gerber files (RS-274X format): all copper layers + silkscreen + soldermask + drill
  2. BOM CSV: columns [Component, Description, Designator, LCSC Part #, Qty]
     All LCSC part numbers must be verified "in stock" at time of submission
  3. Pick-and-Place CSV: columns [Designator, Mid-X, Mid-Y, Layer, Rotation]
     Rotation in degrees; check KiCad coordinate export vs JLCPCB convention (may need 90° adjustment)
  4. Component placement confirmation: verify polarity of diodes, electrolytic caps, IC pin 1 orientation

LCSC part sourcing checklist:
  □ All parts have LCSC part number beginning with "C"
  □ All parts show "In Stock" status at order time
  □ Extended parts (non-basic): surcharge applies, flag in BOM notes
  □ Basic parts: free to use (common resistors, capacitors, standard ICs)
  □ Parts not available from LCSC: specify "Customer Supplied" in BOM → ship separately to JLCPCB

Common non-LCSC parts (ship separately):
  - Large custom heat sinks (machined aluminum)
  - Custom flex PCB components (ordered from PCBWay flex division)
  - Peltier modules (TEC1-12706 from Amazon/AliExpress — inspect for spec compliance)
  - Specialty sensors (SiPM, custom transducers — Hamamatsu, Knowles)
  - Batteries (LiPo packs — source locally, ship separately)
  - Connectors >5mm pitch (Molex, TE Connectivity — order from Mouser/Digi-Key)
```

### 23.2 Component Sourcing by Priority

```
Priority 1 — LCSC (primary for JLCPCB PCBA):
  Standard MCUs (STM32, nRF52840), passives, basic ICs
  URL: lcsc.com
  MOQ: 1 (most parts)
  Shipping: included with JLCPCB board order

Priority 2 — Mouser Electronics (global stock, fast shipping):
  Specialty ICs, sensors, precision components
  URL: mouser.com
  MOQ: 1 (most parts)
  Shipping: 1–3 days (DHL/FedEx)

Priority 3 — Digi-Key Electronics:
  Alternative to Mouser, similar catalog
  URL: digikey.com

Priority 4 — Arrow Electronics (volume pricing):
  For production runs >100 units
  URL: arrow.com

Priority 5 — AliExpress / Amazon (last resort, verify specifications):
  Peltier modules, heat sinks, mechanical hardware, cables
  ⚠ Verify specifications independently — seller claims often unverified
  ⚠ Do not use for any safety-critical components (power semiconductors, batteries)

Specialty suppliers:
  Custom magnets (MRI-01): K&J Magnetics, SuperMagnetMan
  Transducer arrays (ultrasound): Boston Piezo-Optics, Meggitt
  Biological reagents (nanopore): Sigma-Aldrich, NEB, IDT, Avanti Polar Lipids
  Parylene-C coating (neural arrays): Parylene Coating Services, SCS Coatings
  Medical adhesives: 3M Medical Specialties, Nitto Denko
  Medical-grade silicone: Nusil Technology, Elkem Silicones
  Biocompatible polymers: Evonik VESTAMID (PA12), Solvay (PEEK)
```

### 23.3 Quality Control Procedure — Universal Checklist

The following applies to all NFS devices. Device-specific additions are in per-device `/production/[DEVICE]-qc.csv` files.

```
NFSIM Universal QC Checklist v1.0
Device: _____________________ Serial: ________________ Date: _____________
Operator: ___________________ Batch Lot: _____________ FW Version: _______

VISUAL INSPECTION (magnification 10×)
□ QC-V01: No solder bridges between adjacent pads
□ QC-V02: No cold solder joints (dull/grainy appearance)
□ QC-V03: No component tombstoning (one end lifted)
□ QC-V04: No missing components (compare against BOM)
□ QC-V05: No reversed polarity (diodes, electrolytic caps, IC pin 1 marked)
□ QC-V06: No PCB damage (cracks, delamination, scorching)
□ QC-V07: Silkscreen legible, no smearing
□ QC-V08: Connector alignment correct (USB-C, JST battery, probe port)
□ QC-V09: Mechanical assembly correct (enclosure fit, button travel, display alignment)
□ QC-V10: Serial number label applied and legible

POWER-ON TEST
□ QC-P01: Apply nominal input power (USB-C 5V or LiPo 3.7V)
□ QC-P02: No smoke, no excessive heat from any component within 10 seconds
□ QC-P03: Current draw within specification ± 20% (measure with USB power monitor)
□ QC-P04: 3.3V rail: __________ V (expected: 3.30 ± 0.05V) [PASS/FAIL]
□ QC-P05: 5V rail (if present): __________ V (expected: 5.00 ± 0.10V) [PASS/FAIL]
□ QC-P06: HV rail (if present): __________ V (expected: per spec ± 2%) [PASS/FAIL]

FIRMWARE VERIFICATION
□ QC-F01: Connect USB-C → virtual serial port detected (COMx or /dev/ttyACMx)
□ QC-F02: Send NFS:PING → receive NFS:OK response within 5 seconds [PASS/FAIL]
□ QC-F03: Firmware version string matches expected: __________ [PASS/FAIL]
□ QC-F04: Hardware revision string matches: __________ [PASS/FAIL]

BLE VERIFICATION
□ QC-B01: Open BLE scanner (nRF Connect) → device appears as "NFSIM-[TYPE]-XXXXXX"
□ QC-B02: Connect → read Device Info characteristics → correct device type/serial
□ QC-B03: Write to Command characteristic → device responds correctly
□ QC-B04: BLE range test: connection maintained at 10m line-of-sight [PASS/FAIL]

BATTERY SYSTEM
□ QC-BA01: USB-C charge current: __________ mA (expected: ≥ 80% of rated charge current)
□ QC-BA02: Battery state-of-charge reading: __________ % (should be >80% for shipped device)
□ QC-BA03: Low battery alert fires at correct threshold (simulate via NFS:STATUS)

SENSOR FUNCTIONAL TEST (device-specific, abbreviated examples)
□ QC-S01: [ECG-01] Apply 1mV 1Hz sine wave to electrodes → verify signal appears in BLE stream
□ QC-S01: [CGM-01] Immerse sensor in 100 mg/dL glucose reference → reading within ±15 mg/dL
□ QC-S01: [PCR-01] Run temperature calibration protocol → block temp within ±0.5°C of setpoint
□ QC-S01: [US-01] Connect to laptop → B-mode image of tissue phantom appears within 5 seconds

WATERPROOFING (if rated IPX4 or higher)
□ QC-W01: Spray test (IPX4) or submersion test (IPX7/IPX8) per rated specification
□ QC-W02: Post-test: power on, verify normal operation, no water ingress visible

FINAL FIRMWARE BURN
□ QC-FF01: Write unique serial number to device NVS: NFS:CONFIGURE {"serial":"NFSIM-[TYPE]-XXXXXX"}
□ QC-FF02: Verify serial persists after power cycle: NFS:STATUS → check serial field

PACKAGING
□ QC-PK01: Device sealed in anti-static bag
□ QC-PK02: All accessories included (cables, electrodes, calibration reference, quick-start card)
□ QC-PK03: QC sticker applied with serial, date, operator initials, PASS/FAIL
□ QC-PK04: Box sealed, shipping label applied

RESULT: □ PASS — Ready to ship    □ FAIL — Requires rework (see failure log)
Failure notes: _______________________________________________________________
```

### 23.4 Calibration Standards Per Domain

```
MOLECULAR / GENOMIC (thermal calibration):
  Reference: NIST-traceable platinum resistance thermometer (PRT), ±0.02°C
  Points: 60°C, 72°C, 95°C (three PCR stage temperatures)
  Acceptance: Device block temp ± 0.5°C vs PRT at all three points
  Tool: ST-Link + custom calibration firmware mode
  Output: cal_coefficients = [slope, offset] per temperature zone

CHEMICAL (concentration calibration):
  Glucose: NIST-traceable glucose reference solutions (40, 100, 200, 400 mg/dL)
    Prepared from D-(+)-Glucose, anhydrous, TraceCERT (Sigma-Aldrich)
    Acceptance: ±5% at each concentration point
  Lactate: L-Lactic acid reference (1, 5, 15 mmol/L)
  pH: NIST pH buffers (4.00, 7.00, 10.00 ± 0.01 pH)
  Electrolytes: NIST SRM 956e (serum-based multi-analyte certified reference)

ELECTRICAL (signal calibration):
  ECG: Fluke ProSim 4 ECG simulator (1 mV, 1 Hz; 1 mV QRS morphology)
    Acceptance: amplitude within ±5%, timing within ±1ms
  EEG: Custom low-noise voltage divider from 10 µV reference source
    Acceptance: amplitude within ±10%
  EMG: Function generator, 100 mV 200 Hz burst into 1 kΩ resistive load
    Acceptance: amplitude within ±5%

STRUCTURAL / IMAGING (resolution calibration):
  Ultrasound: ATS Laboratories Model 539 Multi-Purpose Tissue Mimicking Phantom
    Targets: 3 mm, 6 mm diameter anechoic spheres at 1, 3, 5, 7 cm depths
    Acceptance: target visible, axial resolution ≤ spec, depth accuracy ±2 mm
  OCT: NIST-traceable optical flat (surface reflectivity ± 1%)
  Microscopy: USAF 1951 resolution test chart
    Acceptance: resolves Group 7 Element 6 (2.19 µm) at 40× objective

All calibration records linked to device serial number and stored in:
  1. Device NVS (for runtime use)
  2. Production batch database (for traceability)
  3. NFS record (UBERON: calibration event, data_type: "device_calibration")
```

---

## 24. Regulatory, Legal and Compliance

### 24.1 Device Classification by Region

| Device | US FDA Class | EU MDR Class | Notes |
|---|---|---|---|
| NFSIM-PCR-01 through PCR-04 | Exempt (RUO) | Not regulated | Label: "For Research Use Only" |
| NFSIM-SEQ-01, SEQ-02 | Exempt (RUO) | Not regulated | Label: "For Research Use Only" |
| NFSIM-CRISPR-01 through 03 | RUO or IVD Class II (if clinical claim) | IVD Class B (EU IVDR) | Clinical use requires regulatory action |
| NFSIM-dPCR-01 | RUO | Not regulated | Absolute quantification tool |
| NFSIM-GELEC-01, 02 | RUO | Not regulated | Standard molecular biology equipment |
| NFSIM-US-01 (General Wellness) | General Wellness, Exempt | Not regulated | Avoid diagnostic claims in marketing |
| NFSIM-US-01 (Diagnostic) | Class II (510k, 21 CFR 892.1550) | Class IIa (MDR) | Requires regulatory submission for diagnostic use |
| NFSIM-US-02 through 09 | RUO or Class II (diagnostic claim) | Class IIa/IIb | Depends on intended use claim |
| NFSIM-MRI-01 | Class II (510k) if diagnostic | Class IIa (MDR) | Research MRI exempt from most requirements |
| NFSIM-XRAY-01 | Requires state/federal radiation authorization | Class IIa | Cannot operate without radiation safety authorization regardless of class |
| NFSIM-OCT-01 | Class II (510k predicate: multiple) | Class IIa | |
| NFSIM-MICRO-01 | Class I (general wellness AI support) | Not regulated | Avoid diagnostic claims |
| NFSIM-CGM-01 (RUO) | Exempt | Not regulated | Clinical use requires 510k and ISO 15197 |
| NFSIM-CGM-01 (closed-loop) | Class III (PMA) | Class III (MDR) | Artificial pancreas = highest class |
| NFSIM-SWEAT-01 | General Wellness | Not regulated | Avoid clinical diagnostic claims |
| NFSIM-CHEM-01 through 07 | IVD Class II if clinical claim | IVD Class B/C (EU IVDR) | Depends on analyte and claim |
| NFSIM-OXY-01 | Class II (510k, cerebral oximeter) | Class IIa | For clinical cerebral monitoring |
| NFSIM-ECG-01 (Wellness) | General Wellness | Not regulated | "Heart Rate Monitoring" = wellness |
| NFSIM-ECG-01 (AFib detection) | Class II (De Novo or 510k) | Class IIa (MDR) | Arrhythmia detection = medical device |
| NFSIM-ECG-02 (12-lead) | Class II (510k, Holter) | Class IIa | |
| NFSIM-EEG-01 | Class II (510k) or RUO | Class IIa | Depends on intended use claim |
| NFSIM-EMG-01 | Class I or II | Class I | Consumer wellness positioning possible |
| NFSIM-NEURAL-01, 02 | Class III (PMA) | Class III | Neurosurgical research only |
| NFSIM-CAP-01 through 10 | Class III (PMA) — ingestibles | Class III (MDR) | Highest regulatory burden; RUO/research only currently |
| NFSIM-PATCH-01 | General Wellness | Not regulated | Multi-parameter wellness monitoring |
| NFSIM-PATCH-02 | Class II (wound monitor) | Class IIa | Wound care application |
| NFSIM-PATCH-03 (iontophoresis) | Class II (510k, 21 CFR 890.5350) | Class IIb | Drug delivery requires regulatory action |
| NFSIM-IMPLANT-01 | Class III (implant) | Class III (MDR) | Animal + IRB research only |
| NFSIM-IMPLANT-02 | Class III (neurostimulator) | Class III (MDR) | IRB + neurosurgeon required |
| NFSIM-FLOW-01 | Class II (hematology analyzer) | IVD Class B | Depends on clinical claim |
| NFSIM-ENV-01 through 05 | Exempt or CLIA-waived equivalent | Not regulated | Environmental monitoring, not clinical |
| NFSIM-DEL-01 through 03 | Class II–III depending on drug | Class IIb–III | Drug delivery regulatory complexity |
| NFSIM-ABL-01, 02 | Class II (electrosurgical) | Class IIb | Requires training; not consumer |

**All NFS devices are shipped with this label:**

> **FOR RESEARCH USE ONLY. NOT INTENDED FOR CLINICAL DIAGNOSTIC USE.
> This device has not been evaluated or approved as a medical device by the FDA, CE authorities, or any other regulatory body. It is not intended to diagnose, treat, cure, or prevent any disease or medical condition. Use for clinical decision-making without appropriate regulatory clearance may be illegal in your jurisdiction.**

### 24.2 Wireless Regulatory Compliance

```
FCC (United States):
  BLE (nRF52840, ESP32): Pre-certified modules eliminate need for independent FCC ID
    nRF52840-QIAA module used in NFS devices: CE/FCC certified when used per Nordic guidelines
    FCC ID: use module's FCC ID on product label (follow module integration instructions)
    Antenna: PCB trace antennas must match certified module antenna design
  
  Wi-Fi (ESP32-WROOM): FCC ID 2AC7Z-ESP32WROOM32D
    Use within certified parameters → use module's FCC ID
  
  434 MHz radio (Si4463 in capsules):
    Capsule is internal to body → Part 15.247 body-worn/implanted device rules apply
    External belt receiver: if TX power < −1 dBm conducted → Part 15B exempt
    If external TX needed: 434 MHz licensed medical MICS band (402–405 MHz preferred) OR
    Part 15 compliance test required for 434 MHz ISM band transmission
  
  USB devices: No FCC certification needed for USB (conducted, not radiated)
  
  X-ray (NFSIM-XRAY-01): Not FCC-regulated (non-radio frequency device)
    Requires state radiation control program notification in most US states
    Federal FDA 21 CFR Part 1020 compliance (diagnostic X-ray equipment performance standard)

CE (European Union):
  Radio Equipment Directive (RED) 2014/53/EU:
    All BLE, Wi-Fi devices must comply
    Pre-certified modules: use module's CE declaration within specified parameters
    434 MHz: must comply with ETSI EN 300 220 (SRD devices, 434 MHz band)
  
  Medical Device Regulation (MDR) 2017/745:
    Clinical use → Notified Body involvement (for Class IIa and above)
    Research use → can self-certify for most Class I equivalent uses
  
  IVDR 2017/746:
    In vitro diagnostic devices sold for clinical use → IVDR compliance
    Research reagents and tools → exempt

Canada (ISED):
  BLE: RSS-247 Issue 2 (covered by pre-certified nRF52840 module)
  Other RF: follow module certifications where available

Japan (MIC/Telec):
  2.4 GHz (BLE/Wi-Fi): Telec R approval required for Japan market
  Pre-certified modules: confirm Telec mark on module

Strategy for pre-market development phase:
  All NFS devices are labeled as "Development/Research Hardware"
  Not offered for sale as finished medical devices
  Community builders are responsible for their own regulatory compliance
  NanoFlowSIM project provides compliance documentation templates to assist community
```

### 24.3 Software Licensing (Complete)

```
NanoFlowSIM SOFTWARE License (MIT):

MIT License
Copyright (c) 2026 NanoFlowSIM Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.


NanoFlowSIM HARDWARE License (CERN OHL-W v2):

All hardware designs (schematics, PCB layouts, Gerber files, BOMs, mechanical
CAD files) are released under the CERN Open Hardware Licence Version 2 —
Weakly Reciprocal (CERN OHL-W v2).

Under CERN OHL-W v2:
  ✓ You may use, study, modify, and distribute these hardware designs
  ✓ You may sell products based on these designs
  ✓ Attribution required: "Based on NanoFlowSIM hardware (CERN OHL-W v2)"
  ✓ Modifications to hardware files must be shared under same license
  ✗ Products themselves need not be open-source (weakly reciprocal)
  ✗ No warranty provided

Full license text: legal/LICENSE-HARDWARE.md


NanoFlowSIM DOCUMENTATION License (CC BY 4.0):

All documentation, guides, and research content are released under
Creative Commons Attribution 4.0 International (CC BY 4.0).

Under CC BY 4.0:
  ✓ Share and adapt freely for any purpose (including commercial)
  ✓ Attribution required: "NanoFlowSIM Documentation, CC BY 4.0"
  ✓ Derivatives allowed under any compatible license
```

### 24.4 Data Privacy Compliance

```
GDPR (EU General Data Protection Regulation):
  Data controller: the individual patient (self-sovereignty model)
  Data processor: NanoFlowSIM software (processes on behalf of patient)
  No NanoFlowSIM central servers collect or store patient data by default
  Rights implemented:
    Right to access: NFS:DUMP exports all patient data on demand
    Right to erasure: NFS:RESET {"factory":true} purges all local data
    Right to portability: full FHIR R4 bundle export available
    Right to object: research contribution is opt-in, revocable
  Genomic data: special category per Art. 9 → explicit consent per use case
  International transfers: no cloud transfers by default
                           Self-hosted servers: patient's own responsibility

HIPAA (US):
  NanoFlowSIM as self-hosted software: patient is covered entity or operates under one
  BAA (Business Associate Agreement) template: provided in /legal/BAA_template.docx
  PHI (Protected Health Information) safeguards:
    Encryption at rest: AES-256 (SQLCipher + MinIO server-side)
    Encryption in transit: TLS 1.3 mandatory for any cloud sync
    Access control: biometric/PIN device lock
    Audit log: all data access events timestamped (stored in SQLite audit table)
    Breach notification: patient responsible; NanoFlowSIM project provides templates
  De-identification standard: HIPAA Safe Harbor (§164.514(b)) compliant export option
    Removes: 18 PHI identifiers from export (name, DOB, zip, etc.)

Nagoya Protocol (Convention on Biological Diversity):
  Genetic resources: patient genomic data from individuals in provider countries
  NanoFlowSIM policy: all genomic data stored locally on patient device by default
  No biological data transmitted to external databases without explicit patient consent
  Sequence data contributions to public databases: patient initiates with full informed consent
  Benefit sharing: not applicable for individual health data (applies to population-level research)

ELSI (Ethical, Legal, and Social Implications) guidelines:
  Genetic discrimination: warn users in jurisdictions without GINA-equivalent protections
  Incidental findings: disclose policy for simulation outputs that suggest disease risk
  Minor users: additional consent flow for users under 18
  Research data sharing: explicit opt-in, revocable, de-identified by default
```

---

## 25. Roadmap

### Phase 1 — Foundation (Months 1–12)

**Simulation Engine:**
- [x] Complete architecture and crate structure design
- [ ] nfsim-core: all shared types, UBERON ontology, patient data structures
- [ ] nfsim-molecular: receptor-ligand Gillespie model, CRISPR efficiency, payload stability
- [ ] nfsim-cellular: endocytosis pathway probabilities, endosomal escape, trafficking
- [ ] nfsim-grpc: gRPC server, proto file, tonic implementation
- [ ] nfsim-cli: basic simulation runner with JSON config
- [ ] Unit tests: >80% coverage for all simulation crates

**Platform:**
- [ ] Django backend: patients, records, sessions, devices API endpoints
- [ ] PostgreSQL schema: all tables with indices
- [ ] SQLite local data model (desktop)
- [ ] Basic 3D body map: generic anatomical mesh, clickable regions, UBERON tags
- [ ] BLE device management (nRF52840 devices)
- [ ] NFS BLE protocol library (Python + TypeScript)
- [ ] Desktop Electron app: skeleton, IPC bridge, SQLite integration, basic UI

**Hardware (Priority Tier 1):**
- [ ] NFSIM-PCR-01: complete KiCad design, prototype fabrication, firmware v1.0
- [ ] NFSIM-ECG-01: complete KiCad design, prototype fabrication, firmware v1.0 + AFib AI model
- [ ] NFSIM-CGM-01: sensor filament chemistry protocol finalized, transmitter prototype, firmware v1.0
- [ ] NFSIM-EEG-01: ADS1299 board, dry electrode headset mechanical design
- [ ] NFSIM-CRISPR-01: optical reader prototype, SHERLOCK assay validation

### Phase 2 — Core Platform (Months 6–18)

**Simulation:**
- [ ] nfsim-tissue: EPR model, TME, BBB crossing model
- [ ] nfsim-systemic: full two-compartment PK, MPS clearance, complement
- [ ] nfsim-ml: LightGBM therapy ranker, Bayesian NP optimizer
- [ ] nfsim-visualization: trajectory data output for Three.js rendering
- [ ] Back-testing framework: clinical data import and Bayesian parameter refinement
- [ ] Simulation validated against 5+ published nanoparticle PK datasets

**Platform:**
- [ ] DICOM import pipeline: file parsing, Cornerstone.js viewer, UBERON auto-tagging
- [ ] FHIR R4 client: OAuth2 SMART-on-FHIR, all resource types, DICOM WADO-RS
- [ ] Consumer mode UI: full 3D body map interaction, region detail, timeline scrubber
- [ ] Data entry flows: manual, hospital import, device connect — all end-to-end tested
- [ ] Mobile app: BLE management, basic body map, live sensor cards, alerts
- [ ] Django backend: Celery FHIR import task, DICOM segmentation subprocess
- [ ] NanoFlowSIM-to-simulation bridge: gRPC client, job submission, result display

**Hardware (Priority Tier 2):**
- [ ] NFSIM-PCR-02: gel-slip reader, gel strip consumable design finalized
- [ ] NFSIM-PCR-03: LAMP reader validated against COVID-19 LAMP assay
- [ ] NFSIM-US-01: ultrasound probe prototype, beamformer FPGA firmware, B-mode validated on phantom
- [ ] NFSIM-EMG-01: armband prototype, gesture classifier trained (NinaPro dataset)
- [ ] NFSIM-SWEAT-01: flexible patch prototype, PDMS microfluidic fabrication
- [ ] NFSIM-EEG-01: full prototype with dry electrodes, OpenBCI GUI compatible

### Phase 3 — Simulation Integration (Months 12–24)

**Simulation:**
- [ ] Full hybrid therapy simulation (CRISPR + chemo + immunotherapy simultaneous)
- [ ] Patient-specific simulation from DICOM-derived mesh (tissue geometry)
- [ ] Blood-brain barrier model validated against published CNS drug delivery data
- [ ] Drug combination optimizer (full Bayesian search over design space)
- [ ] Clinical application: HIV latent reservoir targeting simulation validated

**Platform:**
- [ ] Level 2 body map: DICOM-derived patient-specific organ mesh rendering
- [ ] Level 3: live sensor stream overlay on 3D body (animated per sensor type)
- [ ] Level 4: genomic variant overlay, nanoparticle trajectory rendering
- [ ] Professional mode: complete (all 6 tabs, cohort view, audit log)
- [ ] Python SDK published to PyPI (nfsim-sdk)
- [ ] Node.js SDK published to npm (@nfsim/sdk)
- [ ] AR overlay (mobile): ARKit/ARCore body map overlay functional
- [ ] Pharmacogenomics checker: drug-gene interaction from VCF loaded profile

**Hardware (Advanced):**
- [ ] NFSIM-SEQ-01: nanopore sequencer prototype — membrane stability achieved, reads demonstrated
- [ ] NFSIM-CAP-01: ingestible optical camera capsule — animal model GI transit study
- [ ] NFSIM-CAP-06: pH/pressure motility capsule — human volunteer transit study
- [ ] NFSIM-MRI-01: Halbach magnet assembly completed, first brain images acquired
- [ ] NFSIM-FLOW-01: portable cytometer — CBC results validated against reference hematology analyzer
- [ ] Open basecaller (NFSIM Basecaller): trained model released (accuracy target Q15+)

### Phase 4 — Ecosystem Maturation (Months 18–36)

**Platform:**
- [ ] All 75+ devices have CI-tested firmware (automated build + flash + basic functional test)
- [ ] NanoFlowSIM community forum launched (GitHub Discussions + Discord)
- [ ] Hardware sharing: community PCB order coordination (group buys for expensive boards)
- [ ] Clinical research partnerships: IRB protocols established with 3+ academic institutions
- [ ] Simulation validated against published clinical trial data (target: 10+ datasets)
- [ ] Desktop app: macOS DMG + Windows NSIS + Linux AppImage on GitHub Releases
- [ ] Mobile app: iOS App Store + Android Google Play (consumer wellness positioning)
- [ ] Rust client library published to crates.io

**Advanced Hardware:**
- [ ] NFSIM-CAP-02: GI ultrasound capsule — phantom imaging validated
- [ ] NFSIM-CAP-03: DNA/RNA capture capsule — sequencing from capsule-collected microbiome
- [ ] NFSIM-IMPLANT-01: subcutaneous sensor node — 30-day animal biocompatibility study
- [ ] NFSIM-dPCR-01: digital PCR — ctDNA detection at 0.01% VAF demonstrated
- [ ] All environmental devices: field deployed in 3+ locations (water, air, vector)

### Phase 5 — Future (36+ Months)

- [ ] Continuous liquid biopsy monitor interface: architecture ready to receive cfDNA stream
- [ ] Neural implant data integration: Open Ephys native NanoFlowSIM plugin
- [ ] Full digital twin integration: all modalities fused, AI physiological model
- [ ] Simulation → AI treatment suggestion: with appropriate clinical oversight UI
- [ ] Federated research network: de-identified pattern sharing across consenting users
- [ ] Nanoparticle synthesis verification: simulation → actual NP characterization result comparison
- [ ] Regulatory pathway: initiation of 510(k) or CE submissions for select high-impact devices
  - Priority candidates: NFSIM-CGM-01 (IVD Class II), NFSIM-ECG-01 AFib (De Novo Class II)
- [ ] Open manufacturing guide: distributed production playbook for low-resource settings
- [ ] Companion platform for agricultural and ecological sensing (NanoFlowSIM Environment)

---

## 26. Contributing

NanoFlowSIM is an open-science project welcoming contributions across hardware, firmware, software, biology, chemistry, and documentation.

### Getting Started

1. Read this README in full — it is the single source of truth for the project's architecture and scope
2. Browse open issues: `github.com/[org]/nanoflowsim/issues`
3. Join the community Discord: `discord.gg/nfsim` (channels: #hardware, #firmware, #software, #simulation, #biology, #off-topic)
4. Introduce yourself in `#introductions` — describe your background and what you'd like to work on
5. Pick an issue tagged `good-first-issue`, `hardware-help-wanted`, `firmware`, or `simulation`

### Areas and Skills Needed

| Contribution Area | Skills | Entry Point |
|---|---|---|
| PCB design | KiCad 6+, electronics, analog design | Review existing PCB, open a DRC report |
| Firmware | Embedded C/C++, FreeRTOS, STM32 HAL | Flash an existing device, add a test case |
| Simulation engine | Rust, biophysics, computational biology | Read nfsim-molecular, add a model variant |
| Desktop app | React, TypeScript, Three.js, Electron | Run desktop app, fix a UI issue |
| Mobile app | React Native, Expo, BLE | Run mobile app, add a sensor card component |
| Backend | Django 5, DRF, PostgreSQL | Run backend, add an API endpoint test |
| AI / ML | PyTorch, TFLite, signal processing | Train or improve an on-device classifier |
| Basecaller | PyTorch, nanopore biology, CTC | Improve NFSIM basecaller accuracy |
| Hardware chemistry | Biochemistry, enzymology, microfluidics | Validate sensor chemistry, improve protocols |
| Documentation | Technical writing, medical knowledge | Fix a doc error, add a device theory guide |
| Testing / QA | Biology, electrical testing, software testing | Run QC checklist on a built device |
| Translation | Languages (Spanish, Mandarin, French, Portuguese...) | Translate UI strings or documentation |

### Development Environment Setup

**Simulation engine:**
```bash
# Prerequisites: Rust stable (rustup)
git clone https://github.com/[org]/nanoflowsim.git
cd nanoflowsim/simulation
cargo build --release
cargo test
# Run a basic simulation
./target/release/nfsim-cli --config examples/her2_breast_cancer.json
```

**Firmware (NFSIM-PCR-01 example):**
```bash
# Prerequisites: PlatformIO, ST-Link V3
cd hardware/NFSIM-PCR-01/firmware
pio run                           # Build
pio run --target upload           # Flash via ST-Link
pio device monitor --baud 115200  # Open serial monitor
# Send: NFS:PING
# Expect: NFS:OK {"device":"NFSIM-PCR-01","fw":"1.0.0","hw":"RevA","proto":"1.0.0"}
```

**Desktop application:**
```bash
# Prerequisites: Node.js 20, npm 10
cd platform/desktop
npm install
npm run dev                        # Development mode (Electron + Webpack dev server)
npm run build                      # Production build
npm run package                    # Create distributable (macOS/Windows/Linux)
```

**Backend server:**
```bash
# Prerequisites: Python 3.12, Docker (for PostgreSQL + Redis + MinIO)
cd platform/backend
docker-compose up -d               # Start infrastructure services
pip install -r requirements.txt --break-system-packages
python manage.py migrate
python manage.py runserver
# API available at http://localhost:8000/api/v1/
```

**Mobile app:**
```bash
# Prerequisites: Node.js 20, Expo Go app (iOS/Android)
cd platform/mobile
npm install
npx expo start
# Scan QR code with Expo Go app
```

### Contribution Process

1. **Fork** the repository → create a feature branch (`git checkout -b feature/your-feature`)
2. **Make changes** following code style guidelines (see below)
3. **Write or update tests** for your changes
4. **Update documentation** if API, protocol, or hardware changes
5. **Open a Pull Request** against the `develop` branch (never directly to `main`)
6. **CI must pass**: all automated checks (build, DRC, tests, lint)
7. **Review**: at least 2 approvals required; hardware changes need schematic + Gerber preview images
8. **Merge**: squash merge with conventional commit message (`feat:`, `fix:`, `docs:`, `hw:`)

### Code Style Guidelines

```
Firmware (C/C++):
  Google C++ Style Guide (https://google.github.io/styleguide/cppguide.html)
  Max function length: 50 lines (break into sub-functions)
  Comment: all HAL driver functions with purpose + parameter units
  Naming: snake_case for functions and variables, UPPER_CASE for constants

Rust (simulation engine):
  rustfmt (run: cargo fmt --all)
  clippy (run: cargo clippy --all -- -D warnings)
  All public functions: doc comments with examples
  Error handling: use thiserror crate, no unwrap() in library code

Python (backend, SDK):
  Black (black .)
  isort (isort .)
  flake8 (flake8 --max-line-length=120)
  Type hints: all function signatures must have type annotations
  Docstrings: Google style

TypeScript (desktop, mobile):
  ESLint + Prettier (Airbnb config)
  Strict TypeScript: no `any` types except in legitimate generic boundaries
  React: functional components only, hooks for state
  Props: all component props typed with interface

KiCad (hardware):
  Schematic: net names descriptive (e.g., SPI1_MOSI not MOSI)
  PCB: component reference designators visible on silkscreen
  BOM: LCSC part numbers required for all SMD components
  Gerber export: run DRC before every Gerber export (zero errors policy)
  Git: commit both .kicad_sch and .kicad_pcb together with matching changelog entry
```

### Hardware Contribution Checklist

Before submitting a PCB design PR:
```
□ DRC clean (zero errors in KiCad DRC)
□ All components have LCSC part numbers in BOM
□ Schematic reviewed for correctness (power domains, pull-ups, bypass caps)
□ Gerber preview attached to PR (use kicanvas.org for rendering)
□ hardware_config.md updated with pin assignments
□ BOM cost estimate included
□ Firmware header updated with new pin definitions if applicable
□ Test plan described in PR description
```

---

## 27. Acknowledgements

NanoFlowSIM is built on the intellectual and technical contributions of thousands of open-science pioneers. We acknowledge the following projects, researchers, and communities:

### Open-Source Hardware That Showed the Path

**OpenPCR** (Josh Perfetto, Tito Jankowski, 2012) — proved that PCR thermocyclers could be open-source, Arduino-based, and affordable. The first demonstration that molecular biology hardware could be democratized. NanoFlowSIM's PCR devices build directly on this philosophical foundation and technical lineage.

**OpenBCI** (Joel Murphy, Conor Russomanno, 2013) — democratized EEG neural sensing, proving that research-grade brain measurement hardware could be open and community-built. The ADS1299-based architecture of NFSIM-EEG-01 follows OpenBCI's pioneering work.

**Open Ephys** (Josh Siegle, Jakob Voigts et al., 2016) — created the open-source standard for neuroscience data acquisition, enabling the Intan RHD2000-based ecosystem. NFSIM-NEURAL-01 is fully Open Ephys compatible.

**Hyperfine** — pioneered portable low-field MRI, proving that superconducting magnets are not the only path. NFSIM-MRI-01's Halbach array approach is informed by published academic low-field MRI work.

**Butterfly Network** — demonstrated CMUT-based single-chip ultrasound, making handheld ultrasound feasible. NFSIM-US-01 and NFSIM-US-02 build on the CMUT concept in an open hardware framework.

**Opentrons** — democratized liquid-handling laboratory automation. NFSIM-ENV-02 sample preparation draws on Opentrons' microfluidic automation philosophy.

**Bento Lab** — pioneered the portable complete molecular biology lab concept. NanoFlowSIM extends this to a full multi-domain sensing ecosystem.

### Open-Source Software and Algorithms

**MaRCoS (Magnetic Resonance Control System)** — open-source MRI console that makes NFSIM-MRI-01 achievable without proprietary RF generation hardware.

**Open Ephys GUI** — the foundation for NFSIM-NEURAL-01 neural data acquisition software integration.

**BART (Berkeley Advanced Reconstruction Toolbox)** — open-source MRI reconstruction enabling AI-enhanced low-field image quality.

**FastMRI** (NYU + Facebook AI Research) — open-source accelerated MRI datasets and models that train the AI reconstruction used in NFSIM-MRI-01.

**Bonito** (Oxford Nanopore Technologies, open-source release) — the open-source nanopore basecaller training pipeline used to create the NFSIM basecaller.

**Kilosort** (Marius Pachitariu, Cortexlab UCL) — spike sorting algorithm powering NFSIM-NEURAL-01 analysis.

**MNE-Python** — open-source EEG/MEG analysis toolkit, target compatibility for NFSIM-EEG-01 output.

**3D Slicer** — open-source medical image informatics and 3D visualization, predecessor tool for DICOM import workflows.

**ITK / SimpleITK** — image processing toolkit underpinning DICOM segmentation in NanoFlowSIM.

**QIIME2** — open-source microbiome bioinformatics, downstream analysis for NFSIM-CAP-07 microbiome samples.

**OpenSIM** — musculoskeletal simulation that inspired NanoFlowSIM's physics-first simulation philosophy.

**FreeRTOS** (Amazon Web Services) — the RTOS backbone of NanoFlowSIM device firmware.

**Zephyr RTOS** (Linux Foundation) — alternative RTOS used in select NFS devices.

**Buildroot** — minimal Linux for embedded compute nodes (NFSIM-MICRO-01, MRI-01 console).

**TensorFlow Lite Micro** (Google) — enables on-device AI inference across all NFS devices.

### Scientific Communities

**DIYbio** community — proved that molecular biology can happen outside institutional labs. NanoFlowSIM is a direct heir to the DIYbio spirit.

**iGEM Foundation** (International Genetically Engineered Machine) — synthetic biology democratization that laid cultural groundwork for open biological hardware.

**NIH BRAIN Initiative** — funded open neuroscience tool development that made Neuropixels and Open Ephys possible.

**OpenNeuro** — open neuroscience dataset repository providing training data for neural AI models.

**PhysioNet** — open physiological signal database (MIT-BIH, MIMIC) enabling ECG AI model training.

**NinaPro** — open EMG database for prosthetic control research enabling NFSIM-EMG-01 gesture classification.

### PCB Manufacturing Access

**JLCPCB** — affordable PCB fabrication and assembly making open-source hardware actually buildable by individuals and small teams.

**PCBWay** — specialized PCB fabrication for flex, aluminum-core, and complex multilayer boards.

**OSH Park** — community-friendly US-based PCB fab (purple boards, beloved by makers).

### Foundational Science

The researchers who published the fundamental physics behind every sensing modality documented in this README — from Röntgen's X-ray discovery (1895) through Mullis's PCR invention (1983) through the Oxford Nanopore revolution (2015) — made all of this possible. Open science has always stood on the shoulders of published science.

---

## 28. License

```
NanoFlowSIM Ecosystem — Open-Source Precision Medicine Platform

─────────────────────────────────────────────────────────────────────

SOFTWARE (firmware, simulation engine, desktop app, mobile app,
          backend server, SDKs, scripts, tools)

MIT License
Copyright (c) 2026 NanoFlowSIM Contributors

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject
to the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS
BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN
ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

─────────────────────────────────────────────────────────────────────

HARDWARE (schematics, PCB layouts, Gerber files, BOMs,
          mechanical CAD files, 3D models, consumable designs)

CERN Open Hardware Licence Version 2 — Weakly Reciprocal
(CERN OHL-W v2)
Copyright (c) 2026 NanoFlowSIM Contributors

Full text: legal/LICENSE-HARDWARE.md

Key conditions:
  • Use, study, modify, and distribute freely
  • Products based on this hardware may be sold commercially
  • Attribution required: "Based on NanoFlowSIM hardware (CERN OHL-W)"
  • Modifications to hardware source files must be shared under
    CERN OHL-W v2 or compatible license
  • No warranty provided; users assume all risk

─────────────────────────────────────────────────────────────────────

DOCUMENTATION (README, guides, theory documents, API references,
               assembly guides, calibration procedures)

Creative Commons Attribution 4.0 International (CC BY 4.0)
Copyright (c) 2026 NanoFlowSIM Contributors

Full text: legal/LICENSE-DOCS.md

You are free to:
  Share — copy and redistribute in any medium or format
  Adapt — remix, transform, and build upon the material
  for any purpose, even commercially.

Under the following terms:
  Attribution — give appropriate credit, provide a link to the
  license, and indicate if changes were made.

─────────────────────────────────────────────────────────────────────

THIRD-PARTY COMPONENTS

All third-party dependencies retain their original licenses.
See legal/third-party-licenses/ for the complete set.

Notable third-party licenses included:
  FreeRTOS:          MIT License (Amazon Web Services)
  TensorFlow Lite:   Apache 2.0 (Google LLC)
  Three.js:          MIT License
  React:             MIT License (Meta Platforms)
  Django:            BSD 3-Clause (Django Software Foundation)
  KiCad Libraries:   Creative Commons CC-BY-SA 4.0
  MaRCoS:            GPL v3 (MaRCoS contributors)
  Open Ephys:        GPL v3 (Open Ephys contributors)
  Bonito:            Mozilla Public License 2.0 (Oxford Nanopore)

─────────────────────────────────────────────────────────────────────

DISCLAIMER

ALL NANOFLOWSIM HARDWARE DEVICES ARE LABELED:
"FOR RESEARCH USE ONLY. NOT FOR CLINICAL DIAGNOSTIC USE."

None of the hardware or software in this repository has been
evaluated, cleared, or approved as a medical device by the FDA,
CE/MDR notified bodies, Health Canada, or any other regulatory
authority anywhere in the world.

These designs are not intended to diagnose, treat, cure, prevent,
or monitor any disease or medical condition.

Use of NanoFlowSIM hardware or software for clinical decision-making
without appropriate regulatory clearance in your jurisdiction may
be illegal. Users assume full responsibility for regulatory
compliance in their region.

The NanoFlowSIM project and its contributors expressly disclaim all
liability for any injury, illness, data loss, or legal consequence
arising from the use of these designs, regardless of how such use
occurs.

─────────────────────────────────────────────────────────────────────

Repository:   github.com/[org]/nanoflowsim
Documentation: docs.nfsim.io
Community:    discord.gg/nfsim
PyPI:         pypi.org/project/nfsim-sdk
npm:          npmjs.com/package/@nfsim/sdk
crates.io:    crates.io/crates/nfsim-client
Version:      1.0.0-alpha
Date:         2026
```

---

*NanoFlowSIM is built on the conviction that every layer of biological sensing — from the genome inside the nucleus to the environment outside the skin — should be simultaneously open, portable, affordable, and unified into a single living model of the patient.*

*Every schematic published is a hospital that doesn't need to be built.*
*Every open firmware release is a lab that doesn't need to be staffed.*
*Every simulation that finds a better therapy is a future that was otherwise invisible.*

*Built open. Built portable. Built for everyone.*
