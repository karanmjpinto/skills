# Sandbox

A staging area for experimental skills that aren't ready for the official [packs](../../packs.config.json) yet.

## Why a sandbox?

From the [Anthropic Skills guide](https://medium.com/@tortmario/skills-for-claude-code-the-ultimate-guide-from-an-anthropic-engineer) — it's easy to create duplicate or low-quality skills. A sandbox lets you:

- Try ideas before committing to them
- Share a skill with the team to get feedback
- Iterate in public without bloating everyone's context

## How it works

1. **Propose:** Drop your new skill in this folder as `skills/sandbox/<skill-name>/SKILL.md`
2. **Share:** Open a PR or post the link in Slack so others can try it
3. **Graduate:** When it's battle-tested and useful, move it to the right category (e.g. `skills/design/`) and add it to a pack in [`packs.config.json`](../../packs.config.json)

See [`CONTRIBUTING.md`](../../CONTRIBUTING.md) for the full curation process.

## Installing sandbox skills

Sandbox skills are **not** in any pack — they don't auto-install. To try one:

```bash
# Copy to your Claude Code skills dir
cp -r skills/sandbox/<skill-name> ~/.claude/skills/
```

Or symlink via skillshare.
