#### SPECIFICATIONS.md

| Parameter | Value |
|---|---|
| Form factor | M.2 2280 with custom NFSIM connector pinout |
| SoM option A | NVIDIA Jetson Orin Nano (8 GB) — 6-core ARM A78AE + Ampere GPU + 40 TOPS sparse |
| SoM option B | Rockchip RK3588 (8-core Cortex-A76/A55 + Mali-G610 + 6 TOPS NPU) |
| SoM option C | Raspberry Pi CM5 (4-core ARM A76, no NPU, CPU-only baseline) |
| Connector | PCIe Gen3 ×2 + USB 3.0 + GPIO (via custom M.2 edge fingers) |
| Power | 5–15W @ 12V from CON-04 base |
| Cooling | Passive heatsink + CON-04 chassis fan |
| OS | Ubuntu 24.04 LTS, NanoFlowSIM image preinstalled |
| Software | nfsim-edge-server (gRPC), ONNX Runtime, BART, Dorado, Bonito, Kilosort, 3D Slicer, OpenSlide |
| Local storage | 64 GB eMMC (Orin) or microSD (RK3588/CM5) for OS + models |
| Patient data store | SQLite + MinIO local; primary or mirror of CON-04 base |
| BOM | ~$95 (Pi CM5), ~$180 (RK3588), ~$500 (Orin Nano) |
