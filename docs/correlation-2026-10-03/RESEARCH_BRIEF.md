# When do calibrated error rates justify a decoder comparison?

**ASTERION working research note, 3 October 2026.** James C. Simmonds, independent researcher and RIT Computing Security alumnus. Not submitted or peer reviewed.

For two frozen decoders of a two-round, three-data-qubit repetition X-error model, exact moment optimization shows that individual fault rates do not determine which decoder is better. Holding all twelve rates fixed, the smallest total variation change reaching a tie is 0.0053522424551950587753. A separate rational witness produces strict reversal. Holding all first and second moments fixed gives a sharp negative maximum risk difference of -163/40000, so no reversal is possible in that set.

The resulting dual contains only eleven positive pair terms. Its pointwise inequality gives a uniform sufficient condition across the original rate box:

    history risk - terminal risk <= -49/62500 + sum of eleven positive pair excess allowances.

Higher-order dependence is unrestricted. The bound is conditional on the model and selected moment conditions; it is not claimed sharp throughout the box.

A separate exercise uses 200,000 previously exposed Google Quantum AI measurement rows. All 1.8 million detector/logical parity bits were reconstructed, and 36 empirical ranking-sensitivity radii were exactly certified. These are descriptive histogram results, not population confidence intervals or evidence that latent model assumptions hold on a device.

An independent standard-library checker verifies the rational witnesses and dual bounds. MATLAB replay passed on five hosts. All five RTX GPUs and the M4 GPU evaluated bounded numerical paths. Failed launches, model errors and scientific corrections remain in the record.

Moment-constrained optimization, dependence-aware distributional robustness and calibrated quantum decoding have extensive prior art. The modest present contribution is an explicit finite sparse certificate and reproducible worked example. Novelty and publication value are unresolved.

**Question for an outside reader:** Is a sparse sufficient-moment certificate useful for choosing what to calibrate, and what existing identifiability result or small extraction circuit would be the right next comparison?
