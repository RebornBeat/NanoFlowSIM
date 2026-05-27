#### ASSEMBLY_GUIDE.md

**Time:** ~4 hours for a skilled builder. **Tools:** soldering iron with hot air, microscope or magnifier, multimeter, JTAG/ST-Link, 3D printer.

**Step 1 — Order PCBs and components.** Submit Gerbers + BOM to JLCPCB PCBA service (4-layer ENIG, 1.6mm). Order any non-LCSC components from Mouser. Order Peltier modules and heat sinks separately. Order 3D printer filament (PETG) or print enclosure parts.

**Checkpoint 1:** All parts received; PCBA inspected visually for assembly errors.

**Step 2 — Flash bootloader and firmware.** Connect ST-Link V3 to SWD header on main PCB. Flash NanoFlowSIM bootloader, then application firmware (latest release from GitHub).

**Checkpoint 2:** Open USB-CDC virtual port; send `NFS:PING`; expect `NFS:OK {"device":"NFSIM-PCR-01",...}`.

**Step 3 — Calibrate thermal system.** Mount Peltier modules to heat sink with thermal compound. Bond thin-film heater to chip carrier. Insert NTC thermistors into block wells, heat sink, ambient. Connect to main PCB. Run `NFS:CALIBRATE {"method":"two_point","ref_1":25.0,"ref_2":95.0}` against a NIST-traceable reference thermometer.

**Checkpoint 3:** Calibration coefficients stored; block reaches 95°C ±0.3°C of reference.

**Step 4 — Assemble optics.** Insert 470 nm LEDs and OPT101 photodiodes into chamber wells. Verify dark current and reference fluorescence with a known SYBR-stained sample.

**Checkpoint 4:** Per-chamber fluorescence signal SNR ≥ 30 dB.

**Step 5 — Assemble heated lid.** Install Kapton lid heater + lid NTC. Spring-load the silicone pressure pad.

**Checkpoint 5:** Lid reaches 103°C ±2°C; pressure pad seats firmly on PCR tube caps.

**Step 6 — Mount in enclosure.** Install PCB in PETG shell. Route USB-C, install rubber feet. Install display window. Verify button travel.

**Checkpoint 6:** Enclosure closed; USB-C accessible; display readable; buttons functional.

**Step 7 — Full system test.** Run a known LAMP protocol (65°C hold mode) with a known positive sample (e.g., synthetic SARS-CoV-2 RNA control + LAMP master mix). Verify fluorescence rise within 30 min.

**Checkpoint 7:** Positive control detected; amplification curve classified as `positive_strong`; session JSON saved.

**Step 8 — Field-ready.** Label with unique serial. Pair with NanoFlowSIM app via BLE. Confirm session data appears in patient record.
