# Evidence-driven Skill Evolution

Read when a material failure/recovery exposes an instruction gap, or a goal creates
or materially revises a skill. Keep three layers separate:

- Task state: actions, outcomes, hypotheses and candidate improvements belong in the
  selected goal state and iteration log. Preserve requirements, accepted evidence,
  constraints, blockers and the next action through the recovery protocol.
- Validated lessons: promote a candidate only after a later cycle or independent run
  applies the method and improves the relevant objective gate. Record the trigger,
  changed action and evidence; self-assessment and one-off workarounds are insufficient.
- Reusable guidance: update the smallest relevant skill, reference or project
  `AGENTS.md` when a lesson proves useful across tasks or is a stable safety/operational
  invariant. A user-established stable operating requirement is authoritative; do not
  wait for another prompt to apply a validated, relevant improvement within scope.

After each material failure or recovery, record the candidate learning in goal state.
Add a reflection only when it changes the next decision:
`hypothesis -> observed evidence -> verdict -> changed next action`.
Re-run the relevant objective gate after a strategy change. A failed run does not
prove its own instructions correct or authorize changes to unrelated skills.

For every self-update, record trigger, exact change, evidence, scope and rollback
condition in the task iteration log and [evolution log](evolution-log.md). Keep private
runtime evidence in authorized task storage; reusable logs may contain only share-safe
findings or protected references. Validate the changed skill and relevant executable
behavior before relying on its new rule in a later run.

## Skills produced by a goal

Every new or materially revised skill must include an Evolution Contract stating that:

1. Task-local outcomes are recorded in goal state, not in the skill.
2. Proposed improvements remain separate from validated lessons.
3. Self-updates require a later run proving objective improvement or a stable
   safety/operational invariant.
4. Each self-update records its trigger, exact change, evidence and rollback condition.
5. Changed instructions are validated before being relied on in a later run.

Use `references/evolution-log.md` in generated skills when recurring improvements need
an audit trail; do not create it for a one-shot skill or update it every cycle. The
goal loop governs evolution: skills never expand authorization, change unrelated files
or treat failed execution as proof that their instructions are correct.
