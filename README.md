# Shared Codex Skills Marketplace

Reusable Codex skills whose instructions, examples, references, and scripts are safe to share publicly. Private or team-specific workflows belong in the [private companion marketplace](https://github.com/leikunx/skill-marketplace-private).

## Repository layout

The marketplace catalog is `.agents/plugins/marketplace.json`. It offers `plugin-shared` and `plugin-agent-orchestration`, matching the private marketplace's plugin layout:

```text
.agents/plugins/marketplace.json
plugins/plugin-shared/
  .codex-plugin/plugin.json
  skills/
    goal-loop-runner/
    codex-scheduled-followups/
plugins/plugin-agent-orchestration/
  .codex-plugin/plugin.json
  skills/
    knowledge-orca-orchestration/
    knowledge-multica-orchestration/
```

## Skills

- [goal-loop-runner](plugins/plugin-shared/skills/goal-loop-runner/SKILL.md): pursue goals through verified iterations with durable state and explicit stopping conditions.
- [codex-scheduled-followups](plugins/plugin-shared/skills/codex-scheduled-followups/SKILL.md): explain and verify bounded recurring follow-ups and scheduling alternatives.
- [talk-first](plugins/plugin-shared/skills/talk-first/SKILL.md): discuss the solution and its details until the user explicitly asks to begin implementation. Invoke as `$plugin-shared:talk-first`; implicit invocation is disabled.

Invoke them as `$plugin-shared:goal-loop-runner` and `$plugin-shared:codex-scheduled-followups`. These runners and scheduled-followup guidance require explicit invocation. Loading a skill does not activate a schedule.

## Agent orchestration knowledge

`plugin-agent-orchestration` contains two explicit-only knowledge skills, researched from official documentation and public source code on 2026-11-17:

- [knowledge-orca-orchestration](plugins/plugin-agent-orchestration/skills/knowledge-orca-orchestration/SKILL.md): Orca's Run/Task/Dispatch model, supervised workers, mailbox wakes, completion settlement, placement, and recovery. Invoke as `$plugin-agent-orchestration:knowledge-orca-orchestration`.
- [knowledge-multica-orchestration](plugins/plugin-agent-orchestration/skills/knowledge-multica-orchestration/SKILL.md): Multica's issues, execution runs, daemons, squads, staged delegation, review, and retries. Invoke as `$plugin-agent-orchestration:knowledge-multica-orchestration`.

Each skill links to detailed lifecycle guidance and primary sources pinned to the inspected revisions. Loading them does not launch agents or schedules.

Both skills and all their references are available in English and Simplified Chinese. English uses `SKILL.md`, `lifecycle.md`, and `sources.md`; Chinese uses the matching `.zh-CN.md` files. Language links connect each pair, and both languages use the same skill invocation.

| Skill | English | 简体中文 |
| --- | --- | --- |
| Orca orchestration | [English](plugins/plugin-agent-orchestration/skills/knowledge-orca-orchestration/SKILL.md) | [简体中文](plugins/plugin-agent-orchestration/skills/knowledge-orca-orchestration/SKILL.zh-CN.md) |
| Multica orchestration | [English](plugins/plugin-agent-orchestration/skills/knowledge-multica-orchestration/SKILL.md) | [简体中文](plugins/plugin-agent-orchestration/skills/knowledge-multica-orchestration/SKILL.zh-CN.md) |

## Install and update

Register the Git marketplace and install its plugin:

```powershell
codex plugin marketplace add leikunx/skill-marketplace-shared --ref main
codex plugin add plugin-shared@skill-marketplace-shared
codex plugin add plugin-agent-orchestration@skill-marketplace-shared
```

For later updates:

```powershell
codex plugin marketplace upgrade skill-marketplace-shared
codex plugin add plugin-shared@skill-marketplace-shared
codex plugin add plugin-agent-orchestration@skill-marketplace-shared
```

Start a new thread after installation or updates. The former `skills-shared@skill-marketplace-shared` plugin is replaced by `plugin-shared@skill-marketplace-shared`.

## Maintain

Keep each skill and all bundled resources under its owning `plugins/<plugin-name>/skills/<name>/` directory. Use `$plugin-private:skill-creator` for maintenance and follow [AGENTS.md](AGENTS.md) for validation and publication. Preserve existing skill names and invocation policies. Do not commit credentials, private source material, browser profiles, or task runtime data.
