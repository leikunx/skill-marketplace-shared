---
name: knowledge-orca-orchestration
description: Explain, compare, or diagnose Stably Orca ADE agent orchestration using its Run, Task, Dispatch, worker, mailbox, and completion model. Use for architecture questions and planning supervised coding-agent work in Orca.
---

# Orca orchestration knowledge

**English** | [简体中文](SKILL.zh-CN.md)

For Chinese-language requests, read the Chinese version and its references.
Both versions share the same skill identity and invocation.

This skill covers **Stably's Orca ADE**, at [orca.dev](https://orca.dev/) and
[stablyai/orca](https://github.com/stablyai/orca). Check that identity when a
request says only "Orca"; other projects share the name.

Research baseline: **2026-11-17**, source revision
`bf33c20951d645619f4027da66f534725bee0bd2`. The references distinguish public
documentation from inspected implementation. They establish what was documented
and implemented at that revision; they do not prove a user's installed build behaves identically.

## Use the right model

Orca supplies the development environment and coordination runtime around existing
coding-agent CLIs. A coordinator decomposes the objective and starts workers;
Orca persists ownership, dispatches, messages, gates, and lifecycle observations.

| Object | Meaning |
| --- | --- |
| Run | Durable coordination namespace and coordinator inbox; creating it does not schedule workers. |
| Task | Work specification, dependencies, result, and status. |
| Dispatch | One attempt assigned to a worker; identifies who may settle the Task. |
| Worker | Supervised agent session with an execution location and observable lifecycle. |
| Message / gate | Communication and explicit decisions that can unblock work. |

The normal loop is **specify → start independent workers → yield → receive
messages → settle attempts → dispatch newly ready work → inspect results and report**.
Orca's current guide tells the coordinator to end its turn after starting work;
the runtime wakes it when messages or lifecycle events arrive.

Use [the lifecycle reference](references/lifecycle.md) for dispatch, dependency
handling, completion semantics, remote execution, and recovery. Use
[the source map](references/sources.md) when substantiating a claim or updating this baseline.

## What completion proves

An accepted `worker_done` with the correct Task and Dispatch IDs and an explicit
`succeeded` or `failed` outcome settles the assignment. Silence, an idle terminal,
process exit, and a generic success sentence do not establish that settlement.
The coordinator must still compare the reported artifacts and checks with the
Task's acceptance criteria. Orca tracking alone does not establish that code was
integrated, tested across workers, merged, or deployed.

When diagnosing a problem, identify which layer is unresolved: launch readiness,
worker liveness, mailbox delivery, Task/Dispatch settlement, or delivered work.
Read the exact receipt and retained output before choosing recovery.

## Applying this knowledge

For an explanation, trace one concrete task through the objects above and cite
the relevant reference. For a comparison with Multica, remember that an Orca
**Run is a coordination namespace**; a Multica **run is an execution record**.
Do not equate the two solely because they share a word.

For authorized live operation, first load Orca's version-matched `orca-cli` and
`orchestration` guides. Resolve the executable from `ORCA_CLI_COMMAND`, then
`orca-dev` for an `ORCA_DEV_REPO_ROOT` session; outside Orca-managed Linux terminals
use `orca-ide`; otherwise use `orca`. Bare `orca` on unrelated Linux systems can
invoke the screen reader. Keep the same executable for subsequent commands.

Run `<resolved executable> skills get orchestration`; read only the additional
references needed for the action. Check its current help for flags. This knowledge
skill does not start workers, change permissions, or create schedules merely by loading.

## Evolution Contract

Record task-local outcomes in goal state, outside this skill. Keep proposed
improvements separate from validated lessons. Self-updates require a later run
demonstrating objective improvement or a stable safety or operational invariant.
Record the trigger, exact change, evidence, scope, and rollback condition in the
task's evolution record; validate changed instructions before relying on them in
a later run. Updates do not expand authorization.
