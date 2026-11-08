# ADR-0004: Every change is checked, and a changed plugin needs a new version

Status: **Accepted**

## Context

Claude Code caches an installed plugin by its version. A skill edited without
a version bump never reaches a machine that already has it: the cache is
stale, silently. The repositories are public, so a skill must also never carry
an account id, a key, an email, a local path or a real name.

## Decision

`scripts/check.mjs` runs on every pull request and push to the catalogue. It
refuses:

- a symlink, an account id or ARN with one, a key or token, a cloud hostname,
  an email address, a local path, and any word on a private deny list;
- a skill whose front-matter name is not its folder, or whose description is
  over 1024 characters;
- a plugin changed since the base branch whose version did not move;
- a pointer that reaches no `plugin.json` and no skill, and a link to a
  private repository.

`test.sh` plants each fault in a scratch copy and expects the check to refuse
it, and checks that correct things pass.

## Consequences

- A pointer's skills are swept in their own home; in the catalogue their
  problems are warnings that name where to fix them, so one repository's slip
  does not block the others.
- The check is the reason a gap in the rules is fixed once, in one place.
