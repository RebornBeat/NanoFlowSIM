#### README.md

**Purpose.** Research-grade open nanopore sequencer that uses **wild-type Aerolysin or MspA pores** + **wild-type Phi29 DNA polymerase** + **voltage-feedback translocation speed control**, avoiding Oxford Nanopore's engineered CsgG pores and patented helicases. Compatible with open basecallers (community-trained Bonito models). USB 3.0 to host laptop or NFSIM-CON-06 Edge Compute Module.

**Key R&D pivots:**
- **Aerolysin** (preferred): hourglass geometry with sub-nm constriction; published research shows single-base discrimination capability
- **MspA wild-type** (secondary): octameric, narrow constriction
- **α-hemolysin** (legacy/baseline): widely available, research-only
- **Phi29 DNA polymerase wild-type** (NEB M0269S): processive 5'→3', controls translocation
- **Voltage feedback**: software loop reduces dependence on motor enzymes alone

**Status:** Phase 2 — research prototype. Designed for research use only; not for clinical diagnostic decisions without independent confirmation.
