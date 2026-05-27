#### THEORY_OF_OPERATION.md

**ECG acquisition.** Two skin electrodes capture cardiac depolarization signals. ADS1291 (24-bit Sigma-Delta ADC with integrated PGA, lead-off detection, right-leg drive) samples at 250 Hz.

**On-device AFib classification.** A 1D-CNN (3 conv blocks + 2 dense, INT8 quantized, 25 KB) runs on the nRF52840 ARM Cortex-M4F with CMSIS-NN acceleration. Input: 10-second sliding window. Output: probability scores for {sinus, AFib, PVC, artifact, noise}. Trained on PhysioNet datasets (MIT-BIH AFib, AF Challenge 2017, CinC). Model card shipped with each device.

**Event-based storage.** Continuous recording into a circular buffer (8 MB ≈ 30 days at 250 Hz × 24-bit + compression). When AFib confidence exceeds 0.8 for >30s, the device snapshots a 30s pre/post window as a "burden event" and BLE-alerts the user. User can download burden events on-demand.

**Privacy posture.** **No automatic cloud upload.** Raw ECG never leaves the device unless the user explicitly initiates a share-to-clinician action. The model and weights are inspectable (model card stored alongside the device firmware on GitHub).

**Confidence reporting.** Per-event: classifier confidence, signal-quality index (SQI from Pan-Tompkins), duration, prevalence (% of recording showing the event).

#### Schematic Block Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                  NFSIM-ECG-01 Patch                          │
│                                                               │
│   Hydrogel electrode ×2 ──► [TI ADS1291] ◄── Right-leg drive│
│                                  │  24-bit, integrated PGA   │
│                                  │  Lead-off detection        │
│                                  ▼ SPI                        │
│   ┌──────────────────────────────────────────────────┐       │
│   │  nRF52840 (Cortex-M4F, 64 MHz)                   │       │
│   │   - Sample buffer (FreeRTOS)                      │       │
│   │   - On-device AFib classifier (TFLite Micro 25KB) │       │
│   │   - Event detection + circular buffer            │       │
│   │   - BLE 5.0 event alerts + on-demand download    │       │
│   │   - Activity inference (LSM6DSO accel context)   │       │
│   └──────────────────────────────────────────────────┘       │
│             │              │                                  │
│             ▼              ▼                                  │
│   ┌──────────────┐   ┌──────────────┐                       │
│   │  W25Q64 SPI  │   │ LSM6DSO IMU  │                       │
│   │  8 MB flash  │   │ accel + gyro │                       │
│   └──────────────┘   └──────────────┘                       │
│                                                               │
│   Battery: 200 mAh LiPo (custom slim) + TPS61240 boost      │
│   Adhesive: 3M 1585N hydrocolloid base                       │
│   Electrodes: Ag/AgCl hydrogel pads (replaceable weekly)    │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

#### BOM Framework

| Component | Primary | Alternate | Notes |
|---|---|---|---|
| MCU/BLE | nRF52840-QFAA | nRF5340 | Cortex-M4F + BLE |
| ECG AFE | TI ADS1291 | ADS1192 (2ch) | 24-bit ECG-specific |
| IMU | LSM6DSO (6-axis) | BMI270 | Activity context |
| Flash | W25Q64JVSSIQ 8MB | MX25L6433F | Event storage |
| Battery | Custom 200 mAh LiPo slim | 3.0V CR2032 + boost (less capacity) | 30-day life |
| Boost | TPS61240 | LTC3539 | 1.8/3.3V rails |
| Hydrogel electrodes | 3M 2660 / Vermed RTL | Covidien Kendall | Replaceable per skin tolerance |
| Adhesive base | 3M 1585N | Tegaderm 1626 | Hypoallergenic |
| Enclosure | TPE overmold (medical-grade) | ABS shell | Conforms to chest |
| PCB | 2-layer flex + 4-layer rigid | All-flex hybrid | Tight integration |

**Total:** ~$38 at low volume.

#### Firmware Architecture

**MCU:** nRF52840 with FreeRTOS.

**Tasks:**
- **ECGSamplingTask** (priority 7, 250 Hz from ADS1291 DRDY interrupt): pulls samples via SPI; pushes to circular buffer.
- **AFibClassifierTask** (priority 5, every 5s on 10-s window): runs TFLite Micro INT8 model with CMSIS-NN; emits probability vector + signal quality index.
- **EventDetectorTask** (priority 4): debounces classifier outputs; on sustained AFib > 30s, snapshots event; triggers BLE alert.
- **StorageTask** (priority 4, opportunistic): writes circular buffer + event index to W25Q64 SPI flash; compressed to save space.
- **BLETask** (priority 5): advertises hourly burden + alert events; on connection, supports download of selected event windows.
- **ActivityTask** (priority 3, 25 Hz from IMU): classifies activity (rest/walk/run/sleep); used for context-aware AFib false-positive reduction.
- **PowerTask** (priority 2): targets <150 µA average → 30-day battery life. Aggressive sleep between ADC samples; BLE advertising every 60s.

**NFS protocol.** Standard NFS BLE GATT. Event packets include: event type, confidence, duration, snippet reference (downloadable), activity context, ECG raw flag (always preserved), model identity + weights hash.
