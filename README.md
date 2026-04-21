# Skills

A curated collection of AI coding skills for Claude Code, Cursor, Windsurf, and any tool that supports the [Agent Skills Standard](https://github.com/runkids/skillshare). Also serves as a **Claude Code plugin marketplace** with curated packs for Utopia Capital teams and fellows.

## Install as a Plugin Marketplace (Recommended for Teams)

This repo is a Claude Code plugin marketplace. Team members register it once, then install only the packs they need.

**1. Register the marketplace (one-time):**

```
/plugin marketplace add karanmjpinto/skills
```

**2. Install a pack:**

```
/plugin install utopia-dd-pack@skills          # Due diligence & investment eval
/plugin install utopia-design-pack@skills      # 32 UI/UX design skills
/plugin install utopia-deploy-pack@skills      # Railway + Vercel + production
/plugin install utopia-ml-pack@skills          # HuggingFace & ML tools
/plugin install utopia-content-pack@skills     # Obsidian & research
```

**3. Update packs as they change:**

```
/plugin marketplace update skills
```

See [Available Packs](#available-packs) below for what each pack includes.

## Install All Skills (Individual / Power Users)

**One-line install (with [skillshare](https://github.com/runkids/skillshare)):**

```bash
skillshare install https://github.com/karanmjpinto/skills
```

**With npx skills:**

```bash
npx skills add karanmjpinto/skills
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

# Only want HuggingFace skills?
cp -r skills/huggingface/* ~/.claude/skills/

# Only want production readiness?
cp -r skills/production-readiness/* ~/.claude/skills/
```

## Available Packs

Each pack bundles a set of skills for a specific workflow. Install only what you need — keeps your context lean.

| Pack | Skills | Use case |
|------|--------|----------|
| **utopia-dd-pack** | 6 | Technical due diligence — assess whether a startup's tech works, scales, and is secure |
| **utopia-design-pack** | 32 | Full UI/UX toolkit — plan, build, critique, and polish frontend interfaces |
| **utopia-deploy-pack** | 25 | Ship to production — Railway, Vercel, CI/CD, monitoring, deployment readiness |
| **utopia-ml-pack** | 11 | ML workflows — HuggingFace training, evals, datasets, Transformers.js |
| **utopia-content-pack** | 5 | Knowledge management — Obsidian vaults, markdown, canvases, web extraction |

See [`packs.config.json`](./packs.config.json) for the exact skill list in each pack.

### Adding or Editing Packs

Packs are defined in [`packs.config.json`](./packs.config.json). To add a new pack or move skills between packs:

1. Edit `packs.config.json` — add a pack entry or update the `skills` array
2. Run `./build-packs.sh` — regenerates `.claude-plugin/marketplace.json` and `plugins/`
3. Commit and push — team members get the update via `/plugin marketplace update skills`

Example: add a new `utopia-research-pack`:

```jsonc
{
  "name": "utopia-research-pack",
  "description": "Research and analysis skills for fellows",
  "version": "1.0.0",
  "keywords": ["research", "analysis"],
  "skills": ["defuddle", "huggingface-papers"]
}
```

Then `./build-packs.sh && git add -A && git commit -m "Add research pack" && git push`.

Requires `jq` (`brew install jq`).

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

### HuggingFace (11 skills)
ML model training, evaluation, datasets, and Gradio app building from [HuggingFace Skills](https://huggingface.co).

| Skill | What it does |
|-------|-------------|
| `hf-cli` | HuggingFace Hub CLI for managing models, datasets, spaces, repos |
| `huggingface-llm-trainer` | Train/fine-tune LLMs with TRL or Unsloth (SFT, DPO, GRPO) |
| `huggingface-vision-trainer` | Train vision models — object detection, classification, segmentation |
| `huggingface-community-evals` | Run model evaluations with inspect-ai and lighteval locally |
| `huggingface-datasets` | Dataset Viewer API — fetch rows, search, filter, download parquet |
| `huggingface-gradio` | Build Gradio web UIs and demos in Python |
| `huggingface-papers` | Look up and read HuggingFace paper pages and arXiv metadata |
| `huggingface-paper-publisher` | Publish and manage research papers on HuggingFace Hub |
| `huggingface-tool-builder` | Build tools/scripts using the HuggingFace API |
| `huggingface-trackio` | Track and visualize ML training experiments with Trackio |
| `transformers-js` | Run ML models in JavaScript/TypeScript with Transformers.js |

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

### Obsidian (5 skills)
Obsidian vault management and markdown skills from [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills).

| Skill | What it does |
|-------|-------------|
| `obsidian-cli` | Interact with Obsidian vaults — read, create, search, manage notes, tasks, properties, plugins |
| `obsidian-markdown` | Create and edit Obsidian Flavored Markdown — wikilinks, embeds, callouts, properties |
| `obsidian-bases` | Create and edit Obsidian Bases (.base files) with views, filters, formulas, summaries |
| `json-canvas` | Create and edit JSON Canvas files (.canvas) — nodes, edges, groups, visual canvases |
| `defuddle` | Extract clean markdown from web pages, removing clutter and navigation to save tokens |

### Efecto (3 skills)
Visual design tools powered by [Efecto](https://efecto.dev) MCP integration.

| Skill | What it does |
|-------|-------------|
| `efecto-web-design` | Design web pages and app UIs with JSX and Tailwind CSS |
| `efecto-graphic-design` | Create presentations, posters, cards, infographics, and more |
| `efecto-social-media` | Design social media assets for all major platforms |

### Impeccable (17 skills)
Production-grade UI design toolkit from [pbakaus/impeccable](https://github.com/pbakaus/impeccable). Covers every phase of frontend design — from planning to polish.

| Skill | What it does |
|-------|-------------|
| `impeccable` | Create distinctive, production-grade frontend interfaces with high design quality |
| `shape` | Plan UX and UI for a feature before writing code with structured discovery |
| `critique` | Evaluate design from a UX perspective with quantitative scoring |
| `audit` | Run technical quality checks — accessibility, performance, theming, responsive |
| `layout` | Improve layout, spacing, and visual rhythm |
| `typeset` | Fix font choices, hierarchy, sizing, weight, and readability |
| `colorize` | Add strategic color to monochromatic designs |
| `animate` | Enhance features with purposeful animations and micro-interactions |
| `polish` | Final quality pass — alignment, spacing, consistency, micro-details |
| `adapt` | Make designs responsive across screen sizes and devices |
| `optimize` | Diagnose and fix UI performance — loading, rendering, bundle size |
| `clarify` | Improve UX copy, error messages, microcopy, and labels |
| `distill` | Strip designs to their essence, remove unnecessary complexity |
| `delight` | Add moments of joy and personality to interfaces |
| `bolder` | Amplify safe designs to be more visually interesting |
| `quieter` | Tone down visually aggressive designs while preserving quality |
| `overdrive` | Push interfaces past limits — shaders, spring physics, 60fps animations |

### Taste (7 skills)
High-end visual design skills from [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill). Anti-generic UI standards.

| Skill | What it does |
|-------|-------------|
| `design-taste-frontend` | Senior UI/UX engineering with metric-based rules and strict component architecture |
| `high-end-visual-design` | Design like a high-end agency — exact fonts, spacing, shadows, animations |
| `redesign-existing-projects` | Upgrade existing apps to premium quality, identify generic AI patterns |
| `industrial-brutalist-ui` | Raw mechanical interfaces — Swiss typography meets military terminal aesthetics |
| `minimalist-ui` | Clean editorial-style interfaces — warm monochrome, typographic contrast, bento grids |
| `stitch-design-taste` | Semantic design system for Google Stitch with premium standards |
| `full-output-enforcement` | Override LLM truncation — enforce complete code generation, ban placeholders |

### Design (5 skills)
| Skill | What it does |
|-------|-------------|
| `ui-ux-pro-max` | UI/UX design intelligence — 50+ styles, 161 palettes, 57 font pairings, 99 UX guidelines across 10 stacks |
| `sketch-prompt` | Convert text/notes into conceptual sketch images with ComfyUI + Flux |
| `emil-design-eng` | Emil Kowalski's philosophy on UI polish, component design, and animation decisions |
| `architecture-diagram` | Create professional dark-themed architecture/infrastructure/network diagrams as standalone HTML + SVG |
| `diagram-design` | Create technical and product diagrams — architecture, flowchart, sequence, state machine, ER, timeline, swimlane, quadrant, tree, venn, pyramid — as HTML + inline SVG with editorial skin |

### Dev Workflow (1 skill)
| Skill | What it does |
|-------|-------------|
| `interface-craft` | Build polished, animated React interfaces with Storyboard Animation DSL, DialKit controls, and Design Critique methodology. By Josh Puckett. |

### Personal (3 skills)
| Skill | What it does |
|-------|-------------|
| `kmjp-social` | Generate LinkedIn posts and X threads from raw notes |
| `pitch-deck` | Build investor-ready pitch decks as PPTX from meeting notes |
| `technical-dd` | Generate investment-grade Technical Due Diligence reports |

### Meta (2 skills)
| Skill | What it does |
|-------|-------------|
| `skillshare` | Manage and sync skills across 50+ AI tools from a single source |
| `find-skills` | Discover and install agent skills from the skills marketplace |

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
├── huggingface/
│   ├── hf-cli/
│   │   └── SKILL.md
│   ├── huggingface-llm-trainer/
│   │   └── SKILL.md
│   └── ...
├── vercel/
│   ├── deploy-to-vercel/
│   │   └── SKILL.md
│   └── ...
├── efecto/
│   ├── efecto-web-design/
│   │   └── SKILL.md
│   └── ...
├── design/
│   ├── ui-ux-pro-max/
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
