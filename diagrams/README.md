# Diagrams

Interactive drawings of how Concurrent Agent Skills works, made with Archify. The site
shows them in its gallery at `/diagrams/`.

- `src/<name>.<type>.json`: the source, the only file to edit.
- `<name>.html`: the page rendered from it. Never edit it by hand.
- `src/rendered.json`: which source each page was rendered from.

`npm run diagrams` renders what changed (it needs the Archify skill in
`~/.claude/skills/archify`, or `$ARCHIFY`); `npm run check` says whether every
page is in step with its source and listed once.

A diagram is listed once, with what it explains: under one of the groups
below, or in the ADR it belongs to, under that ADR's `## Diagrams`. Each line
reads `- [Title](../diagrams/<name>.html): what it explains.` and becomes the
gallery card's text.

## Overview

The whole system on one page.

- [One home per skill, many agents](../diagrams/overview-one-home.html): where skills live, how the catalogue points to them, the gate every change passes, and how each kind of agent gets them.

## Flows

What happens, in order.

- [Changing a skill](../diagrams/flow-change-a-skill.html): edit and bump in the skill's home, the gate in CI, a person merges, and the next session loads the new version.
- [A session gets its skills](../diagrams/flow-session-gets-skills.html): from a repository's committed settings through the catalogue's pointer to the plugin cache, and how a task triggers a skill.
- [One source, every agent's format](../diagrams/flow-release.html): a release tag builds zips for claude.ai, the open agents layout, and a manifest of hashes a hosted agent checks.

## Models

The files and what each one holds.

- [The files that hold it together](../diagrams/model-catalogue.html): settings.json, marketplace.json, a plugin entry and its two kinds of source, plugin.json and SKILL.md.

