# NanoFlowSIM

> **Integrated Precision Medicine Platform — Multi-Layered Computational Analysis, Open-Source Portable Biological Sensing Ecosystem, and Full-Stack Patient Data Architecture**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Hardware: CERN OHL v2](https://img.shields.io/badge/Hardware-CERN%20OHL%20v2-blue.svg)](legal/CERN_OHL_v2.txt)
[![Status: Active Development](https://img.shields.io/badge/Status-Active%20Development-green.svg)]()
[![Platforms: Linux | Windows | macOS | Android | iOS](https://img.shields.io/badge/Platforms-Linux%20%7C%20Windows%20%7C%20macOS%20%7C%20Android%20%7C%20iOS-lightgrey.svg)]()

---

## Table of Contents

1. [Project Vision](#1-project-vision)
2. [NanoFlowSIM Software Platform](#2-nanoflowsim-software-platform)
   - 2.1 [Key Features](#21-key-features)
   - 2.2 [System Workflow](#22-system-workflow)
   - 2.3 [Therapy Modeling](#23-therapy-modeling)
   - 2.4 [Expanded Clinical Applications](#24-expanded-clinical-applications)
3. [Data Integration Architecture — The Full Loop](#3-data-integration-architecture--the-full-loop)
   - 3.1 [Non-Continuous Data Sources](#31-non-continuous-data-sources)
   - 3.2 [Continuous Data Sources (Current)](#32-continuous-data-sources-current)
   - 3.3 [Future Continuous Systems](#33-future-continuous-systems)
   - 3.4 [Patient Data Aggregation Model](#34-patient-data-aggregation-model)
4. [UI/UX Specification — Consumer and Professional](#4-uiux-specification--consumer-and-professional)
   - 4.1 [Design Philosophy](#41-design-philosophy)
   - 4.2 [3D Body Map System](#42-3d-body-map-system)
   - 4.3 [Consumer View](#43-consumer-view)
   - 4.4 [Professional/Clinical View](#44-professionalclinical-view)
   - 4.5 [Data Capture Workflow](#45-data-capture-workflow)
   - 4.6 [Live vs. Historical Mode](#46-live-vs-historical-mode)
   - 4.7 [Regional Data Interaction](#47-regional-data-interaction)
5. [Biological Sensing Domains — Complete Evolutionary Study](#5-biological-sensing-domains--complete-evolutionary-study)
   - 5.1 [Molecular / Genomic Sensing](#51-molecular--genomic-sensing)
   - 5.2 [Structural / Anatomical Imaging](#52-structural--anatomical-imaging)
   - 5.3 [Chemical / Metabolic Sensing](#53-chemical--metabolic-sensing)
   - 5.4 [Electrical / Bioelectric Sensing](#54-electrical--bioelectric-sensing)
   - 5.5 [Implantable / Closed-Loop Systems](#55-implantable--closed-loop-systems)
   - 5.6 [Cellular / Microscopic Sensing](#56-cellular--microscopic-sensing)
   - 5.7 [Dynamic Physiological Monitoring](#57-dynamic-physiological-monitoring)
   - 5.8 [Multi-Modal Convergence Systems](#58-multi-modal-convergence-systems)
6. [Open-Source Portable Hardware Ecosystem](#6-open-source-portable-hardware-ecosystem)
   - 6.1 [Philosophy and Mandate](#61-philosophy-and-mandate)
   - 6.2 [Molecular / Genomic Hardware Variants](#62-molecular--genomic-hardware-variants)
   - 6.3 [Structural Imaging Hardware Variants](#63-structural-imaging-hardware-variants)
   - 6.4 [Chemical / Metabolic Sensing Hardware Variants](#64-chemical--metabolic-sensing-hardware-variants)
   - 6.5 [Electrical / Bioelectric Sensing Hardware Variants](#65-electrical--bioelectric-sensing-hardware-variants)
   - 6.6 [Ingestible / Capsule Sensor Variants](#66-ingestible--capsule-sensor-variants)
   - 6.7 [Wearable Patch and Implant Variants](#67-wearable-patch-and-implant-variants)
   - 6.8 [Field / Environmental Sensing Variants](#68-field--environmental-sensing-variants)
7. [Full Hardware Specifications — All Devices](#7-full-hardware-specifications--all-devices)
   - 7.1 [NFSIM-PCR-01 — Portable Individual PCR Unit](#71-nfsim-pcr-01--portable-individual-pcr-unit)
   - 7.2 [NFSIM-PCR-02 — Micro Gel-Slip PCR Strip Reader](#72-nfsim-pcr-02--micro-gel-slip-pcr-strip-reader)
   - 7.3 [NFSIM-SEQ-01 — Open Nanopore Sequencer (Gel Membrane Variant)](#73-nfsim-seq-01--open-nanopore-sequencer-gel-membrane-variant)
   - 7.4 [NFSIM-SEQ-02 — Solid-State Nanopore Research Board](#74-nfsim-seq-02--solid-state-nanopore-research-board)
   - 7.5 [NFSIM-CRISPR-01 — Portable CRISPR Diagnostic Device](#75-nfsim-crispr-01--portable-crispr-diagnostic-device)
   - 7.6 [NFSIM-dPCR-01 — Portable Digital PCR (Droplet)](#76-nfsim-dpcr-01--portable-digital-pcr-droplet)
   - 7.7 [NFSIM-GELEC-01 — Portable Gel Electrophoresis System](#77-nfsim-gelec-01--portable-gel-electrophoresis-system)
   - 7.8 [NFSIM-US-01 — Portable Ultrasound Probe (USB-C)](#78-nfsim-us-01--portable-ultrasound-probe-usb-c)
   - 7.9 [NFSIM-US-02 — Wearable Ultrasound Patch Array](#79-nfsim-us-02--wearable-ultrasound-patch-array)
   - 7.10 [NFSIM-US-03 — Pill Capsule Ultrasound (Ingestible)](#710-nfsim-us-03--pill-capsule-ultrasound-ingestible)
   - 7.11 [NFSIM-MRI-01 — Low-Field Portable MRI (Permanent Magnet)](#711-nfsim-mri-01--low-field-portable-mri-permanent-magnet)
   - 7.12 [NFSIM-XRAY-01 — Low-Dose Portable X-Ray Panel](#712-nfsim-xray-01--low-dose-portable-x-ray-panel)
   - 7.13 [NFSIM-OCT-01 — Portable OCT Probe](#713-nfsim-oct-01--portable-oct-probe)
   - 7.14 [NFSIM-CGM-01 — Open CGM Sensor Platform](#714-nfsim-cgm-01--open-cgm-sensor-platform)
   - 7.15 [NFSIM-SWEAT-01 — Wearable Sweat Chemistry Patch](#715-nfsim-sweat-01--wearable-sweat-chemistry-patch)
   - 7.16 [NFSIM-CHEM-01 — Portable Blood Chemistry Analyzer](#716-nfsim-chem-01--portable-blood-chemistry-analyzer)
   - 7.17 [NFSIM-OXY-01 — Multi-Site Tissue Oxygenation Array](#717-nfsim-oxy-01--multi-site-tissue-oxygenation-array)
   - 7.18 [NFSIM-BREATH-01 — Portable Breath Metabolomics Device](#718-nfsim-breath-01--portable-breath-metabolomics-device)
   - 7.19 [NFSIM-ECG-01 — Open Single-Lead ECG Patch](#719-nfsim-ecg-01--open-single-lead-ecg-patch)
   - 7.20 [NFSIM-ECG-02 — 12-Lead Portable ECG Vest](#720-nfsim-ecg-02--12-lead-portable-ecg-vest)
   - 7.21 [NFSIM-EEG-01 — Dry-Electrode Open EEG Headset](#721-nfsim-eeg-01--dry-electrode-open-eeg-headset)
   - 7.22 [NFSIM-EMG-01 — Multi-Channel Surface EMG Armband](#722-nfsim-emg-01--multi-channel-surface-emg-armband)
   - 7.23 [NFSIM-NEURAL-01 — Open High-Density ECoG Research Array](#723-nfsim-neural-01--open-high-density-ecog-research-array)
   - 7.24 [NFSIM-CAP-01 — Capsule: Ingestible Imaging + Chemical Sensor](#724-nfsim-cap-01--capsule-ingestible-imaging--chemical-sensor)
   - 7.25 [NFSIM-CAP-02 — Capsule: GI Ultrasound Capsule](#725-nfsim-cap-02--capsule-gi-ultrasound-capsule)
   - 7.26 [NFSIM-CAP-03 — Capsule: DNA/RNA Capture Capsule](#726-nfsim-cap-03--capsule-dnarna-capture-capsule)
   - 7.27 [NFSIM-CAP-04 — Capsule: Full Multi-Modal Research Capsule](#727-nfsim-cap-04--capsule-full-multi-modal-research-capsule)
   - 7.28 [NFSIM-FLOW-01 — Portable Cytometry / Cell Counter](#728-nfsim-flow-01--portable-cytometry--cell-counter)
   - 7.29 [NFSIM-ENV-01 — Environmental Bio-Aerosol Sampler](#729-nfsim-env-01--environmental-bio-aerosol-sampler)
   - 7.30 [NFSIM-MICRO-01 — Portable Digital Microscope (Pathology)](#730-nfsim-micro-01--portable-digital-microscope-pathology)
8. [Communication Protocol Specification](#8-communication-protocol-specification)
9. [Firmware Architecture — Universal](#9-firmware-architecture--universal)
10. [Software Architecture](#10-software-architecture)
    - 10.1 [Desktop Application](#101-desktop-application)
    - 10.2 [Mobile Application](#102-mobile-application)
    - 10.3 [Web Dashboard](#103-web-dashboard)
    - 10.4 [SDK](#104-sdk)
    - 10.5 [AI/ML Layer](#105-aiml-layer)
11. [Monorepo Directory Structure — Complete](#11-monorepo-directory-structure--complete)
12. [Production & Manufacturing](#12-production--manufacturing)
13. [Legal, Compliance & Licensing](#13-legal-compliance--licensing)
14. [Roadmap](#14-roadmap)
15. [Contributing](#15-contributing)
16. [Acknowledgements](#16-acknowledgements)

---

---

# 1. Project Vision

NanoFlowSIM is a vertically integrated precision medicine ecosystem with three interlocking pillars:

**Pillar 1 — Simulation Platform**
A Rust-based computational framework that models nanoparticle behavior in biological systems at molecular, cellular, tissue, and whole-system levels. It is designed for oncology, gene therapy, rare disease research, and broad infectious disease modeling.

**Pillar 2 — Patient Data Architecture**
A personal health data aggregation platform that integrates data from every category of biological sensing — past, present, and future. Each data point anchors to a 3D anatomical model of the patient, enabling both consumer-facing health tracking and clinician-facing precision medicine workflows. Individuals own their data. Institutions may access it with consent.

**Pillar 3 — Open-Source Portable Hardware Ecosystem**
A full suite of open-source, open-hardware biological sensing devices spanning every domain of biological measurement: molecular, genomic, structural, chemical, electrical, implantable, and ingestible. Every device in this ecosystem is designed to be portable, affordable, reproducible, and NanoFlowSIM-native.

The unifying thesis:

> Biological data has historically been siloed, episodic, expensive, and inaccessible. NanoFlowSIM treats the entire history of biological sensing — from gel electrophoresis to nanopore sequencing to ingestible capsule sensors — as a single evolving stack, and builds open-source portable versions of every layer, feeding all data into a unified living 3D patient model.

---

# 2. NanoFlowSIM Software Platform

## 2.1 Key Features

### Multi-Layered Simulation Architecture

**Molecular Level**
- Simulates receptor-ligand interactions with thermodynamic binding affinity modeling
- CRISPR guide RNA targeting and off-target prediction
- Nanoparticle stability under physiological pH, temperature, and enzymatic environments
- Payload encapsulation integrity modeling
- Ligand density optimization algorithms

**Cellular Level**
- Endocytosis pathway modeling (clathrin-mediated, caveolae-mediated, macropinocytosis)
- Endosomal escape kinetics and membrane disruption modeling
- Intracellular trafficking and subcellular localization prediction
- Therapeutic payload release kinetics under intracellular conditions
- Cell viability and cytotoxicity prediction

**Tissue Level**
- Tissue permeability and heterogeneity modeling
- Enhanced Permeability and Retention (EPR) effect simulation
- Tumor microenvironment modeling including hypoxia, acidic pH zones, and immune cell densities
- Vascular extravasation prediction
- Lymphatic clearance modeling

**Whole-System Feedback**
- Patient-specific genetic and proteomic data integration
- Immune profile incorporation (checkpoint expression, T-cell densities, NK activity)
- Systemic pharmacokinetics and ADMET prediction
- Real-time clinical feedback loop for iterative refinement

### Back-Testing and Iterative Refinement
- Historical clinical trial data comparison
- Patient case study validation
- Automated nanoparticle design parameter adjustment
- Simulation confidence scoring

### Hybrid Therapy Modeling
- Chemotherapy + gene therapy co-delivery systems
- CRISPR + immunotherapy combinations
- Sequential and simultaneous payload release modeling
- Synergy scoring algorithms for therapy combination ranking

### Machine Learning-Driven Predictions
- Optimal therapeutic combination selection from historical + simulated data
- Ligand design generation from receptor profile inputs
- Adverse event probability prediction
- Patient stratification for trial matching

### Modular and Scalable Framework
- Plugin architecture for new therapeutic modalities
- Scalable from single patient to population-level simulations
- Standards-compliant data formats (FHIR, HL7, DICOM, VCF, FASTQ)

---

## 2.2 System Workflow

### Step 1: Data Collection

**Patient Data Acquisition**

| Data Type | Format | Source |
|---|---|---|
| Genomic mutations | VCF, FASTQ | Sequencing lab, personal sequencer |
| CRISPR target loci | BED, FASTA | Computational prediction + lab |
| Proteomic profiles | mzML, CSV | Mass spectrometry |
| MRI/CT imaging | DICOM | Hospital, portable imaging |
| Immune cell profiling | FCS (flow cytometry) | Lab panel, portable cytometer |
| Continuous biosensor | JSON stream | CGM, ECG, EEG, wearables |
| Microbiome | FASTQ | 16S/WGS sequencing |
| SNP panel | VCF | Array or sequencing |
| Liquid biopsy cfDNA | BAM, VCF | Sequencing |
| Metabolomics | mzML | Mass spec or portable breath |

**Tumor / Target Region Profiling**
- Tissue heterogeneity mapping from imaging data
- Receptor expression quantification per region
- Vascular density estimation from imaging
- Immune infiltrate density mapping
- Permeability coefficient estimation per tissue zone

### Step 2: Simulation Configuration

**Therapeutic Goal Selection**

| Mode | Therapies Available |
|---|---|
| Single Therapy | CRISPR, Chemotherapy, Immunotherapy, Gene Replacement, RNA Therapy |
| Combination Therapy | Any pairing or multi-agent combination of the above |
| Automated Selection | AI-ranked screening of all viable combinations given patient data |

**Nanoparticle Design Parameters**

| Parameter | Options |
|---|---|
| Size | 1–500 nm range |
| Shape | Spherical, Rod, Disc, Core-Shell, Liposomal, Polymeric |
| Surface Coating | PEG, Ligand type, Charge (positive/neutral/negative) |
| Ligand Type | Antibody, Aptamer, Peptide, Small molecule, CRISPR-RNP |
| Ligand Density | Molecules per nm² |
| Payload Type | siRNA, mRNA, CRISPR-Cas9, Chemotherapy drug, Cytokine |
| Payload Loading | % encapsulation efficiency |
| Release Mechanism | pH-triggered, Enzymatic, Thermal, Light-activated, Mechanical |

### Step 3: Simulation Execution

**Molecular Layer Execution**
- Monte Carlo ligand-receptor binding simulation
- Molecular dynamics for membrane interaction
- Payload stability testing across pH 4.5–7.4 and enzymatic environments

**Cellular Layer Execution**
- Agent-based cellular uptake simulation
- Endosomal pH map traversal
- Payload release timing relative to intracellular environment

**Systemic Layer Execution**
- Blood compartment pharmacokinetic modeling
- Mononuclear phagocyte system (MPS) clearance rates
- Complement activation probability
- Tissue perfusion modeling

**Therapy-Specific Metrics**

| Therapy | Key Metrics Computed |
|---|---|
| CRISPR | On-target editing efficiency (%), off-target sites identified, indel rate |
| Chemotherapy | Tumor drug AUC, healthy tissue AUC, therapeutic index |
| Immunotherapy | T-cell activation score, tumor immune infiltration delta |
| Gene Replacement | Transduction efficiency, expression duration |
| RNA (siRNA/mRNA) | Knockdown %, protein expression level |

### Step 4: Back-Testing and Validation

- Import clinical trial datasets (CSV, FHIR, custom JSON)
- Automated comparison of predicted vs. observed outcomes
- Root-cause analysis for prediction deviations
- Iterative parameter refinement via Bayesian optimization
- Confidence interval reporting per simulation output

### Step 5: Output Analysis

**Simulation Results**

| Output | Description |
|---|---|
| Targeting Efficiency | % nanoparticles reaching target site |
| Payload Release Profile | Release % over time with pharmacokinetic curve |
| Off-Target Distribution | Organ-level nanoparticle accumulation heatmap |
| Side Effect Profile | Predicted toxicity events with probability |
| Immune Response Curve | Predicted antibody titer, cytokine release |
| Editing Efficiency Map | CRISPR on/off-target efficiency per locus |

**Visualization Outputs**
- 3D molecular trajectory rendering (WebGL / Vulkan backend)
- Tissue heatmaps of targeting and therapeutic concentration
- Pharmacokinetic curves per compartment
- Animated nanoparticle flow through vasculature
- Off-target risk topology maps

---

## 2.3 Therapy Modeling

### Automated Therapy Combination Selection

The combination engine:
1. Enumerates all feasible therapy pairings from available modalities
2. Filters by patient contraindications (genomic, clinical)
3. Ranks combinations by predicted synergy score and safety margin
4. Selects top N combinations for detailed simulation
5. Reports confidence intervals and uncertainty estimates

### Combination Synergy Modeling

| Combination | Synergy Type | Modeled Interaction |
|---|---|---|
| Chemo + Immunotherapy | Immunogenic cell death enhancement | Calreticulin exposure, DAMP release |
| CRISPR + Chemo | Sensitivity gene editing | Resistance gene knockout before chemo |
| CRISPR + Immunotherapy | Neoantigen generation | Targeted mutation for immune recognition |
| RNA + Immunotherapy | Checkpoint modulation | PD-L1 siRNA knockdown + T-cell activation |

---

## 2.4 Expanded Clinical Applications

### Oncology
- Heterogeneous tumor treatment optimization
- Metastatic cancer multi-site targeting
- Drug resistance evolution modeling
- CAR-T cell delivery optimization

### HIV Treatment
- CRISPR-mediated HIV DNA excision from T-cell latent reservoirs
- Immune checkpoint modulation to reactivate latent reservoirs
- Antiretroviral nanoparticle delivery optimization
- CNS reservoir penetration modeling (blood-brain barrier crossing)

### Herpesvirus Infections (HSV-1, HSV-2, VZV, CMV, EBV)
- CRISPR payload delivery to neural ganglia
- Blood-brain barrier crossing nanoparticle design
- Antiviral combination delivery optimization
- Recurrence suppression protocol design

### Rare Genetic Diseases
- Single-gene therapy delivery simulation
- Tissue-specific targeting for organ-of-interest
- Off-target risk minimization for rare pediatric cases
- Patient-specific variant-to-therapy mapping

### Neurological Disorders (Parkinson's, Alzheimer's, MS)
- Blood-brain barrier (BBB) crossing nanoparticle optimization
- Neuron-targeted gene editing simulation
- Anti-neuroinflammatory delivery
- Alpha-synuclein / amyloid-beta clearance strategies

### Autoimmune Diseases
- Regulatory T-cell targeted immunomodulation
- Localized immunosuppression nanoparticle design
- CRISPR immune tolerance restoration

### Cardiovascular Diseases
- Arterial plaque-targeting nanoparticle design
- Cardiomyocyte gene therapy delivery post-MI
- Growth factor delivery for tissue regeneration
- Clot-targeting thrombolytic delivery

### Antimicrobial Resistance (AMR)
- CRISPR-based bacteriophage resistance disruption
- Antibiotic + nanoparticle synergy optimization
- Biofilm penetration modeling

### Broad Infectious Diseases
- SARS-CoV-2 and respiratory virus nanoparticle antivirals
- Malaria parasite-stage-specific targeting
- Fungal biofilm penetration modeling
- Tuberculosis macrophage-targeted delivery

---

# 3. Data Integration Architecture — The Full Loop

NanoFlowSIM is not a snapshot system. It is a **living biological data architecture** that aggregates, anchors, and interprets data from every category of biological sensing — past scans, present wearables, future continuous molecular monitors — and maps all of it to a patient's 3D model.

## 3.1 Non-Continuous Data Sources

These are episodic or one-time data inputs. They are stored as timestamped events anchored to the 3D anatomical region where they were collected.

| Data Category | Specific Type | Format | Frequency |
|---|---|---|---|
| Genomic | SNP array | VCF | Once / annually |
| Genomic | Whole genome sequence | FASTQ, BAM | Once / rarely |
| Genomic | Exome sequence | FASTQ, BAM | Occasionally |
| Genomic | RNA-seq | FASTQ | Per study |
| Genomic | Liquid biopsy cfDNA | BAM, VCF | Per clinical visit |
| Imaging | MRI (brain, body, joint) | DICOM | Per clinical need |
| Imaging | CT scan | DICOM | Per clinical need |
| Imaging | X-ray | DICOM | Per clinical need |
| Imaging | PET scan | DICOM | Per clinical need |
| Imaging | Ultrasound image | DICOM | Per clinical need |
| Pathology | Tissue biopsy | Slide image (SVS) | Per clinical need |
| Blood labs | CBC, CMP, lipid panel | FHIR/HL7, CSV | Per visit |
| Blood labs | Hormone panels | FHIR/HL7, CSV | Per visit |
| Blood labs | Tumor markers | FHIR/HL7, CSV | Per visit |
| Blood labs | Inflammatory markers (CRP, IL-6) | FHIR/HL7, CSV | Per visit |
| Microbiology | Blood culture | Text/FHIR | Per infection |
| Microbiology | Gut microbiome 16S | FASTQ | Occasionally |
| Immune profiling | Flow cytometry panel | FCS | Per clinical need |
| Proteomics | Mass spec protein panel | mzML | Per study |
| Metabolomics | Plasma metabolomics | mzML, CSV | Per study |
| Medical history | Diagnoses, procedures | FHIR | Continuous import |
| Medications | Drug list | FHIR | Continuous import |
| Family history | Pedigree + variants | PED, JSON | Once |

## 3.2 Continuous Data Sources (Current)

These are live-streaming or near-continuous data feeds from wearable and monitoring devices.

| Device Type | Measurand | Update Rate | Protocol |
|---|---|---|---|
| CGM (Continuous Glucose Monitor) | Interstitial glucose | 1–5 min | BLE, NFC |
| ECG patch | Heart rhythm | Real-time | BLE |
| Smartwatch (optical HR) | Heart rate, SpO2, HRV | Continuous | BLE |
| EEG headset | Brain electrical activity | Real-time | BLE |
| Blood pressure cuff (24h) | Systolic/diastolic | 15–30 min | BLE |
| Pulse oximeter | SpO2 | Real-time | BLE |
| Temperature patch | Core/skin temperature | 1 min | BLE |
| Accelerometer/IMU | Motion, posture, steps | Real-time | BLE |
| Sleep tracker | Sleep staging | Nightly | BLE |
| Sweat sensor patch | Lactate, electrolytes | 10–30 min | BLE, NFC |
| Capnometer | EtCO2 | Real-time | BLE |
| Spirometer | FEV1, FVC | Per session | BLE, USB |
| EMG armband | Muscle activation | Real-time | BLE |
| Intraocular pressure | IOP | Continuous (implant) | Inductive |
| Implantable CGM | Glucose (subcutaneous) | 1 min | NFC, BLE |
| Cardiac implant (pacemaker/ICD telemetry) | Rhythm, events | Real-time | Proprietary/BLE |

## 3.3 Future Continuous Systems

These are emerging or experimental technologies expected to enter clinical and consumer use within the next 5–15 years. NanoFlowSIM's data architecture is pre-built to receive them.

| Future System | Measurand | Status |
|---|---|---|
| Continuous liquid biopsy monitor | cfDNA fragments, tumor DNA | Experimental |
| Continuous proteomics patch | Cytokines, hormones | Research stage |
| Implantable metabolomics sensor | Metabolite panel | Research stage |
| Continuous nanopore sequencer | Pathogen DNA/RNA, cell-free DNA | Early research |
| Ingestible continuous capsule | GI chemistry, microbiome, images | Emerging |
| Wearable mass spectrometry | Skin volatiles, breath | Research |
| Neural implant data stream | Neural spike trains, LFP | Clinical trials (BCIs) |
| Epigenetic methylation monitor | DNA methylation | Experimental |
| Continuous cortisol sensor | Cortisol (stress) | Late research |
| Microfluidic blood panel | CBC, chemistry in real time | Research |

## 3.4 Patient Data Aggregation Model

### Ownership and Consent
- All data belongs to the individual
- Institutional access requires explicit per-study consent
- Data export in standard formats (FHIR, VCF, JSON, CSV) at any time
- Anonymization layer for research data contribution

### Hospital Records Import
- Patient requests records from institution
- FHIR R4 / HL7 v2 compliant import
- DICOM import with automatic segmentation and 3D anchoring
- Historical lab results ingested with date-stamped anchoring to body region

### Data Anchoring to 3D Body Model
Every data point — whether a blood test, a genomic variant, an ECG reading, or an imaging scan — is tagged with:
- Anatomical region (body part ontology: UBERON / FMA)
- Tissue type (if applicable)
- Collection method
- Timestamp
- Data quality / confidence score

This enables region-specific queries such as:
- "Show all data collected about the right lung over the past 2 years"
- "What is the genomic landscape of my liver?"
- "Display all inflammatory markers correlated with cardiac events"

### Storage System
- Patient data stored encrypted at rest (AES-256)
- Each data layer stored in domain-specific schema with shared patient ID
- Local-first option: all data can reside on personal device with optional cloud sync
- Federated model: research institutions can query aggregate patterns without accessing individual identifiers

---

# 4. UI/UX Specification — Consumer and Professional

## 4.1 Design Philosophy

NanoFlowSIM's interface operates on a single core principle: **the 3D human body is the universal data anchor**. Every piece of biological information — a blood test, a gene variant, a biosensor reading, a simulation result — must be accessible by interacting with the body region it relates to.

The interface has two modes that share the same underlying 3D model but differ in information density and interaction depth:

- **Consumer Mode** — designed for individuals managing their own health. Clear, accessible, non-overwhelming. Surfaces actionable insights. Hides technical noise.
- **Professional/Clinical Mode** — designed for researchers, oncologists, genetic counselors, and bioengineers. Exposes raw data, statistical overlays, simulation parameters, and full API access.

Both modes transition smoothly. A consumer user can grant their physician Professional Mode access to their exact same data layer.

---

## 4.2 3D Body Map System

### Generic Body (Default State)
When a patient profile is not yet fully mapped — or for a new user with minimal data — the system displays a **high-quality generic 3D anatomical human**:

- Anatomically accurate surface mesh
- Internal organ visibility (toggle layers: skin → muscle → organ → skeletal → vascular → neural)
- Gender-neutral default; options for male/female/intersex anatomical variants
- Pediatric, adolescent, adult, and geriatric body variants
- Body size/BMI slider for approximate morphological match

The generic body is not a placeholder — it is a fully interactive data-entry surface. A user can click any region even with zero data and see:
- "No data collected for this region yet"
- "Add data" prompt
- Suggested sensor/test for this region

### Patient-Specific Body (Mapped State)
When patient-specific data exists, the generic model progressively transforms:

**Level 1 — Anthropometric Match**
Patient height, weight, and BMI adjust the body mesh proportionally.

**Level 2 — Imaging-Derived Geometry**
When DICOM data (MRI, CT) is imported:
- Automated segmentation extracts organ boundaries
- Patient-specific organ shapes replace generic anatomy
- Tumor locations, lesions, and structural anomalies appear in situ
- Vascular anatomy reconstructed from contrast imaging

**Level 3 — Functional Overlay**
When continuous sensor data is active:
- Organs/regions glow or animate to indicate live data streams
- Color-coded overlays for oxygenation, metabolic activity, electrical activity
- Pulsing animations for cardiac and vascular regions during ECG/PPG feeds

**Level 4 — Molecular Overlay**
When genomic and simulation data is integrated:
- Variant hotspots displayed as localized markers per gene's tissue expression
- Simulated nanoparticle trajectories rendered as particle flows
- Receptor expression heatmaps overlay tissue surfaces

### Camera and Navigation
- Orbit, pan, zoom, and slice navigation
- Pre-set anatomical views (anterior, posterior, lateral, sagittal, coronal, axial)
- Free cross-section slice tool — drag a plane through any axis to reveal interior
- Cinematic fly-through mode for presentations
- AR mode (mobile) — overlay patient body map on camera view

---

## 4.3 Consumer View

### Dashboard (Home Screen)
The consumer home screen prioritizes clarity and action. It shows:

**Body Map Panel (center/left, 60% of screen)**
- 3D body map (generic or patient-specific)
- Active sensor indicators — pulsing icons over active device regions
- Summary overlays: green/yellow/red per region based on latest data

**Live Feed Panel (right)**
- Current readings from active continuous sensors
- Sparkline history for last 24h per metric
- Alert badges for out-of-range values

**Today's Summary (bottom)**
- Key insights: "Your glucose has been stable today. Heart rate variability is within normal range."
- Pending actions: "Add yesterday's blood test results"
- AI health brief: weekly pattern summary

### Body Region Detail (Click on Region)
Clicking any body region opens the **Region Detail Panel**:

```
[ Region Name: Right Lung ]
[ Last Updated: 2 hours ago — Live: Pulse Oximetry ]

LIVE DATA
  SpO2: 98.2%  ↑ Stable
  Respiratory Rate: 14 bpm

HISTORICAL DATA (Timeline scrubber)
  2024-03-01: CT Scan — [View 3D] [View DICOM]
  2023-11-15: Spirometry — FEV1: 3.2L (94% predicted)
  2023-08-01: Blood gas panel — PaO2: 95 mmHg

GENOMIC DATA
  CFTR gene — No pathogenic variants detected
  SFTPC — Variant of uncertain significance (rs#######)

SIMULATION DATA (if applicable)
  Nanoparticle delivery sim — 2024-01-10
  [View Results] [Re-run] [Modify Parameters]

[ + Add Data ] [ Request Lab ] [ Share with Doctor ]
```

### Timeline View
A full chronological timeline of all data collected, filterable by:
- Region
- Data type (imaging, lab, genomic, continuous)
- Date range
- Sensor source

### Notification System
- Glucose out of range alert
- Unusual ECG pattern detected
- Medication adherence reminder
- New simulation result available
- New data from connected hospital records

---

## 4.4 Professional/Clinical View

The professional view adds:

### Patient Panel
- Full demographics
- Active diagnoses (ICD-10 coded)
- Medication list with dosing
- Allergy and contraindication flags
- Active clinical trials eligibility

### Advanced Data Overlay Controls
- Toggle individual data layers on/off
- Adjust visualization scales (log vs. linear)
- Select timeframe for aggregation
- Layer statistical confidence intervals on all continuous readings

### Genomic Analysis Panel
- Full variant browser (filter by pathogenicity, gene, chromosome)
- Polygenic risk score display
- Copy number variation (CNV) viewer
- Pharmacogenomics panel (drug-gene interactions)
- CRISPR target candidate sites per region

### Simulation Control Panel
- Full NanoFlowSIM simulation launcher
- Parameter editor for nanoparticle properties
- Therapy combination selector
- Back-testing data import and comparison
- Result export (PDF report, JSON, CSV)

### Multi-Patient Research View
- De-identified population overlay on shared anatomy
- Variant frequency maps across cohort
- Therapy outcome comparison by patient cluster
- Trial enrollment tracking

### API Access Panel
- Live API key management
- Webhook configuration for data push
- FHIR export endpoint
- Simulation API documentation

---

## 4.5 Data Capture Workflow

### Capturing Data That Doesn't Have a Perfect 3D Region

Some lab values — such as serum sodium, blood glucose, or systemic inflammatory markers — technically relate to the whole body or bloodstream. The system handles this with:

**Option A — Systemic Tag**
Data is tagged to "Systemic / Bloodstream" — a special non-regional category shown as a circulatory overlay on the entire body.

**Option B — Primary Expression Region**
AI suggests the most relevant anatomical anchor:
- Serum glucose → Pancreas + Liver
- Creatinine → Kidneys
- Troponin → Heart
- ALT/AST → Liver
- PSA → Prostate

The user can accept or override the suggestion. Both the systemic tag and the regional anchor are stored.

**Every lab value, imaging study, and genomic result is mappable to at least one region.** The system will never leave data unanchored — even if the anchor is "Systemic."

### Adding Data Manually
1. Tap/click **+ Add Data** anywhere
2. Select data type from categorized list
3. Input values OR upload file (PDF report, DICOM, FASTQ, CSV)
4. System auto-detects format and extracts structured data
5. System suggests anatomical anchor(s)
6. User confirms or adjusts
7. Data appears in region timeline immediately

### Hospital Records Import
1. User selects "Import Medical Records"
2. Enter institution name → system checks FHIR R4 endpoint compatibility
3. OAuth2 patient authorization flow with institution's patient portal
4. Records downloaded and ingested automatically
5. AI categorizes, dates, and anchors all records to body regions
6. Conflicts or duplicates flagged for user review

---

## 4.6 Live vs. Historical Mode

The body map is always in one of two display states:

### Live Mode (Active Sensors)
- Triggered automatically when any connected sensor is streaming data
- Active regions pulse or glow based on data type:
  - **Cardiac region**: rhythmic pulse animation synced to detected heart rate
  - **Glucose region (pancreas/bloodstream)**: color gradient shifting with glucose trend
  - **Brain region**: subtle oscillation representing EEG band activity
  - **Respiratory region**: expansion/contraction animation
- Data values overlay directly on the 3D model in real time
- Sensor connection status icons float near device attachment point on body

### Historical Mode (No Active Sensors)
- Timeline scrubber appears at bottom of body map
- Drag to any date/time to see body state at that moment
- Regions that had data at that time light up
- Regions with no data at that time are dim/greyed
- Animated replay mode: watch body state evolve forward through time

### Transition
- Live mode and historical mode are never exclusive — user can scrub backward in time while a sensor is still streaming, then return to live

---

## 4.7 Regional Data Interaction

Each region supports two access patterns:

**Surface Interaction (Outer Anatomy)**
- Click any visible surface region
- Returns data anchored to that surface: skin sensor data, patch readings, external examination findings, radiation dosimetry from imaging

**Depth Interaction (Inner Anatomy)**
- Slice plane tool exposes interior
- Click any internal organ or structure
- Returns all data anchored to that structure: imaging findings, biopsy results, implant data, simulated nanoparticle trajectories, genomic expression data

**Cross-Layer Correlation**
- Select two regions and invoke "Correlate"
- System runs statistical correlation across all shared data types and timeframes
- Surfaces significant correlations (e.g., liver enzyme elevation correlating temporally with elevated inflammatory markers in bloodstream)

---

# 5. Biological Sensing Domains — Complete Evolutionary Study

This section documents the complete engineering evolution of every biological sensing domain. This study directly informs the design of NanoFlowSIM's portable hardware ecosystem: we identify where each technology is today, what made it expensive/large, what miniaturization pathway opened it up, and where the portable open-source variant sits.

---

## 5.1 Molecular / Genomic Sensing

### Domain Definition
Molecular sensing reads the **information content** of biology: DNA sequences, RNA expression, protein identity, pathogen genomes, genetic variants, epigenetic marks, and direct molecular identity.

### Phase 0 — Pre-Molecular Era (Pre-1950s)
Medicine observed symptoms, tissue damage, and cellular morphology. The information layer of biology (the genome, the proteome) was entirely invisible. Disease was classified by observation and autopsy alone.

### Phase 1 — Gel Electrophoresis (1950s–1970s)

**Core Physics**: DNA is negatively charged. Under electric current, DNA migrates through a gel matrix. Smaller fragments travel faster than larger ones, producing size-based separation.

**Original Hardware Stack**:
| Component | Function |
|---|---|
| Agarose gel matrix | Molecular sieve |
| Buffer solution (TAE or TBE) | Ion-conducting medium |
| Platinum/carbon electrodes | Apply electric field |
| DC power supply | Drive 80–120V gradient |
| UV transilluminator | Excite ethidium bromide / SYBR |
| Casting tray + comb | Form gel wells |
| Staining bath | Intercalating dye application |

**Signal Chain**:
`DNA fragments → Electric migration → Size-based separation → Fluorescent staining → UV excitation → Band visualization → Photograph/digital capture`

**Constraints**: Manual, slow, requires UV safety equipment, semi-quantitative, no sequence information.

**Miniaturization Path**: Microfluidic chip-based electrophoresis (Bioanalyzer, Agilent TapeStation) reduced full gel runs to chip-scale capillary systems. Modern: disposable polymer gel strips loadable in handheld readers.

### Phase 2 — PCR Revolution (1983)
**Core Biochemistry**: Polymerase chain reaction exponentially copies a target DNA sequence using thermocycling.

Three cycle stages:
1. **Denaturation** ~95°C — strands separate
2. **Annealing** ~50–65°C — primers bind
3. **Extension** ~72°C — polymerase copies

**Original Hardware Stack**:
| Component | Function |
|---|---|
| Aluminum thermal block | Holds PCR tubes, conducts heat |
| Resistive heating elements | Rapid temperature rise |
| Peltier thermoelectric module | Active cooling |
| Thermistor/thermocouple | Temperature feedback |
| PID controller | Cycling precision |
| MOSFET/relay drivers | Power switching |
| Microcontroller | Cycle programming |
| Power supply (120–240V) | High current for heaters |

**Constraints**: Bulky thermal mass, slow cycling, large sample volumes (50–100 µL), high power draw (200–800W).

**qPCR Additions**:
| Added Component | Purpose |
|---|---|
| LED array (470 nm, 520 nm) | Excite fluorescent dyes |
| Optical bandpass filters | Wavelength isolation |
| Photodiode / CMOS sensor | Fluorescence detection |
| Real-time DSP | Amplification curve analysis |
| Threshold crossing logic | Ct value determination |

**Digital PCR Addition**: DNA partitioned into 10,000–1,000,000 droplets/wells. Each compartment is either positive (target present) or negative. Absolute quantification without standard curve.

**Miniaturization Path**:
- Better Peltier efficiency → faster cycling
- MEMS thin-film heaters → microscale chambers
- Microfluidics → 2–10 µL reactions
- Battery-compatible power budgets → field portability
- Integrated optical → no external transilluminator needed

### Phase 3 — Sanger Sequencing (1977)
**Core Principle**: Chain-terminating dideoxynucleotides (ddNTPs) randomly stop DNA synthesis. Fragments of different lengths, each terminated at a specific base, are separated and read.

**Hardware Stack**:
| Component | Function |
|---|---|
| Capillary array (50 cm glass) | Electrophoretic separation |
| Laser (488 nm argon ion) | Excite fluorescent dye-terminators |
| CCD/PMT optical detector | Emission detection |
| Fluorescent dye-labeled ddNTPs | Mark each base type |
| Polymer loading robot | Fill capillaries |
| Thermal oven | Denaturation |
| High-voltage power supply (15 kV) | Drive migration |
| Data acquisition PC | Trace capture |

**Read Length**: 700–1000 bp
**Throughput**: ~96 samples/run
**Constraints**: Requires elaborate optical system, expensive consumables, 3–6 hour runs per plate.

### Phase 4 — Next Generation Sequencing (2005–present)
**Core Shift**: Massively parallel sequencing — millions of fragments simultaneously.

**Illumina (Sequencing by Synthesis)**:
| Component | Function |
|---|---|
| Flow cell (glass slide with clusters) | DNA attachment and clustering |
| Fluidics system (pumps, valves) | Reagent delivery |
| Laser lines (4 wavelengths) | Fluorescence excitation |
| Scientific CMOS camera | Image entire flow cell |
| Temperature control plate | Reaction temperature |
| GPU compute cluster | Image analysis, basecalling |
| Data storage (100+ TB) | Per run output |

**Constraints**: Requires vibration isolation, precise optics, fluidic robotics, and massive compute. Machine size: refrigerator to room-scale.

### Phase 5 — Third Generation: Oxford Nanopore (2014–present)
**Core Breakthrough**: No optical system. DNA detected electrically through protein nanopores.

**Physics**: α-hemolysin protein nanopore (1 nm diameter) embedded in artificial membrane. Voltage applied. Ionic current flows. As DNA bases transit the pore, they differentially block current. Four bases → four distinct current signatures.

**MinION Hardware Stack**:
| Component | Function |
|---|---|
| Flow cell membrane | Artificial lipid bilayer support |
| α-hemolysin nanopores | Sensing elements (~512 per flow cell) |
| Motor proteins (helicase) | Ratchet DNA at controlled speed (~400 bp/s) |
| Analog front-end ASIC | Measure picoamp (pA) current per pore |
| ADC (12–16 bit, 3–5 kHz) | Digitize current trace |
| FPGA | Real-time signal processing, multiplexing |
| USB 3.0 controller | Stream data to host at ~300 MB/s |
| Host basecaller (GPU) | Neural network converts signal to bases |

**Read Length**: Theoretically unlimited (megabase reads demonstrated)
**Accuracy**: ~99%+ with R10.4.1 pores + duplex basecalling
**Constraints**: Flow cell cost (~$500–900), pore degradation, signal noise, bioinformatics complexity.

**What MinION Opened**: Sequencing in jungles, ships, field hospitals, Antarctica, ISS. USB-powered, laptop-compatible.

**What Remains Proprietary**: Flow cell chemistry, nanopore protein engineering, ASIC design, motor protein sourcing.

### Phase 6 — CRISPR Diagnostics (2016–present)
CRISPR proteins (Cas12, Cas13) can be reprogrammed to detect specific DNA/RNA sequences. Upon target binding, a "collateral cleavage" activity activates, cutting reporter molecules.

**Detection Methods**:
- Fluorescent reporter cleavage (SHERLOCK, DETECTR) → optical readout
- Lateral flow strip → visual line (like pregnancy test)
- Electrochemical detection → electrode current change

**Significance for portability**: CRISPR diagnostics require no thermal cycling and can run at room temperature with minimal equipment. The detection is isothermal.

### Phase 7 — Continuous Molecular Monitoring (Emerging)
**Target analytes for continuous monitoring**:
- Cell-free DNA (cfDNA) fragments → cancer, organ damage, infection signatures
- Circulating tumor DNA (ctDNA) → real-time tumor evolution
- Pathogen RNA → infection progression
- Cell-free RNA → gene expression dynamics

**Technologies under development**:
- Continuous nanopore flow cells with microfluidic blood sampling
- Aptamer-based electrochemical sensors for specific molecular targets
- Nanotube-based molecular sensors
- Implantable electrochemical biosensors

---

## 5.2 Structural / Anatomical Imaging

### Domain Definition
Structural imaging answers: **What physically exists inside the body?** Shape, density, geometry, tissue organization, pathological mass, organ dimensions.

### Phase 0 — Pre-Imaging Medicine (Pre-1895)
Internal anatomy visible only through surgery or autopsy. Diagnosis from external symptoms, palpation, percussion, auscultation.

### Phase 1 — X-Ray (1895)
**Core Physics**: X-rays are ionizing electromagnetic radiation (0.01–10 nm wavelength). Tissues attenuate X-rays proportionally to their density and atomic number.

| Tissue | Attenuation | Appearance |
|---|---|---|
| Air/gas | Minimal | Black |
| Fat | Low | Dark grey |
| Soft tissue | Moderate | Grey |
| Bone | High | Light grey/white |
| Metal/contrast | Very high | Bright white |

**Hardware Stack**:
| Component | Function |
|---|---|
| X-ray tube (cathode-anode) | Bremsstrahlung X-ray generation |
| High voltage generator (40–150 kV) | Accelerate electrons |
| Tungsten anode target | X-ray production |
| Beam collimator | Shape and limit beam |
| Anti-scatter grid | Reject scattered X-rays |
| Flat panel detector (amorphous silicon + CsI scintillator) | Capture transmission image |
| A/D converter | Digitize detector output |
| Workstation | Image display |

**Miniaturization Path**: Battery-powered portable X-ray generators (4–8 kg) with wireless flat panel detectors (~1.5 kg). Used in field medicine, ICUs, veterinary mobile units.

### Phase 2 — Fluoroscopy
Continuous X-ray imaging for real-time motion visualization. Modern flat-panel fluoroscopy systems use pulsed X-ray to reduce dose. Image intensifiers largely replaced by direct flat-panel detectors.

### Phase 3 — Computed Tomography (CT) (1972)
**Core Physics**: Same X-ray attenuation but acquired from multiple angles (180–360°) around the patient. Filtered back-projection or iterative reconstruction computes 3D volumetric density map.

**Gantry Hardware**:
| Component | Function |
|---|---|
| Rotating X-ray tube | Multiple projection angles |
| Multi-row detector arrays (64–320 rows) | Parallel slice acquisition |
| Slip ring assembly | Continuous rotation without cable wrap |
| High-speed gantry motor | 0.2–0.5 second rotation |
| High voltage generator (80–140 kV, 100–800 mA) | High power X-ray |
| DAS (data acquisition system) | 100+ MB/s data from detectors |
| GPU reconstruction cluster | Filtered back projection / AI recon |
| Patient table with sub-mm positioning | Isocenter placement |

**Modern additions**: AI-based iterative reconstruction (reduces dose 60–80%), dual-energy CT (two voltage acquisitions for material decomposition), spectral CT.

**Portable CT**: Emerging mobile CT systems on wheeled gantries (NeuroLogica, Samsung). Lower kVp/mA. AI reconstruction compensates. Brain, extremity, and point-of-care CT now practical.

### Phase 4 — MRI (1973–present)
**Core Physics**: Nuclear magnetic resonance of hydrogen protons. Strong external field aligns proton magnetic moments. RF pulse at Larmor frequency tips alignment. Protons relax and emit RF signals. Gradient coils spatially encode signal origin.

**Hardware Stack**:
| Component | Function |
|---|---|
| Superconducting magnet (1.5T–7T) | Primary static field |
| Cryostat + liquid helium (4K) | Superconductor cooling |
| Gradient coils (X,Y,Z) | Spatial encoding |
| RF transmit coil (body coil) | Excitation pulses |
| RF receive coil array | Signal detection |
| Gradient amplifiers (1000A+) | Drive gradient coils |
| RF amplifier (15–30 kW) | Transmit power |
| Shim coils | Field homogeneity correction |
| RF shield room | Block external RF interference |
| Helium compressor | Cryocooler |
| Reconstruction computer | K-space Fourier transform |

**Constraints**: Superconducting magnet requires cryogenics, weighs 5–15 tonnes, requires shielded room. $1–5M installed cost.

**Miniaturization Path**:
- Low-field permanent magnets (0.02T–0.3T) eliminate cryogenics
- AI reconstruction compensates for lower SNR at low field
- Hyperfine Swoop (64 mT) — portable, battery-operable, non-shielded room
- Point-of-care brain MRI now demonstrated in ICU, ambulance

**fMRI**: Adds BOLD (Blood Oxygen Level Dependent) contrast. Detects neural activity indirectly via oxygenated hemoglobin concentration changes.

**Diffusion MRI**: Measures water diffusion directionality. Maps white matter tracts (tractography).

### Phase 5 — Ultrasound (1940s–present)
**Core Physics**: Piezoelectric crystals convert electrical signals to ultrasonic pressure waves (1–20 MHz). Sound reflects at tissue interfaces (acoustic impedance mismatch). Return echoes detected by same piezoelectric elements. Time-of-flight × speed of sound = depth.

**Transducer Types**:
| Type | Frequency | Application |
|---|---|---|
| Linear array | 5–15 MHz | Superficial structures, vascular |
| Curved array | 2–5 MHz | Abdominal |
| Phased array | 1–5 MHz | Cardiac (echocardiography) |
| Endocavitary | 5–10 MHz | Transvaginal, transrectal |
| Intravascular (IVUS) | 20–40 MHz | Coronary artery wall |
| High-frequency | 15–50 MHz | Skin, eye, small parts |

**Hardware Stack**:
| Component | Function |
|---|---|
| Piezoelectric array (PZT or CMUT) | Transmit/receive ultrasound |
| Transmit beamformer | Phase delays for beam steering |
| High-voltage pulser (50–100V) | Drive transducer |
| T/R switch | Protect receiver during transmit |
| Low-noise amplifier (LNA) | Receive signal |
| Time-gain compensation (TGC) | Depth-normalized amplification |
| Receive beamformer | Coherent addition of array elements |
| Envelope detection + log compression | Image formation |
| Scan converter | Polar to rectangular |
| Display | Real-time imaging |

**Doppler Mode**: Detects frequency shift of reflected sound from moving blood. Color Doppler maps flow direction and velocity.

**Miniaturization Path**:
- Digital beamforming on ASIC → eliminates analog beamformer
- CMUT (Capacitive Micromachined Ultrasonic Transducers) → semiconductor-fabricated transducer arrays
- SOC integration → single-chip ultrasound
- Result: Butterfly iQ (USB probe), Philips Lumify — smartphone-connected ultrasound probes

**Extreme miniaturization**: Capsule ultrasound (NFSIM-US-03) — described in hardware section. Intravascular ultrasound (IVUS) catheters 1–2 mm diameter.

### Phase 6 — Optical Structural Imaging
**OCT (Optical Coherence Tomography)**: Near-infrared interferometry. Micron-scale resolution to 1–2 mm depth. Dominant in ophthalmology (retinal imaging), cardiology (IVOCT), dermatology.

**Hardware Stack**:
| Component | Function |
|---|---|
| Near-IR light source (840–1300 nm) | Coherence gate illumination |
| Beam splitter | Reference + sample arm |
| Galvo mirror scanner | 2D scan |
| Spectrometer/swept source | Interferometric detection |
| High-speed ADC | Fringe capture |
| GPU | A-scan processing, volume rendering |

**Miniaturized OCT**: Fiber-optic probe OCT — catheter-delivered for coronary, GI endoscopic use.

**Endoscopy**: Direct optical visualization of luminal structures. White-light, NBI (narrow band), fluorescence, and AI-augmented endoscopy.

---

## 5.3 Chemical / Metabolic Sensing

### Domain Definition
Chemical sensing asks: **What is the body chemically doing right now?** Dissolved gases, metabolites, electrolytes, hormones, drugs, inflammatory markers — the ongoing chemistry of physiology.

### Phase 0 — Pre-Electronic Chemistry (1800s)
Visual colorimetric tests, titration, flame tests. Urine glucose by copper reduction (Benedict's test). Manual, slow, subjective.

### Phase 1 — Electrochemical Biosensors (1950s)
**Core Physics**: Chemistry generates or consumes electrons. Electrodes measure:
- **Potentiometry**: voltage from ion concentration
- **Amperometry**: current from redox reaction
- **Conductometry**: solution conductivity

**Ion-selective electrodes (ISE)**:
| Ion | Membrane Material |
|---|---|
| H⁺ (pH) | Glass membrane |
| Na⁺ | Sodium ionophore |
| K⁺ | Valinomycin |
| Cl⁻ | AgCl membrane |
| Ca²⁺ | Calcium ionophore |

**Signal Chain**: Ion concentration → Membrane potential → Nernst equation → Ion activity

### Phase 2 — Blood Chemistry Analyzers (1960s–present)
Automated multi-analyte analyzers (Beckman Coulter, Abbott, Roche). Internal fluidics routes sample to multiple sensing chambers. Combines ISE, spectrophotometry, enzyme reactions.

**Hardware Modules**:
| Module | Analytes |
|---|---|
| ISE module | Na, K, Cl, CO2, Li |
| Spectrophotometer | Glucose, creatinine, BUN, bilirubin |
| Immunoassay | Troponin, HbA1c, TSH, hCG |
| Cell counter | CBC |
| Hemolysis detector | Sample quality |

**Constraints**: Large footprint, expensive reagents, requires trained operator, 15–60 min turnaround.

**Miniaturization Path**:
- Lab-on-chip integration
- Microfluidic reagent cartridges (i-STAT — Abbott)
- Dry chemistry strips
- Result: i-STAT — credit-card-sized cartridge, handheld reader, 2-min blood chemistry panel at bedside

### Phase 3 — Glucose Sensing (1970s–present)
**Enzymatic Electrochemistry**:
`Glucose + O₂ + H₂O → Gluconic acid + H₂O₂` (glucose oxidase reaction)
`H₂O₂ → 2H⁺ + O₂ + 2e⁻` (electrode oxidation)

Current proportional to glucose concentration.

**First-Generation Meters** (1970s): Reflectance photometry on enzyme strip.
**Second-Generation Meters** (1980s+): Electrochemical strips with mediator (ferricyanide, ferrocene).
**Third-Generation** (enzymatic wired, no O₂ dependence).
**Fourth-Generation CGM**: Subcutaneous enzymatic wire, continuous amperometric, wireless BLE.

**CGM Hardware Stack**:
| Component | Specification |
|---|---|
| Sensing filament | 25–400 µm diameter, 5–10 mm length, platinum/carbon working electrode |
| Enzyme layer | Glucose oxidase crosslinked in biocompatible polymer |
| Interference rejection layer | Cellulose acetate membrane, blocks ascorbate, acetaminophen |
| Reference electrode | Ag/AgCl on filament |
| Analog front end | 3-electrode potentiostat, nA-range current |
| ADC | 16-bit, 1 Hz sampling |
| MCU | Ultra-low-power (nRF52840 or similar) |
| NFC/BLE radio | 2.4 GHz |
| Battery | 100–200 mAh coin cell |
| Encapsulation | Medical-grade silicone, waterproof |
| Adhesive | Acrylate skin adhesive, 7–14 day wear |

**Sensor lifetime**: 7–15 days (enzymatic degradation limits)
**Calibration**: Factory-calibrated or finger-stick calibration per 12h

### Phase 4 — Pulse Oximetry (1972–present)
**Physics**: Beer-Lambert law. Oxygenated (HbO2) and deoxygenated (Hb) hemoglobin have different absorption spectra. HbO2 absorbs more IR, less red. Hb absorbs more red, less IR. Ratio of modulated AC component (pulsatile) to DC component isolates arterial signal from tissue background.

**Hardware Stack**:
| Component | Specification |
|---|---|
| Red LED | 660 nm |
| Infrared LED | 940 nm |
| Photodiode | Broadband Si detector |
| Transimpedance amplifier | Convert photodiode current to voltage |
| Bandpass filter | Isolate cardiac pulse |
| ADC | Digitize both wavelengths |
| Ratio computation | R = (AC660/DC660) / (AC940/DC940) |
| SpO2 lookup table | Empirically calibrated |

**Modern extensions**: 4+ wavelength reflectance oximetry (forehead, wrist). Masimo Rainbow — 8 wavelengths, detects carboxyhemoglobin, methemoglobin, total hemoglobin.

### Phase 5 — Sweat Sensing (2010s–present)
**Target analytes in sweat**: Na⁺, K⁺, Cl⁻, lactate, glucose (low correlation to blood), cortisol, urea, ammonium.

**Hardware Stack**:
| Component | Function |
|---|---|
| Microfluidic channels | Route sweat from pores to sensors |
| Flexible ISE array | Multi-ion detection |
| Enzymatic lactate electrode | Amperometric lactate |
| Skin-conformal substrate | Polyimide, PDMS |
| Reference electrode (Ag/AgCl) | Stable electrochemical reference |
| Flexible interconnects | Maintain contact during movement |
| BLE SoC | Wireless data |
| Flexible battery | Power |

**Challenge**: Sweat rate variability, skin contamination, dilution effects, calibration drift.

### Phase 6 — Breath Analysis (present/emerging)
Exhaled breath contains >1000 volatile organic compounds (VOCs) reflecting systemic metabolism.

**Key biomarkers**:
| Compound | Associated Condition |
|---|---|
| Acetone | Ketosis, diabetes |
| Isoprene | Cholesterol metabolism |
| Ammonia | Renal failure, liver disease |
| NOx compounds | Airway inflammation (asthma) |
| Ethanol | Alcohol metabolism |
| Hydrogen, methane | GI dysbiosis |

**Detection technologies**:
- Electronic nose (e-nose): array of non-specific chemiresistors
- Selected ion flow tube MS (SIFT-MS): real-time mass spectrometry
- Proton transfer reaction MS (PTR-MS)
- Photoacoustic spectroscopy: laser-based gas detection
- Quartz crystal microbalance: mass-sensitive detection

---

## 5.4 Electrical / Bioelectric Sensing

### Domain Definition
Bioelectric sensing measures **what the body is actively doing electrically** — ion gradients, action potentials, synchronized field potentials, conduction pathways, muscle activation.

### Core Physics
All bioelectric signals originate from **ion flux across cell membranes**:
- Resting membrane potential: approximately –70 mV (neuron), –90 mV (cardiac muscle)
- Action potential: rapid depolarization to +40 mV followed by repolarization
- Propagation: electrical signal moves along membrane (conduction) and through tissue (volume conduction)

### Phase 1 — ECG (1903–present)
The heart depolarizes in a coordinated wave, generating a dipole that propagates through the body volume. Electrodes on the skin surface detect tiny potential differences (0.1–5 mV) representing this cardiac dipole projected onto the electrode axis.

**P wave**: Atrial depolarization
**QRS complex**: Ventricular depolarization (largest)
**T wave**: Ventricular repolarization

**Hardware Stack**:
| Component | Specification |
|---|---|
| Ag/AgCl gel electrodes | 1–10 kΩ contact impedance |
| Instrumentation amplifier (INA) | 100–1000× gain, CMRR >80 dB |
| High-pass filter (0.05 Hz) | Remove DC baseline drift |
| Low-pass filter (150 Hz) | Anti-alias |
| Notch filter (50/60 Hz) | Power line rejection |
| ADC (16 bit, 500 Hz–10 kHz) | Digitize |
| MCU | Digital filtering, R-peak detection |
| Isolation barrier | Patient safety (IEC 60601-1) |
| Right-leg drive (RLD) | Active common-mode rejection |

**Modern Wearable ECG**:
- Dry electrodes (Ti, Au, or conductive polymer) — no gel required
- Single-lead Holter patch (ZIO patch, Zephyr)
- 12-lead vest or belt systems
- Smartwatch optical + electrical combination

**AI ECG**: Neural networks now detect AFib, LVH, low ejection fraction, potassium level, age, sex, and sleep apnea from ECG alone.

### Phase 2 — EEG (1924–present)
**Core Physics**: Pyramidal neuron populations generate extracellular field potentials from synchronized postsynaptic currents. Dipole fields sum, attenuate through cerebrospinal fluid, skull (~40× attenuation), and scalp. Surface signals: 5–100 µV.

**Frequency Bands**:
| Band | Frequency | Brain State |
|---|---|---|
| Delta | 0.5–4 Hz | Deep sleep |
| Theta | 4–8 Hz | Drowsiness, memory |
| Alpha | 8–13 Hz | Relaxed, eyes closed |
| Beta | 13–30 Hz | Active cognition |
| Gamma | 30–100+ Hz | Binding, perception |

**Hardware Stack**:
| Component | Specification |
|---|---|
| Electrode array (10-20 system, 19–256 electrodes) | Ag/AgCl cup + gel |
| Electrode impedance < 5 kΩ | Signal quality requirement |
| Instrumentation amplifier | 10,000–100,000× gain |
| Anti-aliasing filter | 0.5–70 Hz typical bandwidth |
| Isolation amplifier | Patient safety |
| 24-bit ADC | Microvolt resolution |
| Signal processing (ICA, BSS) | Artifact removal |

**Dry-Electrode EEG**: Spring-loaded dry electrodes (Au, TiN, conductive polymer) allow headset deployment without gel. Higher impedance but viable for consumer/field use.

### Phase 3 — EMG (1929–present)
**Surface EMG**: Electrode pairs detect summed motor unit action potentials through skin. Amplitude: 0.1–10 mV. Bandwidth: 10 Hz–1 kHz (surface), 10 Hz–10 kHz (needle).

**Applications**: Rehabilitation, prosthetic control, gesture interfaces, exoskeleton control, sports science.

**Needle EMG**: Intramuscular electrode records individual or small clusters of motor units. Used clinically to diagnose neuromuscular disease.

### Phase 4 — Invasive Neural Sensing
**ECoG** (Electrocorticography): Electrode grid on brain surface beneath dura. Signals 100–1000× stronger than EEG. Better spatial resolution (1–5 mm vs. 3–5 cm for EEG).

**Intracortical Recording**: Microelectrodes penetrate cortex to record individual unit activity.

**Utah Array**: 10×10 grid of 1–1.5 mm silicon needles, 400 µm spacing. Each electrode records 1–5 neurons. 96 electrodes standard.

**Neuropixels**: 960 recording sites on a 70 µm × 10 mm silicon shank. Simultaneous recording across cortical layers.

**Signal Chain**: Neuron fires → extracellular voltage transient (100–500 µV, 0.5–2 ms) → electrode detects → LNA amplifies → ADC (30 kHz sampling) → spike sorting (template matching, PCA, kilosort) → single-unit or multi-unit activity

### Phase 5 — Brain-Computer Interfaces
**Goal**: Decode neural activity into commands (motor, speech, cognitive) and/or deliver sensory stimulation.

**Current clinical BCIs**:
- BrainGate: Utah array recording → cursor control, robotic arm
- Stentrode (Synchron): endovascular electrode array, no open brain surgery
- Neuralink N1: 64 threads × 1024 electrodes, wireless telemetry

**Challenges**: Signal instability (glial scarring), power delivery, biocompatibility, decoding generalization.

---

## 5.5 Implantable / Closed-Loop Systems

### Core Architecture
All implantable systems follow this fundamental loop:

`Sense → Condition → Interpret → Decide → Actuate → Physiological response → Sense again`

### Pacemakers (1958–present)
**Sensing**: Intracardiac electrogram (IEGM) from tip electrode
**Stimulation**: 1–5V pulse, 0.5–2 ms duration, 60–200 bpm rate
**Modern pacemaker battery**: Li-SVO, 5–15 year life at 5 µJ/pulse
**Modern features**: Accelerometer for rate-response, far-field RF (409 MHz or BLE) telemetry, MRI conditional designs
**Leadless pacemaker** (Medtronic Micra): 0.8 cc capsule, delivered via femoral catheter, 25.9 mm × 6.7 mm

### Cochlear Implants (1978–present)
**External**: Microphone array → DSP (filterbank, 12–22 channels) → RF transmitter coil
**Internal**: Receiver coil → decoder → electrode array in cochlea (scala tympani) → auditory nerve stimulation
**Electrode spacing**: 2–3 mm apart, 22 electrodes (Cochlear) or 16 (MED-EL)
**Frequency mapping**: Base = high freq, apex = low freq (tonotopy)

### Deep Brain Stimulation (1987–present)
**Target nuclei**: STN, GPi (Parkinson's), Vim (tremor), ANT (epilepsy), cg25 (depression research)
**Stimulation parameters**: 60–180 µs pulse width, 60–180 Hz, 1–5V, monopolar or bipolar
**Adaptive DBS**: Records LFP (local field potential) from same electrodes → beta power (13–30 Hz) inversely correlates with Parkinson's motor state → amplitude adjusts automatically

### Artificial Pancreas (Closed-Loop Insulin Delivery)
**Components**: CGM (Dexcom G6/G7) + Insulin pump (Omnipod, MiniMed) + Control algorithm (Model Predictive Control, PID, Fuzzy Logic)
**Control loop**: Glucose reading every 5 min → algorithm predicts 30-min glucose → dose insulin or suspend delivery
**Open-source systems**: OpenAPS, Loop, Android APS — community-built closed-loop using off-label CGM + pump combinations

### Retinal Implants (2002–present)
**Epiretinal** (Argus II, Second Sight): External camera → video processor → RF link → implant → 60-electrode array on retinal surface → optic nerve stimulation
**Subretinal** (Alpha IMS, Retina Implant): Photosensitive microchip subretinally converts light to stimulation directly

---

## 5.6 Cellular / Microscopic Sensing

### Flow Cytometry (1967–present)
**Core Physics**: Cells in suspension flow single-file through a laser. Forward scatter (FSC) → cell size. Side scatter (SSC) → granularity. Fluorescent antibodies bound to cell surface markers → fluorescence intensity → quantify expression.

**Hardware Stack**:
| Component | Function |
|---|---|
| Sheath fluid pump | Focus cells into single file |
| Laser (488 nm, 532 nm, 640 nm) | Excitation |
| Dichroic mirrors + bandpass filters | Wavelength sorting |
| PMT/avalanche photodiode | Fluorescence detection |
| High-speed ADC | Capture per-cell data |
| Computer | Cell classification |

**Throughput**: 10,000–100,000 cells/second
**Miniaturization**: Acoustic focusing replaces hydrodynamic focusing. Microfluidic chips. LED instead of laser. Result: portable cytometers (CytoFLEX S at 14 kg, still not pocket-scale).

### Digital Pathology (1990s–present)
Whole-slide imaging: motorized stage + high-resolution camera + stitching = gigapixel slides. AI: automated grading, mitosis counting, tumor border detection, biomarker quantification.

### Live Cell Imaging
Timelapse microscopy tracks cell behavior over hours-days. Phase contrast, DIC, fluorescence. Microfluidic chambers maintain cells under physiological conditions during imaging.

---

## 5.7 Dynamic Physiological Monitoring

**Cardiovascular**: Continuous blood pressure (photoplethysmography, arterial line), cardiac output (thermodilution, bio-impedance), pulse wave velocity.

**Respiratory**: Capnography (EtCO2), spirometry, respiratory inductance plethysmography (RIP), polysomnography.

**Body Temperature**: Infrared tympanic, forehead temporal, continuous core temperature capsule (ingestible thermometer pill), skin patch NTC thermistor.

**Motion and Posture**: IMU (accelerometer + gyroscope + magnetometer), gait analysis insoles, posture-correcting wearables.

**Sleep**: Polysomnography (PSG) — EEG + EOG + EMG + ECG + SpO2 + respiratory effort. Consumer sleep trackers: optical HRV + accelerometry-based staging.

---

## 5.8 Multi-Modal Convergence Systems

**Digital Twin Medicine**: A computational patient model continuously updated from all sensing modalities. Current state: research/ICU monitoring integration. Near future: ambulatory digital twin.

**PET-CT**: Metabolic function (PET) + anatomical structure (CT) co-registered. Absolute gold standard for oncologic staging.

**PET-MRI**: Simultaneous functional metabolic and soft-tissue anatomical imaging. Emerging in pediatric oncology.

**Cardiac MRI + ECG gating**: ECG triggers MRI acquisition per cardiac cycle. Combines anatomical and functional cardiac data.

**Future convergence direction**:
`Continuous EEG + ECG + CGM + SpO2 + motion + breath + wearable chemistry + episodic sequencing + imaging → AI-integrated living physiological model`

---

# 6. Open-Source Portable Hardware Ecosystem

## 6.1 Philosophy and Mandate

Every domain of biological sensing began with large, expensive, proprietary infrastructure. In each case, the path to portability followed the same pattern:

1. Physical sensing principle identified
2. Large infrastructure required initially (optics, precision mechanics, high power)
3. Key enabling miniaturization technology emerges (semiconductor integration, MEMS, better algorithms, DSP)
4. First commercial portable version released — often still expensive and closed-source
5. **Open-source community replicates core function at fraction of cost**

OpenPCR did this for thermocyclers. Open-source EEG systems (OpenBCI) did this for brain sensing. The NanoFlowSIM hardware ecosystem does this across **all** domains simultaneously.

### Design Mandates for All Devices
- **Portable**: battery-operable, fits in a bag, or wearable
- **Open-source hardware**: full KiCad schematics, Gerbers, BOM, STEP files published
- **Open firmware**: full embedded firmware source published (C/C++/Rust)
- **Open protocol**: standardized JSON data format, BLE/USB, documented API
- **NanoFlowSIM-native**: data streams directly into NanoFlowSIM patient profile
- **Reproducible**: manufacturable from commodity components, JLCPCB/PCBWay compatible
- **Field-deployable**: operates in field conditions (0–45°C, humid environments)
- **Affordable**: component cost target <$500 per device for most variants, <$100 for consumables where possible

### Device Naming Convention
`NFSIM-[DOMAIN]-[NUMBER]`
- PCR: polymerase chain reaction
- SEQ: sequencer
- CRISPR: CRISPR diagnostic
- dPCR: digital PCR
- GELEC: gel electrophoresis
- US: ultrasound
- MRI: magnetic resonance imaging
- XRAY: X-ray
- OCT: optical coherence tomography
- CGM: continuous glucose monitor
- SWEAT: sweat chemistry
- CHEM: blood chemistry
- OXY: oxygenation
- BREATH: breath analysis
- ECG: electrocardiogram
- EEG: electroencephalogram
- EMG: electromyogram
- NEURAL: neural recording
- CAP: capsule (ingestible)
- FLOW: flow cytometry
- ENV: environmental sensing
- MICRO: microscopy

---

## 6.2 Molecular / Genomic Hardware Variants

### A. Portable PCR Variants

**NFSIM-PCR-01**: Portable individual PCR unit (see full spec §7.1)
**NFSIM-PCR-02**: Micro gel-slip strip reader (see full spec §7.2)
**NFSIM-PCR-03**: Loop-mediated isothermal amplification (LAMP) reader — no thermocycling, 65°C isothermal, simpler hardware
**NFSIM-PCR-04**: Recombinase polymerase amplification (RPA) reader — room temperature amplification, fastest time to result
**NFSIM-PCR-05**: Helicase-dependent amplification (HDA) reader — isothermal, near room temperature, high specificity
**NFSIM-PCR-06**: Digital droplet PCR (ddPCR) field unit — droplet generation microfluidics, fluorescence counting

### B. Sequencing Variants

**NFSIM-SEQ-01**: Open nanopore sequencer, biological pore (gel membrane format, see §7.3)
**NFSIM-SEQ-02**: Solid-state nanopore research board (see §7.4)
**NFSIM-SEQ-03**: Microfluidic Sanger sequencing cartridge reader — capillary electrophoresis chip-based, shorter reads but high accuracy
**NFSIM-SEQ-04**: Nanopore array research development kit — bare flow cell substrate holder, external ASIC eval board

### C. CRISPR Diagnostic Variants

**NFSIM-CRISPR-01**: Lateral flow CRISPR reader (see §7.5)
**NFSIM-CRISPR-02**: Fluorescence CRISPR reader — SHERLOCK/DETECTR-compatible, real-time fluorescence quantification
**NFSIM-CRISPR-03**: Electrochemical CRISPR detector — no optics, electrical signal only, lowest power

### D. Gel Electrophoresis Variant

**NFSIM-GELEC-01**: Portable gel electrophoresis system (see §7.7)
**NFSIM-GELEC-02**: Chip-based capillary electrophoresis reader — uses microfluidic chips instead of agarose gels

---

## 6.3 Structural Imaging Hardware Variants

### A. Ultrasound Variants

**NFSIM-US-01**: Portable USB-C ultrasound probe (see §7.8)
**NFSIM-US-02**: Wearable ultrasound patch array (see §7.9)
**NFSIM-US-03**: Ingestible capsule ultrasound (see §7.10)
**NFSIM-US-04**: High-frequency dermal ultrasound probe (25–50 MHz) — skin layer imaging, wound depth assessment
**NFSIM-US-05**: Doppler blood flow sensor — wearable wristband for radial artery continuous flow
**NFSIM-US-06**: Transcranial Doppler (TCD) headband — bilateral temple probes for cerebral blood flow velocity
**NFSIM-US-07**: Endocavity ultrasound probe — transrectal/transvaginal, for gynecologic/urologic field screening
**NFSIM-US-08**: Fetal portable Doppler — handheld, single crystal, fetal heart rate and movement
**NFSIM-US-09**: Guided needle portal — real-time ultrasound needle guidance jig for aspiration/injection

### B. Low-Field MRI Variant

**NFSIM-MRI-01**: Low-field portable MRI, permanent magnet (see §7.11)
**NFSIM-MRI-02**: Earth's field NMR relaxometry — measures T1/T2 in biological fluids. No magnet needed, uses Earth's 50 µT field + pre-polarization pulse.

### C. X-Ray Variant

**NFSIM-XRAY-01**: Low-dose portable X-ray panel (see §7.12)
**NFSIM-XRAY-02**: Fluorescence X-ray analyzer — identifies elemental composition (e.g., lead in blood from spot exposure)

### D. Optical Imaging Variants

**NFSIM-OCT-01**: Portable OCT probe (see §7.13)
**NFSIM-OCT-02**: Fiber-probe OCT for endoscopic/catheter use — 2 mm diameter fiber probe for GI or coronary imaging
**NFSIM-MICRO-01**: Portable digital microscope, pathology grade (see §7.30)
**NFSIM-MICRO-02**: Lensless holographic microscope — no objective lens, computational reconstruction, ultra-low cost

---

## 6.4 Chemical / Metabolic Sensing Hardware Variants

**NFSIM-CGM-01**: Open CGM sensor platform (see §7.14)
**NFSIM-SWEAT-01**: Wearable sweat chemistry patch (see §7.15)
**NFSIM-CHEM-01**: Portable blood chemistry analyzer (see §7.16)
**NFSIM-OXY-01**: Multi-site tissue oxygenation array (see §7.17)
**NFSIM-BREATH-01**: Portable breath metabolomics (see §7.18)
**NFSIM-CHEM-02**: Saliva chemistry reader — strip-based or microfluidic, for uric acid, cortisol, glucose, amylase
**NFSIM-CHEM-03**: Urine chemistry panel reader — multi-analyte urine strips with optical reading
**NFSIM-CHEM-04**: Lipid panel microfluidic chip reader — cholesterol, HDL, LDL, triglycerides from fingerstick
**NFSIM-CHEM-05**: Lactate analyzer — sports/critical care fingerstick, enzymatic amperometric
**NFSIM-CHEM-06**: Ketone monitor — breath acetone or blood BHB strip reader
**NFSIM-CHEM-07**: Cortisol wearable — sweat-based continuous immunoassay patch
**NFSIM-CHEM-08**: Continuous lactate implant — subcutaneous wire sensor, 7-day wear, BLE

---

## 6.5 Electrical / Bioelectric Sensing Hardware Variants

**NFSIM-ECG-01**: Open single-lead ECG patch (see §7.19)
**NFSIM-ECG-02**: 12-lead portable ECG vest (see §7.20)
**NFSIM-ECG-03**: 3-lead Holter monitor patch — 30-day continuous recording
**NFSIM-EEG-01**: Dry-electrode open EEG headset (see §7.21)
**NFSIM-EEG-02**: Research-grade 64-channel wet EEG system — portable amplifier box, standard cap
**NFSIM-EEG-03**: Around-ear EEG (cEEGrid / earEEG) — discreet behind-ear electrode array
**NFSIM-EMG-01**: Multi-channel surface EMG armband (see §7.22)
**NFSIM-EMG-02**: Single-channel EMG patch — muscle fatigue monitoring, prosthetic control
**NFSIM-NEURAL-01**: Open high-density ECoG research array (see §7.23)
**NFSIM-NEURAL-02**: Open intracortical recording headstage — compatible with Utah array or custom microelectrodes
**NFSIM-EOG-01**: Electrooculography glasses — tracks eye movement from periorbital electrodes
**NFSIM-EDA-01**: Electrodermal activity (skin conductance) wrist sensor — sympathetic arousal, stress, pain

---

## 6.6 Ingestible / Capsule Sensor Variants

Ingestible capsules represent a new frontier: a sensor that traverses the GI tract (30–36 hours typical transit), reporting data from stomach, small intestine (duodenum, jejunum, ileum), and large intestine (colon). The capsule tracks its own position using pressure signatures, peristaltic pattern recognition, and external magnetic field sensing or RF triangulation.

**NFSIM-CAP-01**: Ingestible imaging + chemical capsule (see §7.24)
**NFSIM-CAP-02**: GI ultrasound capsule (see §7.25)
**NFSIM-CAP-03**: DNA/RNA capture capsule (see §7.26)
**NFSIM-CAP-04**: Full multi-modal research capsule (see §7.27)
**NFSIM-CAP-05**: Temperature mapping capsule — core body temperature logging during transit, passive, 48h logging
**NFSIM-CAP-06**: pH / pressure / motility capsule (SmartPill-equivalent) — GI pH mapping, pressure waveforms, transit time
**NFSIM-CAP-07**: Microbiome sampling capsule — sterile chamber opens in colon, captures contents, reseals, passed and retrieved for sequencing
**NFSIM-CAP-08**: Drug delivery verification capsule — logs GI conditions and reports when/whether it opens
**NFSIM-CAP-09**: Oxygen mapping capsule — measures dissolved O2 (GI hypoxia mapping)
**NFSIM-CAP-10**: Bleeding detection capsule — spectrometric detection of hemoglobin in GI fluid

---

## 6.7 Wearable Patch and Implant Variants

**NFSIM-PATCH-01**: Biopotential + motion multi-sensor patch — ECG + accelerometer + skin temperature in one adhesive
**NFSIM-PATCH-02**: Wound healing monitor patch — local oxygen, pH, temperature, exudate chemistry over wound
**NFSIM-PATCH-03**: Transdermal drug delivery controller — iontophoresis patch with controlled drug flux, BLE-programmable rate
**NFSIM-IMPLANT-01**: Open subcutaneous sensor node — titanium capsule, ~10 mm × 5 mm, sensor-swappable, NFC-powered, passive
**NFSIM-IMPLANT-02**: Neural stimulation research platform — biphasic current stimulator, 16-channel, wireless, research-grade chronic implant

---

## 6.8 Field / Environmental Sensing Variants

**NFSIM-ENV-01**: Environmental bio-aerosol sampler (see §7.29)
**NFSIM-ENV-02**: Water pathogen PCR station — automated water sampling, LAMP amplification, pathogen detection (E. coli, Salmonella, Cryptosporidium)
**NFSIM-ENV-03**: Soil microbiome sampler — DNA extraction cartridge + LAMP or sequencing for agricultural/field genomics
**NFSIM-ENV-04**: Air quality biomonitor — VOC sensors + PM2.5 + CO2 + temperature/humidity for respiratory exposure assessment
**NFSIM-ENV-05**: Field mosquito/vector trap + genomics — light trap, kill chamber, PCR ID of species and pathogens (Dengue, Malaria, Zika)

---

# 7. Full Hardware Specifications — All Devices

---

## 7.1 NFSIM-PCR-01 — Portable Individual PCR Unit

**Concept**: Single-person portable PCR thermocycler designed for field diagnostics, DIYbio, and personal genomics sample preparation. Battery-operable. Compatible with standard 0.2 mL PCR tubes or 8-strip format.

### Specifications

| Parameter | Value |
|---|---|
| Sample format | 8 × 0.2 mL strip or 1 individual tube |
| Sample volume | 10–50 µL |
| Temperature range | 4°C–98°C |
| Temperature accuracy | ±0.1°C |
| Ramp rate (heating) | 5°C/s |
| Ramp rate (cooling) | 3°C/s |
| Cycle capacity | 1–60 cycles programmable |
| Run time (40 cycles) | ~45–60 min |
| Connectivity | USB-C, BLE 5.0 |
| Power source | 4S Li-Ion battery (14.8V, 5000 mAh) OR USB-C PD 45W |
| Battery life | 6–8 PCR runs per charge |
| Dimensions | 160 mm × 80 mm × 70 mm |
| Weight | 650 g |
| Display | 2.8" color TFT touchscreen |
| IP rating | IP54 (splash-resistant) |
| Operating temperature | 0°C–40°C ambient |

### Hardware Architecture

**Thermal System**:
| Component | Selection | Notes |
|---|---|---|
| Thermal block | CNC-machined aluminum 6061 | 8 conical wells, 0.2 mL format |
| Peltier module (TEC) | TEC1-12710, 10A, 12V | Bidirectional heat pump |
| TEC driver | DRV8876 or L298N + custom PWM | H-bridge for polarity reversal |
| Thermistor | NTC 10kΩ B=3950K (×2, block + ambient) | Embedded in block center and edge |
| PID controller | Software PID, 100 Hz update rate on STM32 | Gain-scheduled for heat/cool |
| Fan | 30×30×10mm, 12V, 6 CFM | Active Peltier cool side dissipation |
| Heat sink | Copper vapor chamber + finned aluminum | Cold side of Peltier |
| Thermal paste | Arctic Silver 5 | TEC-to-block and TEC-to-heat sink |
| Heated lid | Nichrome wire resistive element, 103°C | Prevent condensation |
| Lid thermistor | NTC 10kΩ | Lid temperature feedback |

**Electronics**:
| Component | Selection | Notes |
|---|---|---|
| Main MCU | STM32H743 | 480 MHz Cortex-M7, FPU for PID |
| BLE SoC | nRF52840 (co-processor or integrated) | BLE 5.0, advertising + GATT server |
| TFT display driver | ILI9341 | SPI interface, 320×240 |
| Touch controller | XPT2046 | 4-wire resistive |
| Battery management | BQ25895 | Li-Ion charger, USB-C PD negotiation |
| Fuel gauge | MAX17048 | State of charge estimation |
| Real-time clock | DS3231 | Timestamping |
| Flash storage | W25Q128 (16 MB) | Protocol storage, run log |
| USB-C controller | FUSB302 | PD negotiation |
| Power regulation | LM2596 (12V), AMS1117-3.3 | Buck converter + LDO |

**PCB Design**:
- 4-layer PCB, 2 oz copper
- Thermal isolation zones between power and analog sections
- Dedicated ground plane beneath thermistor signal paths
- Connectors: USB-C (charging + data), 2.54mm TEC connector, 1.25mm thermistor, JST-XH battery
- All SMD components for automated assembly

**Enclosure**:
- PETG or ABS FDM-printable enclosure
- Full STEP file for customization
- Lid hinge mechanism for PCR tube access
- Fan exhaust vents on bottom
- Rubber feet + tripod mount (1/4-20 threaded insert)

**Firmware Architecture**:
- FreeRTOS real-time kernel
- Tasks: PID control (highest priority, 10 ms period), BLE stack, display update, user input, data logging
- Protocol storage: JSON-based PCR programs stored in SPI flash
- BLE GATT services: Device Info, PCR Control, PCR Status, Temperature Stream

**Software Interface**:
- Desktop: electron app, real-time temperature graph, protocol editor, run log export
- Mobile: BLE-connected app, monitor run progress, receive completion notification
- CLI: serial command interface for automated testing / scripting

**NanoFlowSIM Integration**:
- Outputs JSON run report: protocol name, cycle parameters, temperature log, start/end time, sample ID
- Anchors result to "Molecular Lab Sample" data type in patient profile
- Pairs with downstream NFSIM-SEQ-01 or NFSIM-CRISPR-01 for result interpretation

**BOM (Key Components)**:
| Item | Qty | Est. Unit Cost |
|---|---|---|
| STM32H743VIT6 | 1 | $8 |
| nRF52840-QIAA | 1 | $7 |
| TEC1-12710 Peltier | 1 | $6 |
| DRV8876 TEC driver | 1 | $3 |
| Aluminum thermal block (machined) | 1 | $25 |
| 2.8" TFT display | 1 | $8 |
| BQ25895 battery charger | 1 | $2 |
| Li-Ion 4S pack 5000 mAh | 1 | $35 |
| NTC thermistors | 4 | $1 |
| PCB (4-layer, JLC) | 1 | $15 |
| Enclosure (PETG print) | 1 | $12 |
| Fan 30mm | 1 | $3 |
| Heat sink + vapor chamber | 1 | $8 |
| Miscellaneous passives | — | $15 |
| **Total BOM** | | **~$148** |

---

## 7.2 NFSIM-PCR-02 — Micro Gel-Slip PCR Strip Reader

**Concept**: Inspired by pregnancy test / lateral flow simplicity applied to gel electrophoresis. Pre-cast polymer gel strips (similar to Agilent RNA ScreenTape) loaded with DNA sample, inserted into a compact reader that applies voltage, images the result with a CMOS sensor under LED transillumination, and reports band presence/absence + approximate size to NanoFlowSIM.

### Specifications

| Parameter | Value |
|---|---|
| Gel format | Disposable polymer gel strip, 10 mm × 80 mm |
| Lanes per strip | 1 sample + 1 ladder |
| Separation range | 100 bp – 10 kb |
| Resolution | ±5% fragment size |
| Run time | 4–8 min at 200V |
| Stain method | Pre-stained SYBR-Safe or EtBr (strip pre-loaded) |
| Detection | 470 nm LED transilluminator + OV5647 CMOS (Raspberry Pi camera) |
| Buffer | TAE or TBE pre-loaded in sealed cartridge |
| Voltage output | 200V DC, 5 mA max |
| Power source | USB-C 5V (internal boost converter to 200V) |
| Dimensions | 120 mm × 60 mm × 40 mm |
| Weight | 200 g |
| Connectivity | USB-C, BLE |

### Hardware Architecture

**Electrophoresis System**:
| Component | Selection |
|---|---|
| HV boost converter | MC34063 or custom flyback, 5V→200V, <5mA |
| HV safety cutoff | Optocoupler-isolated crowbar circuit |
| Platinum electrodes | Pt wire, 0.5 mm diameter, buffer reservoir contacts |
| Gel strip dock | PTFE channel, press-fit strip insertion |
| Buffer reservoir | Sealed polycarbonate wells, pre-filled on strip |

**Imaging System**:
| Component | Selection |
|---|---|
| LED transilluminator | 2× 470 nm LED, 500mW total, bottom-illumination |
| Blue filter | 520 nm longpass emission filter above gel |
| Camera | OV5647 (5 MP) or OV2640, 25 mm from gel |
| Orange filter (SYBR Safe) | Acrylic optical filter sheet |
| Image processor | Raspberry Pi Zero 2W or ESP32-S3 with camera interface |

**Consumable Strip Design**:
- Agarose/polymer gel pre-cast in polycarbonate strip housing
- SYBR Safe pre-stained in gel during manufacture
- Two wells: 1 ladder (pre-loaded with 1 kb ladder), 1 sample
- Sealed with foil tab (peel to load sample)
- Buffer wells pre-filled, sealed with separate tab
- Shelf life: 12 months refrigerated, 6 months at room temperature

**Software**:
- Automated lane detection and band identification
- Fragment size estimation from ladder interpolation
- Reports: band detected (Y/N), estimated size (bp), image saved as PNG
- NanoFlowSIM output: `{"type":"gel_electrophoresis","bands":[{"lane":1,"size_bp":500,"intensity":0.82}]}`

**BOM (Key Components)**:
| Item | Qty | Est. Unit Cost |
|---|---|---|
| HV boost converter module | 1 | $4 |
| OV5647 camera module | 1 | $8 |
| 470nm LED | 2 | $1 |
| Optical filter (520 nm longpass) | 1 | $5 |
| Raspberry Pi Zero 2W | 1 | $15 |
| PTFE strip dock (machined) | 1 | $12 |
| Enclosure (SLA print) | 1 | $20 |
| PCB | 1 | $8 |
| Passives, connectors | — | $10 |
| **PCB + Electronics total** | | **~$83** |
| **Gel strip (consumable, per 10)** | 10 | **~$30** |

---

## 7.3 NFSIM-SEQ-01 — Open Nanopore Sequencer (Gel Membrane Variant)

**Concept**: An open-source nanopore sequencing platform using biological nanopore proteins (α-hemolysin or MspA) reconstituted in an artificial lipid bilayer or supported gel membrane. Targets research-grade sequencing exploration, educational use, and field sequencing where a full MinION flow cell is inaccessible. Uses FPGA-based analog front-end signal acquisition with open-source basecaller.

### Core Architecture

This device replicates the physics of nanopore sequencing with commodity-accessible components:

**Membrane chamber**: microfluidic PDMS or polycarbonate flow cell with a 20–50 µm diameter aperture in a thin (25 µm) Teflon membrane. Lipid bilayer or supported lipid membrane forms across aperture.

**Nanopore insertion**: α-hemolysin (commercially available from Sigma-Aldrich) or MspA (resurgent open-source protein production) added to cis chamber. Spontaneously inserts into bilayer.

**Ionic current measurement**: Ag/AgCl electrodes in cis (top) and trans (bottom) chamber. Voltage clamped at +100 to +180 mV. Current amplified by low-noise patch-clamp amplifier.

**DNA threading**: dsDNA is prepared with a motor protein (phi29 DNA polymerase works as a DNA ratchet; commercially available). Motor protein ratchets ssDNA through pore at ~400 bases/second.

### Specifications

| Parameter | Value |
|---|---|
| Pore type | α-hemolysin (biological) or MspA |
| Membrane type | Planar lipid bilayer or supported gel membrane |
| Ionic current range | 0–500 pA |
| Voltage clamp range | –200 to +200 mV |
| Noise floor | <1 pA RMS (with careful shielding) |
| Sampling rate | 10–50 kHz |
| ADC resolution | 16-bit minimum |
| Channels | 1 (research), expandable to 16 |
| Temperature control | 18–40°C (Peltier-controlled chamber) |
| Read length | Theoretically unlimited |
| Raw accuracy | ~85–92% (requires training/calibration) |
| Connectivity | USB 3.0 to host for data streaming |
| Dimensions | 200 mm × 150 mm × 80 mm (amplifier + chamber unit) |
| Power | USB or 12V DC |

### Hardware Architecture

**Low-Noise Patch Clamp Amplifier**:
| Component | Selection | Notes |
|---|---|---|
| Input op-amp | AD8625 or OPA140 | Ultra-low noise, FET input |
| Feedback resistor | 1–10 GΩ precision (metal film) | Determines sensitivity: I = V/Rf |
| Shield | Copper Faraday cage, connected to guard | Eliminates cable capacitance |
| Headstage PCB | Rogers 4350B high-frequency PCB | Low dielectric loss for pA signals |
| Voltage clamp DAC | AD5791 (20-bit) | Precise command voltage |
| ADC | ADS1256 (24-bit, 30 kSPS) or AD7177 | High resolution digitization |
| Noise filter | Bessel 4-pole, 5 kHz bandwidth | Anti-alias + signal band |

**Flow Cell**:
| Component | Material/Selection |
|---|---|
| Chamber body | Polycarbonate CNC-machined or SLA printed |
| Teflon membrane (25 µm) | Goodfellow, heat-thinned to aperture |
| Ag/AgCl electrodes | Ag wire chlorinated in bleach |
| Lipid solution | DPhPC in decane, 5 mg/mL |
| Perfusion ports | PEEK tubing, 0.5 mm ID |
| Faraday shield enclosure | Aluminum box, ground to amplifier |

**FPGA Interface**:
| Component | Selection |
|---|---|
| FPGA dev board | Lattice iCE40HX8K or Xilinx Artix-7 |
| Real-time processing | Threshold detection, event capture, data streaming |
| USB interface | FT232H (USB-UART bridge) or USB3 FIFO |
| Host software | Python acquisition, C++ real-time daemon |

**Signal Chain**:
`DNA in cis chamber → motor protein ratcheting → pore translocation → ionic current change (pA) → headstage amplifier → 16/24-bit ADC → FPGA decimation filter → USB stream → host basecaller`

**Open-Source Basecaller** (NFSIM Basecaller Project):
- PyTorch/TensorFlow-based convolutional recurrent neural network (CRNN)
- Trained on public ONT squiggle data (R9.4, R10 models in public domain from academic papers)
- CTC (Connectionist Temporal Classification) decoding
- Outputs FASTQ format

**Key Challenges Acknowledged**:
- Membrane stability: bilayers rupture. Solution: gel-supported lipid bilayers (agarose-DPhPC hybrids) are more robust
- Pore lifetime: channel blockade events. Solution: voltage reversal protocol to clear blockage
- Motor protein sourcing: phi29 DNAP commercially available, expensive. Open-source protein expression protocol published alongside hardware
- Noise: 1/f flicker noise dominates below 1 kHz. Careful shielding and PCB layout essential.

**BOM (Key Components)**:
| Item | Qty | Est. Unit Cost |
|---|---|---|
| AD8625 op-amp | 2 | $8 |
| 1GΩ feedback resistor | 4 | $15 |
| AD5791 DAC | 1 | $35 |
| ADS1256 ADC | 1 | $18 |
| Lattice iCE40 FPGA board | 1 | $45 |
| Polycarbonate flow cell (machined) | 1 | $40 |
| Teflon membrane (sheet) | 1 | $20 |
| Ag wire for electrodes | 1 | $10 |
| Rogers 4350B headstage PCB | 1 | $30 |
| Aluminum Faraday shield | 1 | $25 |
| α-hemolysin (20 µg) | 1 | $80 |
| DPhPC lipid (5 mg) | 1 | $50 |
| Phi29 DNA polymerase (500 U) | 1 | $120 |
| Miscellaneous | — | $40 |
| **Total BOM** | | **~$536** |

---

## 7.4 NFSIM-SEQ-02 — Solid-State Nanopore Research Board

**Concept**: A research development platform for solid-state nanopore fabrication and testing. Solid-state nanopores are drilled or etched in silicon nitride (SiN) or molybdenum disulfide (MoS₂) membranes using focused ion beam (FIB) or TEM. This board provides the electrical infrastructure (amplifier, voltage clamp, data acquisition) to interface with custom-fabricated solid-state nanopore chips.

### Specifications

| Parameter | Value |
|---|---|
| Membrane compatibility | SiN (10–50 nm), MoS₂, Al₂O₃, HfO₂ on Si substrate |
| Pore diameter range | 1–20 nm (varies by fabrication) |
| Chip format | 5 mm × 5 mm substrate with fluidic gasket |
| Voltage clamp | ±1V, 1 mV resolution |
| Current range | 1 pA – 10 nA |
| Bandwidth | DC to 100 kHz |
| Sampling rate | 500 kHz (16-bit) |
| Noise floor | <3 pA RMS at 10 kHz |
| Channels | 4 independent channels |
| Interface | USB 3.0 + SPI (for FPGA extension) |
| Software | Python API, real-time event detection |

### Hardware Architecture

**Multi-Channel Patch Clamp Amplifier**:
- 4× independent low-noise transimpedance amplifier (TIA) channels
- Feedback resistors: 500 MΩ (high sensitivity) / 50 MΩ (high bandwidth) switchable per channel
- Differential voltage clamp per channel (independent control)
- Cross-talk isolation: >80 dB between channels

**FPGA-Based Acquisition**:
- Xilinx Artix-7 FPGA
- 4× 16-bit 500 kSPS ADC (ADS8860 or similar)
- Real-time threshold crossing event detection
- Dwell time and blockade depth extraction in hardware
- USB3 bulk transfer to host

**Chip Interface**:
- PDMS gasket-sealed flow cell for chip mounting
- Two-chamber design (cis/trans) with microfluidic ports
- Ag/AgCl electrode contact pins spring-loaded onto chip
- Peltier temperature control: 10–60°C

---

## 7.5 NFSIM-CRISPR-01 — Portable CRISPR Diagnostic Device

**Concept**: A portable device for running SHERLOCK (Specific High Sensitivity Enzymatic Reporter UnLOCKing) or DETECTR assays. These use CRISPR-Cas13 (SHERLOCK) or CRISPR-Cas12 (DETECTR) with a fluorescent reporter to detect specific nucleic acid sequences (viral RNA, bacterial DNA, genetic variants) without sequencing.

**Key advantage over PCR**: SHERLOCK/DETECTR can run isothermally at 37–42°C. No thermocycler required for the CRISPR step (though sample typically requires isothermal amplification first via RPA/LAMP, which runs at 37–42°C as well). Entire assay: room temperature-capable with modest heating.

### Specifications

| Parameter | Value |
|---|---|
| Assay type | SHERLOCK (Cas13a/b), DETECTR (Cas12a) |
| Amplification | RPA (37°C) or LAMP (65°C) pre-step |
| Reaction temperature | 37°C (SHERLOCK) or 37°C (DETECTR) |
| Detection mode | Fluorescence (FAM/Texas Red) AND/OR lateral flow strip |
| Fluorescence excitation | 470 nm (FAM), 530 nm (Texas Red) |
| Emission detection | 520 nm (FAM), 610 nm (Texas Red) |
| Dynamic range | 1 aM – 1 µM (SHERLOCK) |
| Sensitivity | Single molecule (with pre-amplification) |
| Time to result | 30–60 min (amplification) + 30 min (CRISPR) |
| Heating zones | 2 independent (37°C CRISPR + 65°C LAMP option) |
| Sample wells | 8 |
| Power | USB-C 5V |
| Connectivity | BLE, USB-C |
| Dimensions | 150 mm × 90 mm × 50 mm |

### Hardware Architecture

**Thermal Control**:
| Component | Specification |
|---|---|
| Heating zone 1 (LAMP): | TEC or resistive, 65°C ±0.5°C |
| Heating zone 2 (CRISPR): | Resistive heater, 37°C ±0.5°C |
| Temperature sensors: | NTC thermistor, 10kΩ, ±0.1°C |
| PID controller: | STM32F4 software PID |

**Fluorescence Detection**:
| Component | Specification |
|---|---|
| Excitation LED 1 | 470 nm, 5mW, SMD |
| Excitation LED 2 | 530 nm, 5mW, SMD |
| Emission filter 1 | 520/35 nm bandpass (FAM) |
| Emission filter 2 | 610/40 nm bandpass (Texas Red) |
| Photodetector | SiPM (MicroFC-10035) or OPT101 |
| Lock-in detection | LED chopped at 1 kHz, synchronous demodulation |
| Optical path | Perpendicular excitation/emission, light-tight chamber |

**Lateral Flow Reader** (optional module):
- CMOS camera (OV5640) images test and control lines
- Background-subtracted line intensity quantification
- Pass/Fail determination + confidence score

**Reagent Handling**:
- Lyophilized reagent tubes (freeze-dried Cas13a/Cas12a + guide RNA + reporter)
- Pre-loaded or user-loaded cartridges
- Room-temperature stable: 6 months (lyophilized)

**BOM (Key Components)**:
| Item | Qty | Est. Unit Cost |
|---|---|---|
| STM32F411 MCU | 1 | $4 |
| nRF52840 BLE SoC | 1 | $7 |
| Resistive heater elements | 2 | $4 |
| NTC thermistors | 4 | $2 |
| 470 nm LED SMD | 2 | $1 |
| 530 nm LED SMD | 2 | $1 |
| SiPM detector | 2 | $12 |
| Optical bandpass filters | 4 | $20 |
| OV5640 camera (LF module) | 1 | $8 |
| PCB (4-layer) | 1 | $12 |
| Enclosure (SLA) | 1 | $25 |
| **Total BOM** | | **~$96** |
| **Reagent cartridge (per 8 tests)** | | **~$40–80** |

---

## 7.6 NFSIM-dPCR-01 — Portable Digital PCR (Droplet)

**Concept**: Digital PCR partitions a sample into thousands of nano-volume compartments (droplets or microwells) before PCR. Each compartment either contains target DNA (and amplifies) or doesn't. Endpoint fluorescence reading counts positive vs. negative partitions → absolute copy number (Poisson statistics).

### Specifications

| Parameter | Value |
|---|---|
| Partition method | Droplet generation (oil-aqueous emulsion) |
| Droplet volume | ~1 nL |
| Droplets per run | 10,000–20,000 |
| Reaction volume | 20 µL |
| Thermocycling | Same as NFSIM-PCR-01 |
| Detection | Endpoint fluorescence imaging |
| Dynamic range | 1–100,000 copies/µL |
| Sensitivity | 1 copy per 20 µL reaction |
| Duplexing | 2-color (FAM + HEX/VIC) |
| Run time | 90–120 min |
| Connectivity | USB-C, BLE |
| Power | 12V DC or battery |

### Hardware Architecture

**Droplet Generator**:
- Microfluidic chip: PDMS soft-lithography or injection-molded polycarbonate
- T-junction geometry: aqueous sample + oil + surfactant → droplet formation
- Oil: Mineral oil + 1% Span-80 surfactant
- Flow control: pneumatic pressure (small 5V diaphragm pump) or syringe pump
- Droplet size control: pressure ratio determines droplet volume

**Droplet Imaging**:
- After PCR, droplets sediment in imaging chamber
- High-resolution CMOS camera (OV5640, 5MP) with 10× macro lens
- Green/blue LED excitation
- FAM (520 nm) and HEX (556 nm) emission filters
- Image analysis: watershed segmentation, per-droplet intensity extraction
- Classification: threshold-based positive/negative call per droplet
- Poisson correction → copies per µL

---

## 7.7 NFSIM-GELEC-01 — Portable Gel Electrophoresis System

**Concept**: A full portable agarose gel electrophoresis system. Pours real agarose gels (or uses pre-cast gels). Runs at 100–150V. Images with built-in UV transilluminator (302 nm or 365 nm UV LED) + UV-blocking filter. Suitable for complete gel runs in field environments.

### Specifications

| Parameter | Value |
|---|---|
| Gel dimensions | 70 mm × 60 mm (mini gel) |
| Lane count | 6–10 lanes |
| Voltage output | 50–150V DC, adjustable |
| Current limit | 0–500 mA |
| Run time | 15–45 min |
| UV source | 302 nm or 365 nm UV LED array |
| Emission filter | Orange acrylic (for EtBr / SYBR Gold) |
| Buffer | TAE or TBE, 1× |
| Camera | OV5647, 8 MP |
| Power | USB-C (internal HV boost) |
| Dimensions | 200 mm × 160 mm × 90 mm |
| Weight | 800 g |

### Hardware Architecture

**Electrophoresis Tank**:
- UV-transparent polycarbonate casting tray
- Carbon electrode plates (corrosion-resistant)
- Integrated lid with UV-blocking window
- Buffer level indicator

**High Voltage Power Supply**:
| Component | Selection |
|---|---|
| HV boost converter | Flyback converter, 5V→200V |
| HV regulation | Voltage feedback, ±2V |
| Current monitoring | Inline sense resistor + ADC |
| Safety cutoff | Current limit, auto-shutoff on lid open |
| Polarity control | DPDT relay |

**Imaging System**:
- UV LED array (302 nm or 365 nm), 12× LED in array
- Longpass emission filter: 520 nm for SYBR, 590 nm for EtBr
- Raspberry Pi Zero 2W + HQ camera module
- Image capture on run completion
- Automated band detection software

**Safety**:
- Lid interlock: HV disabled when lid open
- UV shutoff when camera not engaged
- Earthed chassis

---

## 7.8 NFSIM-US-01 — Portable Ultrasound Probe (USB-C)

**Concept**: A handheld ultrasound probe that connects via USB-C to a smartphone, tablet, or laptop. Comparable to Butterfly iQ but fully open-source hardware. Uses CMUT (Capacitive Micromachined Ultrasonic Transducer) array for compact, semiconductor-fabricated transducer, or a conventional PZT linear array if CMUT is not accessible.

### Specifications

| Parameter | Value |
|---|---|
| Transducer type | Linear array (64 elements) or CMUT array |
| Frequency | 3–12 MHz (software-selectable) |
| Imaging modes | B-mode, M-mode, Color Doppler, PW Doppler |
| Field of view | 38 mm wide, 80 mm depth |
| Frame rate | 30–60 fps |
| Axial resolution | 0.2–0.5 mm |
| Lateral resolution | 1–3 mm |
| Interface | USB-C 3.1 (power + data) |
| Power draw | 5V, 3A max (USB-C PD) |
| Dimensions | 28 mm × 155 mm (probe body) |
| Weight | 180 g |
| IP rating | IPX7 (washable, no immersion sequencing) |
| On-probe processing | Digital beamformer ASIC or FPGA |

### Hardware Architecture

**Transducer Array (PZT variant)**:
| Component | Specification |
|---|---|
| PZT-5H element array | 64 elements, 0.3 mm pitch, 15 mm elevation focus |
| Backing layer | High-attenuation epoxy (sound absorption) |
| Matching layers | 1–2 layers, quarter-wave impedance matching |
| Ground shield | Copper foil, bonded to array housing |
| Flex interconnect | 64-conductor FPC cable |
| Lens | Silicone acoustic lens (fixed elevation focus) |

**Electronics**:
| Component | Specification |
|---|---|
| TX beamformer | Programmable delay lines, 64-channel, high-voltage pulser (±50–100V) |
| HV pulser | STHV800 (8-channel, stackable to 64) or equivalent |
| T/R switch | TX810 or custom MOSFET array |
| LNA | Ultra-low noise, 20–30 dB gain, 64-channel |
| TGC (time gain compensation) | Programmable gain, 64-channel |
| RX beamformer FPGA | Xilinx Artix-7 or Lattice ECP5, delay-and-sum in hardware |
| ADC | 12-bit, 40 MSPS, 64-channel (multiple ADS52J90 or similar) |
| USB3 controller | FT601 or custom USB3 FIFO |
| Power management | 5V in → HV (for TX), +3.3V, +1.8V, analog supply |

**Beamforming Signal Path**:
`TX: Host → FPGA → Delay lines → HV pulsers → transducer array`
`RX: Transducer array → LNA → TGC → ADC → FPGA beamformer (delay and sum) → envelope detection → log compression → scan convert → USB3 stream → host`

**Host Software**:
- OpenGL/Vulkan real-time B-mode rendering
- Scan converter (polar to rectangular)
- Doppler processing: autocorrelation, color flow mapping
- DICOM output
- NanoFlowSIM region anchor: user tags imaged anatomy during scan

**BOM (Key Components)**:
| Item | Qty | Est. Unit Cost |
|---|---|---|
| PZT array (custom fab) | 1 | $80 |
| STHV800 HV pulser (×8) | 8 | $60 |
| TX810 T/R switch (×8) | 8 | $24 |
| LNA array (custom PCB) | 1 | $40 |
| ADS52J90 ADC | 2 | $50 |
| Artix-7 FPGA | 1 | $90 |
| FT601 USB3 | 1 | $12 |
| Flex PCB + interconnect | 1 | $35 |
| Probe housing (machined aluminum) | 1 | $45 |
| Acoustic lens (silicone) | 1 | $15 |
| Cables, connectors | — | $20 |
| **Total BOM** | | **~$471** |

---

## 7.9 NFSIM-US-02 — Wearable Ultrasound Patch Array

**Concept**: A flexible adhesive ultrasound patch worn on the skin surface. Contains a 2D CMUT or piezo-polymer (PVDF) element array conforming to the skin. Designed for continuous or periodic imaging of underlying anatomy: cardiac (parasternal), lung (pleural effusion), DVT screening (leg veins), or tissue mechanical properties. Wireless (BLE or UWB) to a wearable compute unit.

### Specifications

| Parameter | Value |
|---|---|
| Patch dimensions | 60 mm × 60 mm |
| Transducer elements | 8×8 = 64 element PVDF or CMUT array |
| Frequency | 2–7 MHz |
| Imaging mode | B-mode, M-mode, tissue Doppler |
| Penetration depth | 10–150 mm |
| Frame rate | 5–15 fps (limited by wireless bandwidth) |
| Wear duration | 24–72 hours (disposable patch + reusable electronics module) |
| Connectivity | BLE 5.0 or UWB |
| Power | 300 mAh flexible LiPo, 12–24h life |
| IP rating | IPX4 (sweat and splash) |
| Patch thickness | <5 mm (electronics pod) + 0.5 mm array |

### Hardware Architecture

**Flexible Transducer Array**:
- PVDF (polyvinylidene fluoride) piezo-polymer: thin, flexible, biocompatible
- Screen-printed silver electrodes on PVDF film
- 64 addressable elements with individual row/column addressing
- Acoustic coupling: medical ultrasound gel layer or hydrogel pad
- Backing: flexible acoustic absorber foam

**Electronics (reusable pod)**:
- miniaturized beamformer ASIC or small FPGA
- Low-power pulsers (40V)
- Analog front end: LNA + TGC + ADC at 40 MSPS
- Wireless SoC (nRF5340 for BLE, or DW3000 for UWB)
- Flexible LiPo + wireless charging (Qi)
- Snap-connect to disposable array patch

**Key Innovation — Continuous Cardiac/Pulmonary Monitoring**:
Patient wears patch in parasternal position → continuous M-mode cardiac imaging → extract: ejection fraction trend, pericardial effusion detection, lung sliding (pneumothorax), B-lines (pulmonary edema). AI interprets each frame and streams physiological parameters rather than raw image.

---

## 7.10 NFSIM-US-03 — Pill Capsule Ultrasound (Ingestible)

**Concept**: A swallowable capsule containing a miniaturized ultrasound transducer array that images the GI tract walls from the inside. Tracks its own position via intestinal pressure signatures and RF localization. Transmits images wirelessly to an external receiver/wearable belt. Passes naturally within 24–36 hours.

### Specifications

| Parameter | Value |
|---|---|
| Capsule dimensions | 26 mm × 11 mm (standard endoscopy capsule size) |
| Transducer type | CMUT ring array, circumferential |
| Imaging geometry | 360° circumferential cross-section of GI lumen |
| Frequency | 5–20 MHz |
| Penetration depth | 5–30 mm (GI wall, adjacent organs) |
| Image resolution | 0.1–0.5 mm |
| Frame rate | 2–5 fps |
| Wireless protocol | 434 MHz or 915 MHz FSK (body penetration), range 1–2 m |
| Wireless data rate | 1–5 Mbps (compressed image stream) |
| Battery | Silver oxide or Li-SO₂Cl₂ primary, 250–300 mAh |
| Battery life | 24–36 hours (GI transit time) |
| Biocompatible shell | Medical-grade polycarbonate or Ultem |
| Position tracking | Accelerometer + gyroscope + pressure sensor combination |
| Data storage | 128 MB onboard NAND flash (backup if wireless fails) |

### Hardware Architecture

**Ultrasound Subsystem**:
| Component | Selection |
|---|---|
| CMUT ring array | Custom MEMS fab, 64 elements in ring, 10 mm diameter |
| Pulser/receiver ASIC | Custom silicon (Si, GaAs) or repurposed hearing aid chip |
| Acoustic coupling | Aqueous saline internal reservoir (transmits US through polycarbonate wall) |
| Image processing SoC | Ultra-low-power ARM Cortex-M4 |
| Image compression | JPEG 2000 hardware encoder |

**Position Tracking**:
- 3-axis accelerometer (BMA456): capsule orientation and motion
- 3-axis gyroscope (BMI088): rotation tracking
- Absolute pressure sensor (BMP581): GI pressure waveforms distinguish anatomical location (stomach: irregular high pressure; small intestine: peristaltic 10–30 mmHg waves; colon: lower pressure, longer interval)
- RF triangulation using external belt antenna array (optional, for enhanced location accuracy)

**Anatomical Position Estimation Algorithm**:
```
Position = f(elapsed_time, pressure_signature, peristaltic_pattern, capsule_orientation, pH_if_equipped)

Zones:
  0–30 min after swallow:    Esophagus → Stomach entry
  30 min – 4 hours:          Stomach (high pressure, churning motion signature)
  4–8 hours:                 Small intestine (peristaltic wave pattern ~3/min)
  8–36 hours:                Large intestine (haustral contraction signature)
```

**Wireless Transmission**:
- Body-penetrating RF at 434 MHz (MICS band medical device approved in many regions)
- External wearable belt: 4–8 antenna patches distributed around abdomen
- Received signals combined (diversity) to ensure coverage regardless of capsule orientation
- Lossless/near-lossless image compression before transmission

**External Receiver Belt**:
- 6× patch antennas, flexible
- RF frontend + ADC
- nRF5340 or ESP32-S3 for packet assembly
- BLE relay to phone/NanoFlowSIM app
- Disposable antenna patches, reusable electronics module

**Regulatory Path**: Device falls under ingestible medical device regulations (FDA 510(k) predicate: Capsule Endoscopy). Open-source design intended for research / IRB-approved studies initially.

---

## 7.11 NFSIM-MRI-01 — Low-Field Portable MRI (Permanent Magnet)

**Concept**: A benchtop MRI system using permanent magnets instead of superconducting electromagnets. Low field (50–100 mT) compromises SNR relative to 1.5T clinical MRI, but AI reconstruction algorithms compensate. No cryogenics. No shielding room required. Suitable for extremity imaging (hand, wrist, foot, ankle, brain in small form factor). Inspired by Hyperfine Swoop, but fully open-source.

### Specifications

| Parameter | Value |
|---|---|
| Field strength | 64 mT (permanent magnet) |
| Magnet type | NdFeB permanent magnets in Halbach array |
| Bore diameter | 320 mm (head) or 120 mm (extremity variant) |
| RF frequency | 2.7 MHz (64 mT proton resonance) |
| SNR | Low (compensated by signal averaging + AI recon) |
| Resolution (AI-enhanced) | 1.5 mm isotropic (brain) |
| Scan time | 5–15 min |
| Weight (head system) | 35–50 kg |
| Weight (extremity system) | 8–12 kg |
| Power | 120/240V, 1.5 kW peak |
| Gradient coils | 3-axis, air-core, ~50 A peak |
| RF coil | Surface coil or birdcage coil, volume |
| Shielding | Passive: aluminum cage sufficient at 2.7 MHz |
| Sequences | SE, GRE, FLAIR, DWI (simplified) |

### Hardware Architecture

**Permanent Magnet System**:
| Component | Specification |
|---|---|
| Magnet material | NdFeB grade N52, permanent |
| Array geometry | Halbach dipole or C-shape dipole |
| Field homogeneity | ±50 ppm over 20 cm DSV (shimmed) |
| Passive shim set | Iron shim plates, iteratively positioned |
| Active shim (optional) | Room-temperature resistive shim coils, ±1 A |

**Gradient Coil Set**:
- Air-core resistive gradient coils (no iron core at low field)
- Maxwell coils (Z-axis), Golay coils (X,Y)
- Peak gradient strength: 10–30 mT/m
- Slew rate: 10–50 T/m/s
- Driver: H-bridge amplifier, 48V, 30–50A peak

**RF System**:
| Component | Specification |
|---|---|
| RF excitation | Birdcage coil or surface coil, transmit/receive |
| Transmit power | <100W (low field requires low RF power) |
| RF amplifier | Linear 100W RF amp at 2.7 MHz |
| Duplexer | T/R switch (low-field: passive LC circuit) |
| Receive chain | Low-noise pre-amp, 2.7 MHz center, 10 kHz BW |
| ADC | 24-bit, 1 MSPS, coherent with gradient timing |

**Reconstruction**:
- Open-source MRI reconstruction: Bart (Berkeley Advanced Reconstruction Toolbox)
- AI super-resolution: trained on paired low-field / high-field datasets (public: FASTMRI challenge data)
- Output: NIfTI or DICOM format

---

## 7.12 NFSIM-XRAY-01 — Low-Dose Portable X-Ray Panel

**Concept**: A portable digital X-ray system comprising a battery-powered X-ray generator (briefcase-sized) and a wireless flat-panel detector. Targets field medicine, dental, veterinary, and point-of-care bone/chest imaging. Designed to be fully open-source with dose-minimizing pulsed technique.

### Specifications

| Parameter | Value |
|---|---|
| Generator type | Battery-powered, portable |
| Tube voltage | 40–90 kVp |
| Tube current | 1–100 mA |
| Exposure time | 1–500 ms |
| Dose per chest PA | <0.02 mSv (comparable to screen-film) |
| Detector size | 35 cm × 43 cm (standard) or 24 cm × 30 cm |
| Detector type | CsI scintillator + amorphous silicon TFT |
| Pixel pitch | 139 µm |
| Wireless protocol | Wi-Fi 802.11ac (detector → acquisition station) |
| Image resolution | 2520 × 3072 pixels (35×43 detector) |
| Bit depth | 14-bit grayscale |
| Battery life (generator) | 300 exposures per charge |
| Generator weight | 4.5 kg |
| Detector weight | 2.8 kg |
| Generator dimensions | 280 mm × 200 mm × 120 mm |

### Hardware Architecture

**X-Ray Generator**:
| Component | Specification |
|---|---|
| X-ray tube | Rotating anode, focal spot 0.6/1.2 mm |
| High voltage module | Resonant inverter, 40–90 kVp, ±1% regulation |
| mA control | Filament current PID control |
| Exposure timer | 1 ms resolution hardware timer |
| Battery | 48V Li-Ion, 20 Ah |
| Collimator | Manual leaf blades, laser alignment |
| Tube stand | Carbon fiber monopod, height-adjustable |

**Flat Panel Detector**:
| Component | Specification |
|---|---|
| Scintillator | CsI:Tl (structured), 500 µm thick |
| TFT array | α-Si TFT, 139 µm pixel pitch |
| Readout ASIC | Charge-integrating mode |
| ADC | 14-bit per pixel |
| Frame memory | DRAM buffer |
| Wireless | Wi-Fi 802.11ac module |
| Battery | 3.7V Li-Ion, 5000 mAh (8h use) |
| Housing | Carbon fiber + foam padding |

**Software**:
- DICOM output compliant
- Automated AEC (automatic exposure control) algorithm
- AI: automatic bone/soft tissue segmentation
- NanoFlowSIM: DICOM import → 3D anchor to imaged body region

---

## 7.13 NFSIM-OCT-01 — Portable OCT Probe

**Concept**: A portable swept-source or spectral-domain OCT probe for ophthalmic (retinal and corneal), dermatologic, or intraoperative imaging. OCT provides micron-scale cross-sectional images to 2–3 mm depth without contact in most configurations.

### Specifications

| Parameter | Value |
|---|---|
| OCT type | Spectral-domain (SD-OCT) |
| Light source | SLD (superluminescent diode), 840 nm, 50 nm bandwidth |
| Axial resolution | 6–7 µm in tissue |
| Lateral resolution | 15–25 µm |
| Scan depth | 1.5–2 mm |
| A-scan rate | 20,000–70,000 A-scans/sec |
| Field of view | 6 mm × 6 mm (retinal) |
| Spectrometer | 2048-pixel line scan CCD/CMOS |
| Probe connectivity | Fiber optic + USB3 |
| Processing | GPU-based FFT reconstruction |
| Output | Volume OCT data (DICOM, HDF5) |
| Dimensions | Handheld probe 120 mm × 30 mm; electronics box 200 mm × 150 mm × 80 mm |

### Hardware Architecture

**Optical Engine**:
| Component | Specification |
|---|---|
| SLD light source | EXS8510-1021, 840 nm, 50 nm FWHM |
| Fiber coupler (50:50) | Single-mode fiber beamsplitter |
| Reference arm | Retro-reflector + dispersion compensation glass |
| Sample arm | Handheld galvo scanner probe |
| Galvo mirrors | 2-axis, 8mm aperture, resonant + linear |
| Objective lens | 50mm focal length achromatic doublet |
| Spectrometer | 1200 lines/mm diffraction grating + F-theta lens + Basler spL4096-140km line scan |

**Electronics**:
| Component | Specification |
|---|---|
| Line scan camera driver | CameraLink interface, 140 kHz line rate |
| Frame grabber | PCIe or USB3 capture card |
| GPU | GTX 1650 or AMD RX 6500 XT for FFT |
| Galvo controller | Sine/ramp waveform DAC, 100 kSPS |
| Trigger synchronization | FPGA (Lattice ICE40) for precise timing |

---

## 7.14 NFSIM-CGM-01 — Open CGM Sensor Platform

**Concept**: An open-source continuous glucose monitor with both an enzymatic sensor filament and a reader/transmitter unit. Designed to enable DIYbio, research modification, and NanoFlowSIM-native continuous glucose streaming. Compatible with OpenAPS / Loop closed-loop insulin systems.

### Specifications

| Parameter | Value |
|---|---|
| Sensing method | Enzymatic amperometric (glucose oxidase) |
| Insertion depth | 8–10 mm subcutaneous |
| Filament diameter | 280 µm (25G equivalent) |
| Wear duration | 10–14 days |
| Measurement range | 40–400 mg/dL (2.2–22.2 mmol/L) |
| Accuracy (MARD) | <10% target |
| Sampling rate | Every 5 min |
| Warm-up time | 1–2 hours |
| Connectivity | NFC + BLE 5.0 |
| Alert capability | High glucose, low glucose, rate-of-change |
| App output | mg/dL, mmol/L, trend arrow, 24h graph |
| Waterproof | IPX8 (1m, 30 min) |
| Transmitter dimensions | 38 mm × 28 mm × 8 mm |

### Hardware Architecture

**Sensor Filament**:
| Layer | Material / Function |
|---|---|
| Core wire | Platinum wire, 127 µm diameter |
| Glucose oxidase layer | GOx crosslinked in BSA + glutaraldehyde |
| Interference membrane | Cellulose acetate (50–100 nm) |
| Biocompatibility layer | Polyurethane outer membrane |
| Reference electrode | Ag/AgCl on secondary track |

**Transmitter Electronics**:
| Component | Specification |
|---|---|
| Potentiostat ASIC | MAX30001 (biopotential + ECG, adaptable) or AFE4300 | 3-electrode potentiostat mode |
| Analog front end | 3-electrode, nA current, 24-bit ADC |
| MCU | nRF52840 (BLE 5.0 + NFC integrated) |
| NFC | ISO 15693, passive power from phone tap |
| BLE | GATT Glucose Profile (GLP) |
| Battery | CR2032 coin cell (NFC powered) or CR2477 (14-day BLE) |
| Flash | 4 MB SPI NOR (2 week data log) |
| Applicator | Spring-loaded single-use insertion mechanism |

**Calibration**:
- Factory calibration coefficients in sensor EEPROM (NFC-readable)
- Optional fingerstick calibration at 12h intervals for improved accuracy
- Temperature compensation from onboard NTC thermistor

**Open Firmware**:
- nRF5 SDK or Zephyr RTOS
- GATT CGM service (blood glucose measurement characteristic)
- NanoFlowSIM NFS-GATT extension for rich metadata (meal tags, insulin events, sensor ID)

---

## 7.15 NFSIM-SWEAT-01 — Wearable Sweat Chemistry Patch

**Concept**: A flexible adhesive patch worn on the forearm or chest that uses microfluidic channels to route sweat from eccrine glands to an electrochemical sensor array. Measures Na⁺, K⁺, pH, lactate, and optionally glucose, cortisol, or uric acid continuously during exercise or under resting conditions.

### Specifications

| Parameter | Value |
|---|---|
| Analytes | Na⁺, K⁺, pH, lactate, glucose (optional), cortisol (optional) |
| Sweat collection | Passive microfluidics, 5–20 µL/h fill rate |
| Detection | Potentiometric ISE (Na⁺, K⁺, pH) + amperometric (lactate, glucose) |
| Na⁺ range | 10–200 mmol/L |
| K⁺ range | 1–30 mmol/L |
| Lactate range | 0–30 mmol/L |
| pH range | 4.5–8.0 |
| Sample refresh | Passive flow via capillary channels |
| Wireless | BLE 5.0 |
| Battery | 20 mAh thin-film LiPo |
| Battery life | 6–12 hours continuous |
| Patch wear time | Single-use, 24h max |
| Waterproof | IPX5 |
| Dimensions | 60 mm × 40 mm × 3 mm |

### Hardware Architecture

**Microfluidic Layer (PDMS)**:
- Serpentine channel: routes sweat from inlet pores → sensor array → waste reservoir
- Air-displacement vent: allows channel priming without bubbles
- Volume: 5 µL active sensor chamber, 50 µL total

**Sensor Array (Flexible PCB)**:
| Sensor | Type | Electrode Material |
|---|---|---|
| Na⁺ ISE | Potentiometric | Sodium ionophore on polyaniline |
| K⁺ ISE | Potentiometric | Valinomycin-doped PVC membrane |
| pH electrode | Potentiometric | PEDOT:PSS or IrOx |
| Reference | Ag/AgCl | Printed Ag/AgCl ink |
| Lactate | Amperometric | Lactate oxidase on carbon paste |
| Glucose (opt.) | Amperometric | Glucose oxidase on carbon paste |

**Electronics (reusable module)**:
| Component | Specification |
|---|---|
| Potentiostat ASIC | LMP91000 (3-electrode, programmable) |
| Multiplexer | ADG708 (8-channel analog mux) |
| ADC | ADS1220 (24-bit, SPI) |
| MCU | nRF52833 (BLE 5.0) |
| Thin-film battery | 20 mAh LiPo + wireless Qi charging |
| Connector | Magnetic pogo pins to disposable patch |

---

## 7.16 NFSIM-CHEM-01 — Portable Blood Chemistry Analyzer

**Concept**: A handheld blood chemistry analyzer operating on 10–50 µL fingerstick blood. Uses a disposable microfluidic cartridge containing dried reagent zones. Reads electrochemically and/or photometrically. Target analytes: glucose, creatinine, BUN, sodium, potassium, chloride, ALT, AST, total protein, albumin, bilirubin, hemoglobin, INR.

### Specifications

| Parameter | Value |
|---|---|
| Sample type | Capillary whole blood (fingerstick) |
| Sample volume | 15–50 µL |
| Cartridge type | Single-use disposable, bar-coded |
| Analyte panels | Basic Metabolic, Liver, Renal, CBC proxy |
| TTFR | 2–4 min |
| Accuracy | ±10% (electrochemical), ±15% (optical) vs. lab reference |
| Detection | Multi-modal: ISE (ions), amperometric (enzymes), photometric (bilirubin, Hgb) |
| Reference standard | Ag/AgCl, pre-printed |
| Display | 3.5" color TFT |
| Connectivity | BLE, USB-C |
| Battery | 3000 mAh Li-Ion |
| Dimensions | 140 mm × 70 mm × 30 mm |
| Weight | 350 g |
| Operating temperature | 15–40°C |

### Hardware Architecture

**Cartridge**:
- Microfluidic polycarbonate card (85 mm × 54 mm × 2 mm)
- Sample inlet, capillary distribution channels
- Dried reagent pads per analyte zone
- Pre-printed carbon + Ag/AgCl electrodes for electrochemical zones
- Clear window for optical zones

**Reader Electronics**:
| Component | Specification |
|---|---|
| Potentiostat array | 8-channel LMP91000 array |
| Spectrophotometer | White LED + photodiode array, 3 wavelengths (450, 550, 620 nm) |
| Incubation heater | Resistive heater, 37°C ±0.5°C |
| Barcode scanner | 1D CCD linear scanner (cartridge lot, analyte encoding) |
| MCU | STM32H7 |
| BLE | nRF52840 |
| Display | ILI9486, 320×480 |
| Battery management | BQ25895 |

---

## 7.17 NFSIM-OXY-01 — Multi-Site Tissue Oxygenation Array

**Concept**: Near-infrared spectroscopy (NIRS) system that places multiple optodes across the body surface and continuously monitors regional tissue oxygen saturation (rSO₂) in underlying tissues. Unlike pulse oximetry (single arterial SpO₂), NIRS reports mixed venous-arterial tissue oxygenation, reflecting regional metabolic balance. Used in cardiac surgery monitoring (cerebral NIRS), muscle physiology, and sports science.

### Specifications

| Parameter | Value |
|---|---|
| Optode count | 4–8 independent channels |
| Wavelengths | 730 nm and 850 nm (±2 nm) |
| Measurement depth | 10–25 mm (brain/muscle) |
| Source-detector separation | 30–40 mm (deep tissue) + 10–15 mm (shallow reference) |
| Output | rSO₂ %, HbO₂ and HHb concentrations (µM·mm) |
| Sampling rate | 1 Hz per channel |
| Wireless | BLE 5.0 |
| Battery | 1000 mAh per optode module |
| Wireless range | 10 m |
| Dimensions | 35 mm × 15 mm per optode module |
| Waterproof | IPX4 |

### Hardware Architecture

**Optode Module**:
| Component | Specification |
|---|---|
| LED 1 | 730 nm, 5 mW, SMD |
| LED 2 | 850 nm, 5 mW, SMD |
| Photodiode | Si avalanche photodiode or OPT101 |
| LED modulation | 1 kHz chopping frequency, lock-in detection |
| Transimpedance amplifier | OPA2134, 10 MΩ feedback |
| Synchronous demodulator | AD630 or digital lock-in on MCU |
| MCU | STM32L4 (low power) |
| BLE radio | nRF52811 |
| Battery | CR2032 or 50 mAh LiPo |
| Adhesive base | Dual-layer: optically opaque outer, foam spacer, optode face |

**Modified Beer-Lambert Law Computation**:
`ΔHbO₂ = ε_HHb(λ₂)·ΔA(λ₁) - ε_HHb(λ₁)·ΔA(λ₂) / [ε_HbO₂(λ₁)·ε_HHb(λ₂) - ε_HbO₂(λ₂)·ε_HHb(λ₁)]·DPF·d`

Differential pathlength factor (DPF) applied per tissue type (brain ~6, muscle ~4).

---

## 7.18 NFSIM-BREATH-01 — Portable Breath Metabolomics Device

**Concept**: A handheld breath analysis device that captures exhaled breath condensate and/or VOCs and reports biomarker concentrations. Using an e-nose array of chemiresistors + photoacoustic spectroscopy for specific analytes (acetone, isoprene, ammonia, NOx). Designed for ketosis monitoring, metabolic health tracking, early infection detection, and asthma monitoring.

### Specifications

| Parameter | Value |
|---|---|
| Sampling mode | Single breath (5 sec exhale into device) |
| Primary analytes | Acetone, isoprene, ethanol, ammonia, H₂, CO, NOx |
| Detection technology | Photoacoustic spectroscopy (specific) + metal oxide chemiresistor array (broad) |
| Acetone range | 0.1–1000 ppm |
| Isoprene range | 10–2000 ppb |
| NH₃ range | 0.1–100 ppm |
| Sampling interval | On-demand |
| Warm-up time | 30 seconds |
| Connectivity | BLE, USB-C |
| Battery | 1200 mAh |
| Battery life | 200 measurements per charge |
| Dimensions | 100 mm × 55 mm × 30 mm |
| Weight | 180 g |

### Hardware Architecture

**Photoacoustic Spectroscopy Cell** (acetone-specific):
| Component | Specification |
|---|---|
| QCL or LED source | 3.4 µm (CH bond, ketone) or 8–9 µm (acetone absorption) |
| Acoustic cell | Helmholtz resonator, Q=50 |
| Microphone | MEMS, 60 dB SNR |
| Lock-in detection | Amplitude-modulated light source + synchronous demodulation |
| Gas cell | 10 mL volume, gold-lined reflection cell |

**Metal Oxide Sensor Array (broad-spectrum)**:
- 8× MOX sensors: SnO₂, ZnO, WO₃, TiO₂ variants
- Different dopants give different selectivity profiles
- Principal component analysis (PCA) → pattern recognition
- Pre-trained neural network (TinyML on MCU) → multi-analyte classification

**Sample Handling**:
- Hydrophobic Nafion membrane dehumidifier (removes water vapor which interferes with MOX)
- Micro-pump: 50 mL/min, diaphragm, draws breath through sensors
- Calibration gas capsule (CO₂/N₂ reference, sealed, good for 1000 measurements)

---

## 7.19 NFSIM-ECG-01 — Open Single-Lead ECG Patch

**Concept**: A chest-worn adhesive ECG patch providing continuous single-lead (modified Lead II) ECG recording for up to 30 days. Dry or hydrogel electrodes. BLE streaming to phone. Open firmware with AI arrhythmia detection running on-device or in cloud.

### Specifications

| Parameter | Value |
|---|---|
| Lead configuration | Single-lead (modified Lead II) |
| Electrode type | Dry AgZn or Ag/AgCl hydrogel |
| ADC resolution | 24-bit |
| Sampling rate | 256 or 512 Hz |
| Bandwidth | 0.05–150 Hz |
| CMRR | >100 dB |
| Input impedance | >10 MΩ |
| Wear duration | 14–30 days |
| Battery | 150 mAh LiPo |
| Connectivity | BLE 5.0 (streaming) + onboard 8 GB flash (logging) |
| Dimensions | 75 mm × 35 mm × 7 mm |
| Weight | 12 g |
| IP rating | IPX7 |
| AI on-device | AFib detection (sensitivity >97%), pause detection, bradycardia/tachycardia |

### Hardware Architecture

| Component | Specification |
|---|---|
| ECG AFE | ADS1291 (Texas Instruments), 24-bit, integrated lead-off detection |
| MCU | nRF52840 (BLE 5.0 + 64 MHz Cortex-M4F) |
| AI inference | TensorFlow Lite Micro (RR-interval AFib classifier, on-device) |
| Flash | W25Q64 (8 MB, 2-week continuous log at 256 Hz) |
| Battery | 150 mAh LiPo (21-day life at 1 Hz BLE advertising) |
| Charger | MCP73831, USB-C |
| RLD | Right leg drive via third electrode or software reference |
| Electrodes | Integrated AgZn dry electrodes on PCB surface + hydrogel pads |
| Housing | Flexible TPU overmold |
| NFC tag | For patient ID programming + passive data dump |

---

## 7.20 NFSIM-ECG-02 — 12-Lead Portable ECG Vest

**Concept**: A washable garment (vest or shirt) with embedded textile electrodes providing full 12-lead ECG equivalent. Designed for 24–48h ambulatory recording, sports physiology, and telemedicine. Electrode positions mapped to standard 12-lead anatomy.

### Specifications

| Parameter | Value |
|---|---|
| Leads | 12-lead equivalent (Wilson central terminal reference) |
| Electrode material | Silver-coated textile, conductive silicone pads |
| ADC | 24-bit, 8-channel |
| Sampling rate | 500 Hz |
| Electrode impedance | <200 kΩ (dry textile) |
| Recording module | Detachable electronics pod (waist clip) |
| Battery | 500 mAh |
| Battery life | 24–48h continuous |
| Storage | 32 GB microSD |
| Connectivity | BLE, USB-C |
| Garment sizes | XS–XXXL, male/female variants |
| Washable | Yes (remove electronics pod before washing) |

### Hardware Architecture

**Garment**:
- Medical-grade compression fabric base
- Silver-coated textile electrode pads at all 10 standard ECG positions (RA, LA, RL, LL, V1–V6)
- Snap connectors from textile electrodes to lead wires
- Lead wires: thin silver-coated nylon, routed inside fabric channels

**Electronics Pod**:
| Component | Specification |
|---|---|
| ECG AFE | ADS1298 (8-channel, 24-bit, for all limb + precordial leads simultaneously) |
| Drive circuit | Wilson central terminal + RLD |
| MCU | STM32H7 |
| BLE | nRF52840 coprocessor |
| Storage | 32 GB microSD |
| Battery | 500 mAh LiPo |
| Charger | USB-C, 5V |

---

## 7.21 NFSIM-EEG-01 — Dry-Electrode Open EEG Headset

**Concept**: A wearable EEG headset with dry electrodes (no conductive gel required). 8–16 channels in standard 10-20 positions. Open-source based on OpenBCI Cyton architecture. Suitable for neurofeedback, BCI research, sleep staging, and meditation monitoring.

### Specifications

| Parameter | Value |
|---|---|
| Electrode count | 8 or 16 channels |
| Electrode type | Spring-loaded gold-tipped dry electrodes |
| Electrode impedance | <50 kΩ (acceptable for dry) |
| ADC resolution | 24-bit |
| Sampling rate | 250 or 500 Hz |
| Bandwidth | 0.5–100 Hz |
| CMRR | >100 dB |
| Reference | Ear clip or CZ |
| Wireless | BLE + 2.4 GHz proprietary (OpenBCI-compatible dongle) |
| Battery | 500 mAh |
| Battery life | 6–8 hours |
| Compatible software | OpenBCI GUI, BrainFlow SDK, Neurosity, EEGLAB |
| Dimensions | Standard EEG cap (various sizes 54–60 cm) |
| Weight | 180 g |

### Hardware Architecture

| Component | Specification |
|---|---|
| EEG AFE | ADS1299 (8-channel, 24-bit, PGA, matched to OpenBCI Cyton) |
| Electrode drive | Bias drive for active electrodes |
| MCU | PIC32MX (OpenBCI Cyton compatible) or STM32 variant |
| Wireless | RFduino (OpenBCI Cyton) or nRF52840 |
| Battery | 500 mAh LiPo |
| Expansion | Daisy module connector (×2 boards = 16 channels) |
| Electrode design | Gold-plated spring pins, 20 mm length, adjustable headset arms |

---

## 7.22 NFSIM-EMG-01 — Multi-Channel Surface EMG Armband

**Concept**: An 8-channel surface EMG armband worn around the forearm. Designed for gesture recognition (prosthetic control, HCI), muscle fatigue monitoring, and rehabilitation feedback. Inspired by the Myo armband, but fully open-source.

### Specifications

| Parameter | Value |
|---|---|
| Channels | 8 bipolar EMG channels |
| Electrode spacing | 45° radial, evenly distributed around forearm |
| Electrode type | Dry Ag or conductive silicone |
| ADC resolution | 16-bit |
| Sampling rate | 1000 Hz |
| Bandwidth | 20–500 Hz |
| Gain | 60–80 dB |
| IMU | 9-axis (3-axis accel + gyro + mag) |
| Wireless | BLE 5.0 |
| Battery | 150 mAh |
| Battery life | 8 hours continuous |
| Gesture recognition | 6+ standard gestures, TinyML on-device |
| Armband size | Adjustable, 200–400 mm circumference |
| Weight | 90 g |

### Hardware Architecture

| Component | Specification |
|---|---|
| EMG AFE | ADS1298 (8-channel, 24-bit, internal PGA 1–12×) |
| Band-pass filter | 20–500 Hz hardware Butterworth |
| MCU | nRF52840 (Cortex-M4F, TensorFlow Lite Micro) |
| IMU | LSM9DS1 or BNO055 |
| Gesture ML | Lightweight 1D CNN, trained on NinaPro dataset |
| Battery | 150 mAh LiPo |
| Charger | USB-C, wireless Qi option |
| Housing | Flexible TPU band with rigid electrode pods |

---

## 7.23 NFSIM-NEURAL-01 — Open High-Density ECoG Research Array

**Concept**: An open-source high-density electrocorticography (ECoG) array designed for research use (acute animal, chronic NHP, or human intraoperative under neurosurgeon supervision). Provides 64–256 channels of cortical surface recording with high spatial resolution (1–5 mm inter-electrode spacing).

### Specifications

| Parameter | Value |
|---|---|
| Electrode count | 64–256 |
| Array geometry | Flexible 8×8, 16×8, or custom grid |
| Electrode material | Platinum-iridium or PEDOT-coated |
| Electrode diameter | 1–3 mm |
| Inter-electrode spacing | 2–5 mm |
| Substrate | Parylene-C flexible film, 5–15 µm thick |
| ADC resolution | 16-bit |
| Sampling rate | 30,000 Hz (spike band) or 1000 Hz (LFP band) |
| Bandwidth | 0.3 Hz – 10 kHz |
| CMRR | >80 dB |
| Data interface | SPI or LVDS to acquisition system |
| Acquisition system | Open Ephys compatible (Intan RHD2000 series) |
| Sterilization | EtO or autoclave (flexible array) |

### Hardware Architecture

**Flexible Array**:
- Parylene-C base substrate (biocompatible, MRI-compatible)
- Electrodeposited Pt-Ir or sputtered TiN electrodes
- PEDOT:PSS electroplating option (lowers impedance, improves biocompatibility)
- Gold trace interconnects in Parylene
- ZIF (Zero Insertion Force) connector to rigid PCB interface

**Acquisition Headstage**:
| Component | Specification |
|---|---|
| Amplifier ASIC | Intan RHD2132 (32-ch, 16-bit, SPI) × 8 = 256 channels |
| ADC | Integrated in RHD2132 (24.4 kSPS per channel) |
| Multiplexer | 256-to-256 routing matrix |
| FPGA | Xilinx Spartan-7 (data aggregation + SPI → USB) |
| Connector to array | 256-pin ZIF, 0.3 mm pitch |
| Power | ±2.5V analog, 3.3V digital |

**Software**:
- Open Ephys plugin (native compatibility)
- Spike sorting: Kilosort 2/3 (open source)
- LFP analysis: MNE-Python compatible output

---

## 7.24 NFSIM-CAP-01 — Capsule: Ingestible Imaging + Chemical Sensor

**Concept**: A swallowable capsule combining:
1. Optical imaging (white-light camera, similar to PillCam)
2. Chemical sensing (pH, temperature, dissolved O₂)
3. GI position tracking

The capsule images at 2–4 fps, continuously logs chemistry, and transmits wirelessly to an external recorder belt. All data streams into NanoFlowSIM anchored to GI anatomy by position estimate.

### Specifications

| Parameter | Value |
|---|---|
| Dimensions | 26 mm × 11 mm |
| Camera | OV7251 (1/7" CMOS), 640×480, wide-angle (170°) |
| Frame rate | 2–4 fps (dual-head: anterior + posterior) |
| Illumination | White LED array (4× SMD LEDs) |
| pH sensor | ISFET (Ion-Sensitive FET), range 1–9 |
| Temperature | NTC thermistor, ±0.1°C |
| Dissolved O₂ | Optical luminescence quenching (ruthenium dye) |
| Wireless | 434 MHz or 915 MHz FSK |
| Battery | Silver oxide SR44, 150 mAh |
| Battery life | 8–12 hours (full GI transit) |
| Data rate | 1 Mbps image stream |
| Position estimate | Pressure + accelerometer + time-elapsed algorithm |
| Biocompatible shell | PEEK or Ultem 9085 |
| Transit time | 24–36 hours (natural) |

### Hardware Architecture

**Optical Subsystem**:
| Component | Specification |
|---|---|
| Image sensor | OV7251, MIPI interface, 1/7" format |
| Lens | 1.7mm FL, 170° FOV, F2.0, fixed focus |
| Illumination | 4× PLCC2 white LED, 120 mW total |
| Image compression | JPEG hardware encoder (on-chip or ASIC) |
| Dual-head option | 2× camera PCBs (head + tail) for bidirectional view |

**Chemical Sensors**:
| Sensor | Technology |
|---|---|
| pH ISFET | Si-based ISFET with SiO₂/Si₃N₄ gate |
| Temperature | NTC 10kΩ thermistor |
| Dissolved O₂ | Optical luminescence quenching (Ru(II) complex dye) with blue LED + photodetector |

**System MCU**:
- Ultra-low-power ARM Cortex-M0+ (STM32L0 or SAMD21)
- Deep sleep between frames: duty cycle 95%+ sleep
- Task sequencing: wake → capture image → read sensors → compress → transmit → sleep

**Wireless Transmission**:
- 434 MHz FSK, 500 kbps
- Omnidirectional ceramic chip antenna
- RSSI-based position refinement (multiple external antennas on belt)

**External Receiver**:
- 8-channel antenna belt (disposable patches)
- SDR-based receiver (RTL-SDR or CC1101) → USB → laptop/phone
- NanoFlowSIM NFS-CAP data format: `{timestamp, position_zone, frame_jpg_b64, pH, temp_C, DO_pct}`

---

## 7.25 NFSIM-CAP-02 — Capsule: GI Ultrasound Capsule

**Concept**: Ingestible capsule with radially-firing CMUT ultrasound array. Images GI wall cross-sections (360° radial scan) at each position during transit, providing acoustic cross-sections of the intestinal wall layers (mucosa, submucosa, muscularis, serosa/adventitia) and nearby organs. This is mini-endoscopic ultrasound (mini-EUS) without a scope.

### Specifications

| Parameter | Value |
|---|---|
| Dimensions | 32 mm × 13 mm |
| Transducer | CMUT ring array, 64 elements, circumferential |
| Frequency | 10–20 MHz |
| Imaging geometry | 360° radial cross-section |
| Wall penetration | 5–30 mm |
| Axial resolution | 75–150 µm |
| Frame rate | 1 frame/position (triggered by motion) |
| Acoustic coupling | Saline-filled balloon (silicone, inflated on capsule) |
| Wireless | 434 MHz, compressed scan data |
| Battery | 300 mAh primary lithium |
| Battery life | 24 hours |
| Biocompatibility | ISO 10993 compliant materials |

### Hardware Architecture

**Acoustic System**:
| Component | Specification |
|---|---|
| CMUT array | 64-element ring, 10 mm diameter, MEMS-fabricated on Si |
| Coupling balloon | Medical silicone balloon, saline-filled by swallowing with water |
| Pulser | Miniaturized HV pulser ASIC, ±30V, 64-channel |
| Receiver | Low-noise TIA, 64-channel multiplexed readout |
| Beam reconstruction | Delay-and-sum in FPGA for radial reconstruction |

**Position Correlation**:
As capsule traverses GI tract:
- Accelerometer records motion profile
- Each ultrasound frame tagged with position estimate
- External position tracking via RF belt refines estimate
- NanoFlowSIM anchors each cross-sectional frame to GI anatomical zone (duodenum, ileum, etc.)

---

## 7.26 NFSIM-CAP-03 — Capsule: DNA/RNA Capture Capsule

**Concept**: A capsule designed to traverse the GI tract and capture luminal DNA/RNA from specific segments (small intestine mucosal shedding, colonic microbiome). The capsule opens a sterile chamber in a target zone (triggered by pH, temperature, or time-elapsed logic), fills with luminal contents, reseals, and is retrieved after natural passage. Captured sample undergoes metagenomic sequencing on the NFSIM-SEQ-01 or sent to a sequencing lab.

### Specifications

| Parameter | Value |
|---|---|
| Dimensions | 26 mm × 11 mm (closed) |
| Capture volume | 0.1–1 mL luminal fluid |
| Opening trigger | pH-triggered (pH >6.5 → small intestine) OR time-elapsed OR manual RF command |
| Sealing mechanism | Wax-plug thermal resealing (nichrome wire melt) OR snap-close spring |
| Sample preservation | RNAlater-equivalent stabilizer pre-loaded in chamber |
| Wireless | 434 MHz (TX-only: position + status, confirms open/close events) |
| Battery | SR44 silver oxide (passive operation, minimal) |
| Temperature log | NTC thermistor during transit (cold chain verification) |
| Retrieval | Natural passage; stool retrieval via strainer/bag kit |
| Sterility | Pre-sterilized by EtO gas |

### Hardware Architecture

**Capture Chamber**:
| Component | Specification |
|---|---|
| Chamber material | Medical-grade PEEK |
| Inlet filter | 20 µm pore nylon mesh (blocks food particles) |
| Wax plug | n-eicosane (melts at 36.7°C) behind nichrome wire trigger |
| Actuator | 10 mA nichrome wire (melt-open); shape-memory alloy wire (mechanical close) |
| Stabilizer | Pre-loaded dried RNAlater (reconstitutes with luminal fluid) |

**pH Trigger Circuit**:
- Sacrificial pH-sensitive polymer coating on inlet port
- Dissolves at pH >6.5 (proximal small intestine) — passive, no power required
- Optional: ISFET pH sensor + microcontroller-controlled valve actuator

**Target Applications**:
- GI microbiome profiling (site-specific: duodenum vs. colon)
- Mucosal gene expression (shed epithelial cell RNA)
- GI infection pathogen identification
- Celiac disease, IBD, IBS biomarker discovery

---

## 7.27 NFSIM-CAP-04 — Capsule: Full Multi-Modal Research Capsule

**Concept**: A research-grade ingestible capsule combining ALL sensing modalities in a single 32 mm × 13 mm form factor:
- Optical imaging (dual-head white light cameras)
- Ultrasound (radial CMUT array)
- Chemical sensing (pH, DO₂, temperature, glucose)
- Electrical (contact bioimpedance of GI wall)
- Position tracking (pressure, IMU, RF)
- DNA/RNA capture (triggered capture chamber)
- Drug release (programmable payload delivery)

### Specifications

| Parameter | Value |
|---|---|
| Dimensions | 32 mm × 13 mm |
| Cameras | 2× OV7251 (anterior + posterior) |
| Ultrasound | CMUT 64-element ring, 15 MHz |
| Chemical sensors | pH ISFET, NTC, O₂ optical, glucose enzymatic |
| Bioimpedance | 4-electrode, 1 kHz–1 MHz sweep |
| IMU | BMA456 + BMI088 |
| Capture chamber | 0.5 mL, pH-triggered opening |
| Drug payload | 100 µL reservoir, pressure-triggered or RF-triggered release |
| Wireless | 434 MHz + 2.4 GHz dual-radio |
| Battery | 300 mAh primary Li-MnO₂ |
| Battery life | 36 hours |
| Data onboard | 256 MB NAND flash backup |
| Biocompatibility | Full ISO 10993 |

This capsule is the most complex variant and intended for:
- Research into GI disease
- Drug delivery verification studies
- Comprehensive GI physiological mapping
- AI training dataset generation for GI diagnostics

---

## 7.28 NFSIM-FLOW-01 — Portable Cytometry / Cell Counter

**Concept**: A portable flow cytometer capable of counting and classifying blood cells (CBC proxy) and optionally detecting specific surface markers (2–3 fluorescence channels) from a 10 µL blood sample. Uses acoustic cell focusing (eliminates sheath fluid) and LED + photodiode detection.

### Specifications

| Parameter | Value |
|---|---|
| Sample type | Whole blood or PBS-diluted cell suspension |
| Sample volume | 10–50 µL |
| Cell throughput | 1000–5000 cells/sec |
| Focusing method | Acoustic (piezoelectric actuator) |
| Laser/LED | 405 nm + 488 nm + 638 nm LEDs |
| Fluorescence channels | 2–3 (FITC, PE, APC or equivalent) |
| Forward/side scatter | Yes |
| CBC output | WBC, RBC, Hgb (proxy), PLT estimate |
| Time to result | 3–5 min |
| Connectivity | USB-C, BLE |
| Battery | 2000 mAh |
| Dimensions | 150 mm × 80 mm × 60 mm |
| Weight | 400 g |
| Disposable | Microfluidic chip cartridge, single-use |

### Hardware Architecture

**Fluidics**:
| Component | Specification |
|---|---|
| Microfluidic chip | PDMS or polycarbonate, 50 µm × 50 µm channel |
| Acoustic focuser | Piezo actuator at side of chip (bulk acoustic wave) |
| Micro-pump | Peristaltic or syringe, 5–50 µL/min |
| Waste collection | Onboard reservoir |

**Optical Detection**:
| Component | Specification |
|---|---|
| LEDs (×3) | 405, 488, 638 nm |
| Beam collimation | Aspheric collimating lens |
| Interrogation point | 50 µm focused spot on flow channel |
| FSC detector | Si PIN photodiode |
| SSC detector | Si PIN photodiode, 90° |
| FL detectors (×3) | PMT or SiPM, bandpass filter per channel |

**Signal Processing**:
- Pulse detection per event (FSC threshold trigger)
- Pulse height, width, area extracted per channel
- On-device cell classification: decision tree + KNN model for CBC
- Reports: scatter plot, histogram, CBC with differential

---

## 7.29 NFSIM-ENV-01 — Environmental Bio-Aerosol Sampler

**Concept**: A portable device that continuously samples ambient air, collects bio-aerosols (airborne bacteria, viruses, pollen, fungal spores), concentrates them onto a collection substrate, and prepares them for on-site LAMP/PCR or sequencing analysis. Deployable for environmental surveillance, outbreak response, or air quality genomics.

### Specifications

| Parameter | Value |
|---|---|
| Air flow rate | 100–500 L/min |
| Collection method | Cyclone separator + wet scrubber or impinger |
| Collection efficiency | >90% for particles >1 µm |
| Collection time | 15 min – 8 hours (continuous) |
| Eluent volume | 1–5 mL |
| Downstream analysis | LAMP (NFSIM-PCR-03) or nanopore (NFSIM-SEQ-01) |
| Power | 12V DC (car socket, solar, or wall) |
| Battery backup | 4h at full flow |
| Connectivity | BLE (operation) + USB (eluent volume log) |
| Dimensions | 300 mm × 200 mm × 150 mm |
| Weight | 2.5 kg |

### Hardware Architecture

**Aerosol Collection**:
| Component | Specification |
|---|---|
| Inlet | Omnidirectional rain-shielded probe |
| PM10 impactor | Removes particles >10 µm |
| Cyclone concentrator | Wet wall, 1 L aqueous buffer |
| Circulation pump | 300 L/min brushless motor |
| Filter backup | 0.1 µm PTFE (if wet collection fails) |
| UV-C sterilization | Pre/post chamber options |

**Monitoring + Control**:
- CO₂ sensor (Sensirion SCD40)
- PM2.5 OPC (Sensirion SPS30)
- Temperature/humidity/pressure (BME280)
- MCU: STM32 for flow control + BLE data logging
- Autosampler: transfers eluent to PCR tube at programmable interval

---

## 7.30 NFSIM-MICRO-01 — Portable Digital Microscope (Pathology)

**Concept**: A portable compound brightfield/fluorescence microscope producing pathology-quality images. Uses a high-resolution CMOS sensor, LED illumination with filter cube turret (brightfield + FITC + TRITC), motorized focus, and AI-assisted cell counting/classification. Outputs TIFF/SVS format for NanoFlowSIM import.

### Specifications

| Parameter | Value |
|---|---|
| Optical magnification | 10×, 20×, 40× objectives |
| Digital magnification | 0.5×–4× digital zoom |
| Image sensor | IMX477 (12.3 MP, 1/2.3") |
| Effective resolution | 0.25 µm/px at 40× |
| FOV at 40× | 0.5 mm × 0.4 mm |
| Illumination | Köhler LED (brightfield), 470 nm + 530 nm LEDs (fluorescence) |
| Filter turret | 4-position: BF, FITC, TRITC, empty |
| Focus drive | Stepper motor, 0.1 µm step size |
| Stage | Manual XY with scale bar; motorized option |
| Connectivity | USB-C 3.1 |
| Whole slide option | Motorized XY + Z auto-focus tiling |
| AI | Cell counting, mitosis detection, WBC differential, parasite ID |
| Power | USB-C or 12V DC |
| Dimensions | 280 mm × 180 mm × 350 mm |
| Weight | 3.5 kg |

### Hardware Architecture

| Component | Specification |
|---|---|
| IMX477 camera | 12.3 MP, 1.55 µm pixel, CSI-2 interface |
| Camera driver | Raspberry Pi HQ camera module compatible |
| Compute | Raspberry Pi 4B or Jetson Nano (AI inference) |
| LED driver | Constant current, PWM intensity control |
| Filter cube | Chroma or Edmund Optics standard epi-fluorescence cubes |
| Z-focus stepper | NEMA8, 200 step/rev, 0.5 mm lead screw |
| Stepper driver | A4988 or TMC2209 |
| Brightfield condenser | Abbe condenser, NA 0.9 |
| Objective turret | 3-position manual turret |
| Stage | 120 mm × 80 mm travel |
| Housing | Aluminum extrusion frame |

---

# 8. Communication Protocol Specification

All NanoFlowSIM hardware devices share a common data format to ensure interoperability.

## 8.1 Physical Layer Options

| Layer | Protocol | When Used |
|---|---|---|
| Wireless (primary) | BLE 5.0 GATT | Wearables, patches, portable devices |
| Wireless (high-BW) | Wi-Fi 802.11ac | Ultrasound, OCT, large imaging streams |
| Wireless (body-area) | 434 MHz FSK | Ingestible capsules (body penetration) |
| Wired | USB-C 3.1 | Lab devices, sequencers, ultrasound probe |
| Short-range | NFC (ISO 15693) | CGM passive readout, implant configuration |

## 8.2 BLE GATT Services (NFS Profile)

### Device Information Service (0x180A)
Standard BLE Device Info:
- Manufacturer Name: "NanoFlowSIM"
- Model Number: e.g., "NFSIM-ECG-01"
- Hardware Revision
- Firmware Revision
- Serial Number

### NFS Device Control Service (UUID: 4a6e-1000-...)
| Characteristic | UUID Suffix | Properties | Description |
|---|---|---|---|
| Device State | ...0001 | Read/Notify | Enum: Idle, Measuring, Error, Calibrating |
| Command | ...0002 | Write | Start, Stop, Calibrate, Reset, Configure |
| Configuration | ...0003 | Read/Write | JSON blob, device parameters |
| Error Status | ...0004 | Read/Notify | Error code + description |

### NFS Data Stream Service (UUID: 4a6e-2000-...)
| Characteristic | UUID Suffix | Properties | Description |
|---|---|---|---|
| Primary Stream | ...0001 | Notify | Main data (ECG samples, glucose, etc.) |
| Secondary Stream | ...0002 | Notify | Secondary data (temperature, accelerometer) |
| Batch Upload | ...0003 | Indicate | Historical data dump (large blocks) |
| Stream Config | ...0004 | Write | Sample rate, channel selection |

### NFS Metadata Service (UUID: 4a6e-3000-...)
| Characteristic | UUID Suffix | Properties | Description |
|---|---|---|---|
| Patient ID | ...0001 | Write | Link device to patient profile |
| Anatomical Tag | ...0002 | Write | UBERON body region code |
| Session ID | ...0003 | Read/Write | UUID for this recording session |
| Timestamp Sync | ...0004 | Write | Unix timestamp for synchronization |

## 8.3 Data Packet Format

All data transmitted by NFS devices uses JSON-encoded payloads:

### Generic Packet Structure
```json
{
  "nfs_version": "1.0",
  "device_id": "NFSIM-ECG-01-A3F2",
  "session_id": "uuid-...",
  "patient_id": "hashed-patient-id",
  "timestamp_unix": 1700000000.123,
  "sequence": 4201,
  "anatomy_region": "UBERON:0000948",
  "data_type": "ecg_waveform",
  "data": { ... },
  "quality": 0.97,
  "device_status": "measuring",
  "battery_pct": 82
}
```

### Domain-Specific Data Payloads

**ECG**:
```json
"data": {
  "lead": "II",
  "sample_rate_hz": 256,
  "samples_mv": [0.12, 0.14, 0.87, 1.23, ...],
  "rr_intervals_ms": [812, 815, 810],
  "hr_bpm": 73,
  "afib_probability": 0.02
}
```

**Glucose (CGM)**:
```json
"data": {
  "glucose_mg_dl": 112,
  "glucose_mmol": 6.2,
  "trend": "stable",
  "rate_of_change_mg_dl_per_min": -0.2,
  "sensor_temperature_c": 36.8,
  "calibration_age_h": 2.3
}
```

**Sequencing (nanopore)**:
```json
"data": {
  "run_id": "uuid-...",
  "read_id": "uuid-...",
  "channel": 142,
  "start_time": 1700000000.0,
  "raw_signal_pA": [85.2, 84.9, 100.3, ...],
  "basecall_status": "complete",
  "sequence": "ATCGATCG...",
  "quality_phred": [30, 28, 35, ...]
}
```

**Capsule Position + Chemistry**:
```json
"data": {
  "position_zone": "small_intestine_jejunum",
  "position_confidence": 0.78,
  "transit_time_min": 185,
  "pH": 7.2,
  "temperature_c": 37.1,
  "dissolved_o2_pct": 12.3,
  "pressure_mmhg": 18.4,
  "image_frame_id": "uuid-..."
}
```

## 8.4 USB Command Set (for USB-C devices)

Devices expose a virtual serial port (USB CDC-ACM, 115200 baud or USB bulk for high-speed):

| Command | Parameters | Response |
|---|---|---|
| `NFS:PING` | — | `NFS:PONG:NFSIM-PCR-01:v1.2.0` |
| `NFS:START` | session_id, patient_id | `NFS:OK` |
| `NFS:STOP` | — | `NFS:OK:SESSION_SAVED` |
| `NFS:CONFIGURE` | JSON config blob | `NFS:OK` or `NFS:ERR:...` |
| `NFS:STATUS` | — | JSON status packet |
| `NFS:CALIBRATE` | calibrant_id | `NFS:CALIBRATING` + streaming status |
| `NFS:DUMP` | start_time, end_time | Binary stream of historical data |
| `NFS:UPDATE` | — | Initiates OTA firmware update mode |

---

# 9. Firmware Architecture — Universal

All NFS devices share the following architectural patterns regardless of domain.

## 9.1 RTOS Selection

| Device Class | RTOS / Runtime |
|---|---|
| Resource-constrained (nRF52, STM32L4) | FreeRTOS or Zephyr RTOS |
| Mid-power (STM32F4, STM32H7) | FreeRTOS |
| High-compute (FPGA + ARM) | Bare-metal FPGA + FreeRTOS on ARM |
| Linux-capable (Raspberry Pi, Jetson) | Buildroot Linux + systemd services |

## 9.2 Universal Task Architecture

```
┌─────────────────────────────────────────────────┐
│                  NFS Firmware                   │
├───────────────┬─────────────────────────────────┤
│  Sensor Task  │  Priority: HIGHEST              │
│               │  Rate: domain-specific          │
│               │  Function: raw data acquisition │
├───────────────┼─────────────────────────────────┤
│  Process Task │  Priority: HIGH                 │
│               │  Rate: per data batch           │
│               │  Function: filtering, feature   │
│               │  extraction, on-device AI       │
├───────────────┼─────────────────────────────────┤
│  Comms Task   │  Priority: MEDIUM               │
│               │  Rate: triggered or periodic    │
│               │  Function: BLE/USB/RF TX/RX     │
├───────────────┼─────────────────────────────────┤
│  Storage Task │  Priority: MEDIUM-LOW           │
│               │  Rate: triggered by buffer full │
│               │  Function: flash write          │
├───────────────┼─────────────────────────────────┤
│  System Task  │  Priority: LOW                  │
│               │  Rate: 1 Hz                     │
│               │  Function: battery, temp,       │
│               │  watchdog, status               │
├───────────────┼─────────────────────────────────┤
│  OTA Task     │  Priority: LOWEST               │
│               │  Rate: triggered                │
│               │  Function: firmware update      │
└───────────────┴─────────────────────────────────┘
```

## 9.3 Memory Map (Example: STM32H743)

| Region | Size | Content |
|---|---|---|
| FLASH Sector 0 | 128 KB | Bootloader |
| FLASH Sectors 1–6 | 768 KB | Application firmware |
| FLASH Sector 7 | 128 KB | OTA staging area |
| RAM1 (512 KB) | 512 KB | Main RAM (stack, heap, FreeRTOS) |
| RAM2 (128 KB) | 128 KB | DMA buffers, sensor ring buffer |
| SPI Flash (external) | 16 MB | Configuration, session log, protocols |

## 9.4 Bootloader

All NFS devices implement a two-stage boot:
1. **Stage 1** (16 KB, ROM-resident): checks Stage 2 signature, enters DFU if button held
2. **Stage 2** (bootloader, 112 KB flash): validates application CRC, supports USB DFU and BLE OTA update

## 9.5 Configuration Storage (NVS)

All device configuration stored as JSON in SPI NOR flash, organized as:
```json
{
  "device_serial": "NFSIM-ECG-01-A3F2",
  "patient_id": null,
  "sample_rate_hz": 256,
  "ble_name": "NFSIM-ECG-A3F2",
  "calibration": { "gain": 1.0, "offset": 0.0, "last_cal_unix": 0 },
  "power_mode": "normal",
  "alert_thresholds": { "hr_high": 150, "hr_low": 40 }
}
```

## 9.6 On-Device AI (TinyML)

Several NFS devices run inference on-device:
- **NFSIM-ECG-01**: AFib detection (5-minute RR interval feature classifier, ~20 KB model)
- **NFSIM-EEG-01**: Sleep stage classifier (EEG band power features, 30-second epoch, ~40 KB model)
- **NFSIM-EMG-01**: Gesture classifier (6-class 1D CNN, ~50 KB model)
- **NFSIM-BREATH-01**: VOC pattern classifier (e-nose PCA + neural net, ~30 KB model)
- **NFSIM-CRISPR-01**: Fluorescence curve classification (amplification curve shape, ~15 KB model)

Framework: TensorFlow Lite Micro (no dynamic allocation)
Quantization: INT8 post-training quantization

---

# 10. Software Architecture

## 10.1 Desktop Application

### Technology Stack
- Framework: Electron 28 (Chromium + Node.js)
- Frontend: React 18 + TypeScript + Tailwind CSS
- 3D rendering: Three.js or Babylon.js (WebGL)
- State management: Zustand
- Database: SQLite (via better-sqlite3) for local data
- BLE: noble-winrt (Windows) / noble (macOS/Linux)
- USB serial: serialport npm package
- DICOM: cornerstone.js + dicom-parser
- FHIR: @medplum/fhirkit

### Architecture

```
/desktop
├── /src
│   ├── /main              # Electron main process
│   │   ├── main.ts        # App entry, window management
│   │   ├── preload.ts     # Secure contextBridge IPC
│   │   ├── ble.ts         # BLE device management
│   │   ├── usb.ts         # USB device management
│   │   ├── store.ts       # electron-store (settings)
│   │   └── updater.ts     # Auto-updater (electron-updater)
│   ├── /renderer          # React frontend
│   │   ├── /components
│   │   │   ├── BodyMap3D.tsx         # Three.js 3D body
│   │   │   ├── RegionPanel.tsx       # Region detail overlay
│   │   │   ├── LiveFeed.tsx          # Real-time sensor data
│   │   │   ├── Timeline.tsx          # Historical scrubber
│   │   │   ├── SimulationPanel.tsx   # NanoFlowSIM launcher
│   │   │   ├── GenomicsBrowser.tsx   # Variant viewer
│   │   │   ├── DicomViewer.tsx       # DICOM display
│   │   │   └── DevicePanel.tsx       # Connected devices
│   │   ├── /views
│   │   │   ├── ConsumerDashboard.tsx
│   │   │   ├── ProfessionalDashboard.tsx
│   │   │   ├── SimulationWorkspace.tsx
│   │   │   └── Settings.tsx
│   │   ├── /store         # Zustand slices
│   │   ├── /hooks         # Custom React hooks
│   │   └── /utils
├── /assets                # Icons, 3D body mesh (GLTF)
├── package.json
└── electron-builder.json
```

### 3D Body Model
- Base mesh: Open-source human anatomy (MBLabstudio, CC0 licensed)
- Format: GLTF 2.0 with morph targets for body shape variants
- Anatomical annotation: UBERON ontology region IDs mapped to mesh face groups
- Rendering: PBR materials, subsurface scattering for skin realism
- Interaction: Raycasting from mouse click to UBERON region identification

### DICOM Processing Pipeline
1. User drops DICOM folder
2. DicomParser extracts series/studies/metadata
3. Cornerstone.js renders 2D slices
4. Optional: call Python subprocess (ITK-SNAP / SimpleITK) for 3D reconstruction
5. Output: NIfTI volume or surface mesh (STL/OBJ) for Three.js rendering
6. Auto-tag region from DICOM BodyPartExamined + PatientPosition tags

## 10.2 Mobile Application

### Technology Stack
- Framework: React Native 0.73 + Expo SDK 50
- Navigation: Expo Router (file-based)
- 3D: React Native Three Fiber (Three.js on RN)
- BLE: react-native-ble-plx
- NFC: react-native-nfc-manager
- Camera: expo-camera (for barcode / QR scanning of reagent cartridges)
- Storage: expo-secure-store (sensitive), AsyncStorage (general)
- Push notifications: expo-notifications

### Key Features
- BLE device scanner and management
- NFC tap-to-read CGM or implant NFC
- Camera: scan QR on reagent cartridges to import lot info
- 3D body map (simplified mesh, touch-to-select region)
- Live sensor graphs
- Alert and notification center
- Offline data logging (syncs to desktop or cloud when available)
- AR overlay (ARKit/ARCore): project body map on camera feed

## 10.3 Web Dashboard

- Framework: React 18 + TypeScript (Create React App)
- Purpose: Cloud-accessible patient portal, research interface, multi-patient cohort view
- Authentication: Auth0 or Keycloak (OAuth2 + OIDC)
- Backend: Django 5 REST API (DRF) + Celery + PostgreSQL + Redis
- FHIR server: HAPI FHIR or Medplum embedded
- Real-time: Django Channels (WebSocket) for live sensor relay
- File storage: MinIO (DICOM, FASTQ, large files)

### API Endpoints

```
/api/v1/patients/                    GET, POST
/api/v1/patients/{id}/               GET, PATCH, DELETE
/api/v1/patients/{id}/data/          GET (all data, filterable)
/api/v1/patients/{id}/regions/       GET (regions with data)
/api/v1/patients/{id}/regions/{uberon}/ GET (region-specific data)
/api/v1/patients/{id}/simulations/   GET, POST
/api/v1/patients/{id}/import/fhir/   POST (FHIR bundle)
/api/v1/patients/{id}/import/dicom/  POST (DICOM files)
/api/v1/patients/{id}/import/vcf/    POST (genomic VCF)
/api/v1/devices/                     GET (authorized devices)
/api/v1/devices/{id}/stream/         WS (live data stream)
/api/v1/simulations/                 GET, POST
/api/v1/simulations/{id}/results/    GET
/api/v1/research/cohort/             GET (aggregate, de-identified)
```

## 10.4 SDK

Published as open-source libraries:

**Python SDK** (`nfsim-sdk`):
```python
from nfsim import NFSIMClient, Patient, Device, Region

client = NFSIMClient(api_key="...", server="https://api.nfsim.io")
patient = client.get_patient("patient-id")
data = patient.get_region_data(region="UBERON:0000948", 
                               data_types=["ecg", "lab"],
                               start="2024-01-01", 
                               end="2024-12-31")
device = Device.connect_ble("NFSIM-ECG-01-A3F2")
device.start_stream(callback=lambda pkt: patient.ingest(pkt))
```

**Node.js SDK** (`@nfsim/sdk`):
```javascript
import { NFSIMClient } from '@nfsim/sdk';
const client = new NFSIMClient({ apiKey: '...' });
const stream = await client.device('NFSIM-ECG-01-A3F2').connect();
stream.on('data', async (packet) => {
  await client.patient('patient-id').ingest(packet);
});
```

**Rust SDK** (`nfsim-client`):
```rust
let client = NfsimClient::new("https://api.nfsim.io", api_key);
let stream = client.device("NFSIM-ECG-01-A3F2").ble_connect().await?;
stream.subscribe(|packet| client.patient(pid).ingest(packet)).await;
```

## 10.5 AI/ML Layer

### On-Device (TinyML)
- Runs on device MCU/FPGA
- Models: <100 KB, INT8 quantized
- Tasks: anomaly detection, alert triggering, gesture recognition, arrhythmia detection

### Edge (Desktop/Local)
- Runs on patient's local machine
- Models: up to 500 MB
- Tasks: basecalling (nanopore), DICOM segmentation, genomic variant annotation
- Framework: PyTorch (local), ONNX Runtime

### Cloud (Optional, Privacy-Preserving)
- Federated learning: model training on local data, gradients only shared
- Differential privacy: Gaussian noise addition to gradients
- Tasks: population-level pattern discovery, simulation optimization

### NanoFlowSIM Simulation Engine (Rust Backend)
- Core simulation: Monte Carlo + agent-based + pharmacokinetic modeling
- API: gRPC for internal communication, REST for frontend
- Scaling: single process to HPC cluster
- Output: JSON results + 3D trajectory data (Protobuf binary)
- Visualization: particle data exported to Three.js / Babylon.js renderers

---

# 11. Monorepo Directory Structure — Complete

```
/nanoflowsim/
├── README.md                          # This document
├── LICENSE                            # MIT (software) + CERN OHL v2 (hardware)
├── CONTRIBUTING.md
├── CHANGELOG.md
├── .github/
│   ├── workflows/
│   │   ├── ci-firmware.yml
│   │   ├── ci-software.yml
│   │   ├── ci-hardware-drc.yml       # KiCad DRC check
│   │   └── release.yml
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
│
├── /hardware/                         # All electronic hardware
│   ├── /NFSIM-PCR-01/
│   │   ├── /schematic/               # KiCad .kicad_sch
│   │   ├── /pcb/                     # KiCad .kicad_pcb
│   │   ├── /gerbers/                 # Manufacturing output
│   │   ├── /bom/                     # BOM.csv
│   │   ├── /assembly/                # Pick & place, assembly drawing
│   │   ├── /simulation/              # LTspice thermal sim
│   │   └── hardware_spec.md
│   ├── /NFSIM-PCR-02/
│   ├── /NFSIM-SEQ-01/
│   ├── /NFSIM-SEQ-02/
│   ├── /NFSIM-CRISPR-01/
│   ├── /NFSIM-dPCR-01/
│   ├── /NFSIM-GELEC-01/
│   ├── /NFSIM-US-01/
│   ├── /NFSIM-US-02/
│   ├── /NFSIM-US-03/
│   ├── /NFSIM-MRI-01/
│   ├── /NFSIM-XRAY-01/
│   ├── /NFSIM-OCT-01/
│   ├── /NFSIM-CGM-01/
│   ├── /NFSIM-SWEAT-01/
│   ├── /NFSIM-CHEM-01/
│   ├── /NFSIM-OXY-01/
│   ├── /NFSIM-BREATH-01/
│   ├── /NFSIM-ECG-01/
│   ├── /NFSIM-ECG-02/
│   ├── /NFSIM-EEG-01/
│   ├── /NFSIM-EMG-01/
│   ├── /NFSIM-NEURAL-01/
│   ├── /NFSIM-CAP-01/
│   ├── /NFSIM-CAP-02/
│   ├── /NFSIM-CAP-03/
│   ├── /NFSIM-CAP-04/
│   ├── /NFSIM-FLOW-01/
│   ├── /NFSIM-ENV-01/
│   ├── /NFSIM-MICRO-01/
│   └── /shared/                      # Shared PCB libraries
│       ├── nfsim.kicad_sym
│       ├── nfsim.kicad_mod
│       └── nfsim_3d.kicad_3dlib
│
├── /mechanical/                       # Physical enclosures and assemblies
│   ├── /NFSIM-PCR-01/
│   │   ├── /cad/                     # Fusion 360 f3d + STEP
│   │   ├── /stl/                     # Print-ready STL
│   │   ├── /drawings/                # 2D technical drawings PDF
│   │   └── mechanical_spec.md
│   ├── /NFSIM-US-03/                 # Capsule tooling drawings
│   ├── ... (all 30 devices)
│   └── /shared/                      # Common hardware fasteners library
│
├── /firmware/                         # Embedded software
│   ├── /NFSIM-PCR-01/
│   │   ├── /src/
│   │   │   ├── /drivers/             # Hardware abstraction layer
│   │   │   │   ├── tec.c / tec.h
│   │   │   │   ├── thermistor.c / thermistor.h
│   │   │   │   ├── display.c / display.h
│   │   │   │   └── ble.c / ble.h
│   │   │   ├── /logic/
│   │   │   │   ├── pid.c / pid.h
│   │   │   │   ├── pcr_engine.c
│   │   │   │   └── protocol_storage.c
│   │   │   └── main.c
│   │   ├── /include/
│   │   ├── platformio.ini
│   │   ├── CMakeLists.txt
│   │   ├── /build/                   # Compiled artifacts (gitignored)
│   │   └── firmware_spec.md
│   ├── /NFSIM-ECG-01/
│   ├── /NFSIM-CGM-01/
│   ├── /NFSIM-SEQ-01/
│   ├── /NFSIM-CAP-01/
│   ├── ... (all 30 devices)
│   ├── /shared/                      # Shared firmware modules
│   │   ├── /nfs_protocol/            # NFS BLE GATT profile
│   │   ├── /nfs_storage/             # NVS config, flash log
│   │   ├── /nfs_ai/                  # TinyML inference wrappers
│   │   └── /nfs_bootloader/          # Common bootloader
│   └── /basecaller/                  # Open nanopore basecaller
│       ├── /models/                  # PyTorch CRNN model
│       ├── /src/                     # Python training + inference
│       ├── /tests/
│       └── requirements.txt
│
├── /software/                         # Host-side applications
│   ├── /desktop/                     # Electron app
│   │   ├── /src/
│   │   │   ├── /main/
│   │   │   └── /renderer/
│   │   ├── /assets/
│   │   │   └── body_mesh.gltf        # 3D anatomical body
│   │   ├── package.json
│   │   └── electron-builder.json
│   ├── /mobile/                      # React Native / Expo
│   │   ├── /app/                     # Expo file-based routes
│   │   ├── /components/
│   │   ├── package.json
│   │   └── app.json
│   ├── /web/                         # Web dashboard (CRA + Django)
│   │   ├── /frontend/
│   │   │   ├── /src/
│   │   │   └── package.json
│   │   └── /backend/
│   │       ├── /nfsim_api/           # Django project
│   │       ├── /simulation/          # Rust simulation bridge
│   │       ├── requirements.txt
│   │       └── manage.py
│   ├── /sdk/
│   │   ├── /python/                  # nfsim Python SDK
│   │   ├── /nodejs/                  # @nfsim/sdk npm package
│   │   └── /rust/                    # nfsim-client Rust crate
│   ├── /protocol/
│   │   └── protocol_spec.md          # THE COMMUNICATION CONTRACT
│   └── software_spec.md
│
├── /simulation/                       # NanoFlowSIM Rust core engine
│   ├── /src/
│   │   ├── /molecular/
│   │   ├── /cellular/
│   │   ├── /tissue/
│   │   ├── /systemic/
│   │   ├── /ml/
│   │   └── main.rs
│   ├── /tests/
│   ├── Cargo.toml
│   └── simulation_spec.md
│
├── /docs/                             # Documentation
│   ├── /guides/
│   │   ├── getting_started.md
│   │   ├── first_device.md
│   │   ├── data_import.md
│   │   ├── running_simulations.md
│   │   └── api_guide.md
│   ├── /theory/
│   │   ├── nanoparticle_physics.md
│   │   ├── molecular_sensing.md
│   │   ├── biosensor_chemistry.md
│   │   └── signal_processing.md
│   ├── /api/                         # Auto-generated from code
│   ├── /hardware/                    # Per-device assembly guides
│   └── /assets/                      # Diagrams, images
│
├── /production/                       # Manufacturing
│   ├── /sop/
│   │   ├── pcb_assembly.md
│   │   ├── calibration_procedure.md
│   │   └── packaging.md
│   ├── /quality/
│   │   ├── qc_checklist_generic.csv
│   │   └── test_procedures/
│   ├── /packaging/
│   └── production_run_template.md
│
├── /legal/
│   ├── MIT_LICENSE_software.txt
│   ├── CERN_OHL_v2_hardware.txt
│   ├── /certifications/              # FCC, CE test reports
│   ├── /third_party/                 # Third-party component licenses
│   └── compliance_checklist.md
│
└── /media/
    ├── /renders/                     # Device renders (Blender/KeyShot)
    ├── /photos/                      # Prototype photos
    ├── /video/                       # Demo video assets
    └── /press/                       # Press kit
```

---

# 12. Production & Manufacturing

## 12.1 PCB Manufacturing

**Recommended Fabricators**:
| Fabricator | Use Case | Notes |
|---|---|---|
| JLCPCB | Low-cost prototyping + small production | 2–4 layer, <1000 units |
| PCBWay | 4–6 layer, flex, RF | Better tolerance for complex boards |
| OSH Park | USA-based, community-friendly | Open-source friendly |

**Gerber Export Checklist** (KiCad):
- Top copper, bottom copper
- Top soldermask, bottom soldermask
- Top silkscreen, bottom silkscreen
- Edge cuts
- Drill file (Excellon)
- Assembly drawing
- Pick and place file

## 12.2 Component Sourcing

**Primary distributors**:
- Mouser Electronics (full stock, fast shipping)
- Digi-Key (reliable, accurate lead times)
- LCSC (for JLCPCB PCBA, low cost)
- Arrow Electronics (volume pricing)

**Critical component sourcing notes**:
- Peltier modules: eBay/AliExpress acceptable for prototyping, verify specifications
- Nanopore flow cell proteins (α-hemolysin): Sigma-Aldrich H9395, lyophilized
- Phi29 DNA polymerase: Thermo Fisher, Biolabs, or produced via open E. coli expression protocol
- PZT transducer arrays: custom fabrication (Boston Piezo-Optics, Meggitt), MOQ 10–50 units
- CMUT arrays: custom MEMS foundry (IMB-CNM, Fraunhofer), research partnership required
- Medical-grade adhesives: 3M 1524 or 1585N, min order $50–200

## 12.3 Quality Control Procedure (Generic)

For each device, a QC checklist must be completed before shipping:

| Test | Method | Pass Criteria |
|---|---|---|
| Visual inspection | Magnification 10× | No bridging, cold joints, missing components |
| Power-on test | Apply nominal power | No smoke, draws expected current |
| BLE advertisement | Smartphone scan | Device appears with correct name |
| Sensor calibration | Reference standard | Within ±X% of reference |
| Battery charge cycle | Full charge/discharge | Capacity within spec |
| Wireless range | 10m BLE test | Stable connection |
| Waterproof (if rated) | Immersion/spray test | No ingress |
| Firmware version | Serial command | Correct version string |
| Serial number burn | Factory tool | NVS confirmed written |
| Final run test | Domain-specific | Expected data output |

## 12.4 Calibration

All NFS devices with quantitative sensors require calibration:

| Device | Calibration Method | Reference |
|---|---|---|
| NFSIM-PCR-01 | Temperature calibration with NIST-traceable thermocouple | ±0.5°C |
| NFSIM-CGM-01 | Glucose solution (100, 200, 400 mg/dL) | ±5% |
| NFSIM-ECG-01 | Signal generator + dummy load | Gain error <1% |
| NFSIM-CHEM-01 | Certified reference material (CRM) | Per-analyte specification |
| NFSIM-OXY-01 | Phantom (tissue-simulating) with reference oximeter | ±3% rSO₂ |

Calibration coefficients stored in device NVS, readable via NFC/BLE.

---

# 13. Legal, Compliance & Licensing

## 13.1 Software License

All NanoFlowSIM **software** (firmware, desktop app, mobile app, backend, SDK) is released under the **MIT License**:

```
MIT License
Copyright (c) 2024 NanoFlowSIM Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
[...]
```

## 13.2 Hardware License

All NanoFlowSIM **hardware** (schematics, PCB layouts, Gerbers, BOM, mechanical designs) is released under the **CERN Open Hardware Licence Version 2 — Permissive (CERN-OHL-P)**:

Key conditions:
- Free to use, study, modify, and distribute
- Attribution required
- Share-alike NOT required (Permissive variant)
- No warranty

## 13.3 Regulatory Classification

All NFS devices are currently designed and documented for:
- **Research use only (RUO)** or **Educational use**
- Not intended for clinical diagnosis without appropriate national regulatory clearance

**Regulatory pathways for clinical use** (guidance only, consult regulatory counsel):

| Region | Body | Pathway | Device Class |
|---|---|---|---|
| USA | FDA | 510(k) or De Novo | Class II (most devices) |
| EU | Notified Body | MDR 2017/745 CE Mark | Class IIa/IIb |
| UK | MHRA | UKCA | Aligned with EU MDR |
| Canada | Health Canada | Medical Device License | Class II/III |

**Specific notes**:
- Ingestible capsules (NFSIM-CAP series): Class III in most jurisdictions (PMA/CE-Mark III)
- Implantable devices (NFSIM-IMPLANT series): Class III, highest regulatory burden
- IVD devices (NFSIM-CRISPR, NFSIM-CHEM, NFSIM-CGM): Separate IVD regulatory pathway in EU (IVDR 2017/746)

## 13.4 Radiation Safety

**NFSIM-XRAY-01**: Complies with IEC 60601-1-3 (radiation protection). Operators in many jurisdictions require training/certification to operate diagnostic X-ray equipment. Check local regulations.

## 13.5 Data Privacy

NanoFlowSIM's data platform is designed to comply with:
- HIPAA (USA) — business associate agreement template included
- GDPR (EU) — data minimization, right to erasure, data portability
- PIPEDA (Canada)

All genomic data handling follows ELSI (Ethical, Legal, and Social Issues) best practices:
- Patient consent for each use case
- De-identification before research sharing
- Secure deletion on patient request

## 13.6 FCC / CE Compliance

All devices with RF transmission (BLE, Wi-Fi, 434 MHz):
- Must undergo FCC Part 15 (USA) or RED Directive (EU) testing for marketing
- BLE modules (nRF52840, ESP32) have pre-certified FCC/CE IDs when used within certification parameters
- Custom 434 MHz capsule radio requires independent type approval

---

# 14. Roadmap

## Phase 1 — Foundation (Current)

- [x] Complete hardware specification for all 30 devices
- [x] Complete communication protocol specification
- [x] Complete software architecture
- [ ] KiCad PCB design complete for NFSIM-PCR-01, NFSIM-ECG-01, NFSIM-CGM-01
- [ ] Firmware complete for NFSIM-PCR-01, NFSIM-ECG-01
- [ ] Desktop application MVP with 3D body map, BLE connection, ECG display
- [ ] Web API and patient data model deployed
- [ ] NanoFlowSIM Rust simulation engine — molecular layer functional

## Phase 2 — Hardware First Wave (6–12 months)

- [ ] PCB design + prototype fabrication: all Tier 1 devices
  - NFSIM-PCR-01, NFSIM-ECG-01, NFSIM-CGM-01, NFSIM-EEG-01, NFSIM-EMG-01, NFSIM-US-01, NFSIM-CRISPR-01
- [ ] Firmware stabilization for Tier 1 devices
- [ ] End-to-end data pipeline: device → BLE → desktop → 3D body map → NanoFlowSIM
- [ ] NanoFlowSIM cellular + systemic simulation layers functional
- [ ] DICOM import + auto-segmentation
- [ ] FHIR R4 patient record import

## Phase 3 — Simulation Integration (12–18 months)

- [ ] Full back-testing engine with clinical trial data
- [ ] Machine learning therapy recommendation engine
- [ ] 3D nanoparticle trajectory visualization
- [ ] Simulation export to PDF/FHIR DiagnosticReport
- [ ] Research cohort view (de-identified multi-patient overlay)
- [ ] Capsule sensor prototypes: NFSIM-CAP-01, NFSIM-CAP-03

## Phase 4 — Advanced Devices (18–36 months)

- [ ] NFSIM-SEQ-01 prototype validation (open nanopore sequencer)
- [ ] NFSIM-CAP-02 (GI ultrasound capsule) prototype
- [ ] NFSIM-MRI-01 prototype (low-field portable MRI)
- [ ] NFSIM-FLOW-01 prototype
- [ ] Open basecaller trained on public squiggle data
- [ ] Closed-loop insulin system integration (OpenAPS protocol)
- [ ] Multi-modal AI digital twin: continuous ECG + CGM + genomics fusion model

## Phase 5 — Ecosystem Maturation (36+ months)

- [ ] Regulatory pathway initiation for clinical-use devices (510(k) or CE)
- [ ] Open manufacturing guide for distributed production
- [ ] NanoFlowSIM clinical trial management module
- [ ] Federation with hospital FHIR servers
- [ ] Patient community and data contribution platform
- [ ] High-throughput ligand and nanoparticle screening module
- [ ] Continuous liquid biopsy monitor integration (when technology matures)

---

# 15. Contributing

NanoFlowSIM is an open-source project welcoming contributions across hardware, firmware, software, and science domains.

## Getting Started

1. Read this README completely
2. Check open issues: `github.com/[org]/nanoflowsim/issues`
3. Join the community Discord: [link]
4. Pick an issue tagged `good first issue` or `hardware-help-wanted`

## Contribution Areas

| Area | Skills Needed | How to Contribute |
|---|---|---|
| Hardware design | KiCad, electronics | PCB review, new device design |
| Firmware | C/C++, embedded systems | Bug fixes, new device firmware |
| Simulation engine | Rust, biophysics | Algorithm implementation |
| Software | React, TypeScript, Django | UI features, API endpoints |
| Basecaller | PyTorch, signal processing | Model training, accuracy improvement |
| 3D body model | Blender, anatomical knowledge | Mesh refinement, annotation |
| Documentation | Technical writing | Guides, theory explanations |
| Testing | QA, biology | Hardware validation, clinical testing |
| Translation | Languages | Internationalization |

## Development Setup

**Firmware**:
```bash
# Install PlatformIO
pip install platformio

# Build NFSIM-ECG-01
cd firmware/NFSIM-ECG-01
pio run

# Flash
pio run --target upload
```

**Desktop App**:
```bash
cd software/desktop
npm install
npm run dev       # Development mode
npm run build     # Production build
```

**Backend**:
```bash
cd software/web/backend
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

**Simulation Engine**:
```bash
cd simulation
cargo build --release
cargo test
./target/release/nfsim-engine --config examples/config.json
```

## Code Style

- **Firmware (C/C++)**: Google C++ Style Guide
- **Rust**: rustfmt + clippy (strict mode)
- **Python**: Black + isort + flake8
- **TypeScript**: ESLint + Prettier (Airbnb config)
- **KiCad**: NFS schematic symbol conventions (see `/hardware/shared/STYLE.md`)

## Pull Request Process

1. Fork → feature branch → PR against `develop`
2. All CI must pass (DRC, build, tests)
3. Hardware changes: attach Gerber preview image
4. Firmware changes: attach test output or logic analyzer screenshot
5. Two approvals required for merge

---

# 16. Acknowledgements

NanoFlowSIM builds upon the shoulders of decades of open-source science and engineering:

**Hardware Communities and Projects**
- OpenPCR (Josh Perfetto, Tito Jankowski) — democratized thermocycling
- OpenBCI (Joel Murphy, Conor Russomanno) — democratized EEG
- Open Ephys (Josh Siegle et al.) — democratized neural recording
- Opentrons — democratized lab automation
- Bento Lab — portable biolab concept
- Hyperfine — low-field portable MRI pioneers
- Butterfly Network — CMUT-based portable ultrasound

**Open-Source Bioinformatics**
- GATK (Broad Institute) — genomic analysis toolkit
- BWA, SAMtools — sequence alignment standards
- Kilosort (Marius Pachitariu) — spike sorting
- MNE-Python — neural signal analysis
- OpenSim — musculoskeletal modeling
- 3D Slicer — medical image processing
- BART — MRI reconstruction
- Guppy/Dorado (Oxford Nanopore) — basecalling reference

**Scientific Literature and Communities**
- DIYbio community
- iGEM Foundation — synthetic biology democratization
- NIH BRAIN Initiative
- FASTMRI Challenge (NYU/Facebook AI)
- Open Worm Project
- OpenNeuro — open neuroscience datasets

**Technologies**
- Zephyr RTOS (Linux Foundation)
- FreeRTOS (Amazon)
- Three.js, Babylon.js — WebGL 3D
- React Native / Expo
- KiCad EDA
- JLCPCB / PCBWay — accessible PCB manufacturing

---

*NanoFlowSIM is built on the belief that biological sensing, simulation, and precision medicine should be accessible to every human on earth — not just those with access to multimillion-dollar clinical infrastructure. Every schematic, every line of firmware, every simulation algorithm in this repository is a step toward that future.*

---

**Repository**: `github.com/[org]/nanoflowsim`
**Documentation**: `docs.nfsim.io`
**Community**: `discord.gg/nfsim`
**License**: MIT (software) + CERN OHL v2 (hardware)
**Version**: 1.0.0-alpha
