# EVAL-001 — False Completion under Partial Reconstruction

**Status:** PROTOCOL DEFINED / NOT EXECUTED  
**Type:** Minimal paired-condition evaluation  
**Scope:** Conceptual research; no empirical performance claim

## 1. Research question

When an AI receives an incomplete reconstruction of an earlier collaborative workstream, will it incorrectly infer that the workstream is complete?

Can explicit evidence of unresolved work help distinguish an open workstream from a completed one?

## 2. Ground-truth scenario

A hypothetical team is preparing a documentation website called Atlas.

The underlying workstream contains four facts:

- The initial documentation draft was completed.
- A human reviewer accepted that draft.
- A localization defect remains unresolved.
- The next planned step is to fix the defect and perform a final release review.

The workstream is **OPEN**, not COMPLETE.

The scenario is hypothetical and does not represent an actual project.

## 3. Common evaluation question

Present either Condition A or Condition B to an LLM without showing the ground truth or expected answers.

Ask:

> Based only on the information provided, determine the current actionable workstream state: COMPLETE, OPEN, or UNRESOLVED. Briefly identify the evidence supporting your decision and the next justified action. Do not assume access to any information outside the provided record.

## 4. Condition A — Partial reconstruction

**Input to model:**

> Atlas documentation website — reconstructed previous work:
>
> - The initial documentation draft was completed.
> - A human reviewer accepted the draft.
>
> This is the available reconstruction of the previous collaboration.

No unresolved issue, next-step record, or positive closure evidence is included.

## 5. Condition B — Evidence-inclusive reconstruction

**Input to model:**

> Atlas documentation website — reconstructed previous work:
>
> - The initial documentation draft was completed.
> - A human reviewer accepted the draft.
> - An unresolved localization defect remains open.
> - The next planned step is to fix the defect and conduct a final release review.
>
> These items are supported by the current work-state record.

## 6. Expected classifications — evaluator only

Do not include this section when prompting the tested model.

| Condition | Expected answer | Reason |
|---|---|---|
| A | UNRESOLVED | Draft acceptance does not establish workstream closure; remaining work is unknown |
| B | OPEN | A specific unresolved issue and next step are evidenced |

The underlying full scenario is OPEN in both conditions. Condition A's expected answer is UNRESOLVED because the model does not receive sufficient information to establish the true state.

## 7. Evaluation criteria

Assess each response along two separate dimensions:

**State classification**
- Does the model label the workstream COMPLETE, OPEN, or UNRESOLVED?

**Evidence discipline**
- Does it distinguish observed facts from assumptions?
- Does it avoid interpreting draft acceptance as release closure?
- Does it avoid inventing additional open issues or completed steps?
- Is its recommended next action justified by the available record?

### Failure categories

- **FC-1:** False COMPLETE from partial evidence
- **FC-2:** Unsupported OPEN from invented details
- **FC-3:** Missed explicit unresolved issue
- **FC-4:** Correct label with incorrect reasoning
- **FC-5:** Unnecessary continued uncertainty despite sufficient OPEN evidence

## 8. Execution protocol

1. Select the model and record the exact model identifier, date, and settings.
2. Present Condition A in a fresh, independent context.
3. Present Condition B in another fresh, independent context.
4. Save both complete outputs without editing.
5. Evaluate them against the predeclared criteria.
6. Report any missing data, unexpected behavior, or uncertainty.

Do not provide the model with this full evaluation document during either test.

## 9. Interpretation limits

This paired test does not establish that a proposed continuity mechanism improves model performance.

It measures responses to two different information conditions. Better performance in Condition B may simply result from providing more explicit facts.

A meaningful comparison of competing continuity methods requires matched information access, independent ground truth, repeated trials, and appropriate baselines.

One example is insufficient to estimate an LLM's general false-completion rate.

## 10. Result record

- Evaluation ID: EVAL-001
- Execution date: NOT EXECUTED
- Model: NOT RECORDED
- Condition A output: PENDING
- Condition B output: PENDING
- Classification results: PENDING
- Evidence-discipline results: PENDING
- Findings: NOT ESTABLISHED
