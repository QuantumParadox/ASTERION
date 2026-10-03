# Review guide

## Choose one narrow question

Start with [research status](RESEARCH_STATUS.md). Identify the exact result, assumptions and artifact you want to review. Public documentation is a summary; it is not a substitute for the underlying evidence packet.

## Record what you actually checked

1. Preserve the source version and file digests before running a copy.
2. Read the statement, input provenance, environment requirements and trust assumptions.
3. Reproduce the ordinary result with the supplied checker.
4. Try a deliberately invalid input or independently constructed counterexample.
5. Where possible, compare with a separately authored method.
6. Report execution limits and distinguish a reproduced result from a novel theorem or operational benefit.

For private packets, request one study through an issue. Review requests are not commitments to provide sensitive data or unrestricted source access.

## Useful issue format

- Study name and version:
- Claim reviewed:
- Public source or requested packet:
- Environment and tool versions:
- Checks actually run:
- Result and minimal reproduction:
- Assumption or prior-art concern:
- What remains untested:

Do not include secrets, personal data, live case evidence or private email. Do not submit provider jobs or contact third parties as part of an offline replay.

## Interpretation

AI-assisted implementation and same-team testing are not independent human review. Matching implementations can share an error. A preserved failure should remain visible. A file hash establishes byte identity relative to a reference, not authorship, soundness or authenticity of a physical experiment.

A helpful review can conclude that a result is known, an assumption needs revision or the proposed application has no demonstrated benefit.
