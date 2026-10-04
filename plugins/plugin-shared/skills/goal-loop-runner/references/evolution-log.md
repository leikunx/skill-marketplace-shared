# Evolution Log

## 2026-10-04: Preserve and audit every user requirement

- Trigger: the user established a durable requirement to capture all task-relevant user
  requirements and amendments, recover them after compaction, and audit them at completion.
- Change: add a separate requirements ledger/template, source and amendment tracking,
  recovery rules, and per-requirement evidence gates; connect them to state, iteration,
  compaction, final status, and unattended handoff. Keep inspection/authoring separate
  from starting execution, and keep secret values out of requirement records.
- Evidence: the prior skill retained corrections and amendments in compact state but
  did not require a complete requirement register or a completion audit of every item.
  This update implements an explicit user-established operating requirement; it does
  not claim long-running behavioral validation or start a goal loop.
- Validation: the private creator's skill validator passes; all five local Markdown
  links resolve; plugin/catalog JSON and UI YAML parse; explicit-only invocation is
  preserved; Git whitespace checks pass. No execution loop was used for validation.
- Scope: this skill and its templates/handoff reference; plugin version advances to
  distribute the revised instructions while preserving explicit-only invocation.
- Rollback: revert this change if ledger reconciliation cannot preserve authoritative
  intent or prevents permitted independent work; keep existing task ledgers intact.
