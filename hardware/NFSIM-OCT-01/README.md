### NFSIM-OCT-01 — Portable Spectral-Domain OCT

**README.** Portable spectral-domain optical coherence tomography. Sub-10 µm axial resolution imaging of skin, retina, finger nail bed, corneal anterior segment. Handheld or table-mounted probe.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Light source | 840 nm SLD (superluminescent diode), 50 nm bandwidth |
| Axial resolution | ~7 µm |
| Lateral resolution | ~15 µm (scan-dependent) |
| Imaging depth | 2 mm |
| A-line rate | 70 kHz |
| Detector | Custom CCD line camera spectrometer |
| Scanner | Galvo X-Y mirror |
| Connectivity | USB 3.0 |
| BOM | ~$680 |

**THEORY.** SD-OCT: broadband light split into sample and reference arms; interferometric backscatter at depth produces wavelength-encoded interference at the spectrometer; FFT recovers axial profile (A-line). Galvo scan builds B-scan/volume.

**BLOCK DIAGRAM.** 840 nm SLD → fiber coupler → reference + sample arms; sample arm with galvo + objective; recombined light to spectrometer (grating + line camera); USB to host (B-scan reconstruction in host).

**BOM.** 840 nm SLD module (Thorlabs SLD831S, $250), fiber coupler ($60), galvo mirror + driver ($120), line camera (CCD, $120), grating + optics ($60), STM32 controller ($10), USB bridge ($15), enclosure ($45). Total ~$680.

**FIRMWARE.** Galvo waveform generation; line camera trigger; data streaming. Host does FFT reconstruction.

**ASSEMBLY.** Critical alignment of free-space optical path. Use kinematic mounts. Calibrate dispersion + sample arm length.
