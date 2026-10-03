# ASTERION

**Mathematics and scientific research with checkable evidence.**

ASTERION is a local research platform for exploring mathematical questions, testing scientific models and retaining reproducible evidence. AI can propose an idea; a calculation, proof obligation or experiment must support the resulting claim.

**Public update: 2 October 2026.** This is a public project overview and research-status repository. The complete local application and private study packets are not distributed here.

[Current research](docs/RESEARCH_STATUS.md) · [Help and replay](docs/HELP.md) · [Review guide](docs/REVIEW_GUIDE.md) · [Download overview](docs/ASTERION_Public_Overview_2026-10-02.pdf) · [Public checker](https://github.com/QuantumParadox/asterion-bernstein-check)

## Start with one checkable result

The separate MIT-licensed [ASTERION Bernstein Check](https://github.com/QuantumParadox/asterion-bernstein-check) verifies rational univariate polynomial bounds on [0,1]. Version 0.1.0 includes 40 recorded polynomials, explicit input limits and deliberate-corruption tests. It runs offline using Python's standard library.

A fresh downloaded copy passed 13 test methods, including 400 synthetic conversion cases, 2,000 exact point comparisons and 240 rejected semantic mutations. These are development tests, not evidence of a new theorem or independent human acceptance.

## Current research

| Track | Recorded result | Limit |
| --- | --- | --- |
| Bernstein proof foundation | Lean accepted two generic coefficient-bound theorems, 40 identities and 40 denominator lower bounds | The full qutrit theorem and the new Python checker are not formally verified |
| Retained quantum measurements | 6,144 saved IBM Quantum / Quantum Inspire shots recounted into 72 outward rational confidence enclosures | Coverage is conditional on stationary IID shots within each circuit/marginal; physical drift and chronology were not established |
| Quantum reliability reference | 28,672 simulated paths; 430,080 interval decisions recounted; 210 reference intervals checked with exact arithmetic and MATLAB | A standard concentration corollary; the condition for a larger campaign was not met |
| Scientific computation | Local Python, MATLAB, proof tools and heterogeneous computing support bounded experiments | Device availability and numerical agreement do not establish GPU speedup or quantum advantage |

The [research status](docs/RESEARCH_STATUS.md) distinguishes recorded measurements, synthetic data, exact checks and outstanding assumptions.

## Research approach

```mermaid
flowchart LR
  A[Question and assumptions] --> B[Candidate construction]
  B --> C[Classical baseline or experiment]
  C --> D[Exact check or bounded replay]
  D --> E[Preserved result and controls]
  E --> F[Independent human review]
```

Negative results and failed research-benefit conditions remain visible. Reproducing a known result is useful validation, but it is not a new discovery. Separate Python and MATLAB calculations provide implementation cross-checks, not automatically independent scientific review.

## Relationship to MIRANDA

[**MIRANDA**](https://github.com/QuantumParadox/MIRANDA) handles authorized defensive cybersecurity and forensic research. **ASTERION** handles mathematics, scientific models and quantum-information experiments. Shared provenance practices do not transfer validation from one project to the other.

## Review and participation

A useful contribution is a concrete counterexample, an independent checker replay, a correction to an assumption, or a reference showing prior art. Start with the [review guide](docs/REVIEW_GUIDE.md) and open an issue on one narrow question.

James C. Simmonds is an independent researcher and RIT Computing Security alumnus. No university or laboratory endorsement, publication acceptance, quantum advantage, award or monetary valuation is asserted.

This repository is a project overview. See [NOTICE.md](NOTICE.md) for its rights boundary. The MIT license of the separate Bernstein checker applies only to that checker repository.
