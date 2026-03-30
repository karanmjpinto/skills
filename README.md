# Skills

A curated collection of AI coding skills for Claude Code, Cursor, Windsurf, and any tool that supports the [Agent Skills Standard](https://github.com/runkids/skillshare). Clone this repo and point your AI tools at it to get production-grade workflows out of the box.

## Quick Start

**One-line install (with [skillshare](https://github.com/runkids/skillshare)):**

```bash
skillshare install https://github.com/karanmjpinto/skills
```

**Manual setup:**

```bash
# Clone the repo
git clone https://github.com/karanmjpinto/skills.git

# Copy skills to your AI tool's skill directory
cp -r skills/*/* ~/.claude/skills/     # Claude Code
cp -r skills/*/* ~/.cursor/skills/     # Cursor
cp -r skills/*/* ~/.windsurf/skills/   # Windsurf
```

**Cherry-pick a category:**

```bash
# Only want Railway skills?
cp -r skills/railway/* ~/.claude/skills/

# Only want production readiness?
cp -r skills/production-readiness/* ~/.claude/skills/
```

## What's Included

### Production Readiness (9 skills)
Everything you need to take a vibe-coded project to production. Based on [vibe-to-prod](https://github.com/osmanio2/vibe-to-prod).

| Skill | What it does |
|-------|-------------|
| `repo-scanner` | Audits your repo's tech stack, hosting, and production readiness |
| `repo-structurer` | Cleans up repo structure, adds READMEs, removes dead files |
| `prompt-engineer` | Makes your repo AI-native with AGENTS.md and .cursorrules |
| `deployment-engineer` | Sets up CI/CD, Docker, and environment pipelines |
| `security-auditor` | Finds hardcoded secrets, vulnerable deps, auth issues |
| `devops-advisor` | Audits database config, caching, scaling patterns |
| `monitoring-setup` | Configures Sentry, PostHog, health checks, and alerting |
| `cost-optimizer` | Identifies unused cloud resources and billing savings |
| `integration-linker` | Connects your tools — Slack + GitHub, Linear + Git, etc. |

### Railway (13 skills)
Full Railway CLI integration for deploying and managing services.

| Skill | What it does |
|-------|-------------|
| `railway-new` | Create projects and services, deploy from GitHub |
| `railway-deploy` | Push code with `railway up` |
| `railway-deployment` | Manage deployments, view logs, debug failures |
| `railway-status` | Check what's running and deployment status |
| `railway-service` | Rename services, change icons, link services |
| `railway-environment` | Manage variables, build/deploy settings, scaling |
| `railway-database` | Add Postgres, Redis, MySQL, MongoDB |
| `railway-domain` | Add custom domains, generate Railway domains |
| `railway-templates` | Deploy from template marketplace (Ghost, n8n, etc.) |
| `railway-projects` | List/switch projects, PR deploys, project settings |
| `railway-metrics` | CPU, memory, network, disk usage monitoring |
| `railway-central-station` | Search Railway community discussions |
| `railway-railway-docs` | Fetch up-to-date Railway documentation |

### Vercel (6 skills)
React, Next.js, and Vercel deployment best practices from [Vercel Labs](https://github.com/vercel-labs/agent-skills).

| Skill | What it does |
|-------|-------------|
| `deploy-to-vercel` | Deploy applications and websites to Vercel |
| `vercel-cli-with-tokens` | Vercel CLI with token-based auth for CI/CD |
| `vercel-react-best-practices` | React and Next.js performance optimization |
| `vercel-composition-patterns` | Scalable React composition and component architecture |
| `vercel-react-native-skills` | React Native and Expo mobile best practices |
| `web-design-guidelines` | Web interface design and accessibility guidelines |

### Dev Workflow (1 skill)
| Skill | What it does |
|-------|-------------|
| `interface-craft` | Build polished, animated React interfaces with Storyboard Animation DSL, DialKit controls, and Design Critique methodology. By Josh Puckett. |

### Personal (2 skills)
| Skill | What it does |
|-------|-------------|
| `kmjp-social` | Generate LinkedIn posts and X threads from raw notes |
| `pitch-deck` | Build investor-ready pitch decks as PPTX from meeting notes |

### Meta (1 skill)
| Skill | What it does |
|-------|-------------|
| `skillshare` | Manage and sync skills across 50+ AI tools from a single source |

## How Skills Work

Each skill is a directory containing a `SKILL.md` file (and optionally assets/references). When your AI tool loads a skill, it gains that capability — like giving it a new manual for a specific workflow.

```
skills/
├── production-readiness/
│   ├── repo-scanner/
│   │   └── SKILL.md
│   ├── security-auditor/
│   │   └── SKILL.md
│   └── ...
├── railway/
│   ├── railway-new/
│   │   └── SKILL.md
│   └── ...
├── vercel/
│   ├── deploy-to-vercel/
│   │   └── SKILL.md
│   └── ...
└── ...
```

## Using with Skillshare

If you use [skillshare](https://github.com/runkids/skillshare) to manage skills across multiple AI tools:

```bash
# Install all skills from this repo
skillshare install https://github.com/karanmjpinto/skills

# Or set this repo as your source
skillshare config set source /path/to/this/repo/skills

# Sync to all your targets
skillshare sync
```

## Contributing

PRs welcome. Each skill should follow the [Agent Skills Standard](https://github.com/runkids/skillshare):

1. Create a directory with your skill name
2. Add a `SKILL.md` with frontmatter (`name`, `description`) and instructions
3. Optionally add `assets/` and `references/` directories
4. Submit a PR

## License

Apache 2.0
