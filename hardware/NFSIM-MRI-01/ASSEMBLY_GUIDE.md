#### ASSEMBLY_GUIDE.md

**Time:** ~200+ hours for first build. **Skills:** mechanical engineering (precision magnet assembly), RF engineering, gradient amplifier design, software integration. **Safety:** strong magnetic field hazard; ferromagnetic objects can become projectiles. Site preparation and safety training required before powering.

**Step 1 — Procure magnets.** N52 NdFeB bricks (verified grade with hall probe). 60+ kg total. **Critical:** ferromagnetic safety — never near pacemakers, oxygen tanks, ferromagnetic tools.

**Step 2 — Assemble Halbach array.** Design via FEMM 2D simulation. CNC aluminum fixturing with 50 µm placement tolerance. Assemble in graduated stages with hall-probe field mapping at each stage.

**Step 3 — Shim the field.** Measure field uniformity over 15 cm DSV with field-mapping probe. Add passive shim shims (small NdFeB + iron pieces). Target <100 ppm uniformity.

**Step 4 — Wind gradient coils.** Three orthogonal coils. Use FEMM to design. Wind on CNC-machined coil formers. Water-cool with embedded copper tubing for thermal stability.

**Step 5 — Build gradient amplifiers.** Class-D full-bridge ±40V × 50A. Test with resistive load before connecting coils.

**Step 6 — Build RF chain.** RF coil tuned to 2.1 MHz; Tx amp + Tx/Rx switch + preamp. Test on bench with signal generator + spectrum analyzer.

**Step 7 — Integrate MaRCoS console.** Connect Red Pitaya STEMlab. Run MaRCoS test pulse sequences against a phantom (CuSO₄ doped water bottle).

**Step 8 — First image.** Run a 2D FLASH sequence on a phantom. Acquire k-space. Run nfsim-mri-reconstruction on CON-06. View image. Expect noisy but recognizable phantom image.

**Step 9 — AI reconstruction.** Run FastMRI U-Net super-resolution. Compare classical FFT vs. AI-reconstructed. Validate Bayesian uncertainty map shows high uncertainty in noisy regions.

**Step 10 — Clinical validation.** First human volunteer scan (with IRB approval). Compare image quality against clinical 1.5T reference on same volunteer. Document clinical applicability per region.
