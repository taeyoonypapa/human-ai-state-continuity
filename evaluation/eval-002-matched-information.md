# EVAL-002 — Matched-Information Completion Decision Test

**Status:** PROTOCOL DEFINED / NOT EXECUTED  
**Design:** Within-case paired prompts, fresh independent Gemini chats for each arm  
**Purpose:** Test whether an explicit *evidence-of-closure decision instruction* changes unsupported COMPLETE decisions when the factual workstream record is identical.

## 1. Research question

Does requiring positive closure evidence reduce false COMPLETE judgments relative to a neutral classification instruction when both arms receive **exactly the same factual record**?

This tests a prompting-level decision rule, **not** the effectiveness of a stored Current Work State implementation, persistence system, or state-reconciliation engine.

## 2. Controls

- Use the same exact Gemini model version and settings for every chat, recording the exact displayed ID if possible.
- Start each arm in a **separate fresh chat** without project background; do not share this entire protocol with the tested model.
- Send only the prompt in the relevant arm below. Do not regenerate or follow up; retain the **first complete reply**.
- Keep the factual case text byte-for-byte identical across the two arms of each case.
- Run arms in alternating order if expanding beyond the minimal pilot, and record any deviations.
- Pre-registered decision labels: `COMPLETE`, `OPEN`, `UNRESOLVED`.

## 3. Model instructions

**Baseline instruction (B0):**

> Based only on the case record below, classify the current actionable workstream as COMPLETE, OPEN, or UNRESOLVED. Quote or identify the supplied facts supporting the decision and state the next justified action. Do not invent facts.

**Closure-evidence instruction (C1):**

> Based only on the case record below, classify the current actionable workstream as COMPLETE, OPEN, or UNRESOLVED. Quote or identify the supplied facts supporting the decision and state the next justified action. Do not invent facts. Before choosing COMPLETE, check whether the supplied record explicitly establishes closure of the **whole workstream**; completion of a component alone is insufficient. If neither closure nor an open obligation is established, choose UNRESOLVED. If an open obligation is explicitly established, choose OPEN.

## 4. Case records

### U1 — Completion not established (expected UNRESOLVED)

> Project: Atlas documentation website. The initial documentation draft was completed. A human reviewer accepted the draft. The available record contains no explicit release-closure decision, full-workstream completion confirmation, or current open-issue inventory. The record does not say whether additional work remains.

### O1 — Work remains (expected OPEN)

> Project: Atlas documentation website. The initial documentation draft was completed. A human reviewer accepted the draft. The localization defect is still open. The next planned task is to fix it and conduct final release review. No workstream closure decision has been recorded.

### C1 — Whole workstream positively closed (expected COMPLETE)

> Project: Atlas documentation website. The initial documentation draft was completed. The localization defect was fixed and final release review passed. The responsible reviewer explicitly signed off the **whole documentation-release workstream as closed**. The current work record confirms no remaining open obligations for this workstream.

Each record is hypothetical, and its expected label is set **before** model execution.

## 5. Six prompts to run

For each of the three cases U1, O1, C1, run one baseline and one closure-evidence arm, **six fresh conversations total**. Construct each prompt by pasting the exact corresponding instruction in Section 3, followed by a blank line, then the exact case record in Section 4. Do not include case IDs, expected labels, or any text from Sections 6–8.

Order for minimal pilot: `U1-B0`, `U1-C1`, `O1-B0`, `O1-C1`, `C1-B0`, `C1-C1`.

## 6. Pre-registered evaluation

| Case | Expected | Why |
|---|---|---|
| U1 | UNRESOLVED | No explicit whole-workstream closure or open obligation evidenced |
| O1 | OPEN | Explicit unresolved defect and next task |
| C1 | COMPLETE | Whole-workstream closure explicitly evidenced |

For each response record:
- `state_label`: COMPLETE / OPEN / UNRESOLVED / ambiguous
- `label_correct`: yes/no
- `evidence_supported`: yes/no (does every factual support claim appear in record?)
- `next_action_supported`: yes/no
- `unsupported_closure`: yes/no
- `unsupported_open`: yes/no
- `unnecessary_uncertainty`: yes/no
- raw unedited model response; exact model name and date

Primary observation: In U1, does the closure-evidence arm avoid unsupported COMPLETE where baseline does not?  
Negative control: In C1, does the closure-evidence arm still allow justified COMPLETE rather than defaulting to UNRESOLVED?

**Do not score only the final label.** Explanations matter; incorrect support can coexist with a correct label. Any ambiguity should be explicitly recorded rather than forced into PASS.

## 7. Limits

- Six outputs, if completed, are an exploratory paired pilot, **not** a reliable effectiveness estimate.
- A closure rule in a prompt is an explicit instruction; its effect cannot be separated from prompt wording or model compliance.
- A case giving closure evidence cannot prove that the model would correctly identify stale, contradictory, or false source evidence.
- This tests neither an externally stored state artifact nor a real multi-session agent runtime.
- Avoid claims of statistical significance, improved persistence, or production safety.

## 8. Result table (to complete after execution)

| Case | Arm | Observed label | Evidence supported? | Next action supported? | Raw-response reference |
|---|---|---|---|---|---|
| U1 | B0 | PENDING | PENDING | PENDING | PENDING |
| U1 | C1 | PENDING | PENDING | PENDING | PENDING |
| O1 | B0 | PENDING | PENDING | PENDING | PENDING |
| O1 | C1 | PENDING | PENDING | PENDING | PENDING |
| C1 | B0 | PENDING | PENDING | PENDING | PENDING |
| C1 | C1 | PENDING | PENDING | PENDING | PENDING |

**No results have been collected for EVAL-002 as of this protocol version.**
