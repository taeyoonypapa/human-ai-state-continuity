# Adjacent Approaches

This project is not primarily a memory-improvement proposal.

It focuses on the question:

> What is the correct actionable state now?

## Conversational memory

**Primary goal:** improve recall of prior interaction.

Useful for:
- preferences;
- prior facts;
- long-term context.

Limitation for this problem:
- better recall does not guarantee correct current-state inference.

## Checkpoint / state persistence

**Primary goal:** restore a previously stored state.

Useful for:
- workflow resumption;
- deterministic recovery of saved state.

Limitation for this problem:
- the saved state may not explicitly preserve unresolved semantic work.

## Human-maintained work log

**Primary goal:** keep an explicit record of what remains.

Useful for:
- inspectability;
- simple operational control.

Limitation:
- requires disciplined maintenance.

## State reconciliation

**Primary goal:** determine whether reconstructed context matches the externally represented actionable state.

Useful for:
- detecting false closure;
- preserving unresolved work;
- keeping uncertainty visible.

Cost:
- requires an externalized state representation and a validation step.

These approaches can be complementary rather than mutually exclusive.

## Possibly related concepts

The following may be structurally similar to false completion. They are listed as pointers for critique, not as established equivalences:

- the closed-world assumption and negation-as-failure in logic and databases (treating "not found" as "false");
- premature closure in diagnostic reasoning (stopping the search once a plausible conclusion appears);
- checkpointing and long-term memory features in existing agent frameworks.

Sources have not yet been compiled. Pointers to prior work under other names are welcome (see [`../evaluation/open-questions.md`](../evaluation/open-questions.md)).
