#### ASSEMBLY_GUIDE.md

**Time:** ~30–40 hours per first prototype. **Skills:** microelectronics assembly, medical-grade encapsulation, PVDF handling.

**Step 1 — PCB.** Custom flex PCB that wraps inside the 11mm capsule shell. JLCPCB flex PCB service or PCBWay rigid-flex.

**Step 2 — Assemble main PCB.** Tiny QFN/BGA placement requires stencil + reflow. Pick-and-place (or use JLCPCB PCBA service for assembly).

**Step 3 — PVDF film electrode patterning.** Print 32 element electrodes on PVDF film using Ag-ink screen printing or photolithography on metallized film. Use 5 MHz half-wavelength element width spacing.

**Step 4 — Bond PVDF to capsule body.** Acoustic-grade epoxy on inner cylinder surface. Backing layer = epoxy + tungsten loading for damping.

**Step 5 — Connect PVDF flex tails to main PCB.** Tiny ZIF connectors or ACF (anisotropic conductive film) bonding.

**Step 6 — Integrate IMU, battery, storage.** Stack components vertically inside the cylindrical capsule.

**Step 7 — Seal outer shell.** Two-piece ABS (or HPMC for dissolvable) with O-ring + UV-cure epoxy. Pressure-test (1 ATM external for 1 hour).

**Step 8 — Verify in benchtop water tank.** Submerge; trigger acquisition; receive 434 MHz on belt; reconstruct image of test phantom.

**Step 9 — Biocompatibility certification.** USP Class VI testing on outer shell (third-party lab).

**Step 10 — Per-batch validation.** Image porcine GI tract ex vivo before live trial.
