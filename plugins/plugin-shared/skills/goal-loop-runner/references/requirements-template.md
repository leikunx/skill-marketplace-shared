# User Requirements Ledger

Keep this record separate from compact progress summaries. Populate it from all available
goal-relevant user input, then reconcile each new message before dependent work. Retain
exact meaningful values and limits; redact secret values and record only their purpose
and protected reference. Do not publish task-local requirements with reusable skills.

## Capture checkpoint

- Goal identity / original objective:
- State-file path:
- Ledger revision:
- Last reconciled user message ID or turn ordinal:
- Available earlier discussion reconciled through:
- Capture coverage and any unavailable-history gap:
- Last complete-ledger read / recovery after compaction or handoff:

## Requirement register

Use stable IDs such as `R-001`. Source includes a message ID when available, otherwise
a turn ordinal and a short faithful quote or paraphrase. Kind identifies an outcome,
feature, quality/verification condition, preference, exclusion, scope/authority boundary,
or deliverable. Provenance distinguishes explicit instructions from user-accepted
proposals; agent assumptions belong in the separate section below.

| ID | User source | Requirement and provenance | Kind | Acceptance check | Status | Evidence location / revision | Change links |
| --- | --- | --- | --- | --- | --- | --- | --- |

Statuses: `pending`, `in_progress`, `verified`, `blocked`, `superseded`, `withdrawn`,
or `deferred_by_user`. Currently binding requirements are pending, in progress, verified,
or blocked; unresolved acceptance or authority remains pending/blocked, not complete.
Only fresh evidence satisfying the acceptance check supports `verified`. Superseded,
withdrawn, or user-deferred entries retain their user source and change links.

## Assumptions and open questions

Keep unaccepted suggestions, material interpretation questions, and implementation
assumptions distinct from binding user requirements. Link any affected IDs. Silence or
an unsubmitted suggested answer does not convert these entries into user decisions.

| ID | Source / rationale | Assumption, proposal, or question | Affected requirement IDs | Status / user decision source |
| --- | --- | --- | --- | --- |

## Amendment history

Append every correction, withdrawal, accepted proposal, and user-directed deferral.
Retain superseded wording in the register; link replacements without reusing IDs.
Reopen verified entries when a change invalidates their evidence.

| Change ID | User source | Affected / replacement IDs | Exact change and disposition | Evidence requiring revalidation |
| --- | --- | --- | --- | --- |

## Completion audit

- Audited ledger revision / capture cursor:
- Complete ledger and amendment history re-read:
- Final deliverable / objective-gate evidence:

| Requirement ID | Binding or user-directed disposition | Acceptance check and fresh evidence | Verified / unmet / needs clarification |
| --- | --- | --- | --- |

Audit every register entry so exclusions are traceable, then require every currently
binding entry to be verified before claiming all requested work complete. Record missing
evidence and remaining work explicitly; do not silently downgrade requirements at a
budget boundary. Preserve the full register and amendment history through compaction.
