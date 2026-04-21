# Contributing

How to propose, share, and graduate skills in this marketplace.

## The Sandbox → Pack Flow

Based on the pattern Anthropic's Claude Code team uses internally. The goal: let anyone propose skills without overloading the default packs that every team member loads.

```
   idea
    │
    ▼
 sandbox/          ← experimental, anyone can add here, PR review light
    │
    ▼  (battle-tested, actually used, consistent quality)
    │
 skills/<category>/  ← official source of truth
    │
    ▼
 packs.config.json ← added to a pack so team installs it
```

## Proposing a New Skill

**1. Create it in `skills/sandbox/<skill-name>/`**

Minimum structure:

```
skills/sandbox/my-skill/
└── SKILL.md
```

`SKILL.md` frontmatter:

```markdown
---
name: my-skill
description: One sentence. Written AS CONDITIONS FOR WHEN TO TRIGGER, not as a summary. E.g. "Use when the user asks to build X, mentions Y, or needs Z."
---

# My Skill

## What it does
...

## Gotchas
- Real mistakes Claude makes when using this skill (update as you find them)

## Examples
...
```

**2. Test it**

Use it in real work for a few days. Record every time Claude misunderstands or goes off-track — those go into the Gotchas section.

**3. Share**

Open a PR, or post a link to the branch in Slack / the team forum. Get at least one other person to try it.

## Graduating a Skill

A skill is ready to graduate when it meets all of these:

- [ ] You (or someone else) has used it 5+ times in real work
- [ ] Gotchas section exists and reflects real edge cases
- [ ] Description is written as **trigger conditions**, not a summary
- [ ] Doesn't duplicate an existing skill (check by category first)
- [ ] Has at least one concrete example

**To graduate:**

1. Move `skills/sandbox/<skill>/` → `skills/<category>/<skill>/` (create new category if needed)
2. Add the skill name to one or more packs in `packs.config.json`
3. Run `./build-packs.sh`
4. Open a PR explaining: what problem it solves, who asked for it, gotchas found so far

## Categories

This repo uses the 9-category taxonomy from [Anthropic's Skills guide](./SKILL_TAXONOMY.md). When proposing, think about which category your skill fits in:

1. **Library & API References** — explains how to use a library/CLI/SDK correctly
2. **Product Verification** — describes how to test and verify code behavior
3. **Data Retrieval & Analysis** — connects to data stacks
4. **Business Process & Team Automation** — automates repetitive workflows
5. **Code Templates & Scaffolding** — generates framework boilerplate
6. **Code Quality & Code Review** — enforces quality standards
7. **CI/CD & Deployment** — ships code
8. **Runbooks** — investigations from symptom to report
9. **Infrastructure Operations** — routine maintenance and ops

Skills that blur multiple categories tend to confuse both Claude and the user. Pick one.

## Curation Principles

When reviewing a proposal:

- **Don't write the obvious** — Claude already knows basic coding. The skill should push past defaults.
- **Leave flexibility** — overly specific instructions backfire. Give Claude what it needs, let it adapt.
- **Prefer scripts over prose** — if a skill can ship a script that does the work deterministically, it should.
- **Kill duplicates** — if a new skill overlaps with existing one, either merge or reject.

## Writing Good Descriptions

The `description` field in SKILL.md is the **only thing Claude sees when deciding whether to use the skill**. It's a trigger condition, not a summary.

**Bad:** `"A skill for generating diagrams"`
**Good:** `"Use when the user asks for architecture diagrams, flowcharts, sequence diagrams, or ER diagrams. Output is standalone HTML + inline SVG."`

Good descriptions include:
- Concrete trigger phrases the user might say
- What the output looks like
- When NOT to use it (if it overlaps with a similar skill)

## Questions?

Ask Karan (@kmjp) or open an issue.
