#### SPECIFICATIONS.md

| Parameter | Value |
|---|---|
| Pore types supported | Aerolysin (primary), MspA (primary), α-hemolysin (research baseline) |
| Membrane | Supported gel lipid bilayer (DPhPC in agarose) |
| Ionic current range | 0–500 pA |
| Voltage clamp | –200 to +200 mV |
| Sequencing voltage | +120 to +180 mV |
| Open-pore current (Aerolysin, 180 mV, 1M KCl) | ~70–90 pA |
| Open-pore current (MspA, 180 mV, 1M KCl) | ~100 pA |
| Noise floor | <2 pA RMS at 5 kHz |
| Sampling rate | 10–50 kHz |
| ADC resolution | 16-bit minimum (24-bit for high-fidelity) |
| Active channels | 1 research, expandable to 16 via daughter board |
| Temperature control | 18–40°C ±0.1°C (Peltier base) |
| Motor protein | Phi29 DNA polymerase wild-type (NEB M0269S), 50–200 nM |
| Voltage feedback | software, 1 kHz update rate, suppresses translocation > target speed |
| Theoretical read length | Unlimited (limited by DNA integrity) |
| Raw accuracy (community-trained Bonito on wild-type pores) | ~85–92% raw, ~98% with consensus |
| Connectivity | USB 3.0 |
| Power | USB 3.0 (5V 0.9A) + optional 12V external |
| Dimensions | 200 × 150 × 80 mm (amplifier + flow cell) |
| BOM target | ~$546 (electronics) + reagents per kit |
| Compute target | laptop (default) or CON-06 Edge Compute Module |
