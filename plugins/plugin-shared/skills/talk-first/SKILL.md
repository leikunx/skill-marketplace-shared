---
name: talk-first
description: Discuss a proposed solution and its implementation details before making changes. Use when explicitly invoked to stay in discussion mode until the user explicitly asks to start implementation.
---

# Talk First

When invoked, enter a discussion-only phase for the current solution. Keep this
phase active across follow-up messages until the user explicitly asks to begin
implementation. Earlier permission to implement does not override this newly
requested discussion phase.

## Discuss the solution

Explain the proposed approach, expected behavior, relevant alternatives and
tradeoffs. Cover practical implementation details appropriate to the task: affected
files or services, data flow, compatibility, dependencies, validation, deployment
and rollback when relevant. State assumptions and resolve material uncertainties
through focused questions. Adapt the depth to the user's questions rather than
forcing a fixed template.

Read-only inspection of relevant files, documentation or current system state is
allowed when it helps answer accurately. Explain findings and recommendations;
keep sample code or commands in the conversation as illustrations.

Do not edit files, create implementation artifacts or prototypes, install
dependencies, run builds or other commands that change state, commit, push,
deploy, or modify external systems during this phase. A proposed plan or displayed
command is not permission to execute it.

## Wait for an explicit start

Begin implementation only after a later user instruction clearly requests it,
such as "start implementing", "implement this solution", or "go ahead and make
the changes". Treat agreement, selecting an option, "looks good", requests for
more detail, and an ambiguous "continue" as continued discussion.

If the instruction is ambiguous about starting implementation, keep discussing
and ask one brief clarification. Do not repeatedly ask for permission while the
user is still exploring the solution.

Once the user explicitly starts implementation, end the discussion-only phase
and carry out the agreed scope under the existing permissions and constraints.
Do not ask for the same start confirmation again. A later explicit request to
return to discussion reinstates this phase.
