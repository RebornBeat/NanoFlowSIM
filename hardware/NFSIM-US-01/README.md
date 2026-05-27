#### README.md

**Purpose.** A pocket ultrasound probe that connects to any USB-C phone, tablet, or laptop. **Primary design uses a 128-element PZT linear array with software beamforming on the host GPU/NPU**, keeping the probe head simple, low-cost, and patent-clear (no CMUT-on-CMOS). Two documented variants: PVDF film wearable and (future research) optical ultrasound for MRI-compatibility.

**Why this design beats CMUT-monolithic.** CMUT-on-CMOS probes (Butterfly iQ, etc.) integrate the transducer + ASIC + beamformer in silicon. They have ~$1500+ retail price and IP encumbrance. NanoFlowSIM US-01 keeps the probe a "dumb" array of standard PZT elements with simple analog front-end, then exports raw RF I/Q data over USB-C 3.2 to the host. **All beamforming runs on the host GPU/NPU.** Software wins on cost, openness, and forward-upgrade path (better beamforming algorithms → better images, same hardware).

**Key features.**
- 128-element PZT linear array (3.5/5/7.5 MHz interchangeable cartridges)
- Software beamforming (Delay-and-Sum + plane-wave compounding + synthetic aperture) on host
- USB 3.2 Gen 1 (5 Gbps) raw I/Q streaming
- BLE 5.0 control channel for low-bandwidth metadata + battery
- Compute target: phone GPU (Adreno/Mali/Apple GPU via Metal/Vulkan/OpenCL), laptop GPU, hub+CON-06
- B-mode, M-mode, Color Doppler, Pulsed Wave Doppler (all GPU-rendered)
- Compatible with any iOS/Android/Linux/Windows host

**Status:** Phase 2 — clinical demo prototype.
