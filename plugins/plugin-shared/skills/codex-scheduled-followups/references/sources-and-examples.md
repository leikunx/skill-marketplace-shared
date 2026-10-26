# Native continuation sources and examples

Verified against official documentation on **2026-10-26**. These sources establish
product capabilities, not a particular session's access or an executed automatic round.

## Native Goal automatic continuation

- [Configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference):
  `features.goals` enables "persisted goals and automatic continuation" and is stable/on by default.
- [Long-running work](https://learn.chatgpt.com/docs/long-running-work): `/goal` starts
  Goal mode in the app, CLI and IDE; steer related work in the same chat/session.

For explicitly requested goal pursuit, use the current thread's available goal tools
or supported `/goal` control. Read the existing goal before creating one; preserve an
unfinished goal. Record the thread, objective, active state, constraints and acceptance
gate. Keep the host continuation/interval scanner at its default. No fixed scan interval
is established by these documents, so do not invent one or promise an exact next-run time.

`codex features list` can inspect installed feature availability without starting an
agent turn. An enabled feature and active goal are configuration evidence. Record an
actual host-triggered continuation before claiming automatic execution was verified.
Do not send a synthetic queued prompt and call it scanner evidence.

## Native scheduled tasks in this chat

[Scheduled tasks](https://learn.chatgpt.com/docs/automations?surface=app), section
**Schedule a task inside a chat**:

> Scheduled tasks in a chat can use minute-based intervals for active follow-up loops

This mode returns to the same chat and its context. Use it when the user needs a fixed
cadence and this installation exposes supported controls. Verify their real schema,
thread target, deadline/stop condition and an actual run. Local project work requires
the machine, app and workspace to remain available. A feature flag alone does not
establish access to the schedule-management interface or connected tools.

Continuation excludes standalone chats, secondary agents, extra terminals, external CLI
schedulers and polling/queue wrappers. Preserve separately authorized validation rules.
If native continuation or same-chat scheduling is unavailable,
report that boundary and continue only the authorized work possible in the current
thread. Do not install a fallback or edit runtime databases.

## Example: continue a PR review in the current thread

```text
Continue this PR task in the same Codex chat using native Goal automatic continuation
at the host's default interval. Do not launch another Codex agent/session, terminal,
standalone task, or external scheduler for continuation. Preserve our branch, tools,
permissions and separately authorized validation rules.

On each automatic round, read the durable state and full requirements ledger, then
inspect the current PR, build and authorized feedback sources. Handle actionable
feedback within scope, verify actual effects, and save the next step. Report only
material changes; preserve message IDs and commit IDs to avoid duplicate actions.

Keep the goal active while authorized work remains and the host permits continuation.
When only an external prerequisite remains, record waiting and follow the host's
repeated-blocker rule. Do not keep resetting the goal or fabricate progress to poll.
Complete the goal when its agreed acceptance gate passes. Respect any user stop,
configured window or budget, and do not create a schedule merely by reading this example.
```

For an explicitly requested fixed cadence, substitute a supported native schedule
attached to this same chat, and record its actual cadence, deadline and stop condition.
Track goal status, schedule status when applicable, last observed automatic round,
last inspected revisions/messages, and verified external effects separately.
