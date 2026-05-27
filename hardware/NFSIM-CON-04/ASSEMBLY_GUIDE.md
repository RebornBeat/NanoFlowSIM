#### ASSEMBLY_GUIDE.md

**Time:** ~8 hours for first build. **Skills:** SMD assembly, PCB integration.

**Step 1 — PCB.** 6-layer ENIG, impedance-controlled (PCIe traces). JLCPCB PCBA service.

**Step 2 — Assemble.** Pick-and-place via JLCPCB. Hand-mount M.2 connector (BGA placement). Hand-mount 4× Si4463 modules.

**Step 3 — Flash firmware.** STM32H7 via SWD; ESP32-S3 via UART.

**Step 4 — Test base alone.** Power on; verify display boots; check Wi-Fi AP appears; pair with phone; verify BLE central scan works.

**Step 5 — Test 434 MHz reception.** Use NFSIM-CAP-05 (core temp capsule) as a test transmitter; confirm reception on hub.

**Step 6 — Install CON-06 (optional).** Insert Edge Compute Module into M.2 slot. Power on; verify CON-06 boots Ubuntu and exposes gRPC service.

**Step 7 — End-to-end test.** Connect NFSIM-PCR-01, NFSIM-ECG-01, NFSIM-CGM-01 simultaneously. Verify each device's data flows through hub to designated compute target.

**Step 8 — Field-ready.** Configure with admin credentials. Install in target site (home/clinic/lab).
