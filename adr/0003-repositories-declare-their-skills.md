# ADR-0003: A repository declares the plugins it needs

Status: **Accepted**

## Context

Skills copied into a repository's `.claude/skills/` arrive with every clone
but drift from each other. Skills installed only on one machine travel nowhere:
a web session, a second machine and a collaborator do not have them.

## Decision

Each repository commits a `.claude/settings.json` that names the d-lab-5
marketplace (`extraKnownMarketplaces`) and the plugins its work needs
(`enabledPlugins`). It holds no copy of any skill. A template's own settings
enable its blueprint plugin, so a product made from it inherits the skill.

`~/.claude` keeps only what is personal: the marketplaces a person added and
skills still under development.

## Consequences

- Every session that starts in the repository, on any machine, sees the same
  list.
- A repository that ignored all of `.claude/` must let `settings.json`
  through, while `settings.local.json` stays ignored.
- Claude Code loads a skill's name and description at start and the rest only
  when a task matches, so enabling a plugin costs little until it is used.
