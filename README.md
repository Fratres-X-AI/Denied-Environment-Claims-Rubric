# Denied-Environment Autonomy — Public Claims Rubric

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-0.1-orange.svg)](CLAIMS_RUBRIC.md)

<p align="center">
  <img src="docs/assets/claims-rubric-hero.png" width="100%" alt="Denied-Environment Autonomy — Public Claims Rubric"/>
</p>

**Thesis: low maturity is not a flaw. Low maturity with absolute language is.**

A neutral, IP-compatible rubric for evaluating public performance claims about autonomous systems under electronic warfare, GNSS denial, or datalink denial.

Nothing in it requires disclosing algorithms, mathematics, hardware topology, or any other proprietary implementation detail. It asks only for the minimum public disclosure that makes a claim evaluable: maturity, denial assumptions, sensor dependencies, error growth, environmental limits, and evidence class.

## Score a claim

Open **[CLAIMS_RUBRIC.md](CLAIMS_RUBRIC.md)**. Score six dimensions 0–2 each (max 12).

| Total | Reading |
| --- | --- |
| 0–4 | Marketing. Unverifiable by construction. |
| 5–8 | Directional. Engineering content present; not yet checkable. |
| 9–12 | Reviewable. A qualified reader can bound the claim and knows what would falsify it. |

**Absolute-language override:** any unbounded absolute — *immune, unjammable, unspoofable, guaranteed, 100%, zero drift, any threat, any environment* — scores the dimension it touches **0**. Bounded evidence cannot support unbounded claims.

## What this is / is not

| This is | This is not |
| --- | --- |
| A public scoring rubric for claim discipline | A technical specification or product |
| Compatible with NDA-protected IP | A demand for equations or hardware topology |
| Applicable to air, ground, and maritime autonomy | An endorsement of any named system |
| Versioned, challengeable, MIT-licensed | Field certification or regulatory guidance |

## Worked example

The rubric includes a self-score of [HEEL-G RUT](https://github.com/Fratres-X-AI/RUT) (11/12) — an open ground-traversability layer, not an EW system — to show that the rubric penalizes language/evidence mismatch, not low maturity.

## Citation

```bibtex
@misc{fratres_claims_rubric,
  title        = {Denied-Environment Autonomy: Public Claims Rubric},
  author       = {{Fratres X AI}},
  year         = {2026},
  howpublished = {\url{https://github.com/Fratres-X-AI/Denied-Environment-Claims-Rubric}},
  note         = {Version 0.1}
}
```

## License

[MIT](LICENSE) — © Fratres X AI. Reuse with attribution welcome.
