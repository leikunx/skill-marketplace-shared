# Goal Loop State

## Recovery entry

- Goal identity / conversation or job identity when available:
- Last complete checkpoint revision / timestamp and timezone:
- Supporting-record paths / revisions (inline unless separate files are useful):
- Last recovery / observed drift / unresolved record gaps:

Keep this entry discoverable through the goal handoff or caller's task metadata. Use
exact paths; do not infer the active goal from the newest folder. Populate applicable
fields only. Keep secret values out of all records.

## Contract

- Objective:
- Done condition:
- Gate:
- State path:
- Requirements-ledger path:
- Limits and approval boundaries:

## User requirements checkpoint

- Ledger revision / last reconciled user message or turn:
- Capture coverage (complete for available history / incomplete, with gap):
- Binding requirement IDs / unresolved IDs:
- Latest amendment IDs and affected requirements:
- Assumptions or open questions affecting acceptance or authority:
- Last full-ledger read / post-compaction recovery:
- Last completion audit revision / verified and unmet IDs:

Keep requirement text, source references, change history, and per-requirement evidence in
the separate ledger. This checkpoint is an index, not a replacement for that record.

## Workspace and artifacts

- Repository / remote and authorized target:
- Exact working directory / worktree / branch when applicable:
- Starting baseline / currently observed revision:
- Uncommitted work / durable diff or artifact reference:
- Pre-existing or unrelated user work to preserve:

| Artifact ID | Requirement IDs | Exact location / revision | Applicable stage / evidence IDs |
| --- | --- | --- | --- |

Stages may include implemented, verified, published, and deployed. Record only stages
that apply; never infer a later stage from an earlier one.

## Effective decisions

| Decision ID | Choice and concise rationale | Source / provenance | Requirement IDs | Reconsideration condition / status |
| --- | --- | --- | --- | --- |

Distinguish user decisions from authorized agent implementation choices and hypotheses.
Retain supersession links. When detailed history moves to a separate record, retain
all effective decisions or their precise retrieval references here.

## Evidence index

| Evidence ID | Requirement / artifact IDs | Command or source / environment | Observed result / time | Tested revision and scope | Durable reference / freshness |
| --- | --- | --- | --- | --- | --- |

Preserve failures and untested scope. Mark evidence invalidated by relevant changes;
compaction alone does not invalidate evidence or require rerunning passing checks.

## Failed approaches and retry conditions

| Attempt ID | Requirement IDs | Action / working directory | Observed error / evidence | Conclusion or hypothesis | Condition for a materially different retry |
| --- | --- | --- | --- | --- | --- |

Keep unsupported diagnoses provisional. Retain the retry condition when archiving detail.

## External operations (when applicable)

| Operation ID | Requirement IDs | Authorized action / exact target | Stage | Remote ID or supported idempotency key / reconciliation check | Outcome / evidence |
| --- | --- | --- | --- | --- | --- |

Stages: prepared, in_flight, uncertain, confirmed, failed. Persist in_flight before
dispatch; interruption leaves an outcome to reconcile. Confirm actual target state
before retrying uncertain writes. A recorded intent or successful tool exit is not proof
that the requested final state exists.

## Runtime and execution context (when applicable)

- Required commands / working directories / relevant configuration references:
- Owned processes / session handles / start times / ports or readiness checks:
- Log paths / cleanup or handoff owner:
- Browser or tool instance / expected identity / last verification evidence:
- External resources / stable IDs / ownership:
- Blocking prerequisite / minimum unblocking action / pending question source:

Recheck live readiness and identity when the next action depends on them. Store only
protected credential references; retain no raw credentials or unnecessary account data.

## Prior-goal learning

- Memory service readiness / MCP or bundled-client evidence:
- Registered project ID / this goal ID / evolution.json revision:
- Retrieval query / excluded current goal:
- Selected 3–5 distinct prior goal IDs and source revisions:
- Per-lesson applicability and decision (apply / reject / test-next):
- Evidence freshness and current verification gate:
- Shortfall or unavailable prerequisite, when fewer than three are relevant:
- Reuse outcomes and next validation / promotion decision:

## Current round packet

- Contract version:
- Requirements-ledger revision / capture cursor:
- Requirement IDs targeted this round:
- All unresolved binding requirement IDs:
- Exact workspace / target revision:
- Relevant effective decision IDs:
- Unresolved external operation IDs:
- Accepted checkpoint:
- Evidence supporting checkpoint:
- In progress:
- Untrusted/rejected:
- Remaining work:
- Blockers:
- Authoritative user amendments:
- Next bounded action:
- Dependencies / expected observable result / verification command or gate:
- Remaining user-specified limits / deadline checked at recovery:

## Scheduled follow-ups / unattended window (when applicable)

- Window start/end/timezone or stop condition:
- Scheduling mechanism / execution environment:
- Shared state and requirements-ledger paths:
- Scheduler command or definition:
- Scheduler id / current job id:
- Scheduler enabled state / next run:
- Last actual scheduled run / verification evidence:
- Current job outcome (progress, waiting, failed, complete):
- Cadence / maximum jobs:
- Per-job timeout:
- Active round lease / expiry:
- Stale-claim recovery evidence:
- Owned processes / readiness / log paths:
- Cleanup or handoff owner:
- Last inspected target revision / message:
- Sent notification identifiers / completion notification evidence:
- Schedule shutdown condition / verified shutdown:

## Iteration log

| Cycle | Requirement IDs | Action | Gate and result | Decision |
| --- | --- | --- | --- | --- |

## Final requirements audit summary

- Complete ledger re-read at revision / capture cursor:
- Original objective gate and fresh evidence:
- Binding requirements verified / unmet, with ledger evidence links:
- Superseded, withdrawn, or user-deferred IDs and user-source links:
- Completion allowed / remaining action or boundary:

## Candidate comparison

| Candidate | Required-gate result | Rubric score | Decision and evidence |
| --- | --- | --- | --- |

## Durable lessons

-
