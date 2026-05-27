#### README.md

**Purpose.** A general-purpose programmable fluorometer + heater + dual-channel optics reader for laboratory use. The hardware is intentionally **decoupled from any specific assay chemistry**. Users supply reagents; NanoFlowSIM ships reference protocols for both licensed (Cas12/Cas13 SHERLOCK/DETECTR — user-licensed) and license-free (Toehold switch + RPA, Argonaute/PfAgo) chemistries.

**Why this positioning.** SHERLOCK and DETECTR diagnostic methods are patented (Sherlock Biosciences / Broad Institute). Building a device marketed as a "CRISPR diagnostic device" invites litigation. By positioning as a programmable laboratory tool — analogous to a thermometer or a spectrophotometer — the hardware is patent-clear; the user assumes responsibility for licensing whatever chemistry they choose to run.

**Key features.**
- Two-zone heater (LAMP/RPA at 65/37°C + CRISPR/assay at 37°C)
- 2-channel fluorescence (FAM 520 nm + ROX 610 nm) with SiPM detection
- Lateral flow strip reader add-on module
- USB-C + BLE 5.0
- NFS protocol with chemistry-agnostic JSON payload

**Status:** Phase 1 — primary build target.
