### NFSIM-OXY-01 — NIRS Oxygenation Array

**README.** Near-infrared spectroscopy patch for tissue oxygenation (StO₂) — cerebral, muscle, fetal. Continuous wave 730/850 nm optical.

**SPECIFICATIONS.** 4 source-detector pairs at varying separations; 730 + 850 nm dual-wavelength LEDs; OPT101 detectors; computes HbO₂ + HHb concentrations via modified Beer-Lambert. ~$180.

**THEORY.** Hemoglobin has different absorption spectra in oxy vs. deoxy forms. Dual-wavelength differential measurement at varying source-detector spacings reveals depth-resolved oxygenation.

**BLOCK DIAGRAM.** STM32G474 + LED drivers + OPT101 ×4 + ADS1115 + nRF52840. Patch form factor.

**ASSEMBLY.** Flexible PCB conforms to forehead, calf, or thigh. Optical isolation between source-detector pairs.
