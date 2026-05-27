#### README.md

**Purpose.** Bedside / clinic / field-deployable low-field MRI scanner (~50 mT) using Halbach permanent magnet arrays + open-source MaRCoS console + FastMRI-class AI super-resolution reconstruction. Targets head, knee, wrist, infant body imaging. Positioned as a **screening and longitudinal monitoring** tool, not a replacement for clinical 1.5T/3T diagnostic MRI.

**Why this exists.** Clinical MRI requires superconducting magnets, cryogenic cooling, shielded rooms, and $1M+ installations. NanoFlowSIM MRI-01 uses room-temperature Halbach permanent magnets (NdFeB), an open-source MaRCoS RF console, and the FastMRI deep-learning reconstruction (published open weights) — enabling MRI in rural clinics, ICUs, and home settings.

**AI Reconstruction Honesty.** Every reconstructed slice is published with: (a) raw k-space data preserved alongside, (b) model identifier + weights hash used for reconstruction, (c) per-voxel uncertainty maps (Bayesian neural network output). Clinicians can re-reconstruct with a different model on the same raw data. UI surfaces low-confidence regions visually.

**Status:** Phase 2 — first prototype magnet assembly + brain imaging trials.
