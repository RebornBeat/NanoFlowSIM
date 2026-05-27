#### README.md

**Purpose.** Swallowable capsule that produces ultrasound images of the GI wall (mucosa + submucosa + muscularis layers) during transit. **Primary design uses a flexible PVDF film ring array** — CMUT-on-CMOS designs are blocked by Butterfly/Kolo patents and require specialized MEMS foundries. PVDF film wraps the capsule's cylindrical body naturally, operates at low voltage (~30V vs. ~100V for PZT), and is sourced from commercial suppliers (PolyK, TE Connectivity).

**Why PVDF in a capsule.** (1) Patent-clear (no CMUT-CMOS), (2) flexible — wraps the cylinder naturally without segmented PZT, (3) low voltage drive (battery-friendly), (4) wide bandwidth (good axial resolution), (5) sourcing is commercial-off-the-shelf.

**Trade-off.** PVDF has lower transmit sensitivity than PZT or CMUT. NanoFlowSIM compensates with: (a) software synthetic aperture imaging, (b) AI denoising on the external belt receiver, (c) longer dwell at each image acquisition (~100 ms vs. ~1 ms typical).

**Status:** Phase 2 — animal model trial design phase.
