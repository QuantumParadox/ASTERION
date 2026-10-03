# What syndrome data can identify: an exact finite decoder audit

James C. Simmonds · ASTERION independent research · 3 October 2026

Working note for criticism. AI assisted; not peer reviewed. The finite arithmetic below is checked, while novelty and practical research value remain unresolved.

## Abstract

We audit the gap between an observable syndrome distribution and a latent fault model in a fixed, two-round repetition-code example. Exact optimization over 4,096 fault assignments shows that the nominal syndrome law permits both signs of a frozen decoder-risk comparison. An exploratory two-atom construction preserves that complete syndrome law and the earlier single-fault rate intervals while reversing the comparison. Its exact minimum total-variation distance to a tie is 1376977939449/625000000000000. Adding the final known-preparation logical outcome identifies the observed decoder risk, but does not in general identify the fault moments in an earlier sufficient certificate. We separately audit label accounting on 200,000 previously exposed measured shots, a public compiled adder, and six small provider diagnostic circuits. These checks establish reproducible finite results and expose assumptions; they do not establish a new general method or quantum advantage.

## 1. Model and registration

The primary question and provider limits were frozen in PROTOCOL.json at 19:05:44 UTC. The stronger rate-box witness and known-single analysis are exploratory extensions, recorded after the primary calculation. Calibration analysis details were fixed before its new resampling; the source data were already exposed.

There are three data bits initially 000 and two extraction rounds. In each round, three X-fault indicators act before parity extraction, one joint X0X1 fault acts after extraction, and two indicators flip the recorded parity bits. The twelve indicators x0,...,x11 are ordered by round as (data0,data1,data2,post-extraction pair,record0,record1). The six observed bits include both round records and an ideal terminal boundary parity. In binary arithmetic:

```
S0 = x0+x1+x4          S1 = x1+x2+x5
S2 = x0+x1+x6+x7+x10   S3 = x1+x2+x3+x7+x8+x11
S4 = x0+x1+x6+x7       S5 = x1+x2+x3+x7+x8+x9
L  = x0+x3+x6+x9
```

Here addition is modulo two. Encode S as sum(2^j Sj); fault mask x is sum(2^j xj). L is final data0, the label required by the frozen decoder comparison. This classical X-sector model assumes ideal boundaries and recovery and excludes phase errors, leakage and arbitrary native-gate noise. It is not a code protecting arbitrary quantum information.

The nominal law p has independent rates (1/100,1/100,1/100,1/200,1/50,1/50), repeated twice. This model and frozen decoders come from ASTERION's HISTORY-20261003; the sparse certificate comes from CORRELATION-20261003. Their required source data and prior notes are retained in inputs/prior. QIDENT-20261002 is earlier project background, not external validation. The history decoder is nominal MAP using all S; the terminal decoder is nominal MAP using S4,S5. Ties choose zero. Both decisions stay fixed under all perturbations. Let d(x) be history failure minus terminal failure, so negative expectation favors history. Exact nominal expectation is

`E_p[d] = -1376977939449/312500000000000 = -0.0044063294062368`.

The earlier independent-rate box has data rates [0.005,0.015], post-extraction pair rate [0.002,0.008], and record rates [0.01,0.03], repeated across rounds. The present unrestricted fiber bounds do not assume that box unless explicitly stated.

## 2. Sharp observable-law bounds

For a finite observation map T and a fixed observed law h, every compatible latent law q satisfies

`sum_y h(y) min_{T(x)=y} f(x) <= E_q[f] <= sum_y h(y) max_{T(x)=y} f(x)`.

Proof: within each fiber, the contribution is h(y) times a convex combination of its f values. Concentrating each fiber's mass at an argmin or argmax attains the endpoints. This is a standard finite linear-programming argument, not a new theorem. Different functionals can require different attaining laws.

For T=S, the binary observation map has rank six and each of its 64 fibers contains 64 masks. T=(S,L) has rank seven and 128 fibers of size 32. Toggling mask 7, the first-round XXX operation, preserves S and flips L. The decoders disagree only in syndrome bins 32,33,35,36,37,39. Their total nominal mass is

`w = 2994467870937/625000000000000 = 0.0047911485934992`.

Thus the exact S-only risk interval is [-w,+w]. For T=(S,L), d is constant on each fiber and the interval collapses to E_p[d]. A measured label can identify the observed comparison without identifying a physical fault model.

The independent checker evaluates 14 functionals under both observation maps: d, the twelve selected singleton/pair terms, and their signed sum g. It checks 28 envelopes, 2,688 fiber records, and both endpoints' attaining distributions. No numerical optimizer tolerance is used for these rational conclusions.

## 3. Same-syndrome reversal within the earlier rate box

Mask 512 contains only x9. Mask 2304 contains x8 and x11. Both produce S=32, but d is -1 at the first and +1 at the second. For

`q_delta = p - delta e_512 + delta e_2304`,

the entire syndrome law is unchanged and the risk difference increases by 2 delta. The source atom has mass 1080061695642659805999/250000000000000000000000, sufficient for both constructions below.

At delta=23/10000, the changed marginal rates are x8=123/10000, x9=27/10000, x11=223/10000. All remain within their earlier intervals; other marginal rates stay nominal. The new risk difference is

`60522060551/312500000000000 = +0.0001936705937632`.

For any two distributions and |d|<=1, the expectation change is at most 2 TV(p,q), where TV is half the L1 distance. A tie therefore requires TV >= -E_p[d]/2. The construction attains equality at

`delta_star = 1376977939449/625000000000000 = 0.0022031647031184`,

while preserving the full syndrome law and the single-rate box. Hence this is the exact minimum distance to a tie under those constraints. A strict reversal occurs above that radius; the radius itself is a tie. Exact nominal single means are not preserved. The correlated witnesses are mathematical fault laws, not separately demonstrated physical device channels. They do not contradict the prior theorem under independent faults or its selected-pair assumptions.

## 4. Which certificate moments are observable?

The earlier pointwise sufficient bound is

`d <= g = -x9 + x9*(x0+x1+x2+x3+x5+x6+x7+x8+x11) + x11*(x2+x8)`.

It holds on all 4,096 masks. The eleven positive pair moments are not automatically observable merely because a conditional certificate uses them. With only the nominal S law, or only the joint (S,L) law, none of the twelve selected moment functionals is identified. The signed function g itself also varies within fibers; nonidentification is checked directly, not inferred just from its individual terms.

An additional assumption changes one conclusion. If all exact single means are externally known, then x9 xor x11 = S3 xor S5 yields

`E[x9*x11] = (E[x9] + E[x11] - Pr[S3 xor S5 = 1])/2`.

The other ten selected pairs remain nonidentified even when both (S,L) and all twelve single means are fixed. For each such pair (i,j), the checker constructs positive laws p +/- epsilon*(-1)^(xi+xj), with epsilon=min(p)/2. Binary-character orthogonality preserves every observed fiber mass, normalization, and every singleton; the selected pair expectation differs by 2048 epsilon. These tiny witnesses prove nonuniqueness. They do not imply an experimentally resolvable difference or quantify a practical learning rate.

## 5. Recorded-data label accounting

We retained four 50,000-shot X-basis, one-round distance-three patches from the Google Quantum AI surface-code dataset. A fresh Stim 1.16.0 conversion from raw measurements and sweep bits reproduced all 1.8 million retained detector/observable parity bits and the four joint histograms. Custody covers selected-member CRC32 and pinned local SHA-256, not the full upstream archive checksum or authorship. This is retrospective reuse, not a new holdout or fresh experiment.

For each patch, three frozen decoders (Bayes, empirical table, QML) are compared with frozen matching. Let D indicate a disagreement, r=Pr(D), and theta=Pr(candidate wrong | D). The paired risk difference is r(2 theta-1). When D=0, the paired difference is exactly zero, so labels there contribute no information to this comparison.

At fixed physical sample counts N=128,512,2048, we simulated 2,000 multinomial draws per setting from the frozen empirical law: 36 settings and 72,000 replicates. Full paired-data reuse and disagreement-only labeling use the same samples and return identical statistics. Two Clopper-Pearson intervals, each with error budget alpha/2 for alpha=0.01, bound r and theta. Conditional coverage given random K disagreements and a union bound justify a per-setting product interval. At K=0, theta's interval is [0,1]. There is no simultaneous 36-setting claim and no adaptive stopping.

Observed simulated coverage was 99.85% to 100%. No setting resolved a decoder improvement in any replicate. Bayes comparisons remained unresolved; some QML comparisons resolved a disadvantage. Coverage is a simulation diagnostic under the assumed iid empirical law, not a physical drift guarantee.

If every screened shot costs 1 and each label costs kappa, full labeling costs N(1+kappa), whereas targeted labeling costs N+K*kappa. We report kappa=0,1,10,100 as hypothetical accounting scenarios. Both methods use N physical shots. At kappa=0 there is no saving. In known-preparation memory experiments the final readouts often already provide labels, so label savings may be bookkeeping only. No shot-efficiency or decoder-improvement gate passed.

## 6. Separate fault-tolerant compilation audit

We pinned PNNL FTCircuitBench at commit 116df005d68404e4c21cbd91b570c171deb06f7c and retained the original adder_10q.qasm, its saved Gridsynth Clifford+T artifact, and the repository license. This is a narrow artifact audit, not reproduction of the full paper. The paper describes initial unoptimized compilations; its saved artifact is not an optimality claim. Its specific generating synthesis tolerance was not found.

Independent counts agree on 10 qubits, 1,202 H, 210 S, 65 CNOT and 1,120 T operations: 2,597 total, dependency depth 1,494 and dependency T depth 640. The original expands to 5 X, 17 CNOT and 8 Toffoli operations. It retains the embedded 1+15 preparation. Only final measurements are removed for unitary comparison.

We reconstruct all 1,024 input columns, using one global phase chosen from the original/compiled trace overlap. At that Frobenius-aligning phase, the numerical operator-norm residual is 0.2031076762 and Frobenius residual 1.5508449558. This is not the minimum operator residual over all possible phases. Worst full-register computational-basis output error is 0.0038585430; not all those inputs satisfy zeroed-ancilla adder conventions. For the file's configured zero input, the correct full-register output is index 514 with probability 0.9998993047. Basis probabilities alone miss coherent error.

A standard, already-known seven-T/T-dagger Toffoli decomposition yields 56 T/T-dagger operations, 65 CNOT, 16 H and 5 X for the same original circuit. Exact algebraic checks of all 64 entries of the local Toffoli identity pass; the whole-unitary numerical comparison has maximum entrywise absolute difference 3.78e-15. The 20:1 T-family count ratio is a comparison with this saved artifact, not a new compiler result, physical cost ratio, or speedup claim. It does not establish a defect in the current FTCircuitBench implementation.

RTX 5090 and RTX 4090 independently replayed all compiled columns in complex128 and agreed with Qiskit CPU to at most 1.05e-13. Timers start after allocation and synchronization; warm-up state was not controlled and implementations differ. These single execution timings are not a GPU ranking or fair speed benchmark. A separately implemented MATLAB full-unitary audit passed at the unchanged 1e-10 comparison tolerance and rejected wrong bit ordering and a reversed T phase. Its receipt is resources/MATLAB_RESOURCE_RESULT.json. The failed parser attempt and original implementation are preserved separately; only scalar operand parsing and the launch path were repaired.

For an explicitly assumed marginal gate-failure model, a union bound gives Pr(any faulty gate) <= sum_i p_i, without independence. A uniform 1% total budget over 2,597 operations gives p_i <= 1/259700. This arithmetic does not cover coherent synthesis discrepancy, physical qubit counts, distillation factories, decoding latency or runtime. Those require their own stated architecture and noise model.

## 7. New provider diagnostics

IBM job db0laopb694s73dr52vg executed six five-qubit circuits on ibm_fez, retaining all 3,072 shots. Provider charge time was 3 QPU seconds. The dated post-run Open Plan snapshot reported 546 seconds remaining. Both preparation and compiled ideal simulations passed before submission.

| Preparation/control | IBM ideal-event count | QI QX emulator |
|---|---:|---:|
| 000 | 491/512 | 128/128 |
| Logical XXX | 480/512 | 128/128 |
| X on data0 | 489/512 | 128/128 |
| X on data1 | 487/512 | 128/128 |
| X on data2 | 488/512 | 128/128 |
| Logical-plus, final X basis | 465/512 | 128/128 |

Quantum Inspire jobs 1497771 through 1497776 ran on QX, a provider simulator. The physical backends were offline or calibrating at the access checks. The local QX simulator was installed in an isolated study runtime from a SHA-pinned official wheel after the initial missing-module preflight. That failure is preserved. There were no speculative retries or additional experiments.

The ideal event includes both extracted parity bits and the expected final data string; the plus control accepts even data parity. All raw shots, provider histograms and QI final results reconcile. Bit-reversed, truncated and altered-count copies are rejected by the offline diagnostic checker. Hoeffding intervals use a union bound over the twelve reported rates, assuming iid shots within each setting. They do not cover systematic errors.

These one-round controls verify wiring, preparation and result handling. They neither identify the two-round latent model nor certify entanglement, fault tolerance or a hardware decoder gain. The XXX syndrome symmetry is an exact ideal-model statement; different physical preparations can have different noise.

## 8. Validation and useful next gate

The exact checker is separate from the producer. A separately implemented MATLAB model passed on Z890, Z790, GE63, Mac mini M4 and Red Hat VM. Its integer propagation and MAP tie decisions are exact; probability sums are numerical with declared tolerance. Semantic corruptions are retained. These are independent implementations operated within one AI-assisted project, not independent human review.

The smallest useful next gate is external assessment of the observation assumptions and the compiled artifact's synthesis provenance. No further QPU campaign is justified by these diagnostics alone. The DOE roadmap is motivation for careful validation and resource accounting, not evidence of DOE participation, eligibility, or endorsement. Broad research completion, publication acceptance and award prospects are not established.

## Sources and prior-art boundaries

- [DOE, The Quantum Inflection Point](https://www.energy.gov/science/articles/quantum-inflection-point-charting-science-first-roadmap-nation): roadmap context only.
- [Wagner et al., Pauli channels can be estimated from syndrome measurements in quantum error correction](https://arxiv.org/abs/2107.14252): existing syndrome-based noise-learning methods and assumptions.
- [Xiao et al., arXiv:2601.21472v2](https://arxiv.org/abs/2601.21472v2): logical-class learnability under specified local-noise and circuit assumptions; see literature review for theorem-level comparison.
- [Zheng et al., arXiv:2601.22286](https://arxiv.org/abs/2601.22286): logical-noise learnability and unlearnable degrees of freedom. Do not reduce its assumptions to independent physical faults.
- [Hockings et al., arXiv:2404.06545](https://arxiv.org/abs/2404.06545): optimized characterization with shared-shot covariance and experiment duration; targeted-label accounting here is not a new allocation algorithm.
- [Google Quantum AI data, Zenodo 13273331](https://zenodo.org/records/13273331) and [Nature paper](https://doi.org/10.1038/s41586-024-08449-y): recorded hardware data and publication context. Dataset derivations and exposure limits are retained in inputs/DATA_CUSTODY.json.
- [Harkness et al., FTCircuitBench v2](https://arxiv.org/abs/2601.03185v2), [pinned source](https://github.com/pnnl/FTCircuitBench/tree/116df005d68404e4c21cbd91b570c171deb06f7c): resource artifact and attribution.
- [Ross and Selinger](https://arxiv.org/abs/1403.2975) and [Gridsynth documentation](https://www.mathstat.dal.ca/~selinger/newsynth/): synthesis norms and phase conventions.
- [Cuccaro et al., ripple-carry adder](https://arxiv.org/abs/quant-ph/0410184): original adder attribution.

The literature review records read depth, theorem assumptions and unresolved overlap. No claim of exhaustive literature coverage or novelty follows from this search.
