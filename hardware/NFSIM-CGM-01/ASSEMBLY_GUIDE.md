#### ASSEMBLY_GUIDE.md

**Time:** ~6 hours per first sensor. **Skills:** microelectronics + biochemistry coating.

**Step 1 — PCB.** 2-layer flex PCB ~12×3 mm for sensor body + 4-layer rigid for adhesive base.

**Step 2 — Assemble electronics.** Pick-and-place via JLCPCB PCBA.

**Step 3 — Insert platinum wire.** Spot-weld 75 µm Pt wire to PCB pad. Insulate all but tip 5 mm with polyimide tape.

**Step 4 — Coat sensor.**
- Layer 1 (inner): GOx + BSA + 0.5% glutaraldehyde, dip-coat 3×, dry 30 min RT.
- Layer 2: Nafion 5% in isopropanol, dip-coat 1×, dry 1h RT.
- Layer 3 (outer): polyurethane 2% in THF/DMF, dip-coat 2×, dry 4h RT.

**Step 5 — Flash firmware.** SWD via Nordic programmer.

**Step 6 — Calibrate.** Soak in 100 mg/dL glucose PBS; record current. Repeat at 250, 400 mg/dL. Store linearity + initial sensitivity in NVS.

**Step 7 — Mount in inserter.** Pre-load into one-shot inserter with adhesive patch.

**Step 8 — Sterilize.** EtO sterilization (single-use disposable).

**Step 9 — Field-ready.** First wear on volunteer, validate against fingerstick over 7 days; record drift model performance.
