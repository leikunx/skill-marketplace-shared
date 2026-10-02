---
name: goal-loop-runner-endless
description: "Run an explicitly requested continuous goal pursuit with verified scheduled follow-ups, retaining evidence gates and iterating on quality after the first deliverable passes. Use for endless improvement or an authorised unattended work window."
---

# Goal Loop Runner Endless

Keep pursuing the user's outcome and improving its verified quality for the authorised
duration. Initial delivery is a milestone; it does not end an explicitly requested
continuing-improvement window. This skill installs no timer merely by being read.

## Explicit companion invocation

Before substantive execution, explicitly invoke and read both companions:

- `$plugin-shared:goal-loop-runner`: [goal contract and execution loop](../goal-loop-runner/SKILL.md).
- `$knowledge-codex-scheduled-followups`: the scheduling capability requested by this
  workflow. In the current shared plugin its maintained name is
  `$plugin-shared:codex-scheduled-followups`; explicitly invoke and read
  [that skill](../codex-scheduled-followups/SKILL.md). Use the discovered installed
  name, and record an alias resolution in task state rather than inventing a skill.

Use the installed source of each companion. These relative links document the same
package's dependencies; never treat a runtime cache as an authoring location.
If a dependency cannot be located, report the exact missing capability, continue
independent authorised work, and do not claim a functioning continuous runner.

Inherit the complete base workflow: six-part contract and fuzzy-input review, native
goal preservation, durable state, round packet, independent verification, checkpoint
trust, browser/account routing, managed-process recovery, unattended handoff and
evidence-driven evolution. The following changes govern continuous pursuit.

## Establish continuing authority

Distinguish initial acceptance from ongoing improvement. Record the user's objective,
measurable acceptance gates, quality priorities, permitted external actions, duration
or explicit until-stopped authority, timezone, cadence, per-job runtime and existing
budget limits. Explicit execution of this skill for a stated task requests continuing
pursuit of that task; a request to explain or author the skill does not start it.

Reuse established authorisation. Never infer indefinite recurrence from an ordinary
one-off task. If the user grants a finite window, use its exact end; if the user
explicitly requests indefinite pursuit, record `until user stops` and bounded jobs.
Resolve routine schedule choices from the task. Ask only for a material missing
decision, and honour an already-started unattended window without blocking questions.

Define what better means before optimising: retain objective gates and a small quality
rubric tied to the user's priorities. Preserve the highest-quality passing baseline.
Do not replace the original outcome with easier proxies or move acceptance thresholds
merely to create more work. Record initial completion as a milestone when the overall
task still includes the continuing window.

## Make continuation real

Apply the scheduling companion rather than promising to keep working:

1. Discover supported existing-chat schedules, app controls or an external CLI scheduler.
   Check for a matching active schedule before creating one.
2. Install one schedule within the user's authority. Persist its identifier, actual
   command/definition, execution environment, shared state, cadence, deadline or stop
   rule, per-job timeout, logs and notification destination.
3. Use an exclusive lease or process lock for mutable targets. Record the owner and
   expiry; reclaim stale ownership only after confirming the process and external
   operation are inactive. Coordinate foreground turns and scheduled jobs too.
4. Verify an actual scheduler-launched job, including required files, tools, browser
   profile, signed-in account and final evidence. A manual probe, saved definition,
   CLI login or running process does not prove the intended work can execute.
5. Distinguish scheduler health, tool access, account authentication and task progress.
   Report an inaccessible inbox as an operational failure, never as no new messages.
   Repair recoverable environment failures using a materially different supported
   mechanism; never change security permissions or bypass an access denial silently.

Keep machine/session prerequisites explicit. Do not modify undocumented automation
databases, invent scheduling schemas or treat the skill itself as a daemon.

## Every scheduled round

Read the latest accepted state and inspect the real environment. Choose one dominant
action with a credible path to an objective improvement, then verify independently.
Checkpoint actual effects and evidence; keep partial, failed or self-reported output
untrusted. Preserve IDs/revisions/timestamps to avoid duplicate external actions.

Select work in this order when it fits the task:

- Finish unmet acceptance gates or repair a verified regression.
- Resolve the next highest-impact evidenced quality gap.
- Process newly arrived task-related feedback within existing messaging authority.
- Recheck the highest-risk result or a changing external dependency at an appropriate
  cadence, then prepare the next useful experiment.

After a passing initial deliverable, continue the authorised quality, feedback and
monitoring rounds. The base rule to disable a schedule at initial completion is
overridden **only while the user has authorised continuing pursuit**. Keep the schedule
until that authority ends. No initial-success claim permits additional deployments,
messages, payments, identity changes or unrelated edits.

“Perfect” is an aspiration, not proof. When no evidenced improvement is available,
leave the accepted baseline intact, record that the current job is waiting, and let the
verified schedule recheck at its cadence. Do not fabricate findings, repeat unchanged
failures, add unnecessary tests, generate cosmetic churn or spam notifications to
appear continuously busy. Do not declare perfection from self-assessment.

Compact state every 3–5 material rounds. Separate proposed improvements from lessons
validated in a later round. Each job owns its started processes and must stop or hand
them off with handles, readiness evidence and a cleanup owner before releasing its lease.

## End and blockage semantics

Honour an explicit user stop, finite-window end, applicable budget limit or revoked
authority immediately. Stop launching new work, clean up owned processes, disable the
schedule and report the last verified checkpoint and remaining gates. A finite window
must never turn into indefinite pursuit automatically.

Use the host's repeated-blocker threshold for native goal status. Preserve a separately
authorised schedule for later read-only prerequisite checks when useful; a blocked goal
does not create or cancel a schedule. Never reset the blocker audit or invent progress.
At a genuine prerequisite, record evidence and the minimum unblocking action, continue
independent safe work, and do not fabricate credentials, consent or human decisions.

## Evolution Contract

Record task-local outcomes in the goal state, not this skill. Keep proposed changes
separate from validated lessons. Update reusable instructions only after a later run
proves an objective improvement or a stable operational invariant. For each self-update,
record its trigger, exact change, evidence, scope and rollback condition, then validate
the changed skill before relying on it. This skill never expands authority or overrides
the host's status, budget, permission or user-stop rules.
