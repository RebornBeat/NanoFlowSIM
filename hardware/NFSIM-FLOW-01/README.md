#### README.md

**Purpose.** Portable cell-counting and flow cytometry using **lensless holographic imaging as the primary mechanism** — no lasers, no lenses, no acoustic focusing. The CMOS sensor records diffraction patterns from cells in a flow channel; AI reconstructs cell images. Acoustic focusing (ThermoFisher Attune patents) and inertial focusing (Dean flow) documented as alternative variants.

**Why lensless wins.** Conventional flow cytometers use lasers + focusing + fluorescence + multiple PMTs — complex, expensive (~$100k+), bench-top only. Lensless holographic: a flow channel + LED + bare CMOS sensor + AI reconstruction. Almost no optics. Portable. ~$300 BOM. Reconstruction quality scales with AI model quality (forward-upgradeable).

**Status:** Phase 2 — research prototype + community validation against reference cytometer.
