# ASTERION research status

Dated 2 October 2026. This curated public summary describes selected local studies. Original failures, assumptions and older results are preserved in local records. This documentation update checked source-artifact hashes and the published checker release; it did not repeat the scientific campaigns.

## Public Bernstein checker

Version 0.1.0 at [commit 469b851](https://github.com/QuantumParadox/asterion-bernstein-check/tree/469b851402c96a72cc90e554b4328934c415dc89) checks rational univariate polynomial enclosures on [0,1]. The normalized coordinate is not automatically the physical measurement parameter.

All 11 public files matched the approved release. A fresh GitHub download passed 13 test methods: 40 recorded denominator polynomials, 400 deterministic synthetic conversions, 2,000 exact point comparisons and 240 semantic mutations. The source, manifest and tests are public. The implementation relies on Python and its rational arithmetic; it is not formally verified.

A rejected certificate can state a true inequality that the supplied certificate fails to prove. A hash detects a change relative to the referenced bytes; it is not a signature.

Next test: an outside replay and review of parser behavior, certificate soundness and usefulness relative to existing tools. Main false-positive risk: treating a correct polynomial enclosure as proof of a physical reduction or complete qutrit compatibility result.

## Partial Lean foundation

The retained 2 October run used Lean 4.33.1 and mathlib commit 0df444a360eaa60ab8c11dca51a86af692955474. It accepted two generic coefficient-bound theorems, 40 polynomial identities and 40 bounds D(z) >= 1 on [0,1]. Two false-proof variants were rejected. A separate exact bridge checked coefficients against the original data.

The recorded axiom audit contains propext, Classical.choice and Quot.sound. That Lean run is historical evidence and was not repeated for this public update. The public Python checker does not invoke the Lean kernel.

Matrix PSD obligations, operator curvature, parent-effect repair, dual normalization and the complete uniform-width theorem remain outside this formalization. The underlying Bernstein method is established mathematics.

Next test: independent review of the full statement and bridge, then one explicitly scoped missing proof obligation. No universal theorem or full-stack verification is claimed.

## Uncertainty in retained quantum measurements

The study used 6,144 real saved shots: 5,632 IBM Quantum and 512 Quantum Inspire. It produced 72 outward rational enclosures of equal-tailed binomial confidence limits. Exact integer tails, 325 small-case sums, eight semantic controls and a separate MATLAB numerical recount passed. Bit-reversal controls were rejected even after recomputing counts and intervals.

The simultaneous coverage lower bound is 95% conditional on stationary IID shots within each circuit/marginal. Different bits and circuits need not be independent for the union bound. Stationarity was not physically validated. Hypothetical total-variation budgets are sensitivity assumptions, not measured drift.

These are retained measurements, not a fresh provider experiment or a calibrated platform ranking. Next test: establish acquisition chronology and a defensible physical calibration model before making drift claims. Main false-positive risk: reporting conditional confidence coverage as a measured device guarantee.

## Quantum reliability reference pilot

A frozen local simulation used seven scenarios with 4,096 paths each. A separate replay recounted 430,080 observation-level interval decisions. Exact arithmetic checked 210 reference intervals and rejected six altered scientific inputs. MATLAB separately evaluated 210 formulas.

The comparison of a stationary-prefix interval with a current-probability target is deliberately misspecified when the mean drifts. It is not a competitive drift-aware baseline. Under linear drift, the reference covered 4,094 of 4,096 simulated paths; its wider intervals reflect the cost of the assumed drift allowance. Intentional invalid-assumption controls failed and were preserved.

The implemented bound is a standard concentration corollary. No new hardware-reliability or decoder gain was established, and the condition for a large distributed campaign was not met. The pilot ran on CPU and MATLAB; it establishes no GPU acceleration or quantum advantage.

Next test: identify a concrete prior-art gap or consenting external use case before enlarging the study. Empirical simulated coverage is not a proof or a real-device reliability estimate.

## Evidence and next priorities

[EVIDENCE_INDEX.json](EVIDENCE_INDEX.json) lists retained artifact digests. Apart from the separate public checker, the full packets are local and available for scoped review on request. Their historical release receipts record fresh-extraction replay and corruption rejection. Hashes are unsigned and do not establish authorship.

Priorities are independent review, a useful contribution to an existing benchmark and a frozen evaluation with meaningful baselines. Novelty, full qutrit formalization, physical drift validation and outside acceptance remain open. A larger hardware inventory is not evidence that these gaps are resolved.
