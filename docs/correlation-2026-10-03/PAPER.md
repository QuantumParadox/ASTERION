# Moment certificates for the dependence sensitivity of a fixed syndrome-history decoder

James C. Simmonds · Independent ASTERION research · Rochester, New York

Working research note, 3 October 2026. Not submitted or peer reviewed. AI-assisted construction and checking are disclosed below. Affiliation with RIT is alumni status, not an institutional research appointment.

## Abstract

Independent fault models can support uniform decoder comparisons while concealing sensitivity to dependence. We examine two fixed decoders of a finite, two-round, three-data-qubit repetition-code X-error model. At the nominal independent law, the history-aware decoder has lower failure probability than terminal-only MAP decoding. An exact linear-programming certificate shows that the minimum total variation distance to a tie, while preserving every single-fault marginal, is 0.0053522424551950587753. In contrast, preserving all pairwise moments gives a sharp nominal upper bound of -163/40000 on the history-minus-terminal risk. A sparse quadratic majorant then supplies a uniform bound of -49/62500 throughout the original probability box, requiring only eleven pair-moment conditions and allowing arbitrary higher-order dependence. The proof also yields an explicit allowance for positive deviations in these moments. A separate retrospective study applies the finite sensitivity calculation to 200,000 previously exposed experimental surface-code shots. It characterizes empirical ranking fragility rather than physical fault correlations. The contribution is a small, reproducible certificate and a model-specific sufficient condition; the optimization machinery is established, and novelty and publication suitability remain open.

## 1. Question and relation to prior work

For fixed decoders H and T, let d(x) be their failure-indicator difference on fault assignment x. We ask which information about the fault law is sufficient to maintain E[d]<0. The purpose is to distinguish uncertainty in individual rates from uncertainty in dependence. We do not optimize or retrain either decoder during this analysis.

Moment-constrained probability bounds and polynomial majorants have extensive prior art. Bertsimas and Popescu formulate such bounds through convex optimization and duality [1]. Optimal uncertainty quantification also explicitly optimizes over laws consistent with available information [2]. Neither finite linear programming nor its exact rational verification is introduced here.

Molavi, Saad and Albarghouthi analyze decoder accuracy through fault polynomials and physical-rate intervals [3]. Their Section 5 writes fault-string probabilities as products of independent channel outcomes. Our earlier ASTERION HISTORY benchmark used the same elementary multi-affine principle on a small example. This note instead varies the joint law while retaining specified moments. It is a complementary finite example, not a claim that [3] is incorrect or that no related dependence-robust methods exist.

Experimental syndrome extraction on restricted connectivity provides motivation, including the repetition-code study by Kim et al. [4]. That work is not reproduced by our twelve-variable model. Google Quantum AI's public dataset [5,6] provides a separate empirical test of the sensitivity implementation. Its detector bits must not be interpreted as directly observed fault indicators.


Related dependence-aware optimization is much broader than this example. Delage and Ye model uncertain means and covariance with statistical ambiguity sets [7]; our exact equalities are conditional assumptions or observed histogram constraints, not estimated confidence regions. Gao and Kleywegt combine distributional distance and dependence information [8]. Their Wasserstein and rank-dependence formulations establish close prior art for combining distance and moment constraints; our finite total-variation problem is not proposed as a new optimization framework.

Experimental decoder calibration also has substantial prior art. Chen et al. estimate correlation-based decoder weights, with independent-hyperedge assumptions stated in their supplement [9]. Wagner et al. give identifiability conditions for learning correlated Pauli noise from syndromes [10]. Our certificate does not satisfy or replace an identifiability theorem: its latent fault moments have not been reconstructed from observed syndrome data. Exact circuit-level repetition-code decoding is separately studied by Cao et al. [11]; matching its model would require a new registered comparison. A realistic contribution would connect a sparse sufficient certificate to identifiable, statistically bounded observables.

## 2. Registered finite model

There are three data qubits and two reset ancillas. Each of two rounds has six binary fault indicators. In round r, the first three toggle the data X frame before extraction; four ideal CX operations extract Z0Z1 and Z1Z2; the fourth indicator toggles data qubits 0 and 1 together after extraction; the last two flip the ancilla measurement records. Ancillas are reset between rounds. An ideal final boundary measurement gives the two data parities.

Indicators x0,...,x5 belong to round one and x6,...,x11 to round two. Observations are the four noisy round records followed by the two ideal final parities, encoded little-endian. The target label is the final X-frame bit on data qubit zero. The final parities specify the frame up to the logical XXX ambiguity; adding the target bit fixes the full three-bit frame uniquely.

At nominal rates, each round has probabilities (1/100,1/100,1/100,1/200,1/50,1/50). H is the exact MAP choice for each of 64 observation strings under that law; ties choose zero. T is the exact nominal MAP choice using only the final two parities. Both are frozen. For any fault assignment, d equals 1 when H alone fails, -1 when T alone fails, and zero otherwise. All 4,096 assignments are enumerated, and separate implementations rebuild these semantics.

This is a classical stochastic X-sector model of a repetition code. It assumes ideal preparation, boundary measurement and recovery. It is not a distance-three quantum code protecting arbitrary states. It excludes coherent faults, Z errors, leakage, crosstalk and a complete native-gate error model.

## 3. Minimum dependence distance and its certificate

Let p be a reference law on the finite assignments, M contain a normalization row and selected moment rows, and assume d·p<0. Define

    rho(M,p,d) = min { TV(q,p) : q>=0, Mq=Mp, d·q>=0 },
    TV(q,p) = (1/2) sum_x |q_x-p_x|.

If a feasible q has strictly positive d·q, mixing it with p produces a tie at smaller distance. Therefore a finite optimum occurs at d·q=0. This is a radius to the loss of strict superiority; it is not itself a strictly reversed ranking. If p is already tied, the radius is zero.

For discovery we write q=p-r+a with 0<=r<=p, a>=0, and minimize sum r. Normalization forces sum r=sum a. Cancelling overlapping removal and addition shows that this optimum equals TV. Put A=[M;d] and b=(0,...,0,-d·p). Here A denotes a linear constraint matrix, not a circuit operator.

An independently checkable lower bound uses any rational vector y for which h_x=(A^T y)_x<=0 for every atom:

    L(y) = -y_last (d·p) + sum_x p_x min(0,1+h_x).

Indeed, minimizing the Lagrangian over a>=0 gives a finite infimum when h<=0; minimizing over 0<=r<=p contributes the displayed terms. A rational feasible q gives an upper bound TV(q,p). Equality of these values proves optimality using only rational additions, products and comparisons. The checker reconstructs the constraint matrix rather than trusting one supplied by the optimizer.

At the nominal law d·p = -1376977939449/312500000000000. The registered results are:

| Preserved information | Minimum TV to tie | Conclusion |
|---|---:|---|
| Normalization only | 1376977939449/625000000000000 = 0.0022031647031184 | Finite exact optimum |
| Normalization and all twelve single marginals | 53522424551950587753/10000000000000000000000 = 0.0053522424551950587753 | Finite exact optimum |
| All singles and all 66 pair moments | No feasible tie | Exact separation certificate below |

The numerical solver's original infeasibility message is preserved. We do not treat that message as proof: a separate exact maximization certificate establishes that d·q is at most -163/40000 over all laws with the nominal first and second moments. An explicit rational law attains this value. With singles alone, the sharp maximum is instead 1/50. A separate exact mixture of the tie witness and this maximizer has strictly positive difference 1/50000; its construction is retained in ADDITIONAL_CONTROLS.json. These are properties of a mathematical uncertainty set, not claims that the extremal laws occur in a device.

## 4. A sparse sufficient condition without higher-order independence

The nominal pair-moment dual gives the following pointwise majorant on the Boolean cube:

    d(x) <= P(x)
    P(x) = -x9 + x9(x0+x1+x2+x3+x5+x6+x7+x8+x11)
                 + x11(x2+x8).

All 4,096 inequalities are checked exactly. This finite check is part of the proof artifact; it does not rely on floating-point optimization. There are eleven positive pair terms, each with coefficient one.

**Proposition.** Let q be any law on these fault assignments, and write p_i=E_q[x_i]. In each round suppose the three data-fault marginals lie in [1/200,3/200], the post-extraction joint-XX indicator lies in [1/500,1/125], and the two record-flip marginals lie in [1/100,3/100]. For the eleven pairs J appearing in P, assume

    E_q[x_i x_j] <= p_i p_j + epsilon_ij,  epsilon_ij>=0.

Then

    R_H(q)-R_T(q) <= -49/62500 + sum_(i,j in J) epsilon_ij.

**Proof.** Take expectations in the pointwise majorant. With zero excess terms its upper bound is

    p9[-1+p0+p1+p2+p3+p5+p6+p7+p8+p11] + p11(p2+p8).

The positive sum in the brackets is at most 79/500. Since p9>=1/500 and the bracket is negative, the first term is at most -421/250000. The second term is at most 9/10000. Their sum is -49/62500. Each permitted positive pair excess contributes at most its epsilon. No higher-order moment appears. This proves the result.

The polynomial bound was also evaluated at all 4,096 box vertices with rational arithmetic. Its maximum is -49/62500. We do not assert that this uniform bound is sharp over all corresponding joint laws. Equal pair products suffice, and negative pair deviations cannot invalidate this particular upper bound. Equal independent moments for all 66 pairs are stronger than necessary.

For a common per-pair allowance epsilon, strict superiority is guaranteed if epsilon<49/687500, approximately 0.0000712727. This is a tolerance on a joint probability, not a percentage correlation coefficient or measured calibration precision. The original fully independent uniform risk advantage was at least 0.0013612443. The new 0.000784 bound is weaker numerically but applies to a larger class of laws. This extension was declared after examining the primary nominal certificate and is explicitly exploratory.

## 5. Retrospective experimental-data exercise

We reused four distance-three, X-memory, one-round patches from the public Google Quantum AI data: d3_at_q6_3, d3_at_q6_7, d3_at_q8_5 and d3_at_q8_9. Each has 50,000 measured rows. Stim 1.16.0 independently converted the stored measurements and sweep bits through each supplied ideal circuit into eight detector bits and one logical-observable bit. All 1,800,000 derived parity bits matched the retained detector/observable files. Histograms agreed exactly with the prior QIDENT extraction; sixty retained member hashes also matched.

The original 5.7 GB archive's full MD5 was not verified in this campaign. Provenance is limited to previously validated range extraction, selected-member CRC checks and pinned SHA-256 hashes. The repository and original Nature paper identify the dataset [5,6]. The 2026 author correction [12] changes Figure 3a labels; it does not report replacement of the raw records used here. We retain this custody limitation rather than treating local hashes as proof of authorship.

The existing matching, Bayes, empirical-table and quantum-inspired lookup tables were not retrained. For each patch, three pairs compare a candidate to matching. The sign is oriented toward the empirically better decoder using all 50,000 previously exposed rows. This is a descriptive retrospective analysis, not prospective model selection or an independent test set.

For each of twelve comparisons, we compute three exact radii: preserving all nine observed bit marginals; additionally preserving their 36 pair moments; or preserving the complete eight-bit detector histogram. All 36 finite radii have equal rational primal and dual objectives. The last family preserves no logical-label prevalence and is not nested with the first two. Its radius must not be portrayed as a monotone step in a single hierarchy. The same full detector histogram can conceal changing conditional logical labels.


All twelve comparisons are reported below. Gaps are the candidate minus matching risks before orientation; negative favors the candidate. Radius decimals are rounded for display; exact fractions are supplied in EMPIRICAL_RESULTS.csv. A displayed zero would not replace its exact value.

| Patch | Candidate | Empirically better | Raw gap | Singles TV | Singles+pairs TV | Detector histogram TV |
|---|---|---|---:|---:|---:|---:|
| q6_3 | bayes | bayes | -0.00004000 | 0.000020000 | 0.000040000 | 0.000020000 |
| q6_3 | empirical_table | matching | 0.00066000 | 0.000330000 | 0.000426041 | 0.000330000 |
| q6_3 | qml | matching | 0.03876000 | 0.019380000 | 0.028540000 | 0.019380000 |
| q6_7 | bayes | bayes | -0.00004000 | 0.000020000 | 0.000040000 | 0.000020000 |
| q6_7 | empirical_table | matching | 0.00082000 | 0.000410000 | 0.000442503 | 0.000410000 |
| q6_7 | qml | matching | 0.04780000 | 0.023900000 | 0.029675870 | 0.023900000 |
| q8_5 | bayes | matching | 0.00002000 | 0.000013684 | 0.000021190 | 0.000010000 |
| q8_5 | empirical_table | matching | 0.00018000 | 0.000090000 | 0.000115572 | 0.000090000 |
| q8_5 | qml | matching | 0.03696000 | 0.018480000 | 0.023703056 | 0.018480000 |
| q8_9 | bayes | matching | 0.00012000 | 0.000080000 | 0.000128263 | 0.000060000 |
| q8_9 | empirical_table | empirical_table | -0.00056000 | 0.000280000 | 0.000369574 | 0.000280000 |
| q8_9 | qml | matching | 0.02934000 | 0.014670000 | 0.017255380 | 0.014670000 |

For q6_3 Bayes versus matching, the singles-preserving radius is 1/50000 and the pair-preserving radius is 1/25000. For q8_9 Bayes it rises from 1/12500 to 6333/49375000. Additional measured moments can therefore constrain empirical ranking changes, but neither example establishes a population-level benefit. The qml table performs worse than matching in all four patches; its large radii describe the stability of that observed disadvantage, not a quantum-inspired improvement.

These experimental calculations validate the sensitivity method on actual measured records. They do not verify the latent eleven-fault-moment assumptions of Section 4, transfer the repetition-code theorem to Google's surface code, or establish an improved device decoder. No population confidence statement follows from exact empirical arithmetic. Independence and chronological ordering of the retained shots remain unverified.

## 6. Verification, implementation and reproducibility

The optimizer uses SciPy/HiGHS and rational basis reconstruction through SymPy. A separate standard-library Python checker imports neither library nor the producer. It rebuilds the model's decoder semantics and each empirical loss vector; checks complete case and certificate inventories; verifies rational probability, moment and dual constraints; and rejects semantic corruptions. The current suite verifies 38 finite optima, two extremal certificates and the uniform majorant. The pair-constrained empty crossing set is resolved by its negative extremal bound.

The code and mathematical condition received a separate automated review. That review found missing-certificate and unknown-constraint parser weaknesses; both were repaired before release. Independent computational checking by agents is not independent human peer review.

Fleet MATLAB, GPU and five-model results are recorded separately in VALIDATION.md after execution. These components cannot change the exact result. GPU timing is a bounded replay benchmark and is not a speedup claim for rational optimization. Existing SciPy, SymPy, Stim, NumPy, MATLAB and MLX installations were sufficient; no new package was needed for the core calculation.

Run `python -B check_exact.py` for offline exact replay. `raw_replay.py` additionally requires NumPy and Stim and the retained raw files. `study.py` is a discovery script and refuses to overwrite its existing results; regenerate in a new output copy. Checksums establish consistency relative to the supplied manifest, not external authenticity. Packaging and corrupted-copy checks are described in RELEASE_RECEIPT.json.

## 7. Limits and useful next question

The finite state space is deliberately small. Exhaustive enumeration scales exponentially and no scalable certificate-discovery method has been established. Fixed decoders and ideal boundaries make the theorem inapplicable to generic adaptive decoding, leakage or native hardware without further modeling. Satisfying a selected set of first and second moments does not establish a complete physical noise model.

The useful next external question is whether sparse, exact moment certificates can guide which correlations to calibrate for a realistic syndrome-extraction circuit. That requires an identifiable link between physical fault parameters and recorded observables. Our empirical exercise deliberately does not supply that link. A larger search or hardware campaign should follow a domain expert's assessment of this gap and a concrete test protocol.

No priority claim, quantum advantage, award, institutional endorsement or publication acceptance is made. A suitable current description is a reproducible research note for methodological feedback. A full research paper would need a stronger literature comparison, a meaningful scalable extension or an experimentally identifiable calibration design.

## AI and author contribution disclosure

The user initiated and authorized the study. Codex selected and implemented this bounded extension, researched sources, ran deterministic experiments, coordinated independent automated checks and drafted this note. ASTERION attempted a five-role local advisory panel after the exact calculations. The first run was PARTIAL: three role outputs completed, two were withheld, and some completed advice was mathematically misleading. A separately recorded bounded retry and explicit correction ledger are described in VALIDATION.md. All original outputs and failures are retained. Neither model agreement nor stylistic review is treated as evidence of mathematical truth. The named human author must review the manuscript and its claims before any journal submission.

## References

1. D. Bertsimas and I. Popescu. Optimal Inequalities in Probability Theory: A Convex Optimization Approach. SIAM Journal on Optimization 15(3), 780–804 (2005). https://doi.org/10.1137/S1052623401399903 . Author-hosted precursor read: https://flora.insead.edu/fichiersti_wp/inseadwp2004/2004-62.pdf , especially the moment dual and weak duality discussion.
2. H. Owhadi, C. Scovel, T. J. Sullivan, M. McKerns and M. Ortiz. Optimal Uncertainty Quantification. SIAM Review 55(2), 271–345 (2013). https://arxiv.org/abs/1009.0679 . Abstract and bibliographic record consulted; not a full theorem-by-theorem audit.
3. A. Molavi, F. Saad and A. Albarghouthi. Analyzing Decoders for Quantum Error Correction. arXiv:2603.20127 (2026). https://arxiv.org/abs/2603.20127 . PDF Section 5 inspected; publication status treated as a preprint here.
4. Y. Kim, H. Kim, J. Kang, W. Choi and Y. Kwon. Effectiveness of the syndrome extraction circuit with flag qubits on IBM quantum hardware. Quantum 9, 1893 (2025). https://doi.org/10.22331/q-2025-10-23-1893 . Abstract and circuit/model sections inspected.
5. Google Quantum AI and Collaborators. Quantum error correction below the surface code threshold. Nature 638, 920–926 (2025). https://doi.org/10.1038/s41586-024-08449-y . Dataset statement inspected; a 2026 correction is separately recorded in the literature review.
6. Google Quantum AI. Data for Quantum error correction below the surface code threshold. Zenodo (2024). https://doi.org/10.5281/zenodo.13273331 . Retained subset described in Section 5.

7. E. Delage and Y. Ye. Distributionally Robust Optimization Under Moment Uncertainty with Application to Data-Driven Problems. Operations Research 58(3), 595-612 (2010). https://doi.org/10.1287/opre.1090.0741 . Author-hosted draft introduction and confidence-region sections inspected: https://web.stanford.edu/~yyye/distRobOpt_OR_rev0.pdf .
8. R. Gao and A. J. Kleywegt. Distributionally Robust Stochastic Optimization with Dependence Structure. arXiv:1701.04200. https://arxiv.org/abs/1701.04200 . Abstract and Sections 1.1-1.2 inspected; cited version is the preprint.
9. E. H. Chen et al. Calibrated decoders for experimental quantum error correction. https://arxiv.org/abs/2110.04285 . Abstract, decoder comparison and Supplement G inspected. Published as Physical Review Letters 128, 110504 (2022); cited full text is the accessed preprint.
10. T. Wagner, H. Kampermann, D. Bruss and M. Kliesch. Pauli channels can be estimated from syndrome measurements in quantum error correction. Quantum 6, 809 (2022). https://doi.org/10.22331/q-2022-09-19-809 . Introduction, informal Theorem 1 and data-syndrome discussion inspected; full proof not independently rederived.
11. H. Cao et al. Exact Decoding of Repetition Code under Circuit Level Noise. https://arxiv.org/abs/2501.03582 . Abstract and opening model sections inspected; no claim of reproducing that model.
12. Google Quantum AI and Collaborators. Author Correction: Quantum error correction below the surface code threshold. https://doi.org/10.1038/s41586-026-10559-8 (2026). Correction text inspected.
