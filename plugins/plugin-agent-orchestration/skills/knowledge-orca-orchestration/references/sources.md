# Orca source map

**English** | [简体中文](sources.zh-CN.md)

Checked **2026-11-17** using browser-rendered official pages and a shallow Git
checkout. Web search was used for discovery; search summaries and third-party
tutorials are not the authority for lifecycle behavior. Source revision:
`bf33c20951d645619f4027da66f534725bee0bd2`.

| ID | Primary source | Supports |
| --- | --- | --- |
| O1 | [Orchestration documentation](https://orca.dev/docs/cli/orchestration), [pinned source](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/docs/site/content/docs/cli/orchestration.mdx) | Runtime prerequisite, objects, statuses, commands, mail, gates, worker_done, retired commands. |
| O2 | [Versioned orchestration guide](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skill-guides/orchestration.md) | Normal coordinator/worker loop, yields and wakes, placement choices, follow-ups, acceptance evidence. |
| O3 | [Coordinator loop](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skill-guides/orchestration/references/coordinator-loop.md) | Dependencies, ready Tasks, multiple Runs. |
| O4 | [Placement and remote execution](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skill-guides/orchestration/references/placement-and-remote.md) | Folder/worktree distinction, Run home, connected-server placement and routing. |
| O5 | [Recovery and cleanup](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skill-guides/orchestration/references/recovery-and-cleanup.md) | Retry chain, breaker, cancellation, abandonment, release uncertainty. |
| O6 | [Database implementation](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/src/main/runtime/orchestration/db/orchestration-db.ts), [graph schema](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/src/main/runtime/orchestration/db/schema/create-graph-tables-sql.ts) | SQLite/WAL, durable Task/Dispatch/gate records and identity fields. |
| O7 | [Worker report settlement](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/src/main/runtime/orchestration/db/dispatch-context/worker-report-settlement.ts) | Transactional settlement, duplicate handling, mismatched/stale/conflicting attempts, cleanup hooks. |
| O8 | [CLI settlement verification](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/src/cli/orchestration/workers/orchestration-worker-settlement.ts) | Lifecycle verdicts, legacy read-back verification, unresolved mutation recovery. |
| O9 | [CLI discovery skill](https://github.com/stablyai/orca/blob/bf33c20951d645619f4027da66f534725bee0bd2/skills/orca-cli/SKILL.md) | Version-matched guide and executable resolution. |

For a different installed release, obtain its bundled guide and inspect the
corresponding tagged source before transferring version-sensitive commands,
retry thresholds, mailbox semantics, or remote limitations. Keep documented
behavior, source inspection, and runtime-tested observations distinct.
