# Human–AI State Continuity

[English](README.md) | [한국어](README_KO.md)

Version: v0.5 (revised 2026-10-09) · Status: experimental, conceptual

**An experimental approach to a specific failure mode in long-running Human–AI collaboration: an AI may reconstruct enough past context to sound coherent while still deriving the wrong current work state.**

## Core claim

The problem is not simply whether the model remembers enough.

The problem is whether it reconstructs the **correct current actionable state**.

A model may recover most of the prior conversation and still miss the one unresolved issue that determines what should happen next.

```text
90% correct reconstruction
        +
10% missing unresolved work
        ↓
100% wrong actionable conclusion:
"Work is complete."
```

*The percentages are illustrative, not measurements.*

This leads to the central rule of this project:

> **Absence of reconstructed work is not evidence of completion.**

A workstream should not resolve to COMPLETE merely because no remaining task was reconstructed.

Completion should require positive evidence.

## False Completion Failure

```text
Previous work state
│
├─ Completed work
├─ Human-confirmed decision
├─ Open issue         ← missed during reconstruction
└─ Intended next step ← missed during reconstruction

          ↓

New session reconstructs:
Completed work + Human-confirmed decision

          ↓

Model inference:
"Nothing remains."

          ↓

FALSE COMPLETION
```

The dangerous failure is not forgetting by itself.

> **The dangerous failure is deriving a false current state from incomplete reconstruction.**

## Memory is not state

Conversation memory and current work state are related, but they are not the same object.

```text
Conversation history
        ↓
Reconstruction
        ↓
Candidate current state
        ↓
Validation against externalized work-state evidence
        ↓
Continue / Revalidate / Preserve uncertainty
```

Reconstructed conversational context is therefore treated as **evidence about state**, not as authoritative state by itself.

## Minimal Current Work State

A minimal public template may look like this:

```text
Workstream:
Last confirmed work:
Human-confirmed decision:
Open issue:
Next intended step:
Evidence / source:
```

This is intentionally simple.

Its purpose is not to capture everything that happened.

Its purpose is to preserve the small set of facts most likely to determine what should happen next.

## Completion Challenge

When a reconstructed state proposes that a workstream is complete, completion should be challenged rather than accepted by default.

```text
Candidate state: COMPLETE
        ↓
Check:
- Is there any open issue?
- Is there any intended next step?
- Is there any unresolved contradiction?
- Does externalized state still mark the workstream as active?
- Is there positive evidence that closure actually occurred?
        ↓
Any unresolved mismatch?
        ↓
YES → Reject or revalidate completion
NO  → Completion may proceed
```

This is not a production algorithm.

It is a conceptual safeguard against fluent but unsupported closure.

## Insufficient evidence

The system should not force a single state when the evidence is insufficient.

```text
Required state evidence missing
        ↓
Cannot establish COMPLETE
        ↓
Preserve uncertainty
        ↓
Request or recover missing evidence
```

A useful principle is:

> **If required state fields cannot be evidenced, the system should not silently resolve the workstream as complete.**

## Validation model

```text
Reconstructed Context
        +
Externalized Current Work State
        ↓
Reconciliation
        ↓
Consistent      → Continue
Contradictory   → Revalidate
Insufficient    → Preserve uncertainty
```

The goal is not perfect memory.

The goal is to reduce the probability that incomplete reconstruction silently becomes an incorrect current state.

## How this differs from adjacent approaches

This project is not primarily about improving recall.

It focuses on **state reconstruction and closure safety**.

| Approach | Main question | Typical strength | Main limitation for this problem |
|---|---|---|---|
| Conversational memory | What should the model remember? | Better recall | Remembered context may still produce the wrong current state |
| Checkpoint / persistence | What state was stored? | Restores a saved point | A stored checkpoint may still omit unresolved semantic state |
| Human-maintained work log | What remains to be done? | Explicit and inspectable | Requires disciplined manual maintenance |
| State reconciliation | What is the correct actionable state now? | Separates reconstruction from acceptance | Requires an externalized state representation and validation step |

The claim is not that these approaches are mutually exclusive.

State reconciliation may sit on top of memory, checkpointing, or human-maintained logs.

## Why this matters

Long-running Human–AI collaboration increasingly depends on continuity across sessions, documents, decisions, unresolved issues, and planned next actions.

A system that remembers many facts but loses the current actionable state may still appear coherent while being operationally wrong.

That makes **state continuity** a distinct problem from ordinary memory retrieval.

## Authority boundary

If an inferred current state can trigger consequential action, a separate decision boundary may still be required.

```text
Reconstructed state
        ↓
Validated current state
        ↓
Decision boundary
        ↓
Consequential action
```

The focus of this repository is the continuity problem itself, not the broader control architecture around it.

## Repository map

- [`docs/reconstruction-vs-memory.md`](docs/reconstruction-vs-memory.md)
- [`docs/current-work-state.md`](docs/current-work-state.md)
- [`docs/completion-challenge.md`](docs/completion-challenge.md)
- [`docs/validation-model.md`](docs/validation-model.md)
- [`docs/adjacent-approaches.md`](docs/adjacent-approaches.md)
- [`docs/limitations.md`](docs/limitations.md)
- [`cases/false-completion.md`](cases/false-completion.md)
- [`evaluation/open-questions.md`](evaluation/open-questions.md)
- [`README_KO.md`](README_KO.md)

## Public scope

This repository covers the **problem structure and a conceptual response** only. Operational state schemas and implementation details are out of scope, so everything here is a conceptual proposal, not an implementation-validated result.

## Known limitations

The approach has real weaknesses, including the risk that the externalized state is itself incomplete or stale. See [`docs/limitations.md`](docs/limitations.md).

## Project status

This is an experimental research project, not a production-ready continuity framework or a generally validated standard.

Publication is intended to invite critique of the problem framing, the distinction between memory and state, the completion rule, and the conceptual validation model.

Critical feedback is preferred over endorsement.

## Feedback

Please use GitHub Issues or Discussions on this repository. Counterexamples, simpler alternatives, and pointers to existing work are the most useful contributions.
