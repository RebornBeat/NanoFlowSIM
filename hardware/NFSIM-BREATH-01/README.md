### NFSIM-BREATH-01 — Breath Metabolomics

**README.** Metal oxide gas sensor array (e-nose) + optical photoacoustic NO/CO₂ for breath VOC analysis. Asthma monitoring (NO), ketogenic state (acetone), lung cancer pattern (research).

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Sensors | SGP41 (VOC/NOx) + SCD41 (CO₂) + photoacoustic NO module + MOX 4-sensor array |
| Analytes | NO, CO₂, acetone, ethanol, VOCs |
| Sample | Single exhale through mouthpiece |
| Time | 30s analysis |
| BOM | ~$210 |

**THEORY.** Metal oxide semiconductor sensors change resistance in response to VOC adsorption. Pattern of responses + AI classification identifies breath signatures. Photoacoustic for NO: modulated laser → NO absorbs → pressure wave → microphone → ppb sensitivity.

**BLOCK DIAGRAM.** STM32H7 + sensor array (I2C) + photoacoustic chamber (laser + microphone) + nRF52840.

**ASSEMBLY.** Sensor chamber with controlled flow path. Mouthpiece + disposable filter.
