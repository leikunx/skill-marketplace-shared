---
name: codex-scheduled-followups
description: "Use native Goal continuation and supported same-chat scheduled follow-ups for PR/status/reply checks. Default to the host's continuation scanner; never use another agent, standalone chat, extra terminal, or external scheduler for continuation. Reading this guidance alone enables nothing."
---

# Codex Scheduled Follow-ups

Keep work in the current Codex agent and chat. Default to native Goal automatic continuation
(the host's built-in interval scanner) with its existing defaults. When a fixed cadence is
needed, use only supported native scheduling attached to this same chat. Never launch another
agent/session, a standalone scheduled chat, an extra terminal, or an external CLI scheduler
for continuation. Missing native controls are a limitation to report, not permission to
use that fallback. Preserve separately authorized validation rules.

## Required companion skill

Load and follow `$goal-loop-runner` with this skill. This skill supplies scheduling-specific knowledge; `$goal-loop-runner` owns the iterative execution contract, durable state, evidence gates, and stop behavior. If `$goal-loop-runner` is unavailable, report the missing dependency and do not claim that a recurring follow-up has been configured.

## Verified knowledge

Verified against official documentation on **2026-10-26**. Read [sources and examples](references/sources-and-examples.md) for citations, the relevant passages, and a reusable monitoring prompt. Refresh the official sources when availability, UI, schema, or product-version details matter; do not treat this snapshot as a permanent capability guarantee.

- **Scheduled task in an existing chat:** returns to that chat on a schedule and uses its existing context. Minute-based intervals are documented for monitoring a long-running operation, checking a connected source, and continuing a review loop.
- **Native Goal continuation:** `features.goals` enables persisted goals and automatic continuation, and is on by default. Verify the effective feature and current goal state. Its native scan interval is not a user-specified schedule; do not invent a fixed duration or next-run time.
- **Local project execution:** keep the computer powered on, the desktop app running, and the selected project present. Git projects can use the local checkout or an isolated worktree; do not assume every scheduled run creates a worktree.
- **Goal, skill, and schedule are different:** native goals can continue automatically; a skill supplies instructions; a native schedule supplies a configured time trigger. A saved file or a promise is not execution evidence. Azure DevOps auto-complete does not wake Codex.

## Choose the mechanism from the actual environment

For ongoing project progress, inspect the current goal and use its native automatic continuation.
Create a goal only when the user requests goal pursuit, and preserve the current thread, model,
permissions and workspace. If the user requests a fixed cadence, discover a supported native
schedule attached to this chat. Neither mode authorizes another Codex agent or terminal.

Inspect the current tools and supported app controls before creating a schedule. No exposed
scheduling tool means that control is unavailable here, not that Codex lacks the feature.
Report that boundary and continue authorized current-thread work. Never compensate with
`codex exec`, `codex exec resume`, Task Scheduler, cron, launchd, a polling/queue wrapper,
or a forked/standalone agent. Do not queue self-prompts to simulate the native scanner.

Use official documentation or available schemas for exact controls. Do not edit runtime
databases or install community monitors. A feature flag and active goal prove configuration;
verify an observed automatic round before claiming execution. Keep fixed-cadence scheduling
separate from native Goal continuation.

## Preserve the current environment

Reuse the current provider, model, account and tool connections. Do not start a separate
agent to test authentication. A custom provider may work without OpenAI sign-in; inspect
actual tool failures rather than treating `codex login status` as a universal prerequisite.
Native continuation does not establish access to an external service: verify the relevant
service/account through the current tools and keep credential material out of task records.

## When the user requests unattended setup

Authorization and scope come from the user, not this knowledge skill. A request to explain or save the knowledge is not a request to create a task. A request to set up monitoring already authorizes ordinary reversible preparation; do not add another permission step for routine implementation choices.

Make the recurrence concrete: target PR or service, sources to inspect, allowed actions, cadence, timezone, stop condition or pursuit window, and notification destination. Reuse settled preferences. Ask only for a material missing choice. For a stated away/asleep window, apply the `$goal-loop-runner` unattended protocol.

Before claiming automatic follow-up is working:

1. Inspect the live target and run the proposed check once with the intended account and tools.
2. Preserve the native Goal, or create/update one supported same-chat schedule after checking for duplicates. Record thread/goal status or the actual schedule identifier, configured cadence/next run when exposed, environment, state path and stop rule.
3. Verify an actual automatic round in this thread, or a native scheduled run through Run Now/its first execution. A manual check or a saved definition alone does not prove unattended execution works. Do not queue a synthetic turn and label it scanner evidence.
4. Verify the real effects and saved evidence. Record a failed connection or authentication attempt as an operational failure, never as "no new replies" or "nothing changed."

For repeated external actions, retain the last inspected revision/message, sent-message identifiers, and timestamps. Prevent overlapping jobs against the same mutable target with a lease and bounded runtime. Only notify again for new information or an appropriate reminder interval. A pending human review normally ends the current job as waiting; a separately authorized schedule can inspect it again until its stop condition. Preserve the host's goal-blocking rules rather than treating repeated polling as completed progress.

For local browser workflows, verify the scheduler-launched run can connect to the intended Playwright Extension instance and authenticated profile. Keep the required browser session available. Native cloud scheduling or a CLI login does not establish access to a local Teams/Outlook browser session. Follow the user's browser-tool choice and verify recipients before sending messages.

On success, verify the final state, perform any already-authorized notification once, and
complete the goal or disable the native schedule as appropriate. Respect the host's stop,
budget and repeated-blocker rules; never keep a blocked goal artificially active to poll.
Report unverified automatic execution separately from verified configuration.

## Evolution Contract

- Keep task-local observations, schedule IDs, and outcomes in that task's state, not this skill.
- Separate proposed improvements from validated lessons.
- Revise reusable guidance only after a later run demonstrates improvement or an established operational invariant supports it.
- Record the trigger, exact change, evidence, scope, and rollback condition for each self-update in the task's evolution record.
- Validate the changed skill before relying on the revised guidance in a later run. This skill never expands authorization.
