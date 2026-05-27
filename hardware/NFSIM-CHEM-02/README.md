### NFSIM-CHEM-02 — Saliva Analyzer

**README.** Pocket reader for salivary cortisol, glucose, lactate, hormones via lateral flow + electrochemical strips.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Strips | Lateral flow (immunoassay) + electrochemical |
| Analytes | Cortisol, glucose, lactate, melatonin (research) |
| Time | 5–10 min |
| BOM | ~$80 (+ strips $4–10) |

**THEORY.** Saliva sampled via swab; analyte transferred to strip; reader photographs (lateral flow) or potentiostats (electrochemical).

**BLOCK DIAGRAM.** STM32L0 + OV2640 camera + LMP91000 + nRF52840 → BLE.

**BOM.** STM32L0 ($1.50), nRF52840 ($5), OV2640 ($8), LMP91000 ($3), LED + diffuser ($1), strip slot ($8), display ($5), battery ($4), enclosure ($25), misc ($19.50). Total ~$80.

**FIRMWARE.** Strip ID, capture + analyze, NFS output.

**ASSEMBLY.** Compact handheld. Strip insertion slot. AI line detection for lateral flow.
