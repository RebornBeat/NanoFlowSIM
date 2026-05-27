#### README.md

**Purpose.** Adhesive single-lead ECG patch designed for 30-day continuous wear. Detects AFib + other arrhythmias **on-device** using a 25 KB TFLite Micro model — never streams continuous raw ECG to a cloud service by default. Raw waveform preserved in onboard 8 MB flash; arrhythmia events trigger BLE alerts; user downloads the full waveform via phone for clinician review.

**Why Edge AI as primary.** Commercial 30-day ECG patches (Zio XT, BodyGuardian, etc.) stream raw ECG to a cloud service for over-read by a technician + cardiologist. This is expensive ($300–$1500 per study) and raises privacy concerns. On-device AI puts the user in control: nothing leaves the device unless the user explicitly consents to share specific event clips with a clinician.

**Status:** Phase 1 — primary build target.
