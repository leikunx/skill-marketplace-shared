# Multica source map

Checked **2026-11-17** using browser-rendered official pages and a shallow Git
checkout. Search results were discovery aids. Source revision:
`670082cffe0b6c25ea36d62fb31939adbd2d5e93`.

| ID | Primary source | Supports |
| --- | --- | --- |
| M1 | [Repository README](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/README.md) | Product identity, clients/backend/database/daemon architecture. |
| M2 | [How Multica works](https://multica.ai/docs/how-multica-works), [pinned source](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/how-multica-works.mdx) | Trigger-to-result path, execution/data boundary, run vs issue completion. |
| M3 | [Daemon and runtimes](https://multica.ai/docs/daemon-runtimes), [pinned source](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/daemon-runtimes.mdx) | Registration, notifications/polling, heartbeats, concurrency, recovery, remote Qoder exception. |
| M4 | [Runs](https://multica.ai/docs/tasks), [pinned source](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/tasks.mdx) | States, queue/offline behavior, retry defaults and continuity, stop, completion boundary. |
| M5 | [Squads](https://multica.ai/docs/squads), [pinned documentation](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/squads.mdx), [built-in squad reference](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/service/builtin_skills/multica-platform/references/squads.md) | Leader routing, exact mentions, no automatic member fan-out, wakeups, status authority and project workflows. |
| M6 | [Built-in sub-issue reference](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/service/builtin_skills/multica-platform/references/sub-issues.md) | Staged barriers, backlog/todo admission, parent wakeups, agent-driven promotion, terminal categories. |
| M7 | [Autopilots](https://multica.ai/docs/autopilots), [pinned source](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/autopilots.mdx) | Schedule/webhook triggers, create-issue vs run-only modes, issue wakeup distinction. |
| M8 | [Daemon execution](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/daemon/daemon.go), [durable terminal-report queue](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/daemon/terminal_report_queue.go) | Batch claim loop, complete/fail reporting, persistent callback outbox, replay, cancellation checks. |
| M9 | [Task service](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/internal/service/task.go), [queue SQL](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/server/pkg/db/queries/agent.sql) | Claim/transition arbitration, transactional completion, idempotent terminal callbacks, retry eligibility. |
| M10 | [Project resources](https://multica.ai/docs/project-resources), [pinned source](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/project-resources.mdx) | Repository worktrees, local in-place serialization, explicit worktree capability and failure behavior. |
| M11 | [Security model](https://multica.ai/docs/security-model), [pinned source](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/security-model.mdx) | Daemon-user permission boundary; worktrees and per-run state do not provide a general sandbox. |
| M12 | [Skills](https://multica.ai/docs/skills), [pinned source](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/apps/docs/content/docs/skills.mdx) | Reusable guidance, assignments, imports and refresh semantics. |
| M13 | [CLI and daemon guide](https://github.com/multica-ai/multica/blob/670082cffe0b6c25ea36d62fb31939adbd2d5e93/CLI_AND_DAEMON.md) | CLI diagnostics and profile-specific daemon state/log paths. |

Implementation observations above describe this commit, not a promise about
every hosted deployment. Product pages and `main` can advance independently.
For operational advice, check the deployed version, runtime type, project
workflow, and current command help. Do not copy volatile provider counts,
concurrency caps, or timeout values into universal requirements.
