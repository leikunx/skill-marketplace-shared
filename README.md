# Shared Codex Skills Marketplace

Reusable Codex skills whose instructions, examples, references, and scripts are safe to share publicly. Private or team-specific workflows belong in the [private companion marketplace](https://github.com/leikunx/skill-marketplace-private).

## Repository layout

The marketplace catalog is `.agents/plugins/marketplace.json`. It installs `plugin-shared` from `plugins/plugin-shared/`, matching the private marketplace's plugin layout:

```text
.agents/plugins/marketplace.json
plugins/plugin-shared/
  .codex-plugin/plugin.json
  skills/
    goal-loop-runner/
    knowledge-codex-scheduled-followups/
```

## Skills

- [goal-loop-runner](plugins/plugin-shared/skills/goal-loop-runner/SKILL.md): pursue goals through verified iterations with durable state and explicit stopping conditions.
- [knowledge-codex-scheduled-followups](plugins/plugin-shared/skills/knowledge-codex-scheduled-followups/SKILL.md): explain and verify bounded recurring follow-ups and scheduling alternatives.
- [talk-first](plugins/plugin-shared/skills/talk-first/SKILL.md): discuss the solution and its details until the user explicitly asks to begin implementation. Invoke as `$plugin-shared:talk-first`; implicit invocation is disabled.

Invoke them as `$plugin-shared:goal-loop-runner` and `$plugin-shared:knowledge-codex-scheduled-followups`. The goal runner retains automatic invocation; scheduled-followup guidance requires explicit invocation. Loading a skill does not activate a schedule.

## Install and update

Register the Git marketplace and install its plugin:

```powershell
codex plugin marketplace add leikunx/skill-marketplace-shared --ref main
codex plugin add plugin-shared@skill-marketplace-shared
```

For later updates:

```powershell
codex plugin marketplace upgrade skill-marketplace-shared
codex plugin add plugin-shared@skill-marketplace-shared
```

Start a new thread after installation or updates. The former `skills-shared@skill-marketplace-shared` plugin is replaced by `plugin-shared@skill-marketplace-shared`.

## Maintain

Keep each skill and all bundled resources under `plugins/plugin-shared/skills/<name>/`. Use `$plugin-private:skill-creator` for maintenance and follow [AGENTS.md](AGENTS.md) for validation and publication. Preserve existing skill names and invocation policies. Do not commit credentials, private source material, browser profiles, or task runtime data.
