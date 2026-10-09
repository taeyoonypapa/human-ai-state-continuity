# Evidence-Based State Reconstruction

## Research objective

The goal of Human–AI State Continuity is not perfect conversational memory.

Its primary objective is to prevent an AI system from converting incomplete memory or partial reconstruction into an unsupported conclusion about the current actionable work state.

When memory is incomplete, uncertainty is preferable to unjustified certainty.

## Proposed reconstruction process

1. Identify the relevant workstream.
2. Retrieve available external records, work-state artifacts, and event traces.
3. Order events chronologically while preserving source identifiers and provenance.
4. Reconstruct relevant state transitions, including unresolved obligations and their subsequent disposition.
5. Compare the candidate current state against the evidence.
6. Accept a state conclusion only when sufficiently supported; otherwise preserve uncertainty.

Chronological ordering alone does not establish correctness, completeness, or authority.

## Important distinctions

- Discussion is not approval.
- A proposed fix is not an implemented fix.
- Implementation is not successful verification.
- Component completion is not whole-workstream closure.
- A recent message is not necessarily authoritative evidence.
- Missing evidence of open work is not positive evidence of completion.

## Example

Consider the following event sequence:

| Time | Event | State implication |
|---|---|---|
| T1 | Payment-to-enrollment defect discovered | Open obligation created |
| T2 | Possible fix proposed | Defect remains unresolved |
| T3 | Four other workstreams completed | Partial readiness established |
| T4 | Readiness meeting concluded | Meeting completed, not necessarily launch |
| T5 | No verified defect closure recorded | Whole-workstream completion not established |

A system must not infer whole-project completion merely because the latest visible events concern completed tasks.

The absence of a closure record does not independently establish that the defect remains open; it establishes that closure cannot be verified from the available evidence.

## Evidence and uncertainty

External records may be stale, incomplete, contradictory, or incorrectly attributed.

A reconstruction mechanism should account for these weaknesses rather than treating stored traces as automatically authoritative.

If sufficient evidence is unavailable, the appropriate outcome may be UNRESOLVED.

## Research status

This document defines a conceptual research direction.

It does not establish that a working reconstruction engine has been implemented, that the method outperforms existing memory or checkpoint approaches, or that it prevents false completion in production.

Empirical comparisons with simpler alternatives remain necessary.

## Relation to existing evaluations

EVAL-001 observed an unsupported COMPLETE judgment from partial context.

EVAL-002 and EVAL-003 tested model judgments using supplied records, but did not establish an advantage for additional closure-check instructions.

EVAL-004 tested an extended collaboration and subsequent session transition. The model reported that it could not access the prior conversation. The study did not test retrieval and chronological reconciliation using external trace records.

These observations motivate the research question but do not validate the proposed mechanism.
