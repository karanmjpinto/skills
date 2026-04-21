# Hooks

Optional hook scripts you can wire into your Claude Code settings.

## `log-skill-usage.sh`

A PreToolUse hook that logs every skill invocation to a local JSONL file. Based on the pattern Anthropic uses internally to measure skill adoption.

**Why:** With 82+ skills available, you want data on which are actually used. Skills that fire less than expected either have a bad description (Claude isn't finding them) or aren't useful enough. Data tells you which to keep, rewrite, or retire.

### Setup (per user)

1. Copy the script somewhere Claude can execute it:
   ```bash
   mkdir -p ~/.claude/hooks
   cp hooks/log-skill-usage.sh ~/.claude/hooks/
   chmod +x ~/.claude/hooks/log-skill-usage.sh
   ```

2. Add to `~/.claude/settings.json`:
   ```json
   {
     "hooks": {
       "PreToolUse": [
         {
           "matcher": "Skill",
           "hooks": [
             {
               "type": "command",
               "command": "~/.claude/hooks/log-skill-usage.sh"
             }
           ]
         }
       ]
     }
   }
   ```

3. Start using Claude normally. Each skill invocation appends a line to `~/.claude/skill-usage.log`.

### Example log output

```jsonl
{"ts":"2026-04-21T14:32:01Z","user":"kp","host":"kp-mbp","session":"abc123","skill":"diagram-design"}
{"ts":"2026-04-21T14:35:44Z","user":"kp","host":"kp-mbp","session":"abc123","skill":"technical-dd"}
{"ts":"2026-04-21T15:02:17Z","user":"kp","host":"kp-mbp","session":"def456","skill":"pitch-deck"}
```

### Aggregating across the team

For a shared view, have each fellow set `SKILL_USAGE_LOG` to a path they rsync to a shared S3 bucket / Google Drive folder nightly. Or build a tiny Railway service that accepts POSTs from the hook.

### Quick analysis

Top skills by usage:

```bash
cat ~/.claude/skill-usage.log | jq -r '.skill' | sort | uniq -c | sort -rn | head -20
```

Sessions per user:

```bash
cat ~/.claude/skill-usage.log | jq -r '"\(.user) \(.session)"' | sort -u | awk '{print $1}' | sort | uniq -c
```

Skills that haven't been used in 30 days (candidates to retire):

```bash
CUTOFF=$(date -u -v-30d +%Y-%m-%d)
comm -23 \
  <(ls ~/.agents/skills | sort) \
  <(cat ~/.claude/skill-usage.log | jq -r --arg cutoff "$CUTOFF" 'select(.ts > $cutoff) | .skill' | sort -u)
```
