# Validation Model

Reconstruction alone is not enough.

A candidate current state should be checked against externalized work-state evidence where available.

```text
Reconstructed Context
        +
Externalized Current Work State
        ↓
Reconciliation
```

Three outcomes are conceptually useful:

### 1. Consistent
The reconstructed state and externalized work-state evidence materially agree.

**Action:** continue.

### 2. Contradictory
The reconstruction conflicts with evidence about unresolved work, prior decisions, or intended next steps.

**Action:** revalidate before continuing.

### 3. Insufficient evidence
The system cannot establish whether the reconstruction is reliable.

**Action:** preserve uncertainty instead of silently completing the state.

## Design principle

> Uncertainty should remain visible when the available evidence cannot support a confident current-state conclusion.

The purpose is not to eliminate uncertainty.

It is to prevent uncertainty from being hidden by a fluent reconstruction.

## Caveat

Reconciliation is only as reliable as the externalized state it is compared against. See [`limitations.md`](limitations.md).
