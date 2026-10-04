---
name: goal-loop-runner
description: "Run a long-horizon task as a goal-driven, stateful, evidence-gated iteration loop. Use for Goal mode, 'continue until done', scheduled follow-ups, recurring or unattended pursuit windows, or fuzzy voice-transcribed requests that need a reviewable goal contract."
---

# Goal Loop Runner

Combine Codex goal tracking with an execution loop: preserve the user’s objective across turns and produce fresh evidence and a useful next decision each iteration.

## Turn a natural-language request into a strong Goal

Before creating a Goal or taking substantive action, translate the user's natural-language request into this six-part draft:

1. **Outcome:** what must be true at completion.
2. **Verification surface:** the concrete evidence that will prove it.
3. **Constraints:** behavior, quality, safety, or compatibility that must not regress.
4. **Boundaries:** permitted files, systems, tools, data, and external actions.
5. **Iteration policy:** how to choose the next smallest experiment after each result.
6. **Blocked stop condition:** when to stop, what evidence to report, and what input or authority would unblock progress.

### Fuzzy or voice-transcribed input preflight

Unless the user says otherwise, presume speech-to-text input. Silently resolve obvious homophones, repetitions, missing punctuation, and implausible words against the active goal and evidence. Treat inferred meaning as an assumption; never change authority, outcome, verification, or risk boundaries. If interpretations differ materially on those points, surface the alternatives and ask one narrow question. Keep confirmed corrections in goal state; promote only stable, user-established conventions to reusable guidance.

Input is **fuzzy** when disfluencies, fragments, vague references, missing success criteria, or conflicting directions leave any contract element materially uncertain. Informal wording alone is not uncertainty; infer ordinary implementation details without changing authority, risk, verification, or outcome.

For fuzzy input, show the draft in the first progress update before creating a Goal or taking substantive action. Mark material inferences `Assumption:` and show a **Contract review** with one finding per element:

1. Does the Outcome describe an observable end state rather than an activity?
2. Can the Verification surface produce evidence independent of the agent's opinion?
3. Do Constraints protect the important safety, quality, and compatibility requirements?
4. Do Boundaries name the allowed systems/actions and avoid silently expanding authority?
5. Does the Iteration policy choose a smallest evidence-producing next action and avoid unchanged retries?
6. Does the Blocked stop condition name the evidence, missing input, or authority needed to proceed?

End with `Decision: proceed`, `Decision: proceed with stated assumptions`, or `Decision: clarification required`. This review checks contract usefulness, not eventual outcome correctness.

Safely repair weak findings once with explicit assumptions and review the revision. Ask one narrow question only if a remaining weakness materially affects objective, proof, authority, safety, or external impact; defer Goal creation and substantive action until resolved. For concrete requests, show the compact contract; itemize the review only when an assumption or material tradeoff needs confirmation.

Present the contract in the first progress update. Discover or reasonably assume routine details. Once the contract is concrete, create the Goal and copy its six parts and review decision into the state file.

Use this compact form when presenting a draft:

```text
Outcome: ...
Verified by: ...
Constraints: ...
Boundaries: ...
Iteration: ...
Blocked when: ...
```

## Establish the contract

Before the first substantive action, establish:

- **Objective:** preserve the active Codex goal if present; otherwise state a concise proposed objective.
- **Done condition:** a concrete result plus an objective gate wherever possible.
- **State file:** use the user-named path; otherwise `.codex/goals/<goal-slug>/STATE.md` in the task workspace. Never reuse a state file belonging to another objective.
- **Requirements ledger:** use the user-named path; otherwise `REQUIREMENTS.md` beside the state file. Record its exact path in state and keep it separate from compact progress summaries. Never reuse it for another objective.
- **Limits:** attempts, duration, cost/token budget when supplied, and approval boundaries.

Create the state file and requirements ledger from [the state template](references/state-template.md) and [the requirements template](references/requirements-template.md) when needed. At iteration start, read current state, reconcile ledger revisions/updates, and read applicable project instructions; full recovery is required at setup and after compaction/resume/handoff. At the end, persist requirement updates and record facts: action, outcome, evidence, blockers, and the next action.

## Preserve every user requirement

During goal execution, maintain the requirements ledger as the durable record of user intent. The native Goal objective and `STATE.md` summarize progress; neither replaces the complete requirement register.

- **Capture:** extract all goal-relevant requirements from the available user messages, including earlier discussion and accepted decisions, not just the latest prompt. Reconcile every subsequent user message, including structured answers. Persist new or amended requirements before dependent actions and before ending a user-facing turn; do not keep them solely in conversation memory. Preserve outcomes, features, exact values and ranges, quality/verification requirements, preferences, exclusions, scope and authority limits, and requested deliverables. Record a message reference or turn ordinal with a short faithful quote or paraphrase; keep a capture cursor so later input is not skipped.
- **Separate provenance:** distinguish explicit user instructions and user-accepted proposals from agent assumptions or pending suggestions. Questions and hypothetical exploration are not automatically implementation requirements; record any resulting user decision. An unsubmitted default option is not acceptance. Record material uncertainty without inventing an answer or expanding authority.
- **Track changes:** split multi-part messages into independently checkable requirements, retaining their shared source; give each a stable ID, acceptance check, status, and evidence. Append corrections, withdrawals, and user-directed deferrals to change history, linking affected IDs. Preserve superseded entries and their replacement/source links. A later amendment changes only the affected requirements unless the user explicitly replaces the objective; do not silently drop earlier scope or defer it to declare completion.
- **Protect secrets:** preserve a credential requirement's purpose and protected reference, never its password, token, or other secret value in the ledger, summaries, public skill sources, or logs. Keep task requirement records within the task's authorized storage and publication boundaries.

## Durable state and recovery

At execution setup, read [the recovery protocol](references/recovery-protocol.md). Keep a compact recovery entry in `STATE.md`: goal identity, checkpoint revision/time, exact workspace and artifact locations, supporting-record paths/revisions, current decisions, evidence references, unresolved operations, and the next bounded action. Record only applicable fields. Separate implemented, verified, published, and deployed stages when those stages apply; a progress label alone is not evidence.

Persist decisions and their reconsideration conditions, failed approaches and their retry conditions, and verification scope/version so recovery can reuse valid work. Save after material decisions, results, user amendments, and before ending a turn; record intent before a consequential external write and its observed outcome afterward. Do not wait for a predicted compaction threshold. Write supporting records before updating the checkpoint entry, and preserve evidence of interrupted or uncertain operations. Keep task records within authorized storage, excluding secret values and unrelated user data.

### Recovery after compaction or handoff

Before the next substantive action after context compaction, a resumed turn, a scheduled job, or a handoff, re-read the state and the complete requirements ledger from disk, in chunks when needed. Include change history and superseded/deferred entries when reconstructing the current requirements; do not rely only on a compacted conversation summary, the native Goal text, or the latest round packet.

Follow the recovery protocol: confirm goal/workspace identity, reconcile newer user input, restore effective decisions, inspect actual artifacts and unresolved external operations, and invalidate only evidence affected by changes. Read the complete requirements ledger while loading detailed logs and archived attempts only when the next action needs them. Reuse passing evidence whose tested revision, scope, and relevant conditions remain valid; compaction alone does not require repeating research, tests, or completed writes.

If records are missing, inconsistent, or incomplete, reconstruct them from available authoritative records and mark the gap; never claim full coverage from an incomplete summary. Continue independent safe work and clarify only material intent that cannot be recovered. Before a handoff or known compaction boundary, flush updates and include goal identity, exact state/supporting-record paths and revisions, capture cursor, unresolved requirement/operation IDs, and the next action in the handoff. Saved runtime and authentication observations require fresh checks when the next action depends on them.

### Requirement completion gate

Before marking the Goal complete or reporting all requested work done, re-read the complete ledger and audit every currently binding requirement against the actual deliverable and fresh evidence. Each must be `verified` with its acceptance check and evidence location; implementation claims, progress summaries, and a passing unrelated check do not suffice. Evidence invalidated by an amendment or later change returns the affected requirement to an unverified status.

Record the audit in the ledger and summarize its coverage in state. A pending, in-progress, blocked, uncertain, or unverified requirement prevents an all-done claim. Superseded, withdrawn, and user-deferred requirements need explicit user-source/change links; document their disposition rather than deleting them. On a bounded handoff, stop, or budget boundary, report verified and unmet requirements honestly and follow the host's Goal-status policy without relabeling partial work complete.

## Round packet and checkpoint trust

Start each iteration with a compact round packet: original objective, active contract, requirements-ledger path/revision and all unresolved binding IDs, IDs targeted this round, exact workspace/target revision, relevant effective decisions, latest accepted checkpoint and evidence, unresolved operation IDs, remaining work/dependencies, relevant failures or rejections, and authoritative user amendments. Raw transcripts, tool logs, executor claims, partial output, and timed-out work support diagnosis, not accepted progress.

Keep attempt, verification, and checkpoint decisions distinct:

1. **Attempt:** perform one bounded action that targets one dominant state change.
2. **Verification:** inspect the real file, application, browser, service, or other final-state carrier against the original contract and the action's gate. Treat the action report only as a claim.
3. **Checkpoint:** promote only independently supported facts and artifacts into accepted state. Put failed, ambiguous, contaminated, or not-yet-verified output under `Untrusted/rejected` with the evidence needed for recovery; never overwrite the last accepted checkpoint with it.

For complex or consequential work, prefer a separate reviewer or verifier when available; otherwise use a dedicated pass without task-state mutations. Reconstruct the original acceptance constraints to prevent contract drift, incomplete subtasks, or easier proxies from redefining completion. Goal state and logs never substitute for the deliverable.

## Browser automation default

For browser automation, first check Playwright Extension MCP availability. When available, use it for the initial browser action and collect evidence. Use another mechanism only at the user's explicit request, when the extension is unavailable or disconnected, or for an unsupported capability; first record the reason in goal state.

This browser-only preference does not require browser tools for other work or override authorization or safety boundaries.

### Multiple browser profiles and accounts

Separate Playwright Extension MCP instances may use different authenticated profiles. Honor an explicit instance choice; otherwise use task account/organization context and user-established mappings in project memory or `AGENTS.md`. Use the project default only without profile-specific context. Tool names do not prove identity; instances need not share sessions.

Before an account-sensitive action or external write, verify the live signed-in account and relevant organization or tenant through a read-only check in the selected instance. Record the selected instance, expected identity, and verification evidence in goal state. A remembered mapping is a routing hint, not proof of current authentication. If identity is wrong or uncertain, inspect or recover the intended session; ask only when the target identity cannot be determined from existing context and evidence. A disconnected or signed-out instance does not justify silently substituting another identity, transferring credentials, or changing authorization boundaries. Verify non-browser tool authentication separately when needed; browser sign-in does not establish Git, CLI, or API identity.

Keep exact instance/profile/account mappings in project memory, updating them when the user changes them; keep task observations in goal state. Shared guidance must remain general, without local account names, tenant identifiers, or machine-specific mappings.

## Scheduled follow-ups

Consider scheduling during contract and handoff when checks must continue after the turn, such as review, build, reply, or deployment waits. Distinguish the outcome from its later-work trigger: a goal, skill, state file, or service-side auto-complete setting does not establish a Codex schedule.

If available, read `$plugin-shared:codex-scheduled-followups` for scheduling, CLI alternatives, and verification. This reference is optional; otherwise use the current [official scheduled tasks documentation](https://learn.chatgpt.com/docs/automations?surface=app) and guidance below. Discover actual schemas or supported app controls before scheduling; never invent tools, copy unverified parameters, or equate missing session tools with missing product capability.

- Prefer supported existing-chat schedules for context-dependent follow-ups; official documentation describes minute-based intervals. Use standalone schedules for independent runs. When native scheduling is unavailable or the environment requires it, an external scheduler can invoke `codex exec`; see [non-interactive mode](https://learn.chatgpt.com/docs/non-interactive-mode).
- Reuse established execution scope and scheduling authorization. Specify cadence, timezone, stop condition or pursuit window, permitted actions, and notification destination; ask only for material missing choices. Editing or explaining guidance does not create a monitor; ordinary goals do not authorize indefinite recurrence.
- Check for a matching schedule before creating one. Record its identifier, enabled state, next run, exact definition, environment, shared state and requirements-ledger paths, bounded runtime, and non-overlap lease. Verify an actual scheduler-launched run with required tools, browser profile, authentication, and resulting evidence before claiming monitoring works; a saved definition or manual check is insufficient.
- If only external review or a confirmed running job remains, mark the current job waiting and preserve a separately authorized schedule until its stop condition. Keep goal, job, and scheduler status distinct. Follow the host's repeated-blocker policy; never fabricate progress, reset its audit, or imply that blocking a goal creates or cancels a schedule.
- On verified completion, send any already-authorized notification once and disable the schedule. At its configured end or user stop, stop launching jobs and report the accepted checkpoint and remaining gates. Without a verified scheduler, state that future checks are not configured.

Use scheduling state fields only when applicable. For away/asleep windows, also follow the handoff protocol below.

## Unattended pursuit windows

For a stated away/asleep period, follow [the unattended handoff protocol](references/unattended-handoff.md). Before it begins, present the contract and consolidate material uncertainties requiring user input into one clarification. Record confirmed start/end and timezone, cadence, job/round limit, per-job timeout, exact scheduler command or definition and identifier, non-overlap lease and stale-claim policy, process/log cleanup owner, verification gate, and shared goal-state path. After contract confirmation or explicit window start, send no blocking questions during it.

Keep pursuing the goal through recoverable failures during the window. Follow Scheduled follow-ups to launch bounded, stateful jobs through a supported native or external scheduler; the skill creates no timer. Prevent overlap on mutable targets unless concurrency is explicitly safe. Each job records its scheduler/job id, claims a round with a time-bounded lease, rebuilds the round packet, and resumes the accepted checkpoint, not executor claims. Reclaim a stale lease only after verifying its process or external action is inactive.

Each job applies the recovery protocol, including reading goal state and the complete requirements ledger, reconciling available new user input and uncertain operations, and inspecting the current browser, process, service, or remote state. After failure, record the hypothesis and try a materially different safe diagnostic or recovery within that job. Browser options include connectivity checks, tab selection or creation, readiness waits, console/network evidence, and revisiting authenticated routes. Never retry unchanged or stop solely over one failed navigation, selector, or process start.

Resolve routine choices from available resources or authorized safe defaults. For external prerequisites—interactive sign-in, missing credentials, multifactor approval, payment confirmation, or product decisions—never fabricate answers or wait inside a job. Record exact evidence and the minimum unblocking action, continue independent safe work, and let later jobs revalidate until window end. Never bypass authentication, fabricate credentials, accept payment terms, or create charges to avoid waiting.

At window end, report accepted changes, objective-gate evidence, failed and recovered attempts, remaining external prerequisites, and the next scheduled or user action. Follow the normal repeated-blocker policy; user absence during an authorized window is no reason to abandon safe exploration.

## Evidence-driven self-evolution

For long-running work, improve the workflow through evidence, not unconstrained self-critique. Keep information in three layers:

- **Task state:** Refresh the selected `STATE.md` and requirement coverage each cycle using the recovery protocol; retain completed evidence, current constraints, blockers, and one credible next action. Compact progress and speculation without dropping user requirements or their amendment history.
- **Validated lessons:** Record a lesson only after a later cycle confirms that applying it improved an objective gate. A lesson states the trigger, changed action, and evidence. Keep unvalidated ideas in the iteration log, not durable lessons.
- **Reusable guidance:** Promote a lesson to a project `AGENTS.md` or a skill only when it has proven useful across tasks or is a stable safety/operational invariant. Do not turn a one-off incident into a universal rule.

At the end of each cycle, add a concise reflection only when it changes the next decision: `hypothesis -> observed evidence -> verdict -> changed next action`.

Every 3-5 material cycles, compact progress using the recovery protocol: preserve the accepted baseline, effective decisions and reconsideration conditions, exact workspace/artifact revisions, evidence references and freshness, supporting-record paths/revisions, capture cursor, unresolved requirement/operation IDs, open risks, and next action/dependencies. Move detailed attempts and output to referenced records; retain failed-method retry conditions. Keep the complete requirements ledger and amendment history intact. Re-run the applicable gate after any strategy change. Never treat an agent's self-assessment as proof of improvement.

### Evolving skills created during a goal

When this goal produces a new or materially revised skill, give that skill an **Evolution Contract**. Its `SKILL.md` must state that it:

1. records task-local outcomes in the goal state, not in the skill itself;
2. keeps proposed improvements separate from validated lessons;
3. may update its own instructions or references only after a later run proves an objective improvement or a stable safety/operational invariant;
4. records the trigger, exact change, evidence, and rollback condition for every self-update; and
5. validates the changed skill before relying on the new rule in a later run.

Use `references/evolution-log.md` in the generated skill when recurring improvements need a durable audit trail. Do not create that file for a one-shot skill or write to it every cycle. The goal loop remains the governance layer: a skill never expands authorization, changes unrelated files, or treats a failed run as evidence that its own instructions are correct.

## Evolution Contract

This skill records task-local outcomes in the selected goal state, not in this file. Proposed improvements remain provisional until a later run demonstrates an objective improvement or a stable safety/operational invariant. Any self-update must record its trigger, exact change, evidence, scope, and rollback condition in the goal iteration log and [the evolution log](references/evolution-log.md); validate the changed skill before relying on its new rule in a later run. This contract grants no authority to alter unrelated files, expand external actions, or treat self-review as outcome evidence.

## Iteration

For every cycle:

1. Read the active goal, applicable project instructions, current state, and ledger revisions/updates using the recovery protocol; reconcile new user input, fully recover when resuming, and rebuild the compact round packet from the last accepted checkpoint and all binding requirements.
2. Choose the smallest action that can produce one dominant, observable state transition; link it to the requirement IDs it advances.
3. Execute it within the current round budget, recording consequential external intent before dispatch and its outcome afterward; preserve partial output as untrusted evidence if execution fails or times out. Reconcile uncertain effects before retrying a write.
4. Run a distinct verification pass using the defined gate (tests, build, lint, data check, visual check, or another stated proof) against the real final-state carrier and original contract.
5. Inspect the resulting diff or artifact. Promote verified facts into the accepted checkpoint and update evidence/status for affected requirement IDs, with actual revision, verification scope, and durable evidence references; keep rejected or uncertain output explicitly untrusted.
6. When a failure or blocker changes the approach, record its hypothesis, evidence, and revised action; promote only later-validated lessons.
7. Continue only if a specific next action has a credible path to improvement. Do not repeat an unchanged failed action. If the remaining budget cannot honestly reach the full gate, pursue the most complete verifiable action or report the exact boundary instead of spending the last round on a knowingly insufficient prerequisite.

## Final-deliverable ownership

Treat the stated deliverable as the execution mandate, including intermediate diagnostics and repairs. Record its done condition and objective gate in goal state; continue while a safe, authorized, evidence-backed next action remains.

Failure is an **iteration result** when evidence exposes a credible next action. Record the failed hypothesis and evidence, then choose a materially different action that improves the objective or distinguishes causes. Re-run the objective gate after every repair. Discover or safely infer ordinary implementation details.

Before final status, perform the requirement completion gate and check goal state for an untried, safe, authorized action with a credible path to completion; take it if one exists. Conclude only when:

- **Complete:** the final deliverable exists, fresh objective-gate evidence proves its done condition, and every currently binding user requirement passes the recorded completion audit.
- **Blocked:** progress requires a genuine external prerequisite and the host's repeated-blocker threshold across goal turns is satisfied. Report the exact evidence, attempts, minimum unblocking action, and any independently configured schedule. A bounded scheduled job may end as waiting without claiming the goal is achieved; subsequent goal-status updates still follow the host policy.
- **User-directed stop:** the user explicitly ends or changes the objective.

### Validated skill evolution during pursuit

After each material failure or recovery, decide whether it exposed a reusable instruction gap. Always record the candidate learning in the goal state. When a later cycle or independent run validates that the changed method improves the relevant gate—or when the user establishes a stable operating requirement—update the smallest relevant skill or reference without waiting for another prompt. Record the trigger, exact change, evidence, scope, and rollback condition in [the evolution log](references/evolution-log.md). Do not modify unrelated skills, and do not promote a one-off workaround or self-assessment as a reusable rule.

## Managed process recovery

Own the lifecycle of local long-running processes started for the goal—watchers, servers, builds, or test runners—until it ends. Detect failed starts without waiting for the user.

Record each process's command, working directory, session/process handle, log path, readiness signal, and start time in goal state. Each relevant cycle, inspect its handle and objective readiness: listening port, health endpoint, build-complete log, or expected artifact.

If unready, diagnose stdout/stderr, exit code, process tree, dependencies/tools, configuration, and the smallest relevant network or credential check. Apply an evidence-supported safe repair and re-run readiness; never repeat a known failed start unchanged.

Escalate recovery only for credentials, organization membership, destructive actions, external approval, or product decisions. Log diagnosis, repair, and result. Process existence never proves readiness.

### Recovery capture and promotion

When recovery improves a managed-process gate, first add a **provisional recovery record** to goal state: trigger, failed command/action, observed error, exact changed action, readiness evidence, scope/preconditions, and rollback condition. One run preserves a usable method, not a universal rule.

Promote recovery only after a later cycle or independent run applies the method and passes the same gate. For a stable operational invariant needed by later users, update the relevant skill/reference with trigger, exact change, evidence, and rollback condition. Keep one-off quirks task-local.

Finish only when the done condition and fresh gate evidence both hold. If the same external blocker persists across the required consecutive goal turns, follow Codex's blocked-goal policy. Escalate immediately for missing authority, credentials, risky external actions, or a decision that requires human judgment; escalation does not waive the host's blocked-status threshold.

## Candidate improvement and selection

Use multiple candidates only for subjective quality, independent alternatives, and an explicit comparison rubric. Keep an accepted baseline. Apply the same gate and user criteria to each; select the highest-scoring passing candidate. Self-voting cannot replace objective gates; candidate generation must respect user budgets.

For code, prefer one implementation with an independent reviewer/verifier when available. For writing, design, or plans, respect the requested candidate limit; otherwise use two only if their benefit justifies the work.

## Boundaries

Invoke as `$goal-loop-runner`; it adds no native `/loop`, daemon, or timer. Recurrence requires a verified native Codex schedule or external scheduler launching bounded jobs with the same contract and accessible state path. Loading the skill or scheduling reference does not enable recurrence.

When the user asks only to inspect, explain, or edit this skill, perform that requested work without starting a Goal, requirement ledger, execution loop, or schedule for the underlying task.
