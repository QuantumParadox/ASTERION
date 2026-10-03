# Validation and reproduction

This package is a bounded completed study. It does not mean the entire ASTERION research programme is complete.

## Offline checks

Extract the ZIP into a new directory, then run `python -B REPRODUCE.py` from that directory. This standard-library command performs no network, model or provider calls. It verifies the manifest and source pins, independently rebuilds exact fiber bounds and exploratory witnesses, checks the 36 calibration settings, recounts provider shots, and checks resource counts and recorded validation receipts. MATLAB and GPU execution are recorded evidence in this portable core replay, not rerun tests.

With NumPy and Stim available, `python -B REPRODUCE.py --full` also rederives all retained detector and logical parity bits from the original recorded measurements and circuits. The full raw-data check was run with Stim 1.16.0. The package uses selected public dataset members; it does not claim verification of the entire upstream archive checksum.

## Rebuilding numerical experiments

Use a separate writable copy when regenerating results. Existing result receipts are deliberately preserved. calibration/study.py uses NumPy and SciPy; resources/audit.py uses NumPy, Qiskit and PyTorch; resources/exact_baseline.py uses SymPy and Qiskit. They do not need live quantum jobs. Producer outputs and independent checks are distinct files. The public resource source license is resources/LICENSE.

For MATLAB, add the `matlab` directory to the path, then call `observable_matlab(root)` in a copy with no existing matlab/MATLAB_RESULT.json. Call `resource_matlab(fullfile(root,'resources'))` for the full-unitary comparison in a copy without its existing receipt. MATLAB reserves directories named resources, so add only the matlab directory to the path. Both scripts preserve an existing output receipt.

## Evidence boundaries

- Exact rational fiber bounds and witness identities are mathematical statements in the declared finite model. They do not validate a physical noise law.
- MATLAB propagation and decoder decisions are exact integer calculations; envelope probability sums and complete-unitary comparisons are numerical.
- Five-host agreement verifies portability of these inputs and calculations. It is not a full audit of every ASTERION algorithm or GPU speed claim.
- Recorded Google data are real measurements, already exposed. Their multinomial resampling is simulation under an iid empirical-law assumption.
- IBM shots are physical; Quantum Inspire QX shots are simulated. No postselection or mitigation was used.
- CP intervals are per comparison. Hoeffding intervals are simultaneous over twelve provider event rates under stated shot assumptions. Neither accounts for unmodeled physical drift.
- The compiled artifact's trace-aligned operator residual is numerical and is not minimized over arbitrary global phase. The exact-baseline scalar residual is a maximum entrywise difference.
- An archive hash verifies consistency against the receipt; it does not authenticate authorship or establish independent human acceptance.

## Preserved failures and limits

The initial QX preflight lacked a simulator module. An isolated, official hash-pinned wheel resolved it. The first calibration harness included an extra zero-output diagnostic decoder, causing an inventory assertion before output; the registered three comparators are now explicit. Its initial weak normalization control was replaced with a computed unequal-sign fixture; the earlier result is retained. MATLAB first rejected a reserved folder name, and its resource parser then rejected scalar custom-gate arguments. Repair receipts and failed outputs remain in the archive; scientific tolerances were not loosened.

No calibration setting established an improvement, and physical-shot savings are zero. The public adder comparison establishes neither compiler novelty nor physical resource savings. Publication suitability and human review remain pending.
