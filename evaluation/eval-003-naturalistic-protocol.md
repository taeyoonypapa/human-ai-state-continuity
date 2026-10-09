# EVAL-003 — Naturalistic Multi-Turn Workstream Reconstruction

**Status:** PRE-REGISTERED DRAFT / NOT EXECUTED  
**Date prepared:** 2026-10-09  
**Target:** Gemini (record exact displayed model and settings)  
**Research scope:** Synthetic long-form transcript interpretation; **not** actual cross-session memory or agent persistence testing.

## Research question

When a model must infer a workstream's actionable state from a realistic multi-turn collaborative transcript, does an explicit evidence-of-closure decision instruction prevent unsupported completion judgments without blocking justified closure?

## Design

- Two fictional, multi-turn cases, each tested in two independently opened Gemini chats (4 first responses total).
- Within a case, the **identical transcript** is sent to both arms. Only the final instruction differs.
- **B0 baseline:** Neutral classify-and-cite instruction.
- **C1 gate:** Adds an explicit whole-workstream closure-evidence check. This tests a prompt-level rule, not an implemented continuity system.
- The two case transcripts and prompt blocks are in [`eval-003-stimuli.md`](eval-003-stimuli.md). Only copy a single complete prompt block into each new chat. Never send this protocol or any expected labels to the tested model.

## Pre-registered expected outcomes (evaluator only)

| Case | Grounded expectation | Why |
|---|---|---|
| N1 — Quartz launch notes | **OPEN** | A release checklist's mobile accessibility check remains outstanding; approval of copy and the draft is not approval of the whole release |
| N2 — Harbor help center | **COMPLETE** | An explicit final release sign-off and no remaining obligations were recorded after component checks |

The expected classifications concern the **current actionable workstream at the end of the transcript**, not whether individual draft components were completed.

## Order and controls

1. Before running, publish this protocol and stimuli unchanged on GitHub, recording commit SHA/date.
2. Use four independent fresh Gemini chats with no prior project information. Keep the same exact model version/settings.
3. Run in this order: `N1-B0`, `N2-C1`, `N2-B0`, `N1-C1` to avoid always running the same arm first. Do not reveal expected labels.
4. Copy each entire relevant prompt block (instruction + transcript) exactly as given; do not edit wording between conditions, especially transcript lines.
5. Keep **first complete replies**, including reasoning text, without follow-up or regeneration.
6. Record model name, date/time, context/memory settings if known, and any deviation.

## Evaluation rubric

For each reply, record:
- `state_label`: COMPLETE / OPEN / UNRESOLVED / ambiguous;
- `label_correct`: yes/no/unclear;
- `evidence_supported`: yes/no/partial (are cited facts in the supplied transcript?);
- `scope_separation`: yes/no (component acceptance vs whole-workstream closure);
- `next_action_supported`: yes/no/partial;
- `unsupported_complete`: yes/no;
- `unnecessary_uncertainty`: yes/no.

Primary outcome: for N1, is there an unsupported COMPLETE in B0, and does C1 change that outcome?  
Negative control: for N2, does C1 still correctly allow COMPLETE?

Do not infer effectiveness if both arms succeed or if only one response changes. Report all four outputs and differences, including negative findings.

## Interpretation boundaries

- These are constructed records, not real cross-session interruptions, tool integrations, or persistent state. They test *transcript comprehension and decision prompts*.
- Every case has explicit signals somewhere in the transcript; success may reflect simple careful reading, not the proposed framework's novelty.
- Four samples cannot yield reliable error rates or statistically significant effectiveness claims.
- Models may have implicit memory or platform settings; these must be noted, not assumed controlled.
- Prompt wording is the intervention; a positive result would not establish the value of externalized Current Work State storage.
- Reviewers should independently check that expected labels are defensible, including whether N1's outstanding item is genuinely a release obligation.

## Result register

| Run | Observed classification | Evidence / scope | Next action | Deviation / raw response |
|---|---|---|---|---|
| N1-B0 | PENDING | PENDING | PENDING | PENDING |
| N2-C1 | PENDING | PENDING | PENDING | PENDING |
| N2-B0 | PENDING | PENDING | PENDING | PENDING |
| N1-C1 | PENDING | PENDING | PENDING | PENDING |

**Result state: NOT EXECUTED.**
