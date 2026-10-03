# ASTERION 4.1.0: five-model and software audit

Recorded 3 October 2026. **The audited local application operates, but model advice still contains scientific errors.** This report distinguishes software execution from factual correctness. It does not establish a new scientific result, independent peer review or hallucination-free operation.

This public repository remains documentation-only. The complete application, model weights, private data and internal research packets are not included. This is a first-party report of retained local evidence, not a public independent reproduction of the entire application.

## Five-model evaluation

Five different pinned model identities contribute specialist advice. GPT-OSS 120B is the registered judge and performs an additional closing review. It was the largest tested model and passed the bounded question set; this does not establish universal superiority.

| Role | Selected local model | Correct and well-formed |
| --- | --- | --- |
| diagnostician | qwen3.8:27b-q8_0 | 24/24 |
| patcher | devstral-small-2:latest | 16/24 |
| adversary | asterion-gemma4:31b-ud-q6-k-xl | 24/24 |
| verifier | granite4.2:30b | 24/24 |
| judge | gpt-oss:120b | 24/24 |

Each model answered two sets of 12 questions covering exact arithmetic, probability, density-matrix validity, Bell-state measurements, missing evidence, unsupported references and instructions embedded in quoted data. Expected answers were not included in the requests. Several question families repeat across sets.

The protocol was refined during development, so these are adaptive operational results. Earlier failures were retained. They included malformed answer types, an unsuccessful formatting clarification, arithmetic mistakes and an unsupported reasoning-mode setting. The lower-precision Gemma download was not promoted after missing two cases. Devstral remains a coding adviser; its arithmetic and quantum-state mistakes require independent checking.

Its generated Euclidean GCD and Horner polynomial functions passed 125 finite cases in a restricted arithmetic interpreter. This verifies those cases, not arbitrary generated programs or general coding ability.

## A factual failure that the judge did not catch

The installed panel completed all five roles and the closing review. Its constructor and judge incorrectly stated that eigenvalues 5/4 and -1/4 violate trace one. Their exact sum is 1. The matrix is invalid because one eigenvalue is negative.

The constructor also proposed idempotency as a general density-matrix validity condition. The valid mixed state diag(1/2,1/2) is a counterexample: it has trace one and is positive semidefinite, but its square differs from itself. Some advice also conflated separate examples with the three-bit decoding test.

The original answers remain unchanged. Exact corrections are bound to their evidence and displayed in Five Minds. No proposed scientific claim was accepted. The output gate passed this incorrect prose because its scope is format, evidence binding and limited style checks. It is not a general truth detector. Model agreement cannot replace a mathematical or experimental check.

## Repairs

- Corrected Windows service readiness and process-ownership checks, with a compute lock protecting active work during shutdown.
- Installed the verified Ollama 0.35.1 release and an isolated application environment. The shared MIRANDA model service was left unchanged.
- Separated ASTERION's model catalog and retired six superseded or rejected registrations. Models needed by Model Lab, retrieval and optional profiles were retained.
- Removed expected-answer leakage from a legacy quality-test request. Previous scores from that test cannot establish independent accuracy.
- Rejected duplicate JSON keys, nonfinite numbers, unexpected fields, unbound citation identifiers and known instruction canaries.
- Replaced generated Python execution in the two-function coding benchmark with a restricted interpreter and explicit resource limits.
- Corrected secondary inference endpoint and reasoning-mode selection.
- Repaired five Discovery Studio section links and added model-role explanations and operating instructions.

The model-runtime release was checked against its published asset digest. Official reference: [Ollama releases](https://github.com/ollama/ollama/releases). Model catalogs consulted included [Qwen](https://ollama.com/library/qwen3.8/tags), [Devstral](https://ollama.com/library/devstral-small-2/tags), [Gemma](https://ollama.com/library/gemma4/tags), [Granite](https://ollama.com/library/granite4.2) and [GPT-OSS](https://ollama.com/library/gpt-oss).

## Validation performed

| Check | Recorded outcome | Limit |
| --- | --- | --- |
| Application suite | 477 tests and 128 subtests passed | Available suite, not proof of every algorithm |
| Separate code review | No remaining Critical or Important findings in the reviewed changes; 31 focused tests replayed | Independent agent review, not outside human acceptance |
| Live panel | Five roles and closing review completed | Incorrect scientific prose required visible corrections |
| MATLAB | Independent arithmetic, variance, three-bit decoding and quantum-state checks passed | Finite known-answer examples |
| CPU and two local GPUs | 32 generated two-qubit density-matrix cases agreed; largest eigenvalue difference about 5.55e-16 | Numerical classical checks, not physical quantum data or speedup evidence |
| Actual Chrome | 27 main workspaces, 12 Neural Lab tabs, one CIFAR display control and five Studio links checked | Not an exhaustive test of all possible user actions |
| CIFAR display | Temporary real-data run inspected; smoothing left numerical content unchanged | No training-performance claim |
| Local resources | Checked linked resources returned successfully; no duplicate navigation IDs or final page errors | Intentional cross-links between sections remain |
| External links | 55 reachable, 7 unverified; no confirmed 404/410 | DNS/access failures were retained as unverified |
| Dependency audit | No known advisories in the audited set after updates; dependency consistency passed | Local package and registry coverage limits remain |
| Static scan | 156 low and 7 medium findings retained, none rated high | Automated ratings do not establish absence of vulnerabilities |
| Installed application | Version, service identity, file hashes, model pins and request rejection checks passed | Local deployment only |

Two test-harness assumptions were corrected and their earlier receipts retained: origin rejection applies to mutation requests, and the CIFAR display control is intentionally hidden until a run exists. No application behavior was weakened to make those checks pass.

## How to interpret the interface

Five Minds lists the pinned roles and displays scientific review corrections above the advice. COMPLETE means responses were recorded. Check each limitation and use the relevant exact checker or independently defined experiment before accepting a conclusion.

Help explains the workspaces, recorded-versus-live labels and the model test limits. The panel runs sequentially to manage GPU memory. Models remain advisory and cannot authorize provider jobs or promote claims.

No new quantum-provider jobs, researcher emails or recurring automations were created for this audit. Remote MATLAB systems, operating-system security, external provider infrastructure and every historical research campaign were outside its scope.

The [machine-readable summary](MODEL_SOFTWARE_AUDIT_2026-10-03.json) records the same status. The full local evidence retains failed attempts, test logs, hashes, requests and responses, independent checks, review corrections and browser receipts. A checksum identifies bytes relative to a manifest; it does not authenticate authorship or scientific acceptance.
