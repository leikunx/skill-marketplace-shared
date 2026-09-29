# Sources and examples

Last verified: **2026-09-18**. These sources establish documented capabilities and published patterns. They do not prove that a particular user's installation exposes scheduling tools or that a browser integration works unattended.

## Official scheduled tasks documentation

https://learn.chatgpt.com/docs/automations?surface=app

This was the fetched destination of the official Codex automations search result. Relevant section: **Schedule a task inside a chat**.

> Scheduled tasks in a chat can use minute-based intervals for active follow-up loops

The page explains that an existing-chat schedule returns to the same chat with its context. Its examples include checking a long-running operation until it finishes and continuing a PR review loop. Standalone schedules start separate chats. Local project tasks require the computer and desktop app to stay running; Git execution can use a local project or a worktree.

Use this page for current setup/UI guidance. Its support for scheduling does not prove any particular MCP connection, browser profile, messaging permission, account entitlement, or installed tool schema.

## Official non-interactive CLI documentation

https://learn.chatgpt.com/docs/non-interactive-mode

Relevant sections: **When to use codex exec**, **Make output machine-readable**, **Authenticate in automation**, and **Resume a non-interactive session**.

Verified command shapes:

```text
codex exec "Perform one bounded status check and record the result"
codex exec --json "Perform one bounded status check"
codex exec resume <SESSION_ID> "Recheck the target and continue from verified state"
```

These are invocation examples, not schedules. An external scheduler must trigger them. Choose permissions and authentication for the requested workflow using current CLI documentation; do not copy broad-access flags from a community example without a task-specific reason.

For Windows, Task Scheduler can launch a wrapper containing the chosen command, timeout, non-overlap handling, and log capture. Verify browser access under the actual scheduled account/session before relying on this approach for Playwright Extension.

## Community patterns inspected

These repositories were read, not installed or independently tested. Their instructions are examples, not authoritative Codex schemas or permission grants.

- [thinkingjimmy/codex-reset-watchdog](https://github.com/thinkingjimmy/codex-reset-watchdog): a skill plus hourly project automation with a one-shot checker, baseline state, duplicate suppression, dry-run, and Run Now verification. Its exact automation tool fields are implementation/version dependent.
- [jimprosser scheduling guide](https://github.com/jimprosser/claude-code-to-codex/blob/main/sections/04-automation.md): describes `codex exec` with cron, launchd, or Windows Task Scheduler and separate state/log files. Some app/model statements predate the current official documentation; use the scheduler pattern and verify current details.
- [PR Review Reminder template](https://github.com/onurkanbakirci/awesome-codex-automations/blob/main/automations/pr-review-reminder/README.md): identifies ready PRs awaiting review for over 48 hours. This is a report-oriented prompt, not a complete Azure DevOps/Teams/Outlook integration.

## Example: bounded PR follow-up

Adapt the cadence and end time to the user's request; these example values are not defaults or existing authorization.

```text
Every 10 minutes until the agreed end time, perform one bounded follow-up for
the specified PR using the existing chat context and shared state file.

Inspect the live PR status, required reviewer votes, builds, review comments,
and the explicitly authorized reviewer conversations using the chosen tools.
Handle actionable feedback within the established scope. If only human review
or a running build remains, record waiting and let the next scheduled job check.
Do not send duplicate reminders, bypass policies, or overlap another active run.

Only after verifying that the PR is completed, send the authorized reply in the
original requester's conversation, verify it was sent, and disable this schedule.
At the end time, stop and report any remaining gates.
```

The task state should distinguish: schedule enabled, next run due, last actual run, target state, last verified message, current lease, and completion notification sent. This makes both missed runs and duplicate actions detectable without claiming that a prompt alone provides persistent monitoring.
