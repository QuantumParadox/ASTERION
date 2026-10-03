# Help: ASTERION public project and replay

## What is this repository?

A project overview, dated research summary and guide for outside readers. It is not the complete local application. It does not contain the dashboard installer, provider credentials, private correspondence, live account status or the whole research archive.

## How do I try a public calculation?

Open [asterion-bernstein-check](https://github.com/QuantumParadox/asterion-bernstein-check), download or clone that separate repository, and read its README and MIT license. With an existing Python 3.10+ installation, run from that checker's directory:

```text
python -B replay.py
python -B checker.py qutrit_denominators.json
```

No provider account, API key, quantum computer, MATLAB installation or GPU is needed for this example. The manifest check detects changed files relative to the manifest; it does not authenticate the author.

Acceptance establishes only the supplied rational polynomial enclosure. Rejection does not by itself refute the inequality. The 40 shipped cases are recorded mathematical fixtures, not new physical measurements.

## How do I interpret the status pages?

- Recorded measurement: retained observations from a named historical study.
- Simulation: generated data under a stated model.
- Exact check: arithmetic or identities checked without floating-point rounding.
- Numerical cross-check: a separate implementation agrees within a stated tolerance.
- Formal proof: a precisely stated obligation accepted by a proof kernel.
- Pending outside review: the specific scientific argument has not received independent human acceptance.

None of these labels can be substituted for another. A formal proof is only as applicable as its statement and assumptions. A fast GPU calculation is not evidence of better scientific inference.

## Does the public project start the Monitor 4 dashboard?

No. The native wall and the complete local application are maintained separately. This repository does not publish a remote dashboard or establish that a live service is online.

## How can a researcher help?

Read [REVIEW_GUIDE.md](REVIEW_GUIDE.md). Select one claim, reproduce the available evidence and report assumptions or counterexamples. Ask for the corresponding scoped packet if it is not public. Do not post credentials, nonpublic datasets or personal correspondence in an issue.

## License scope

Read [NOTICE.md](../NOTICE.md). The separate Bernstein repository is MIT-licensed. That license does not cover the full ASTERION or MIRANDA platforms.
