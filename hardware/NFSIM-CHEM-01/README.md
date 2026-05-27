### NFSIM-CHEM-01 — Blood Chemistry Analyzer

**README.** Cartridge-based point-of-care chemistry. Single drop blood (fingerstick) → cartridge → panel of 10–20 analytes (electrolytes, BUN, creatinine, glucose, hemoglobin, etc.) in 5 min.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Cartridge | NFSIM-CON-02 universal cartridge interface |
| Analytes | Na, K, Cl, BUN, Cr, glucose, Hb, Hct, anion gap, lactate, troponin (cardiac panel cartridge) |
| Sample | 65 µL whole blood |
| Time | 2–8 min |
| Detection | Mix of ISE (electrolytes), amperometric (glucose, lactate), spectrophotometric (Hb) |
| Connectivity | BLE 5.0 + USB-C |
| BOM | ~$185 (reader only; cartridges $8–25 each) |

**THEORY.** Combined electrochemistry + spectrophotometry on a disposable cartridge. Hemoglobin via 540 nm absorbance. Electrolytes via ISE. Glucose/lactate amperometric. Single-use cartridges fab'd in volume.

**BLOCK DIAGRAM.** STM32H7 + LMP91000 ×4 + MCP3424 ×2 + LED+photodiode pair (540 nm + 700 nm) + cartridge interface (NFSIM-CON-02). BLE/USB-C output.

**BOM.** STM32H7 ($15), potentiostats + ADCs ($20), optics ($15), cartridge connector + heater ($25), BLE ($5), enclosure + display ($60), PCB + misc ($45). Total ~$185.

**FIRMWARE.** Cartridge identification (RFID/barcode), per-cartridge protocol load, sequential analyte measurement, result emission via NFS.

**ASSEMBLY.** Reader is mostly electronics. Disposable cartridges manufactured separately (injection-molded plastic + screen-printed electrodes + sealed reagent reservoirs).
