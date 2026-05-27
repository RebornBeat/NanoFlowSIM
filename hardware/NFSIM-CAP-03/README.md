### NFSIM-CAP-03 — DNA/RNA Capture Capsule

**README.** Capsule with pH-triggered nitinol valve that opens in the small intestine, drawing in luminal contents to capture intestinal microbiome + free DNA/RNA. Sealed at exit; recovered post-excretion for ex-vivo sequencing on NFSIM-SEQ-01.

**SPECIFICATIONS.**
| Param | Value |
|---|---|
| Capture volume | 0.5 mL |
| Trigger | pH > 5.5 (small intestine entry) detected by ISFET |
| Valve | Nitinol heated-wire actuated (~50ms open) |
| Preservative | RNAlater or DNA/RNA Shield pre-loaded in capture chamber |
| Recovery | Post-excretion (user retrieves from stool sample using included tools) |
| Sensors | pH (trigger), 6-axis IMU (location estimate), 434 MHz uplink for confirmation |
| Battery | 30 mAh (only for ~24h coverage + valve trigger) |
| BOM | ~$95 |

**THEORY.** Microbiome composition varies dramatically along GI tract; sampling specific regions is medically important (small intestinal bacterial overgrowth, IBD location). Sealed capsule captures region-specific microbiome for off-body sequencing/PCR.

**ASSEMBLY.** Critical: USP Class VI capsule shell + reliable nitinol valve actuator. Pre-load preservative under sterile conditions. Single-use only.
