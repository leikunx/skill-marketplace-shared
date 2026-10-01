# Repository Workflow

After changing this repository, validate the affected skill, review the exact diff, commit only the intended files, and push the resulting commit to its configured upstream before handoff. If the push cannot complete safely, report the exact blocker; do not claim the change is published.

## Plugin and skill layout

The marketplace catalog is `.agents/plugins/marketplace.json`. Plugin sources live under `plugins/<plugin-name>/`, with `.codex-plugin/plugin.json` and `skills/<skill-name>/` inside each plugin. Maintain this marketplace's skills under `plugins/plugin-shared/skills/`; its installable ID is `plugin-shared@skill-marketplace-shared`.

Use `$plugin-private:skill-creator` for skill creation and updates. Preserve existing skill names, bundled resources, and invocation policies. Knowledge/reference skills use `knowledge-<topic>` for their directory and frontmatter name; retain the established `goal-loop-runner` and user-requested `codex-scheduled-followups` names.

## Sharing and validation

Only publish instructions, examples, references, scripts, and assets that are safe to share publicly. Private work belongs in its owning private plugin or user-established project location. Do not author in installed caches or standalone user-skill directories, and do not commit credentials, browser profiles, private source material, or task runtime data.

Validate affected skills with the private creator's `quick_validate.py`, check local links and plugin metadata, and run relevant existing helper tests when code changes. Preserve unrelated local work and publish only scoped verified changes.
