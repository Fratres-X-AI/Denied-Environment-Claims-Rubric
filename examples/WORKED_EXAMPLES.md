# Worked Examples

These examples are anonymized. They demonstrate how the rubric evaluates the
relationship between language, maturity, assumptions, and evidence. They are
not judgments about any real company or person.

## Example A — Concept claim

**Claim:** “Our architecture could preserve navigation during GNSS denial.”

**Public record:** A block diagram and simulation concept are provided. No
hardware or field result is claimed.

**Assessment:** Directional. This is appropriately bounded language for an E0
concept. The next useful artifact is a declared sensor inventory, error model,
and repeatable simulation case.

## Example B — Bench claim

**Claim:** “A breadboard maintained position estimates during a 30-minute
record-replay GNSS denial test in the lab.”

**Public record:** The author reports the IMU class, denial duration, test count,
95% error, and pass criterion. The truth source is a separate motion reference.

**Assessment:** Reviewable for that laboratory envelope if the evidence is
available for inspection. It does not support a field, operational, or
universal claim.

## Example C — Overbroad claim

**Claim:** “Our system is unjammable, unspoofable, and guaranteed to complete
the mission in any environment.”

**Public record:** No denial waveform, sensor inventory, error envelope,
environmental conditions, test count, or independent truth source is stated.
The author says detailed information is available only under NDA.

**Assessment:** Marketing / unverified. The NDA may protect implementation
details, but it does not supply public bounds or establish evidence class.
The claim becomes reviewable only after it is rewritten around a defined
envelope and supported by evidence appropriate to that envelope.

## Example D — Honest maturity correction

**Original:** “Field-ready autonomy that works under total denial.”

**Bounded revision:** “Prototype visual-inertial estimator demonstrated in 12
indoor record-replay tests with a 95% position error below 1.5% of path length
for 180 seconds. Outdoor lighting, obscurants, and live RF conditions remain
untested.”

**Assessment:** The revision is more useful even if the technology has not
changed. It tells a qualified reader what happened, what did not happen, and
what the next gate should measure.
