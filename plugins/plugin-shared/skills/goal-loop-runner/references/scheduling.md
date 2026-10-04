# Scheduled Follow-ups

Read when later checks require recurrence or the user requests a pursuit window. For an away/asleep window, also follow [unattended handoff](unattended-handoff.md).

Consider scheduling during contract and handoff when checks must continue after the turn, such as review, build, reply, or deployment waits. Distinguish the outcome from its later-work trigger: a goal, skill, state file, or service-side auto-complete setting does not establish a Codex schedule.

If available, read `$plugin-shared:codex-scheduled-followups` for scheduling, CLI alternatives, and verification. This reference is optional; otherwise use the current [official scheduled tasks documentation](https://learn.chatgpt.com/docs/automations?surface=app) and guidance below. Discover actual schemas or supported app controls before scheduling; never invent tools, copy unverified parameters, or equate missing session tools with missing product capability.

- Prefer supported existing-chat schedules for context-dependent follow-ups; official documentation describes minute-based intervals. Use standalone schedules for independent runs. When native scheduling is unavailable or the environment requires it, an external scheduler can invoke `codex exec`; see [non-interactive mode](https://learn.chatgpt.com/docs/non-interactive-mode).
- Reuse established execution scope and scheduling authorization. Specify cadence, timezone, stop condition or pursuit window, permitted actions, and notification destination; ask only for material missing choices. Editing or explaining guidance does not create a monitor; ordinary goals do not authorize indefinite recurrence.
- Check for a matching schedule before creating one. Record its identifier, enabled state, next run, exact definition, environment, shared state and requirements-ledger paths, bounded runtime, and non-overlap lease. Verify an actual scheduler-launched run with required tools, browser profile, authentication, and resulting evidence before claiming monitoring works; a saved definition or manual check is insufficient.
- If only external review or a confirmed running job remains, mark the current job waiting and preserve a separately authorized schedule until its stop condition. Keep goal, job, and scheduler status distinct. Follow the host's repeated-blocker policy; never fabricate progress, reset its audit, or imply that blocking a goal creates or cancels a schedule.
- On verified completion, send any already-authorized notification once and disable the schedule. At its configured end or user stop, stop launching jobs and report the accepted checkpoint and remaining gates. Without a verified scheduler, state that future checks are not configured.

Use scheduling state fields only when applicable. For away/asleep windows, also follow [unattended handoff](unattended-handoff.md).
