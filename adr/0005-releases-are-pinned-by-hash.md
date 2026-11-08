# ADR-0005: One source, released for every agent, pinned by hash

Status: **Accepted**

## Context

Not every agent reads Claude Code plugins. claude.ai takes uploaded zips,
Codex, Cursor and others read an open `.agents/skills` layout, and a hosted
agent should never load "whatever is latest" at run time.

## Decision

A release tag `v*` runs the check, then `scripts/build-dist.mjs`, which builds
from the same SKILL.md files:

- `dist/claude-ai/<name>.zip`, one per skill, uploaded by hand;
- `dist/agents/skills/<name>/`, the open layout;
- `dist/manifest.json`: each skill's name, plugin, version, sha256 and source
  commit.

The release attaches them. A hosted agent fetches one release at build time and
compares each skill's sha256 with the manifest before loading it.

## Consequences

- Every format says the same thing, because there is one source.
- The hashes prove the files are the released ones. They are not signatures:
  trust rests on the release coming from the d-lab-5 repository.
- Uploading to claude.ai stays a person's step; there is no API for it in
  scope.
