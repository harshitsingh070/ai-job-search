# opencode Setup: AI Job Search

This repo runs the full ai-job-search workflow under [opencode](https://opencode.ai).
opencode natively discovers the canonical skills under `.claude/skills/` and `.agents/skills/`;
everything in this folder is a **thin pointer** - nothing here duplicates the specs.
The cross-runtime contract is described in [AGENTS.md](../AGENTS.md).

## Requirements

| Tool | Needed for | Check |
|------|-----------|-------|
| [opencode](https://opencode.ai) | the agent runtime | `opencode --version` |
| [bun](https://bun.sh) | portal-search CLIs (`/scrape`) | `bun --version` |
| Python 3 | helper tools (`job_key.py`, `verify_pdf.py`, ...) | `python --version` |
| LaTeX (MiKTeX / TeX Live) | `/apply` PDF compile + verification (`lualatex` + `xelatex`) | `lualatex --version` |

If `bun` is missing, `/scrape` falls back to WebSearch. If LaTeX is missing, `/apply` cannot do its
mandatory PDF verification locally - install MiKTeX or compile on Overleaf instead.

## How to run

From the repo root (or any folder inside it - opencode walks up to the worktree root):

```sh
opencode                     # start the TUI
```

Then type a slash command, e.g. `/scrape`, or just ask in plain language ("find new jobs",
"rank these postings", "prepare me for the interview") - the matching skill auto-loads.

Non-interactive / scripted:

```sh
opencode run --command scrape            # run /scrape headless
opencode run --command scrape broad      # ...with arguments (broad, health, a focus area)
opencode --continue                      # jump back into the last session
```

> **Restart after config changes.** opencode loads `opencode.json`, commands, agents, and skills
> once at startup. After editing any of them (or pulling repo updates), quit and restart opencode.

## Commands

All 14 commands live in `.opencode/command/*.md` as thin wrappers that execute the canonical
specification under `.claude/` (a `.claude/commands/*.md` file, or the skill's `SKILL.md` for
`scrape` and `upskill`). Edit the `.claude/` source - the wrapper follows.

| Command | What it does |
|---------|--------------|
| `/setup` | Profile onboarding from your documents, a pasted CV, or an interview (`/setup --section search` to update search queries only) |
| `/scrape` | Find new job postings via the installed portal CLIs, dedup against seen jobs, draft referral outreach messages (`/scrape broad`, `/scrape health`) |
| `/rank` | Batch-score scraped postings against the full fit framework into a ranked shortlist |
| `/apply` | Drafter-reviewer workflow: fit evaluation, then tailored CV + cover letter for a posting (URL or pasted text) |
| `/interview` | Prepare answers, questions, and talking points for a tracked application |
| `/outcome` | Record the result of an application (feeds calibration back into `/setup` data) |
| `/expand` | Enrich the profile by scanning linked public sources (GitHub, portfolio, ...) |
| `/upskill` | Skill-gap heatmap + prioritized learning plan with study resources (`/upskill <URL>` for one posting) |
| `/add-portal` | Generate a new job-portal search skill for your market |
| `/add-template` | Register a custom CV/cover-letter LaTeX template and activate it |
| `/reset` | Reset candidate profile data (keeps framework rules) |
| `/notion-sync` | Push ranked jobs and applications to a Notion database |
| `/gmail-sync` | Sync application status from Gmail |
| `/html-report` | Generate an application-tracker dashboard |

## Skills

Skills are auto-discovered from `.claude/skills/` and `.agents/skills/` - there is no copy of them
here. `scrape` and `upskill` additionally have slash-command wrappers (above); everything else
auto-loads by topic.

### Workflow skills (`.claude/skills/`)

| Skill | What it does | Trigger examples |
|-------|--------------|------------------|
| `job-application-assistant` | Core assistant: fit evaluation, CV tailoring, cover letters, interview prep | "evaluate this job posting", "cover letter", "interview prep" |
| `scrape` (dir: `job-scraper/`) | The job-scraper workflow behind `/scrape` | `/scrape`, "find new jobs" |
| `upskill` | Gap analysis behind `/upskill` | `/upskill`, "what should I learn" |

### Portal search skills (`.agents/skills/`)

Each portal is a self-contained CLI skill with a `search`/`detail` contract; `/scrape` runs every
**enabled** one in parallel. Toggle a portal by flipping `enabled:` in its `SKILL.md`.

| Portal | Status | Notes |
|--------|--------|-------|
| `linkedin-search` | enabled | Public jobs-guest endpoints, any market; personal use only |
| `freehire-search` | enabled | freehire.me aggregator API; tech-focused, multi-market |
| `jobbank-search` | disabled | Danish demo portal |
| `jobdanmark-search` | disabled | Danish demo portal |
| `jobindex-search` | disabled | Danish demo portal |
| `jobnet-search` | disabled | Danish demo portal |

### Built-in skill

- `customize-opencode` - opencode config/skill/command authoring guidance; loads automatically when
  you edit this directory or `opencode.json`.

## Subagents

- `.opencode/agent/gemini-research-expert.md` - thin pointer to
  `.claude/agents/gemini-research-expert.md`; runs the Gemini CLI headless for external research.

## The typical loop

```
/setup -> /scrape -> /rank -> /apply -> /interview -> /outcome
```

with `/upskill`, `/expand`, `/add-portal`, `/add-template`, `/reset`, and the sync/report commands
around it.

## This directory

```
opencode.json                        # repo root: loads CLAUDE.md as instructions + pre-approved bash permissions
.opencode/
├── command/                         # 14 thin-pointer command wrappers (one per /command)
├── agent/
│   └── gemini-research-expert.md    # subagent pointer
└── README.md                        # this file
```

## Troubleshooting

- **Slash command not found in the TUI** - the wrapper file is missing in `.opencode/command/`, or
  opencode was not restarted after it was added. Quit and restart.
- **`/scrape` finds nothing** - check `bun --version`; check the portal `enabled:` flags; run
  `/scrape health` for a per-portal diagnosis.
- **`/apply` can't verify PDFs** - install MiKTeX (or TeX Live) so `lualatex` and `xelatex` are on
  PATH, or compile on Overleaf.
- **Privacy** - files touched by `/setup` contain personal data and are tracked by git. Keep commits
  local or push to a private repository - see [SETUP.md](../SETUP.md) section 8.

## Learn more

- opencode docs: <https://opencode.ai/docs>
- Workspace contract / thin-pointer design: [AGENTS.md](../AGENTS.md)
- Framework usage and full workflow: [README.md](../README.md)
