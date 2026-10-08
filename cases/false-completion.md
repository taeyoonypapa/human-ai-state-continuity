# Case Study — False Completion by Partial Reconstruction

> Illustrative, hypothetical scenario. It is not a record of a specific session or an empirical result.

## Scenario

A workstream contains four relevant elements:

```text
1. Completed analysis
2. Human-confirmed decision
3. Unresolved issue
4. Intended next step
```

A later session successfully reconstructs items 1 and 2, but misses items 3 and 4.

The model concludes:

> The workstream is complete.

## Why this is dangerous

The model may sound coherent because most of the recovered history is correct.

The failure is therefore easy to miss.

The problem is not low-quality recall in general.

It is a specific semantic failure:

```text
Incomplete reconstruction
        ↓
Incorrect actionable-state inference
        ↓
False completion
```

## Detection question

Before accepting completion, ask:

> What positive evidence establishes that no unresolved issue or intended next step remains?

If the system cannot answer that question with externalized evidence, completion should not be accepted automatically.

## Conceptual mitigation

Maintain or reconstruct a separate representation of current work state and compare it against conversational reconstruction.

If the two disagree, do not silently choose the more fluent reconstruction.

## Lesson

> A continuity system should optimize not only for remembering prior content, but for preserving unresolved state.
