# Roadmap

Where Concurrent Agent Skills is heading: what is done, what is next, and what
is only an idea. Each step links to the decision behind it.

## Now

- **Done:** the catalogue d-lab-5/agent-skills, with its gate and CI
  ([ADR-0004](adr/0004-a-change-needs-a-version.md)).
- **Done:** the skills that lived only on one machine have homes: each
  template's `plugin/`, the blueprinting platform, the workstation
  configuration ([ADR-0002](adr/0002-one-home-per-skill.md)).
- **Done:** one copy of the MCP-server and API-key skills, in `dlab5-house`;
  repositories enable it instead of copying it
  ([ADR-0003](adr/0003-repositories-declare-their-skills.md)).
- **Done:** DigitalHome.Cloud's skills are one `dhc` plugin, and its symlinks
  are gone. Two security audits became one `dlab5-security-audit`, with a
  module per landscape.

## Next

- Third-party skills from one lock file, refreshed in every place that vendors
  them.
- `.claude/settings.json` in every active repository and template.
- Release v1: the zips uploaded to claude.ai
  ([ADR-0005](adr/0005-releases-are-pinned-by-hash.md)).

## Later

- Skills that agents propose for themselves, reviewed like any other change.
