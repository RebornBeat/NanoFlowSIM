#### THEORY_OF_OPERATION.md

**Base unit responsibilities (always present):**
- Discover NanoFlowSIM devices on BLE/Wi-Fi/USB
- Receive 434 MHz capsule data (4-receiver diversity)
- Relay NFS JSON packets to the user's chosen compute target (phone, hub-itself, hub+CON-06, laptop, institution)
- Audit log all packets with ed25519 signatures
- Local SQLite database (mirror of patient record subset)
- Web UI (served from STM32H7 + ESP32-S3 + Wi-Fi) for headless configuration

**With CON-06 installed:** the hub becomes a full compute target. The base unit forwards raw streams to CON-06 over PCIe; CON-06 runs reconstruction, basecalling, AI inference. Output writes back to base unit storage and is exposed via Wi-Fi/Ethernet to clients (phone app, laptop browser).

**Two-phase initialization.** Base unit boots independently (initializes radios, BLE, USB, Wi-Fi, displays UI). If CON-06 is present, after base unit boot, it loads CON-06 over the M.2 connector and waits for CON-06 gRPC service to come up; once up, compute-heavy services become available.

#### Schematic Block Diagram

```
┌────────────────────────────────────────────────────────────────────┐
│                  NFSIM-CON-04 Gateway Hub                            │
│                                                                      │
│   ┌────────────────────────────────────────────────────┐           │
│   │  STM32H7 (main orchestrator, Cortex-M7 480 MHz)    │           │
│   │   - BLE central management                          │           │
│   │   - 434 MHz capsule receive (Si4463 ×4)             │           │
│   │   - NFS protocol routing                            │           │
│   │   - SQLite local store                              │           │
│   │   - Audit log signing (ed25519)                     │           │
│   │   - LVGL touch UI                                   │           │
│   └────────────────────────────────────────────────────┘           │
│       │                                                              │
│       ├──SPI──► [nRF52840 BLE module]                                │
│       ├──SPI──► [Si4463 ×4 434 MHz receivers + diversity combiner]   │
│       ├──USB──► [USB 3.0 hub IC] ──► 4× USB-A ports                  │
│       ├──I2C──► [PN5180 NFC reader]                                  │
│       ├──Ethernet via WIZnet W6100                                    │
│       ├──Wi-Fi via ESP32-S3 module                                    │
│       │                                                              │
│       ├──MMC──► [32 GB eMMC + microSD slot]                          │
│       ├──I2C──► [DS3232 RTC + battery backup]                        │
│       ├──SPI──► [4" capacitive touch IPS]                            │
│       │                                                              │
│       │                                                              │
│       └─── M.2 2280 connector (PCIe Gen3 ×2 + USB 3.0 + 12V) ─────► │
│                              (optional CON-06 Edge Compute Module)   │
│                                                                      │
│   Power: 12V/5A wall + PoE+ option; cooling fan if CON-06 installed │
└────────────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary | Alternate | Notes |
|---|---|---|---|
| Main MCU | STM32H743ZIT6 | STM32H753 | High-performance Cortex-M7 |
| BLE module | nRF52840-DK or module | nRF5340 | BLE central, 8 simultaneous |
| 434 MHz Tx/Rx | Si4463 ×4 | RFM69CW | Capsule data, diversity |
| USB 3 host | Microchip USB7002 | TUSB8041 | 4× USB-A |
| Wi-Fi/BT | ESP32-S3-WROOM | WL18MK module | Dual-band Wi-Fi 6 |
| Ethernet | WIZnet W6100 | KSZ8081 + PHY | 1 GbE |
| NFC | NXP PN5180 | TRF7970A | ISO 15693 |
| Display | 4" cap touch 480×800 IPS | 3.5" alt | LVGL UI |
| Storage | 32 GB eMMC | microSD slot only | Main NV |
| RTC | DS3232 + CR2032 | DS3231 | Backup time |
| M.2 connector | Custom NanoFlowSIM 2280 | — | For CON-06 |
| Power | 12V/5A barrel + PoE+ PD | USB-C PD 100W alt | Hub power |
| Enclosure | CNC aluminum + ventilation | 3D-print PETG | Heat dissipation |

**Total:** ~$110 base unit at low volume.

#### Firmware Architecture

**STM32H7 (main orchestrator) running FreeRTOS:**
- **BLECentralTask** — manages 8 simultaneous BLE peripheral connections (each NanoFlowSIM device)
- **RadioRxTask** — receives 434 MHz capsule data via Si4463 ×4 diversity combine
- **USBHostTask** — enumerates connected USB devices (US-01 probes, SEQ-01 sequencers, etc.)
- **WiFiTask** — manages ESP32-S3 for wireless connectivity to phone/cloud (optional)
- **EthernetTask** — manages WIZnet W6100 for wired connectivity
- **NFSRoutingTask** — receives NFS packets from all sources; routes to compute target per configuration
- **ComputeTargetMonitorTask** — pings phone (BLE), laptop (Wi-Fi), CON-06 (PCIe) to determine availability
- **AuditLogTask** — signs every packet with ed25519 keypair; appends to immutable log
- **UITask** (LVGL) — touchscreen UI for status, configuration, manual data review

**ESP32-S3 firmware:** Wi-Fi station + AP modes, MQTT broker for local pub/sub, web server (configuration UI).

**With CON-06 installed:** PCIe initialization handler loads CON-06 SoM, mounts it as a device, waits for gRPC service handshake. Routing layer then includes CON-06 as a viable compute target.
