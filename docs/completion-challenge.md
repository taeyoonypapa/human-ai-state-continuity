# Completion Challenge

False Completion becomes most dangerous when the model's reconstructed state is fluent enough to sound final.

A simple conceptual safeguard is to treat COMPLETE as a state that requires evidence.

## Completion challenge

```text
Candidate state: COMPLETE
        ↓
Check:
- Open issue exists?
- Next intended step exists?
- Unresolved contradiction exists?
- Externalized work state still active?
- Positive closure evidence exists?
        ↓
Any unresolved mismatch?
        ↓
YES → Reject or revalidate completion
NO  → Completion may proceed
```

## Key rule

> Absence of reconstructed work is not evidence of completion.

The system should not infer closure merely because no unfinished task was recovered.

## Insufficient evidence

If required evidence is missing:

```text
Missing state evidence
        ↓
Cannot establish COMPLETE
        ↓
Preserve uncertainty
```

The purpose is not to make the model more cautious in general.

The purpose is to make closure a positively evidenced state rather than a default inference from missing context.
