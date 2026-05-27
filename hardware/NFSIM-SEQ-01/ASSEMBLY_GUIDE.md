#### ASSEMBLY_GUIDE.md

**Time:** ~12–20 hours for first build. **Skills required:** patch clamp electrochemistry, microfluidic handling, soldering, FPGA flashing.

**Step 1 — Order PCBs.** Submit Gerbers to PCBWay for Rogers 4350B 2-layer headstage. Submit main controller PCB to JLCPCB 4-layer ENIG. Order Lattice iCE40HX8K evaluation board. Order all Mouser parts.

**Checkpoint 1:** All PCBs and parts in hand.

**Step 2 — Assemble headstage.** Hand-solder OPA637, 100 MΩ feedback resistor, guard ring traces. Critical: clean PCB thoroughly (isopropanol + ultrasonic if available) before mounting OPA637; any contamination ruins the femtoamp performance.

**Checkpoint 2:** Headstage assembled. Apply ±10V via DAC; measure TIA output noise <2 pA RMS RTI with no input.

**Step 3 — Build Faraday shield.** CNC or sheet-metal aluminum enclosure. Ground it to circuit ground.

**Checkpoint 3:** Headstage inside shield; noise floor confirmed <2 pA RMS.

**Step 4 — Build flow cell.** CNC polycarbonate 2-chamber design. Drill 50 µm aperture through 25 µm Teflon film (or use a Class II reusable laser). Glue Teflon film between chambers.

**Checkpoint 4:** Chambers hold 1M KCl buffer; no leak; aperture intact under microscope.

**Step 5 — Prepare Ag/AgCl electrodes.** Anodize 0.5 mm Ag wire in 0.1M HCl at 1 mA for 30 min. AgCl coating should appear gray.

**Checkpoint 5:** Electrodes show stable reference potential in KCl (<5 mV drift over 10 min).

**Step 6 — Form supported gel bilayer.** Dissolve 2% agarose in 1M KCl, melt at 80°C, pipette into flow cell partition. Cool to RT. Apply 5 mg/mL DPhPC in decane to the agarose surface. Bilayer self-forms over the aperture. Apply +100 mV; expect <5 pA current (membrane sealed).

**Checkpoint 6:** Sealed bilayer formed (current <5 pA at +100 mV).

**Step 7 — Insert pore.** Add 1 µL of 0.1 mg/mL Aerolysin (or α-HL/MspA) to cis chamber. Watch for pore insertion event (sudden current jump to ~70–100 pA at +180 mV).

**Checkpoint 7:** Single pore inserted; open-pore current stable.

**Step 8 — Library preparation and load.** Use NFSIM-PCR-01 to amplify target region. Clean with SPRI beads. End-repair + dA-tail (NEB E7596). Ligate motor-enzyme adapter (Phi29 pre-loaded). SPRI cleanup. Dilute to 5–50 ng/µL in 1M KCl. Load 5 µL to cis chamber.

**Checkpoint 8:** Translocation events visible (current drops to ~30% of open-pore baseline, dwell times in ms range).

**Step 9 — Stream and basecall.** Start `nfsim-seq-client` on host laptop. Stream squiggles for 1–4 hours. Run `nfsim-basecaller` to convert to FASTQ. Align to expected reference with minimap2.

**Checkpoint 9:** Reads aligned; identity ≥85% raw; consensus accuracy ≥98% with sufficient coverage.

**Step 10 — Provenance.** Verify session JSON emitted with raw_signal_ref pointing to pod5 file, reconstruction_chain listing basecaller version + weights hash.
