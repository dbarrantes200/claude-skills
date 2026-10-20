# Claude Skills — Danny's collection

My curated Claude skills: custom-built ones live in `skills/`, plus a catalog
of third-party skills I use (installed from their own repos, not copied here).

## My skills (`skills/`)

| Skill | What it does |
|---|---|
| `danny-site-standards` | My reusable design, content, and delivery standards for bilingual (ES/EN) landing pages and micro-SaaS tool sites. Apply automatically on every site build/update. |
| `presentaciones-visuales` | Creates self-contained bilingual (ES/EN) HTML slide presentations from an idea, outline, document, transcript, or PowerPoint — for meetings, classes, pitches, proposals, and videos. |
| `youtube-upload-checklist` | Prepare, review, and publish YouTube videos and Shorts on my channels with one repeatable checklist for packaging, retention, Studio settings, captions, audience rules, and post publish analytics. |

## Curated for my work (Deloitte)

| Skill | Repo | What it does |
|---|---|---|
| `factcheck` | [analystacademy/claude-skills](https://github.com/analystacademy/claude-skills/tree/main/factcheck) | Verifies factual claims in a text against sources, with evidence links |
| `humanizer` | [blader/humanizer](https://github.com/blader/humanizer) | Rewrites AI text to sound natural/human; learns my style from 2–3 samples |
| `frontend-slides` | [zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides) | Turns notes into designed, animated slide decks (HTML) |
| `last30days` | [mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill) | Researches what was said about a topic in the last 30 days (Reddit, HN, GitHub) |
| `pdf` / `docx` / `pptx` / `xlsx` | [anthropics/skills](https://github.com/anthropics/skills) | Create and edit PDF, Word, PowerPoint, Excel files (official Anthropic) |

## Curated for my projects (micro-SaaS + Mila y Leo)

| Skill | Repo | What it does |
|---|---|---|
| `impeccable` | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | Polishes AI-generated website design (boulder/delight presets + critique mode) |
| `claude-video` | [bradautomates/claude-video](https://github.com/bradautomates/claude-video) | Analyzes video content (frames + subtitles) — for studying reference reels |
| `remotion` | [remotion-dev/remotion](https://github.com/remotion-dev/remotion) | Teaches Claude to build videos with code — for shorts/promos |
| `webapp-testing` | [anthropics/skills](https://github.com/anthropics/skills) | Tests web apps (official Anthropic) |
| `frontend-design` | [anthropics/skills](https://github.com/anthropics/skills) | Frontend design guidance (official Anthropic) |

## For building new skills

| Skill | Repo | What it does |
|---|---|---|
| `skill-creator` | [anthropics/skills](https://github.com/anthropics/skills) | Generates a skill from a description; reviews existing ones |
| `mcp-builder` | [anthropics/skills](https://github.com/anthropics/skills) | Builds MCP servers |
| `template/` | (in this repo) | Skeleton for authoring a new skill |

Official Anthropic repos: [anthropics/skills](https://github.com/anthropics/skills) (19 skills)
and [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) (11 plugins).

## How to install a skill

**Claude Code** (in your working folder):
> Instala esta skill desde GitHub siguiendo sus instrucciones de instalación: `<repo-url>`

Or via plugin marketplace:
```
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
```

**Claude.ai** (paid plan): upload a skill's folder as a custom skill
(Settings → Skills), or enable the pre-built ones.

## Security note

A skill is a set of instructions Claude obeys. Before installing one from a
third-party repo, open its `SKILL.md` and review what it asks Claude to do —
especially any scripts it runs. Trust, but verify.
