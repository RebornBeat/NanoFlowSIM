#### ASSEMBLY_GUIDE.md

**Time:** ~16–24 hours (skilled). **Skills:** high-density SMD, FPGA programming, RF design.

**Step 1 — PCBs and components.** 8-layer impedance-controlled PCB via PCBWay. AFE5832 chips from TI (Mouser stock). HV pulsers, PZT array (4–6 week lead from Imasonic).

**Step 2 — Assemble main board.** AFE5832 BGA placement; reflow profile per TI app note. Hand-touch QFN pulsers. Verify LVDS lines impedance.

**Step 3 — Build interchangeable cartridge holder.** Hirose FX12 200-pin connector mounted on cartridge end; PZT array bonded to cartridge body with ground/signal flex cable.

**Step 4 — Flash FPGA.** Use Lattice Diamond or open-source nextpnr-ecp5. Verify LVDS deserialization works (loopback test).

**Step 5 — Flash MCU.** nRF Connect SDK. Flash USB-CDC + BLE firmware.

**Step 6 — Connect to host.** Plug USB 3.2 cable to host laptop. Run `nfsim-us01-host`. Verify I/Q stream visible (random noise pattern initially).

**Step 7 — Plug PZT cartridge.** Attach 5 MHz array. Run pulse-echo on tissue phantom.

**Checkpoint:** Phantom image resolves expected structures.

**Step 8 — Calibrate.** Acoustic calibration against a NIST-traceable tissue phantom (CIRS Model 040). Save per-element gain compensation table.

**Step 9 — Probe surface thermal verification.** Run worst-case Doppler 10-min protocol; surface temp must stay <43°C against skin/phantom.

**Step 10 — Field-ready.** Pair with phone via BLE. Confirm clip save → NFS packet → patient record.
