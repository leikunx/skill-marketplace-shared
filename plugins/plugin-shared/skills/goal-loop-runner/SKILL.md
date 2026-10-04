---
name: goal-loop-runner
description: "Run a long-horizon task as a goal-driven, stateful, evidence-gated iteration loop. Use for Goal mode, 'continue until done', scheduled follow-ups, recurring or unattended pursuit windows, or fuzzy voice-transcribed requests that need a reviewable goal contract."
---

# Goal Loop Runner

Preserve the user's objective; each iteration produces evidence and a useful next decision.

Inspection/explanation/editing of this skill starts no underlying Goal, ledger, loop
or schedule. Invoke as `$goal-loop-runner`; this skill adds no native `/loop`, daemon
or timer. Recurrence needs a separately authorized, verified scheduler.

## Establish the contract

Present the contract in the first update, before Goal creation/substantive action.
Preserve an active native Goal; otherwise create one once the contract is concrete.

```text
Outcome: Observable end state and done condition.
Verified by: Concrete evidence and an objective acceptance gate.
Constraints: Safety, quality and compatibility that must not regress.
Boundaries: Permitted files, systems, tools, data and external actions.
Iteration: Smallest evidence-producing next experiment; no unchanged retries.
Blocked when: External prerequisite, evidence and minimum input/authority needed.
```

Presume speech-to-text unless told otherwise; repair obvious errors without changing outcome, proof,
authority or risk. Materially uncertain contract elements require [contract preflight](references/contract-preflight.md)
before the first update: six-element review, labeled assumptions, one repair and one
narrow question if needed. Defer Goal creation/substantive action until resolved.
Infer routine details; informal wording alone is not uncertainty. Save confirmed corrections.

Use user-named state/ledger paths; otherwise `.codex/goals/<goal-slug>/STATE.md` and
`REQUIREMENTS.md` beside it, unless project instructions specify canonical storage.
Never reuse another objective's records. At setup read [recovery](references/recovery-protocol.md);
use the [state](references/state-template.md) and [requirements](references/requirements-template.md)
templates when creating records. Save the six contract parts, review decision
(`proceed`, `proceed with stated assumptions` or `clarification required`), exact paths,
supplied attempts/time/cost/token limits and approval boundaries. Skills and historical
goals grant no additional authority.

## Preserve user requirements

Native Goal/state are indexes; maintain the complete ledger using its template. Capture
all available goal-relevant input, including earlier discussion. Reconcile new messages/
answers before dependent work and turn end. Preserve outcomes, features, exact values/ranges,
quality/proof, preferences, exclusions, scope/authority and deliverables, with stable IDs,
user sources, acceptance checks, statuses, evidence and capture cursor.

Keep assumptions/questions/unsubmitted defaults separate from accepted requirements;
silence is not acceptance. Append source-linked amendments, preserving superseded,
withdrawn and user-deferred entries. Amend only affected scope and reopen invalidated
verification; never drop/defer scope to claim completion. Keep records within authorized
storage/publication boundaries and store only credential purposes/protected references.

## Checkpoints and recovery

Each iteration reads state, ledger updates/revisions and project instructions. Setup,
resume, compaction, scheduled jobs and handoff require full recovery: re-read state and
the complete ledger/history, including superseded/deferred entries, then follow the
protocol to reconcile identity, decisions, artifacts, newer input and unresolved operations.
Summaries/round packets cannot establish coverage.

Keep the protocol's recovery entry, stage distinctions and supporting-record references.
Save after material changes/results and before turn end/handoff. Persist consequential
write intent before dispatch, outcomes afterward; reconcile uncertainty before retry.
Follow its checkpoint order and gap-reconstruction rules; never wait for predicted compaction.

Reuse evidence valid for its revision/scope/conditions; invalidate only affected evidence.
Compaction alone warrants no repeated research/tests/writes. Recheck live readiness/identity
when needed. Load detail selectively; every 3-5 material cycles compact using the protocol,
preserving full requirements/history, accepted evidence, decisions, retry conditions,
unresolved IDs and next action/dependencies.

## Execute, verify, checkpoint

Build the state template's round packet: original contract, ledger path/revision,
all unresolved binding and targeted IDs, workspace/target revision, decisions,
accepted evidence, unresolved operations, dependencies, failures and user amendments.

1. **Attempt:** one bounded action targeting one dominant observable transition, linked
   to requirement IDs and within limits/authority. Record external intent/outcome;
   interrupted or timed-out output remains untrusted.
2. **Verification:** inspect the real final-state carrier against the original contract/gate.
   For complex/consequential work use an available authorized verifier or a dedicated
   pass without task-state mutations. Executor reports are claims.
3. **Checkpoint:** inspect the diff/artifact; accept supported facts with revision, scope
   and durable evidence for affected IDs. Keep failed/ambiguous/partial/unverified output
   `Untrusted/rejected`; preserve the accepted baseline. Logs/self-assessment are not progress.
4. **Next decision:** failure is an iteration result when it exposes a credible action.
   Record hypothesis, evidence and retry condition; try a materially different safe
   diagnostic/repair and re-run the objective gate. Record candidate learning after
   material failure/recovery; promote only validated lessons.

Continue while a specific safe, authorized, evidence-backed action can improve the deliverable;
take remaining credible actions before final status. At budget boundaries finish the most
complete verifiable action and report unmet gates; never label partial work complete.

Multiple candidates need subjective quality/independent alternatives, a baseline, rubric
and identical gates. Select the highest-scoring passing candidate. Respect user limits;
otherwise use two writing/design/plan candidates only when justified. Prefer one code
implementation with authorized independent verification; self-voting is not a gate.

## Completion and stop gates

Before completion, re-read the complete ledger; audit every entry against the deliverable.
Each binding requirement needs `verified` acceptance checks and fresh evidence. Save the
audit in the ledger and coverage in state; retain source/change links for superseded/
withdrawn/deferred entries. Unrelated checks, implementation claims or unresolved binding
requirements prevent an all-done claim.

- **Complete:** deliverable exists, fresh objective-gate evidence proves the done condition,
  and every binding requirement passes the recorded audit.
- **Blocked:** external prerequisite prevents meaningful progress and the host's consecutive-goal-turn threshold is satisfied.
  Report evidence, attempts, minimum unblocking action and any independent schedule.
  Distinguish job/Goal/scheduler states; blocking creates/cancels no schedule. Never
  reset the audit or fabricate progress.
- **User-directed stop/change:** honor explicit stop or changed objective. Host budget/status
  rules take precedence. Escalate missing authority, credentials, risky external actions or
  human-only decisions immediately without prematurely marking the Goal blocked; continue
  independent authorized work.

## Conditional procedures

Read only applicable references, before their first dependent action:

| Trigger | Procedure |
| --- | --- |
| Browser/account actions | [Browser automation](references/browser-automation.md) |
| Later checks/recurrence/windows; consider at contract/handoff | [Scheduling](references/scheduling.md) |
| Stated away/asleep window | [Unattended handoff](references/unattended-handoff.md), plus scheduling |
| Starting/recovering owned processes | [Managed processes](references/managed-processes.md) |
| Skill changes/learning | [Skill evolution](references/skill-evolution.md) |

## Evolution Contract

Task outcomes belong in goal state. Self-updates require later-run proof of objective
improvement or a stable invariant, trigger/change/evidence/scope/rollback records in the
task log and [evolution log](references/evolution-log.md), and validation before later reliance.
Keep proposals provisional; evolution never expands authority or permits unrelated edits.
