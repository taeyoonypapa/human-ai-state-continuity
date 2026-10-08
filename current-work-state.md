# Current Work State

A continuity mechanism needs some representation of what matters **now**, not only what happened previously.

## Minimal template

```text
Workstream:
Last confirmed work:
Human-confirmed decision:
Open issue:
Next intended step:
Evidence / source:
```

## Why each field matters

### Workstream
Identifies which line of work is actually active.

### Last confirmed work
Separates completed work from merely discussed or proposed work.

### Human-confirmed decision
Prevents proposals or model interpretations from being reconstructed as accepted decisions.

### Open issue
Protects unresolved work from disappearing during summarization or reconstruction.

### Next intended step
Provides a forward-looking continuity anchor.

### Evidence / source
Allows the reconstructed state to be checked against something external to the model's current inference.

## Design objective

The goal is not exhaustive logging.

The goal is to preserve the minimum information required to avoid losing the actionable state of the workstream.

This is a conceptual public template, not an internal operational schema.
