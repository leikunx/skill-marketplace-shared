---
name: knowledge-multica-orchestration
description: Explain, compare, or diagnose Multica agent orchestration through issues, execution runs, runtimes, daemons, squads, staged sub-issues, and review. Use for Multica architecture questions and planning human-and-agent workflows.
---

# Multica orchestration knowledge

This skill covers [multica.ai](https://multica.ai/) and
[multica-ai/multica](https://github.com/multica-ai/multica), the source-available
workspace for human and coding-agent teams.

Research baseline: **2026-11-17**, source revision
`670082cffe0b6c25ea36d62fb31939adbd2d5e93`. Cite the
[source map](references/sources.md) for facts. Verify version-sensitive behavior
against the deployment and its CLI help before live use.

## Use the right model

Multica records and coordinates work. For a local runtime, a daemon on a connected
computer claims queued runs and invokes an installed coding-agent tool. The
server retains context, status, transcripts, comments, and reported results.

| Object | Meaning |
| --- | --- |
| Issue | Durable goal, discussion, assignee, and work status; can span many runs. |
| Agent | Configured identity, instructions, skills, provider/model, and runtime binding. |
| Run | One execution and its trigger, state, transcript, result, and retry lineage. |
| Runtime / daemon | Execution environment available to a workspace / the process that discovers tools, claims work, and reports back. |
| Squad | Leader-based routing and coordination object; members do not start automatically. |
| Autopilot / issue wakeup | New recurring or event-triggered work / continuation of an existing issue. |

The normal path is **trigger → queue → claim → prepare → execute → report →
review or continue the issue**. Read [the lifecycle reference](references/lifecycle.md)
for the implementation, staged delegation, completion, retries, and diagnosis.

## What completion proves

A run marked `completed` means that execution ended normally. It does not
establish that the issue's goal was met. Inspect the result, artifact or PR,
verification evidence, and issue/workflow state. A leader finishing its initial
delegation turn does not finish the squad's parent issue.

For the built-in issue flow, agents hand completed work to `in_review`; a human
reviewer or configured integration can close it. Custom project workflows can
supply a different step contract. Follow the run's actual workflow context rather
than hard-coding built-in status transitions everywhere.

## Applying this knowledge

For a design discussion, identify the trigger, execution machine, working-directory
mode, delegation mechanism, and final acceptance owner. In comparisons, a Multica
**run is one execution**; an Orca **Run is a coordination namespace** containing Tasks
and Dispatches.

For diagnosis, begin with read-only evidence: issue and run records, the selected
runtime, the correct daemon profile's status/logs, transcript, and source artifact.
Distinguish queued capacity, directory-lock waiting, missing tools, runtime
disconnects, agent failure, result-delivery failure, and unaccepted work.

Use current `multica <command> --help` before operational commands. Assignments,
mentions, comments, and status changes can trigger agents; loading this knowledge
skill grants no authority to make those writes or enable an Autopilot.

## Evolution Contract

Record task-local outcomes in goal state, outside this skill. Keep proposed
improvements separate from validated lessons. Self-updates require a later run
demonstrating objective improvement or a stable safety or operational invariant.
Record the trigger, exact change, evidence, scope, and rollback condition in the
task's evolution record; validate changed instructions before relying on them in
a later run. Updates do not expand authorization.
