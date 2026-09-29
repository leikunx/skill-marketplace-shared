---
name: knowledge-codex-scheduled-followups
description: "Explain Codex minute-based scheduled follow-ups, recurring monitoring, and CLI scheduler alternatives. Use for unattended PR/status/reply checks and scheduling setup questions; reading this knowledge alone does not create or enable a schedule."
---

# Codex Scheduled Follow-ups

Codex supports scheduled follow-ups inside an existing chat. Current official documentation explicitly describes minute-based intervals for active follow-up loops. Do not tell the user that Codex cannot check again after a turn ends: determine whether a real schedule exists and whether the required execution environment is available.

## Verified knowledge

Verified against official documentation on **2026-09-18**. Read [sources and examples](references/sources-and-examples.md) for citations, the relevant passages, and a reusable monitoring prompt. Refresh the official sources when availability, UI, schema, or product-version details matter; do not treat this snapshot as a permanent capability guarantee.

- **Scheduled task in an existing chat:** returns to that chat on a schedule and uses its existing context. Minute-based intervals are documented for monitoring a long-running operation, checking a connected source, and continuing a review loop.
- **Standalone scheduled task:** starts a new chat for each run. Suitable for independent recurring work; store shared state at a stable, explicitly accessible path when runs must coordinate.
- **Local project execution:** keep the computer powered on, the desktop app running, and the selected project present. Git projects can use the local checkout or an isolated worktree; do not assume every scheduled run creates a worktree.
- **CLI alternative:** an external scheduler can invoke `codex exec` for a bounded check. The CLI supports JSONL output and resuming a specific session with `codex exec resume <SESSION_ID>`. It reuses saved CLI authentication by default; that does not establish authentication to external services.
- **Goal, skill, and schedule are different:** a goal preserves the objective, a skill supplies instructions, and a scheduler triggers future execution. An active goal, a saved state file, or a promise to monitor is not evidence that a schedule is installed. Azure DevOps auto-complete can merge independently, but does not wake Codex to inspect replies or send a completion message.

## Choose the mechanism from the actual environment

For a conversation-specific follow-up, prefer a supported schedule attached to the existing chat when available. For independent checks, use a standalone task. Use Windows Task Scheduler, cron, or launchd with `codex exec` when the task requires that operational model or native scheduling is unavailable.

Inspect the current tool catalog and supported app controls before creating a schedule. Do not invent a scheduling tool or assume a community example's tool name or parameter schema is supported here. No scheduling tool in the current turn means that tool is unavailable to this session; it does not prove the app lacks scheduling. Explain the verified boundary and inspect a supported UI or external scheduler when setup is requested.

Use current official documentation or available tool schemas for exact creation/update commands. Do not edit undocumented automation databases or install a community monitor merely because its pattern looks useful. Prefer a specific CLI session ID over `--last` when other conversations may run concurrently.

## When the user requests unattended setup

Authorization and scope come from the user, not this knowledge skill. A request to explain or save the knowledge is not a request to create a task. A request to set up monitoring already authorizes ordinary reversible preparation; do not add another permission step for routine implementation choices.

Make the recurrence concrete: target PR or service, sources to inspect, allowed actions, cadence, timezone, stop condition or pursuit window, and notification destination. Reuse settled preferences. Ask only for a material missing choice. For a stated away/asleep window, apply the goal-loop-runner unattended protocol if available.

Before claiming the monitor is active:

1. Inspect the live target and run the proposed check once with the intended account and tools.
2. Create or update one schedule, checking for an existing matching task to avoid duplicates. Record its identifier, enabled state, cadence, next run, execution environment, state path, and stop rule.
3. Verify a run launched by the scheduler, using Run Now or the first scheduled execution. A manual chat check or a saved task definition alone does not prove unattended execution works.
4. Verify the real effects and saved evidence. Record a failed connection or authentication attempt as an operational failure, never as "no new replies" or "nothing changed."

For repeated external actions, retain the last inspected revision/message, sent-message identifiers, and timestamps. Prevent overlapping jobs against the same mutable target with a lease and bounded runtime. Only notify again for new information or an appropriate reminder interval. A pending human review normally ends the current job as waiting; a separately authorized schedule can inspect it again until its stop condition. Preserve the host's goal-blocking rules rather than treating repeated polling as completed progress.

For local browser workflows, verify the scheduler-launched run can connect to the intended Playwright Extension instance and authenticated profile. Keep the required browser session available. Native cloud scheduling or a CLI login does not establish access to a local Teams/Outlook browser session. Follow the user's browser-tool choice and verify recipients before sending messages.

On success, verify the final state, perform any already-authorized completion notification once, and disable the schedule. At the configured end, stop launching runs and report unfinished gates. Do not claim continued monitoring without a verified active scheduler and a working environment.

## Evolution Contract

- Keep task-local observations, schedule IDs, and outcomes in that task's state, not this skill.
- Separate proposed improvements from validated lessons.
- Revise reusable guidance only after a later run demonstrates improvement or an established operational invariant supports it.
- Record the trigger, exact change, evidence, scope, and rollback condition for each self-update in the task's evolution record.
- Validate the changed skill before relying on the revised guidance in a later run. This skill never expands authorization.
