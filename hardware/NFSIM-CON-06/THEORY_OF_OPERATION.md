#### THEORY_OF_OPERATION.md

**Architecture.** CON-06 plugs into CON-04's M.2 slot, drawing 5–15W from the base unit's 12V supply. PCIe Gen3 ×2 link gives ~16 Gbps to the base. USB 3.0 lane for additional bandwidth-flexibility. GPIO for status signaling.

**Software stack (nfsim-edge-server).** Rust gRPC service exposing:
- `Beamform(rf_iq) -> image` (for US-01 probes)
- `Basecall(squiggle) -> fastq` (for SEQ-01)
- `ReconstructMRI(k_space) -> dicom_with_uncertainty` (for MRI-01)
- `ReconstructFlow(holograms) -> cell_counts` (for FLOW-01)
- `RunSimulation(model_params) -> simulation_results` (for nanoparticle workflows)
- `AIInference(model_id, input) -> output` (generic ONNX runner)

**Model registry.** Preinstalled with SHA-256 hashes. Models can be added (with explicit user approval) for custom workflows.

**Per-SoM optimization.**
- **Orin Nano**: CUDA + JetPack + TensorRT acceleration; runs full-resolution beamforming + FastMRI at clinical quality
- **RK3588**: OpenCL on Mali-G610 + RKNN on 6 TOPS NPU; runs reduced-resolution AI workflows
- **CM5**: CPU-only baseline; runs simple workflows + raw data relay

**Privacy posture.** CON-06 storage is local-first. No cloud sync by default. User can enable cloud federation (with patient consent) for cohort analytics.

#### Schematic Block Diagram

```
┌────────────────────────────────────────────────────────────────────┐
│                  NFSIM-CON-06 Edge Compute Module                    │
│              (M.2 2280 with NanoFlowSIM custom pinout)              │
│                                                                      │
│   ┌────────────────────────────────────────────────────┐           │
│   │  SoM (one of):                                       │           │
│   │   - Jetson Orin Nano (8 GB SOM + carrier board)     │           │
│   │   - Rockchip RK3588 (8-core SoC + 8 GB LPDDR)       │           │
│   │   - Raspberry Pi CM5 (4-core + 8 GB LPDDR)          │           │
│   └────────────────────────────────────────────────────┘           │
│                                                                      │
│   ┌────────────────────────────────────────────────────┐           │
│   │  64 GB eMMC (Orin) or microSD (RK3588/CM5)          │           │
│   │   - Ubuntu 24.04 LTS                                 │           │
│   │   - nfsim-edge-server (Rust gRPC)                    │           │
│   │   - ONNX Runtime + per-SoM GPU/NPU backend          │           │
│   │   - Dorado, Bonito, BART, Kilosort, 3D Slicer       │           │
│   │   - Patient SQLite + MinIO local                     │           │
│   └────────────────────────────────────────────────────┘           │
│                                                                      │
│   M.2 edge fingers:                                                  │
│     - PCIe Gen3 ×2 (16 Gbps to CON-04 base)                          │
│     - USB 3.0 lane                                                   │
│     - GPIO (status, reset)                                            │
│     - 12V power input + ground                                       │
│                                                                      │
│   Cooling: passive Cu heatsink, active fan in CON-04 chassis        │
└────────────────────────────────────────────────────────────────────┘
```

#### BOM Framework (Three Variants)

**Orin Nano variant:**
- NVIDIA Jetson Orin Nano 8 GB Dev Kit (~$499)
- M.2 carrier board (custom design or modified vendor board) (~$0 if custom-routed onto CON-06 PCB)
- Heatsink + thermal interface (~$10)
- Total: ~$500

**RK3588 variant:**
- RK3588 SoM (Radxa CM5 SoM or Banana Pi M7 SoM) (~$120)
- Custom carrier with M.2 fingers + RAM if separate (~$30)
- Heatsink (~$10)
- Storage (microSD 64 GB) (~$20)
- Total: ~$180

**Pi CM5 variant:**
- Raspberry Pi CM5 (~$55)
- Custom carrier (~$15)
- Heatsink (~$10)
- Storage (microSD 32 GB) (~$15)
- Total: ~$95

#### Firmware / Software Architecture

**Boot.** SoM boots Ubuntu 24.04 from local eMMC/SD. Init scripts launch `nfsim-edge-server` on system boot. CON-04 base detects CON-06 over PCIe; handshake establishes gRPC channel.

**Services:**
- `nfsim-edge-server` (Rust, gRPC, port 50051) — exposes compute service endpoints
- `nfsim-models` (model registry; SHA-256 verified) — pre-loads ONNX Runtime sessions
- `nfsim-storage` (SQLite + MinIO local; optional mirror of CON-04 base)
- `nfsim-monitor` — exposes Prometheus metrics for CON-04 base to read

**Update path.** OTA via CON-04 base when network connected; or USB stick for offline updates.
