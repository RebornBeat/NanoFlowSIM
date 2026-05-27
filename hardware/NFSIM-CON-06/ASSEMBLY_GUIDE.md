#### ASSEMBLY_GUIDE.md

**Time:** ~6 hours per variant. **Skills:** module integration, Ubuntu admin.

**Step 1 — Choose SoM tier.** Decide Orin Nano (clinical-grade), RK3588 (general), or CM5 (entry/budget).

**Step 2 — Custom M.2 PCB.** PCB carrier board with M.2 edge fingers + SoM landing pattern + power converters (12V → SoM rails). Order from JLCPCB.

**Step 3 — Install SoM on carrier.** SoMs typically use board-to-board connectors (Hirose DF40) or M.2 SOM standard.

**Step 4 — Flash Ubuntu image.** Pre-built NanoFlowSIM Ubuntu 24.04 image via USB Imager (RPI/RK3588) or NVIDIA SDK Manager (Orin).

**Step 5 — Install in CON-04.** Insert into M.2 slot. Power on CON-04; verify CON-06 boots and exposes gRPC service.

**Step 6 — Verify pipelines.** Run sample workflows: basecall test squiggle (SEQ-01 simulator data); reconstruct test k-space (MRI-01 simulator data); run sample simulation. Verify all complete successfully.

**Step 7 — Optional: configure as primary data store.** Migrate patient SQLite to CON-06 local storage; CON-04 base becomes thin client.
