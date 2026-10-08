# Limitations

This document lists known weaknesses of the approach described in this repository.

## 1. The failure may move one layer down

The Completion Challenge asks whether an open issue or next step exists in the externalized state. If the issue was never recorded, or the record is stale, the check passes vacuously and the same false completion occurs. Reconciliation shifts the problem to the quality of the externalized state; it does not remove it.

## 2. "Still marked active" can itself be stale

An externalized workstream may remain marked active after it was actually closed, or marked closed while work remains. The check does not say how freshness is established.

## 3. The reverse failure is not covered

The model guards against false COMPLETE. It does not address false OPEN: closed work kept as an open issue, which can cause endless revalidation and noise.

## 4. "Positive evidence of closure" is unspecified

The rule requires positive evidence but does not define what qualifies. Candidates (a human sign-off, a recorded artifact, a passed check) each have their own failure modes. This is left open on purpose and listed in the open questions.

## 5. Who writes and confirms the state is unspecified

"Human-confirmed decision" assumes a reliable way to record human confirmation. How that is captured, and what happens when the human forgets or the AI writes the record itself, is not addressed.

## 6. No empirical validation

The claims here are conceptual. The case study is hypothetical. Whether the approach reduces false completion in practice, compared with retrieval plus summarization or a plain human-maintained log, is **UNKNOWN**.

## 7. Maintenance cost

Externalized state requires upkeep. At some point the burden may outweigh the benefit; where that point lies is not established.
