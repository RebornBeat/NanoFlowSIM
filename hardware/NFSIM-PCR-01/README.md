#### README.md

**Purpose.** A genuinely portable PCR thermocycler that runs a 40-cycle protocol in 15–20 minutes (vs. 45–90 min for conventional) by using thin-film resistive heating directly on a microfluidic chip carrier rather than heating a bulky aluminum block. Operates on USB-C PD or 3000 mAh battery. BLE 5.0 + USB-C connectivity. Open KiCad design, open FreeRTOS firmware, MIT licensed.

**Key features.**
- **Thermal Sprint primary**: thin-film heater bonded to chip carrier; 8°C/s heating, 6°C/s cooling
- **Legacy mode**: standard 8-tube 0.2 mL strip via swap-in aluminum block (Peltier-based, slower, fallback)
- **Heated lid** (103°C) prevents condensation
- **AI amplification curve classifier** runs on-device (TFLite Micro) for go/no-go calls
- **NFS protocol** (BLE + USB-C); compute target hint configurable per session
- **Status:** Phase 1 — primary build target

**Compute target options.** Phone (TFLite go/no-go), hub (relay), hub+compute (curve-fit / quantitation), laptop (full analysis), institution server (cohort).

**License.** Hardware: CERN OHL-W v2. Firmware: MIT.
