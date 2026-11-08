# ADR-0002: Each skill has one home, and the catalogue points to it

Status: **Accepted**

## Context

An inventory of one workstation found 262 SKILL.md files. The same skill sat
in several repositories in different versions; the newest knew how to host
its server, the older copies did not. Others reached their repositories
through symlinks, which break on a Windows clone, and some lived only in a
user's home folder, invisible to a web session or a collaborator.

## Decision

A skill lives in the repository that owns its subject, in that repository's
`plugin/`, and nowhere else. The catalogue, d-lab-5/agent-skills, lists it with
a git-subdir pointer: repository and path, never a copy. Skills that belong to
no one repository, how D-LAB-5 works anywhere, live in the catalogue's own
`plugins/dlab5-house`. Third-party skills are pinned by a lock file with a
content hash and never forked.

There are five kinds: house, blueprint (one per template), domain, product or
tool, and third party. A skill's name carries its domain as a prefix.

## Consequences

- A change to a skill is made in the same pull request as the code it
  describes, by the people who own that code.
- There is nothing to drift: every machine fetches the one copy.
- Adding a plugin to the catalogue is one entry, written once; the catalogue is
  not on the path of any later change.
- A pointer that names a folder not yet on its repository's main fails the
  catalogue's check until the home is merged. The order is: home first, then
  catalogue.
