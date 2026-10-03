# ASTERION: observation limits and compilation checks

3 October 2026 · OBSERVABLE-20261003 · Working results, human review pending

The useful result is a precise account of what the available evidence can and cannot establish.

1. **Exact finite mathematics.** In a fixed 4,096-state, two-round X-error model, identical syndrome statistics can support opposite frozen decoder rankings. A rational two-atom construction stays inside the earlier single-rate intervals. The exact minimum total-variation distance to a tie is 0.0022031647031184. Adding a known-preparation logical label determines the observed decoder risk, but leaves hidden fault correlations underdetermined. This is a specific example using established methods, not a new general theorem.
2. **Real recorded data.** A fresh conversion reproduced 1.8 million parity bits from 200,000 public measured Google shots. Fixed-data resampling over 36 settings and 72,000 replicates found no decoder improvement and no physical-shot saving. Selective labels save hypothetical label cost only; labels may already be provided by the same readout.
3. **Compilation audit.** One pinned, saved PNNL adder artifact has 1,120 T gates. A standard exact Toffoli baseline uses 56 T/T-dagger gates for the same input circuit. The original saved artifact's specific synthesis tolerance is undocumented. This is a baseline and provenance question, not a new compiler or a demonstrated current-tool defect.
4. **New provider controls.** IBM ibm_fez returned all 3,072 physical shots, charged 3 QPU seconds. Quantum Inspire QX returned all 768 emulator shots. Physical QI hardware was unavailable. These are small preparation/readout controls, not proof of fault tolerance, device noise identification or quantum advantage.

The exact observation calculation passed independent Python and MATLAB implementations; MATLAB ran on all five authorized hosts. RTX 5090 and RTX 4090 replayed the full compiled adder unitary. Same-project checks are not external peer review.

**Read and reproduce:** Start with PAPER.md and VALIDATION.md. The archive's offline checker verifies exact bounds, calibration accounting and provider counts. Full raw-data replay additionally requires the listed scientific Python packages. The archive contains no credentials or installed environments. Do not execute provider submission helpers to reproduce this study; all required provider outputs are already recorded.

**Next useful gate:** Ask whether the finite observation model is a useful regression case, and obtain the compiled artifact's generating settings. Await expert feedback before another provider campaign. The DOE roadmap motivates the work; it does not imply DOE affiliation, funding or endorsement.
