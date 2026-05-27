#### README.md

**Purpose.** Multi-protocol gateway aggregating data from every NanoFlowSIM device in the household, field clinic, or lab. **Two-tier architecture:** (1) **Base Unit** (~$110) handles all I/O and relay — BLE central + USB host + 434 MHz receiver + Wi-Fi/Ethernet + NFC + audit logging. (2) **Optional Edge Compute Module (CON-06)** plugs into the base via M.2 connector to add a Jetson Orin Nano / RK3588 / Pi CM5 SoM — turning the hub into a complete standalone "AI workstation" that doesn't need a phone or laptop.

**Why the flexible architecture.** Users have radically different setups: a home user with a phone wants relay only; a rural clinic wants an all-in-one offline AI workstation; a hospital wants ethernet integration with their FHIR system. One hardware base + optional compute module covers everyone.

**Status:** Phase 1 (base unit) — primary build target. CON-06 module is Phase 1 follow-on.
