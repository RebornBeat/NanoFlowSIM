#### ASSEMBLY_GUIDE.md

**Time:** ~3 hours. **Skills:** standard SMD assembly.

**Step 1 — PCBs and parts.** Order via JLCPCB PCBA. SiPMs ship from Mouser. Optical filters from Chroma or Edmund Optics. Aluminum optical block CNC-machined locally or via SendCutSend.

**Step 2 — Solder and flash.** Standard assembly. Flash firmware via ST-Link.

**Checkpoint 2:** `NFS:PING` returns device identity.

**Step 3 — Optical assembly.** Insert filters into optical block. Mount SiPMs and LEDs. Verify optical isolation: dark current per SiPM <100 mV with all LEDs off.

**Checkpoint 3:** Dark current acceptable per channel.

**Step 4 — Calibration.** Use NIST-traceable FAM and ROX fluorescence standards. Run `NFS:CALIBRATE` to set per-channel gain/offset.

**Checkpoint 4:** Standards read within ±5% of nominal.

**Step 5 — Heater calibration.** Insert NTC reference probe in well. Run two-point thermal calibration at 25°C and 65°C.

**Checkpoint 5:** Zone temperatures within ±0.5°C of reference.

**Step 6 — Reference assay test.** Run reference LAMP positive control (e.g., SARS-CoV-2 N-gene LAMP). Verify fluorescence rise over 30 min.

**Checkpoint 6:** Positive control detected; raw RFU trace exported to NanoFlowSIM session record.

**Step 7 — Field-ready.** Pair via BLE; label with serial.
