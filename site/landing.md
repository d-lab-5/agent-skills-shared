# Concurrent Agent Skills

How D-LAB-5 shares what its AI coding agents know, across many repositories,
five development domains, several teams, and several kinds of agent working at
the same time.

<div class="apps">

<section>

## The rule

**Each skill has exactly one home:** the repository that owns its subject. A
template's skill lives in the template, a domain's in the domain's repository,
a tool's in the tool. The catalogue holds a pointer to each home and never a
copy, so there is nothing to drift.

</section>

<section>

## The catalogue

[d-lab-5/agent-skills](https://github.com/d-lab-5/agent-skills) is a Claude
Code plugin marketplace. Each repository commits a `.claude/settings.json`
naming the plugins it needs, so a session on this PC, on the web or in a
collaborator's clone loads the same skills. A gate checks every change, and a
release builds the same skills for claude.ai and other agents.

</section>

</div>

- **[Diagrams](diagrams/)**: {diagrams} interactive drawings: the whole system, the flows a change and a session follow, and the files that hold it together.
- **[Decisions](adr/)**: {adrs} architecture decision records.
- **[Roadmap](roadmap.html)**: the migration, step by step.
