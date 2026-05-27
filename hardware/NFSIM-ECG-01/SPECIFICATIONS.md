#### SPECIFICATIONS.md

| Parameter | Value |
|---|---|
| Leads | 1 (modified bipolar across chest) |
| Sampling | 250 Hz, 24-bit ADS1291 |
| Wear duration | 30 days continuous |
| Storage | 8 MB onboard flash (~30 days raw + events) |
| AI detection | AFib classifier (25 KB INT8 TFLite Micro) + PVC + heart rate |
| Latency | ~10 s detection-to-alert |
| Connectivity | BLE 5.0 (event alerts + on-demand download) |
| Battery | Custom 200 mAh LiPo, 30 days continuous wear |
| Adhesive | 3M 1585N hydrocolloid |
| Form factor | 60 × 25 × 5 mm |
| Water resistance | IPX7 (showerable) |
| BOM target | ~$38 |
| Compute target | Device (default); user-initiated upload to phone/hub for review |
