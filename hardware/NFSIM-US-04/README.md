### NFSIM-US-04 — Dermal Ultrasound Scanner (high-frequency)

**README.** 40 MHz high-frequency ultrasound for skin imaging — epidermis, dermis, subcutaneous structures. Used for skin cancer screening, wound depth assessment, scar evaluation. Mechanical single-element scanning.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Transducer | 40 MHz single-element PVDF or PMN-PT focused |
| Resolution | ~40 µm axial, ~80 µm lateral |
| Depth | 0–8 mm |
| Scanning | Stepper-motor mechanical sweep, 20 mm range |
| Frame rate | 5 fps (2D B-mode) |
| Coupling | Water/gel bag standoff |
| Power | USB-C 5V 2A |
| BOM | ~$180 |

**THEORY.** Very high frequency for high resolution at shallow depth (skin). Single focused element mechanically scanned across the region of interest. Each line is acquired sequentially → 2D B-mode reconstruction.

**BLOCK DIAGRAM.** STM32G474 → stepper motor (TMC2209) + pulser (±50V) + 100 MSPS ADC (AD9226) → USB-CDC + BLE → host (image build via synthetic aperture or simple delay-and-sum).

**BOM.** PMN-PT 40 MHz element from Boston Piezo Optics ($60), stepper + driver ($15), 100 MSPS ADC ($15), STM32G474 ($4), nRF52840 ($5), pulser ($10), water bag + coupling ($20), enclosure ($25), misc ($26). Total ~$180.

**FIRMWARE.** Stepper sweep + per-position acquisition; B-mode image emit. NFS streaming.

**ASSEMBLY.** Mount focused element on stepper linear rail. Water bag standoff with optical-grade plastic window. USB-C interface.
