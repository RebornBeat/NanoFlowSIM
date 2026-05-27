#### README.md

**Purpose.** Subcutaneous interstitial glucose sensor with **AI-based drift correction as the primary mechanism**. Uses open polyurethane + Nafion + glucose oxidase chemistry (no proprietary 14-day membrane) and compensates for drift via a Bayesian Kalman filter trained on community datasets. Optional fingerstick reference anchors for high-confidence intervals.

**Why drift correction is the win.** Commercial CGMs (Dexcom G7, Libre 3) achieve 14-day wear by using proprietary anti-fouling membranes. Open polyurethane + Nafion drifts more — but a properly calibrated drift model recovers most of the accuracy. NanoFlowSIM ships the model card so users see exactly how their readings are corrected and what confidence to apply.

**Status:** Phase 1 — primary build target.
