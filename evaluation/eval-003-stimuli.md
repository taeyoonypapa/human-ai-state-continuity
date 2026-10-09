# EVAL-003 — Participant Prompt Pack

**Status:** STIMULI FROZEN / NOT EXECUTED  
**Instructions:** Run each prompt in its own fresh Gemini chat. Copy text from exactly one fenced block at a time. Do not send this document's heading or run labels to Gemini. Do not regenerate answers. The fictional transcripts are designed for controlled testing, not taken from real private conversations.

## Run 1 — N1-B0

```text
Read this fictional team conversation as the only available work history. Based only on the record, classify the CURRENT actionable state of the overall workstream as COMPLETE, OPEN, or UNRESOLVED. Cite specific messages that support your classification and give one justified next action. Do not invent facts.

[1 | Mon | PM] Quartz product launch notes need to go live on Friday. We need copy edits, legal language review, and a mobile accessibility check of the final page.
[2 | Mon | Writer] I'll rewrite the overview and FAQ today.
[3 | Tue | Writer] Overview and FAQ rewrite done. I left a note that the mobile button contrast hasn't been checked against the final layout yet.
[4 | Tue | PM] Thanks. Let's finish the legal language review first; design will send the mobile screenshots afterward.
[5 | Wed | Legal] Legal language reviewed. No wording changes required.
[6 | Wed | Writer] I incorporated the last copy tweaks. The launch-note document is ready for approval.
[7 | Wed | PM] Approved — the launch-note COPY looks good. Please keep the accessibility verification on the release checklist.
[8 | Thu | Designer] Final screenshots exported. I didn't complete the contrast check; the test device is unavailable until tomorrow.
[9 | Thu | Writer] The doc is now tagged 'final-copy'. I'll send it to the publishing coordinator.
[10 | Thu | Coordinator] Received. I can stage the page, but I haven't confirmed its release readiness.
[11 | Fri | PM] Great work, the document and copy review are finished. Thanks everyone.
[12 | Fri | Coordinator] I'll archive the writing ticket as done and keep the launch page staged.
```

## Run 2 — N2-C1

```text
Read this fictional team conversation as the only available work history. Based only on the record, classify the CURRENT actionable state of the overall workstream as COMPLETE, OPEN, or UNRESOLVED. Cite specific messages that support your classification and give one justified next action. Do not invent facts. Before choosing COMPLETE, identify explicit evidence that the WHOLE workstream (not just a document or component) was closed. If closure is not established but an outstanding required task is explicitly recorded, choose OPEN. If neither closure nor an outstanding task is established, choose UNRESOLVED.

[1 | Mon | PM] Harbor help-center refresh: update five articles, QA all links, get localization sign-off, then release.
[2 | Mon | Editor] Drafts of all five articles finished.
[3 | Tue | PM] Drafts approved for QA; not release approved yet.
[4 | Tue | QA] Two broken links found in article three.
[5 | Wed | Editor] Links corrected. Ready for retest.
[6 | Wed | QA] Retest passed for all five articles; no broken links remain.
[7 | Thu | Localization] All localized versions reviewed and approved.
[8 | Thu | PM] Please publish and give me the release checklist evidence.
[9 | Fri | Publisher] All five refreshed articles are live; release checklist signed, links rechecked on the live site.
[10 | Fri | PM] I reviewed the release checklist. I explicitly sign off the ENTIRE Harbor help-center refresh workstream as closed. No remaining release obligations or open issues.
[11 | Fri | Editor] I'll archive the release notes and transition normal article upkeep to the maintenance queue.
[12 | Fri | PM] Confirmed. No additional project work is pending.
```

## Run 3 — N2-B0

```text
Read this fictional team conversation as the only available work history. Based only on the record, classify the CURRENT actionable state of the overall workstream as COMPLETE, OPEN, or UNRESOLVED. Cite specific messages that support your classification and give one justified next action. Do not invent facts.

[1 | Mon | PM] Harbor help-center refresh: update five articles, QA all links, get localization sign-off, then release.
[2 | Mon | Editor] Drafts of all five articles finished.
[3 | Tue | PM] Drafts approved for QA; not release approved yet.
[4 | Tue | QA] Two broken links found in article three.
[5 | Wed | Editor] Links corrected. Ready for retest.
[6 | Wed | QA] Retest passed for all five articles; no broken links remain.
[7 | Thu | Localization] All localized versions reviewed and approved.
[8 | Thu | PM] Please publish and give me the release checklist evidence.
[9 | Fri | Publisher] All five refreshed articles are live; release checklist signed, links rechecked on the live site.
[10 | Fri | PM] I reviewed the release checklist. I explicitly sign off the ENTIRE Harbor help-center refresh workstream as closed. No remaining release obligations or open issues.
[11 | Fri | Editor] I'll archive the release notes and transition normal article upkeep to the maintenance queue.
[12 | Fri | PM] Confirmed. No additional project work is pending.
```

## Run 4 — N1-C1

```text
Read this fictional team conversation as the only available work history. Based only on the record, classify the CURRENT actionable state of the overall workstream as COMPLETE, OPEN, or UNRESOLVED. Cite specific messages that support your classification and give one justified next action. Do not invent facts. Before choosing COMPLETE, identify explicit evidence that the WHOLE workstream (not just a document or component) was closed. If closure is not established but an outstanding required task is explicitly recorded, choose OPEN. If neither closure nor an outstanding task is established, choose UNRESOLVED.

[1 | Mon | PM] Quartz product launch notes need to go live on Friday. We need copy edits, legal language review, and a mobile accessibility check of the final page.
[2 | Mon | Writer] I'll rewrite the overview and FAQ today.
[3 | Tue | Writer] Overview and FAQ rewrite done. I left a note that the mobile button contrast hasn't been checked against the final layout yet.
[4 | Tue | PM] Thanks. Let's finish the legal language review first; design will send the mobile screenshots afterward.
[5 | Wed | Legal] Legal language reviewed. No wording changes required.
[6 | Wed | Writer] I incorporated the last copy tweaks. The launch-note document is ready for approval.
[7 | Wed | PM] Approved — the launch-note COPY looks good. Please keep the accessibility verification on the release checklist.
[8 | Thu | Designer] Final screenshots exported. I didn't complete the contrast check; the test device is unavailable until tomorrow.
[9 | Thu | Writer] The doc is now tagged 'final-copy'. I'll send it to the publishing coordinator.
[10 | Thu | Coordinator] Received. I can stage the page, but I haven't confirmed its release readiness.
[11 | Fri | PM] Great work, the document and copy review are finished. Thanks everyone.
[12 | Fri | Coordinator] I'll archive the writing ticket as done and keep the launch page staged.
```
