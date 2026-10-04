# Evolution Log

## 2026-10-05: Reduce entrypoint context through conditional references

- Trigger: the user requested optimization after discussing a roughly 9 KB entrypoint.
- Change: consolidate repeated contract, requirement, recovery, iteration and completion
  rules in `SKILL.md`; move fuzzy-input review, browser/account selection, scheduling,
  process recovery and skill-evolution procedures into linked conditional references.
  Connect unattended handoff directly to scheduling and retain its execution safeguards.
- Evidence: the entrypoint decreases from 30,068 to 8,719 UTF-8 bytes (71.0%); even with
  CRLF line endings it stays below 9,000 bytes. Including the unchanged recovery and
  creation templates, the core setup reading decreases from 48,352 to 27,003 bytes.
  These are file-size measurements, not model-token counts, speed or quality benchmarks.
- Validation: creator validation, 16 local Markdown links, plugin/catalog JSON,
  unchanged UI YAML and explicit-only policy, and Git whitespace checks pass. Browser,
  managed-process and fuzzy-review procedures retain their original text. Existing state,
  requirements and recovery resources are byte-identical. Dedicated instruction review
  covers amendments, uncertain writes, evidence reuse, incomplete acceptance, identity
  selection, scheduling authorization, unavailable users and provisional learning.
- Scope: this skill's instructions/references and plugin version 0.1.22. No native Goal,
  execution loop, model benchmark or scheduler is created by this editing task.
- Rollback: revert the routing/consolidation if a later run misses a required procedure,
  loses user requirements or weakens an objective gate; preserve task records and accepted
  evidence, restore the affected rule, and revalidate before relying on it.

## 2026-10-04: Restore execution state efficiently after compaction

- Trigger: the user requested stronger post-compaction performance by preserving the
  execution context needed to continue all original goals efficiently.
- Change: add a recovery protocol and structured state fields for effective decisions,
  workspace/artifact revisions, evidence scope/freshness, failed-method retry conditions,
  next-action dependencies, unresolved external operations, and live runtime ownership.
  Save at meaningful events, persist external intent before dispatch, restore complete
  user requirements, and retrieve detailed records only as the next action needs them.
- Evidence: the previous state template retained checkpoint and iteration summaries,
  but lacked structured workspace/decision/evidence/operation records and a sequenced
  drift-reconciliation procedure. This implements a user-established operating rule;
  it makes no measured performance claim or claim of a long-running execution test.
- Validation: the creator validator, seven local Markdown links, plugin/catalog JSON,
  UI YAML, and Git whitespace checks pass. Instruction review covers unchanged-evidence
  reuse, requirement/dependency changes, interrupted writes, workspace drift, and
  missing/inconsistent records. No Goal, execution loop, or scheduler was started.
- Scope: this skill, state template, recovery/handoff references, UI metadata, and
  plugin version 0.1.21. Explicit-only invocation and inspection-only boundaries remain.
- Rollback: revert the affected guidance if recovery loses requirement coverage or
  misclassifies changed artifacts/uncertain effects; preserve task records and accepted
  evidence, then revalidate affected requirements before continuing.

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
