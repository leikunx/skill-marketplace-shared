# Durable Recovery Protocol

Read at execution setup and after compaction, resume, or handoff. The recovery entry
must let another run locate the actual work and take the next verified step without
replaying the conversation. This is task-local state, not reusable skill knowledge.

## Keep recovery records small and findable

Keep `STATE.md` as the entry point beside the complete `REQUIREMENTS.md`. Start with
inline decisions and evidence indexes from the state template. If their history grows,
move detail into task-local `DECISIONS.md`, `EVIDENCE.md`, or existing artifact/log files;
record exact paths, revisions, and useful headings or IDs in state. Separate files are
optional, not empty scaffolds to create for every task.

Record goal identity, exact state path, supporting paths/revisions, capture cursor,
unresolved requirement/operation IDs, and next action in handoffs and caller metadata
that can carry this information. Do not assume a native Goal has a custom file field
or that the newest goal directory belongs to the current conversation. If the entry
path is lost, inspect the known workspace's goal records and match objective/identity
before resuming. Preserve records for other goals.

## What survives compaction

Keep the following when applicable; link records to requirement IDs:

| Record | Minimum durable content |
| --- | --- |
| Decisions | Selected approach, concise rationale, authoritative source or agent-choice provenance, rejected alternatives that affect later work, supersession links, and conditions that justify reconsideration. |
| Workspace and artifacts | Repository, exact worktree/cwd, branch and baseline/current revision, uncommitted-work reference, pre-existing user changes, and actual deliverable locations/stages. Use equivalent version identifiers for non-Git artifacts. |
| Evidence | Check command or source URL, relevant environment, observed result/time, tested revision/scope, untested parts, durable log/artifact reference, and conditions that invalidate the result. |
| Failed approaches | Attempt/action and cwd, decisive error/evidence, proven exclusions versus hypotheses, and the change needed for a useful retry. |
| Continuation | Current step, one to three useful next actions when known, prerequisites, expected observable result/gate, unresolved questions with user-source references, and user-specified limits/deadlines. |
| External operations | Authorized action/target, local operation ID, remote identifier or supported idempotency key, dispatch/outcome stage, read-only reconciliation method, and observed effects. |
| Runtime | Owned processes/session handles, startup command/cwd, logs and readiness checks, browser/tool instance and expected identity, stable resource IDs, ownership, and cleanup/handoff responsibility. |

Persist verifiable observations and concise decision rationale. Label assumptions and
unconfirmed diagnoses. Keep credentials in authorized protected storage and record only
their purpose/reference. Exclude unnecessary personal data and private task records
from public skill sources or automated repository publication.

## Checkpoint at meaningful events

Update records after a user amendment, material decision, useful research finding,
completed verification, failed experiment, or changed blocker, and before ending a
turn. Save the current step and recovery references before a long-running operation.
Do not wait for a guessed context-window threshold or promise a pre-compaction hook
that the current environment does not provide.

Before a consequential external write, persist the authorized target, action, and
operation ID; mark it `in_flight` before dispatch. Record the observed response and
stable remote ID afterward. A timeout, interruption, or missing result leaves an
`uncertain` operation rather than proof of failure. Query the actual target before
retrying; use idempotency only when the service supports it. If the effect cannot be
determined safely, retain the uncertainty and continue independent work.

Write supporting records/artifacts first and update the state entry with their
revisions last. For a fragile overwrite, write a temporary file beside the target and
replace it only after the write succeeds. A multi-file checkpoint is not automatically
atomic: if interrupted, reconcile revision mismatches and retain the last verified
baseline. A saved checkpoint never rolls back external effects. Concurrent authorized
jobs must respect the existing non-overlap lease; this protocol adds no new concurrency.

## Recovery order

Before substantive work:

1. **Locate and match.** Read the entry, native Goal when present, and current applicable
   project instructions. Match objective/identity and exact workspace. Confirm state
   and supporting-record revisions; flag partial writes or unavailable history.
2. **Restore user intent.** Read the complete requirements ledger and amendment history,
   in chunks if needed. Reconcile available newer messages through the capture cursor.
   Restore all effective decisions, keeping assumptions separate. User amendments
   supersede only their affected scope and invalidate dependent decisions/evidence.
3. **Inspect actual state.** Check real artifacts, revision/diff, and relevant remote
   state. Reconcile unresolved writes before another mutation of their targets.
   Revalidate relevant process readiness and tool/account identity. Saved observations
   do not prove a process still runs, authentication still holds, or a deployment exists.
4. **Resolve drift.** Preserve user and unrelated edits; do not reset a worktree to match
   the checkpoint. Reconcile changed artifacts and mark affected evidence/requirements
   unverified. Recheck remaining limits/deadlines against the current Goal and clock.
   Reconstruct missing facts from authoritative sources and explicitly retain gaps.
5. **Load what the next action needs.** Read linked evidence, relevant failure/retry
   conditions, and source/artifact sections for the selected requirement IDs. Keep
   detailed historical logs available on disk. Reuse valid decisions and evidence;
   repeat research or checks only for new changes, failures, or unresolved concerns.
6. **Resume and save.** Rebuild the compact round packet from all binding requirements,
   accepted artifacts, effective decisions, unresolved operations, and dependencies.
   Select a safe action with an observable result, record recovery/drift/gaps, then
   continue the normal execute/verify/checkpoint cycle.

Routine recovery uses discoverable facts and existing authorization. Ask only when a
material decision or authority cannot be recovered; continue independent safe work.
Passing an unrelated check or reconstructing a plan does not establish completion.

## Control context cost without losing scope

After compaction, fully read the requirement register and its amendment history. On
ordinary cycles in the same restored context, read current state/ledger updates and
reconcile revisions; reload affected requirements and dependencies. A revision mismatch,
new amendment, or uncertain coverage requires rereading enough authoritative material to
restore coverage; a new resume/handoff always uses the full recovery sequence.

Keep all currently binding requirements visible through IDs and an unresolved-work
index. Keep effective decisions accessible with concise rationale and reconsideration
conditions. Archive detailed attempts/output with indexed references while retaining
their decisive findings and retry conditions. Do not repeatedly load whole transcripts,
unchanged source trees, or raw logs when targeted retrieval answers the next question.

Existing verification remains usable only for its recorded artifact revision, scope,
and relevant conditions. Amendments, dependency changes, or live-state drift invalidate
affected evidence; unchanged unrelated evidence remains usable. The final requirement
audit still reads the complete ledger and verifies the actual final deliverable.
