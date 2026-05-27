### NFSIM-ECG-02 — 12-Lead ECG Vest

**README.** Wearable textile vest with 12 standard ECG leads. Clinical-grade diagnostic ECG without the wired cable mess. Wireless to phone/hub. Battery powered.

**SPECIFICATIONS.** 12 leads (RA, LA, LL, RL, V1–V6) via conductive textile or hydrogel electrodes. ADS1298 ×2 (8 channels each, sharing reference) → 24-bit, 250 Hz. Resting ECG (10s) or exercise ECG (continuous). BLE + Wi-Fi. ~$145.

**THEORY.** Standard 12-lead diagnostic ECG.

**BLOCK DIAGRAM.** ADS1298 ×2 → STM32H7 → BLE + Wi-Fi. Textile electrodes integrated into vest.

**ASSEMBLY.** Conductive textile electrodes (woven Ag) sewn into vest at precise anatomical positions. Flex PCB routes signals to chest pocket housing electronics.
