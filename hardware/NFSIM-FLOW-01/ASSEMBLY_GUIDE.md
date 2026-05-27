#### ASSEMBLY_GUIDE.md

**Time:** ~20 hours for first build. **Skills:** PDMS microfluidics, precision mechanical alignment.

**Step 1 — Fabricate PDMS chips.** SU-8 master fabrication (academic clean room or contract) or 3D-print master with Form 3+. Cast PDMS replicas. Bond to glass coverslip. Inlet/outlet ports with luer-lock connectors.

**Step 2 — Assemble main electronics.** JLCPCB PCBA for STM32G030 board + Pi CM4 carrier.

**Step 3 — Build optical assembly.** Mount LED with diffuser + pinhole + 100 mm distance from CMOS. Critical alignment: LED-pinhole-sample-sensor on single optical axis.

**Step 4 — Mount microfluidic chip.** Chip mounted directly above bare CMOS sensor (~500 µm gap). Mechanically clamped.

**Step 5 — Build sample handling.** Syringe pump + tubing to chip inlet. Bubble sensor in line.

**Step 6 — Calibration.** Run reference sample (commercial calibration beads of known size + count, e.g., AccuCount). Verify reconstruction CNN identifies bead size + count within ±5% of expected.

**Step 7 — Diluted blood test.** Run 1:200 diluted whole blood (in saline). Verify WBC count vs. reference hematology analyzer.

**Step 8 — Field-ready.** Pair via BLE. Compute target = CON-06 default for reconstruction.
