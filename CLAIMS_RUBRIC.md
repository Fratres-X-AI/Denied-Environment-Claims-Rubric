# Denied-Environment Autonomy — Public Claims Rubric

**Version:** 0.1 (2026-07-23) · **Status:** open draft · **License:** [MIT](LICENSE) — reuse with attribution welcome.

Public performance claims about autonomous systems under electronic warfare, GNSS denial, or datalink denial are frequently absolute and rarely bounded. This rubric defines the **minimum public disclosure** required for such a claim to be evaluable by a qualified reader. Nothing in it requires disclosing algorithms, mathematics, hardware topology, or any other proprietary implementation detail.

It applies to air, ground, and maritime autonomy claims. A worked example against an open Fratres X AI repository appears at the bottom.

**Thesis: low maturity is not a flaw. Low maturity with absolute language is.**

## How to score

Score each of the six dimensions **0, 1, or 2**:

| Score | Meaning |
| --- | --- |
| 0 | Absent, or contradicted by absolute language |
| 1 | Named, but not quantified |
| 2 | Quantified, with conditions stated |

**Absolute-language override:** any unbounded absolute — *immune, unjammable, unspoofable, guaranteed, 100%, zero drift, any threat, any environment* — scores the dimension it touches **0**, regardless of other content. Bounded evidence cannot support unbounded claims.

| Total | Reading |
| --- | --- |
| 0–4 | Marketing. Unverifiable by construction. |
| 5–8 | Directional. Engineering content present; not yet checkable. |
| 9–12 | Reviewable. A qualified reader can bound the claim and knows what would falsify it. |

## The six dimensions

### D1 — Maturity level

State the TRL (NASA/DoD definition) **and what it attaches to**: a component, a subsystem, or the integrated system. Component TRL is not system TRL — integration risk means the least-proven critical function bounds honest system-level claims.

Public language must stay inside the ceiling for the stated maturity:

| Stated maturity | NASA/DoD meaning | Ceiling for public language | Not supportable |
| --- | --- | --- | --- |
| TRL 1–3 | Principles observed through analytical / experimental proof of concept | "concept", "analysis indicates", "simulation suggests" | Any performance claim |
| TRL 4 | Component / breadboard validated in a **laboratory** environment | "components bench-validated under stated lab conditions" | "field-verified", system-level outcome claims, guarantees |
| TRL 5–6 | Component → system prototype demonstrated in a **relevant** environment | "demonstrated in a relevant environment under conditions X" | Operational claims, "any environment" |
| TRL 7–8 | Prototype demonstrated in an **operational** environment → system qualified | "demonstrated / qualified within the tested operational envelope" | Claims beyond the tested envelope |
| TRL 9 | Proven through successful mission operations | "proven over N operations under conditions X" | "immune", "guaranteed", universal claims |

No TRL supports the words *immune*, *unjammable*, or *guarantee*. Higher TRLs buy tested envelopes, not certainty.

### D2 — Denial model

State exactly what is denied, how, and when:

- **Channels:** GNSS (which constellations; jammed, spoofed, or meaconed), two-way links (C2, mesh, SATCOM), and receive-only channels.
- **Threat classes:** noise/barrage jamming (with J/S or field strength), matched spoofing, repeater/meaconing, HPM/DEW exposure (field level, pulse class).
- **Geometry and onset:** denial from launch or mid-mission; contiguous or intermittent; over what portion of the route.

Two physics notes that a complete denial model must survive:

- **Receive-only paths count.** A platform with zero outbound RF can still carry receive apertures (GNSS, EO/IR, acoustic, altimetry). A GNSS receiver emits nothing and is still the canonical spoofing victim. Emission control changes detectability and link dependence; it does not, by itself, change navigation error growth or sensor deception exposure.
- **HPM does not require cooperation.** High-power microwave couples through apertures, seams, and cabling ("front door" and "back door") regardless of whether the target intentionally transmits or receives. Hardening is qualified against named standards and field levels (e.g., MIL-STD-461, MIL-STD-464), per configuration — results are level-specific, never absolute.

### D3 — Sensor and dependency inventory

Enumerate every input channel and external dependency: inertial unit (grade and bias instability), magnetometer, barometer, cameras (visible/IR), lidar or radar altimeter, terrain/feature databases, odometry, clocks (holdover spec).

Every input channel is a potential degradation or deception surface: vision degrades under illumination, obscurants, decoys, and camouflage; terrain matching degrades over featureless, changed, or seasonal terrain and stale maps; magnetometers degrade near anomalies and vehicle interference; barometers drift with weather; clocks drift under holdover.

"Unspoofable" is only evaluable against a named input inventory. A claim that names no inputs has no meaning.

### D4 — Error growth model

State horizontal error (CEP or 95%) **as a function of time and distance** under the declared denial model, naming the aiding source. For reference, well-published behavior:

- **Unaided inertial:** position error from accelerometer bias grows roughly quadratically with time, and from gyro bias roughly cubically. Consumer/industrial MEMS units reach kilometre-class error within minutes unaided. Better grades improve the constants, not the shape.
- **Visual / visual-inertial odometry:** published benchmark-class results typically fall in the 0.5–2% of distance-traveled range under favourable illumination and texture.
- **Terrain- / feature-relative navigation:** bounded by map currency and feature density; fails over featureless or changed terrain.
- **Celestial:** visibility-limited. **Magnetic anomaly:** map- and interference-limited. **Signals of opportunity:** unavailable under total RF denial, by definition.

Terminal-accuracy claims additionally require the handoff error budget versus the endgame sensor's acquisition basket. All of these are envelope statements — publishing "CEP ≤ X m at Y km under conditions Z" reveals nothing about implementation.

### D5 — Environmental and platform limits

State the conditions under which the numbers hold: illumination, weather, obscurants, terrain class, wind, temperature, and the EMI environment. State platform constraints: SWaP and **cost class** — claimed performance must be consistent with the sensor grade the stated cost class can carry (a navigation-grade inertial unit alone can exceed the total cost of an attritable airframe).

The absence of any stated limit is itself a red flag. No real system is condition-free.

### D6 — Evidence class

State which class of evidence backs each claim, with sample size and **pre-declared** pass/fail criteria:

| Class | What it is | Minimum disclosure |
| --- | --- | --- |
| E0 | Analysis / simulation (stated models, Monte Carlo) | Model class, parameter ranges, run count |
| E1 | Bench / hardware-in-the-loop (lab denial emulation, record-replay spoofing, anechoic EMI) | Rig class, injected threat model, N runs, pass criteria |
| E2 | Subscale or captive field trials, instrumented | Venue class, truth source, N sorties, conditions |
| E3 | Full-system field trials under controlled live denial, independently witnessed | Truth instrumentation independent of the system under test, N, pre-declared criteria |
| E4 | Operational employment | Aggregate outcomes under stated conditions |

Two rules:

1. **Claim class cannot exceed evidence class.** "Field-verified" requires E2 or above; bench/HIL is E1 by definition.
2. **The truth source must be independent** of the system under test.

## What IP protection does and does not cover

Legitimately protectable behind NDA: algorithms, filters, mathematics, hardware topology, waveforms and frequencies, integration interfaces, exact venues and partners.

Publishable without exposing any of that: everything this rubric asks for — maturity level, denial model, dependency inventory at class level, error envelopes, environmental limits, evidence class with N and criteria. Mature defense programs publish envelope-level facts (range classes, accuracy classes, environmental qualifications) while protecting implementation, routinely.

Secrecy can protect *how* a system works. A public performance claim remains publicly accountable for *whether* it works, to what bound, under which conditions. When every bound is secret, the public claim reduces to an appeal to trust.

## Red-flag lexicon

| Public phrase | Why it cannot be supported |
| --- | --- |
| "unjammable" / "immune to EW" | Jamming margin is measured in dB against stated waveforms and geometries; margin is finite by physics |
| "unspoofable" | Only evaluable against a named input inventory; every sensor is an input channel |
| "zero drift" / "no operational drift" | Unaided inertial error growth is unbounded; aiding bounds error only under stated conditions |
| "guaranteed outcome under 100% denial" | A guarantee over an open-world environment requires evidence over that world; no finite test campaign provides it |
| "any threat vector / any environment / any platform" | Universal quantifiers are not testable; envelopes are |
| "field-verified" backed by lab evidence | Field claims require evidence class E2+; bench/HIL is E1 |
| "the math guarantees it" | Deterministic logic over stochastic inputs yields bounded-probability outcomes at best; state the uncertainty model |
| "absolute EMP / EW hardening" | Hardening is qualified against named standards, field levels, and configurations; results are level-specific |

## Worked example — HEEL-G RUT

[HEEL-G RUT](https://github.com/Fratres-X-AI/RUT) is not an EW system; it is an open ground-traversability layer. The dimensions generalize to any autonomy performance claim (D2 maps to "declared operating assumptions"). Scoring its public claims:

| Dimension | Score | Basis |
| --- | --- | --- |
| D1 Maturity | 2 | Phase 0/1/2 labels; "not field-certified, not NRMM-equivalent" stated in the README |
| D2 Assumptions | 2 | Bekker/Janosi model domain and soil-provenance classes stated; sim ≠ field throughout |
| D3 Dependencies | 2 | Inputs enumerated (soil YAML, slope, moisture, perception confidence); demo priors flagged illustrative |
| D4 Error growth | 1 | Residuals vs open corpora published with honest limits; no field error envelope yet |
| D5 Limits | 2 | Small-wheel / light-load regime warnings on the assess path; explicit out-of-scope list |
| D6 Evidence | 2 | E0–E1 (CI-locked synthetic scenarios, literature kernels, verifiable evidence JSON) — and the claim language stays at that class |

**Total: 11/12.** The missing point is a real gap — no field error envelope exists yet — and the public claim language reflects that. The rubric penalizes only the mismatch between language and evidence, never the maturity itself.

## References

- NASA, *Technology Readiness Level Definitions* (NPR 7123.1).
- U.S. DoD, *Technology Readiness Assessment (TRA) Guidebook*.
- P. D. Groves, *Principles of GNSS, Inertial, and Multisensor Integrated Navigation Systems*, 2nd ed., Artech House, 2013.
- MIL-STD-461 (EMI requirements) and MIL-STD-464 (electromagnetic environmental effects) — how hardening is actually specified.
