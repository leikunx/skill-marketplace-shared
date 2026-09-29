# Shared Codex Skills Marketplace

The canonical Git marketplace for reusable Codex skills that contain no company-internal source, tenant details, service URLs, credentials, or customer information.

## Companion repository

The team-only companion is [`leikunx/skills-private`](https://github.com/leikunx/skills-private). The installable plugin is `skills-shared`, declared in `.agents/plugins/marketplace.json`; its `.codex-plugin/` manifest and `skills/` directory are at this repository's root.

## Placement rule

Put a skill here only when its instructions, examples, references, and scripts are safe to share publicly. Put it in the private companion repository when it mentions internal projects, systems, URLs, architecture, tenant behavior, or team-only operating procedures. When uncertain, use `private` first and make a reviewed public extraction later.

Create and update skills through `$skills-private:skill-creator`. Except for user-established project skill locations (including validation skills in `m365-validator/.agents/skills/`), new sources belong in the two repositories' `skills/` directories, not standalone user/project locations or plugin caches. Knowledge/reference skills must be named `knowledge-<topic>`; the creator's `--kind knowledge` option supplies that prefix. Workstation activation and the portable creator tooling are maintained in the private companion.

## Engineering review

- `$skills-shared:architecture-health-review` produces architecture and production-readiness findings backed by executable receipts, counter-searches, and explicit blast-radius gates. It is read-only unless implementation is separately requested.

## Browser validation

`validation-web-loop` has moved, with its generator, tests, metadata and references, to [`leikunx/m365-validator/.agents/skills`](https://github.com/leikunx/m365-validator/tree/main/.agents/skills/validation-web-loop). The destination is private and requires access. Open that checkout and invoke `$validation-web-loop` without the former plugin qualifier. Refresh this plugin and start a new session after updating. Its scenario revision, browser ownership, evidence, and authorization rules are unchanged.

## Use on a workstation

Register both Git marketplaces once:

```powershell
codex plugin marketplace add leikunx/skills-shared --ref main
codex plugin marketplace add leikunx/skills-private --ref main
codex plugin add skills-shared@skills-shared
codex plugin add skills-private@skills-private
```

For later updates, run `codex-m365`. Before it refreshes and reinstalls the plugins, it safely commits and pushes non-ignored changes in this repository and its private companion. It blocks likely secret files, merge divergence, missing upstream branches, or failed Git operations rather than overwriting or force-pushing.

New-machine installation and migration are owned by `$skills-private:knowledge-codex-m365-setup`; its [guide and scripts](https://github.com/leikunx/skills-private/tree/main/skills/knowledge-codex-m365-setup) live together in the private repository.
