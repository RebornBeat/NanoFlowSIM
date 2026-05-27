#### SPECIFICATIONS.md

| Parameter | Value |
|---|---|
| Field strength | 50 mT (Halbach NdFeB array) |
| Field homogeneity | <100 ppm over 15 cm DSV (with shimming) |
| Gradient strength | 100 mT/m peak (water-cooled gradient coils) |
| RF | 2.1 MHz Larmor at 50 mT |
| Console | MaRCoS open-source (Red Pitaya STEMlab 125-14 SDR base) |
| RF amplifier | 100 W class-D |
| RF coil | Tx/Rx solenoid or birdcage, application-specific |
| Imaging modes | T1, T2, T2*, DWI, MRA (limited at low field) |
| Reconstruction | FastMRI U-Net (open weights) + compressed sensing |
| Scan time | 5–20 min per sequence |
| Imaging volume | Head, knee, wrist, infant body |
| Weight | ~80 kg (transportable on wheeled cart) |
| Power | 110/220V AC, 1 kW |
| BOM target | ~$4,520 |
| Compute target | CON-06 Edge Compute Module (BART + ONNX) OR laptop with GPU OR institution server |
