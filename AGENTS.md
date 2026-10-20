---
framework_version: 1.0.0
---

# Agent Guidelines: AI Job Search

This workspace is structured to manage job search activities, scraper tools, CVs, cover letters, and interview preparation.

## Thin-Pointer Design (Single Source of Truth)

To prevent duplication and configuration drift across different AI agent frameworks (Claude Code, Google Antigravity, Codex, Cursor, Gemini CLI, etc.), this workspace uses a unified thin-pointer design. All agent runtimes should load the canonical specifications and candidate profiles from the files and directories below:

1. **Personal Candidate Profile:**
   - The candidate profile, contact details, education, and target preferences are defined in [CLAUDE.md](CLAUDE.md) and the individual profile methodology files under [.claude/skills/job-application-assistant/](.claude/skills/job-application-assistant/) (specifically `01-*.md` etc.).
2. **Canonical Workflow Specifications:**
   - The step-by-step instructions and triggers for tasks (setup, scrape, rank, apply, upskill, interview) are defined in the [.claude/](.claude/) directory (specifically under `.claude/skills/` and `.claude/commands/`).
   - Do not duplicate these rules or specifications. Treat `.claude/` files as the single source of truth.
3. **Portal Search Skills:**
   - Job-portal search CLIs live under [.agents/skills/](.agents/skills/) in the portable Agent Skills format (with a `SKILL.md` per portal). Codex and Antigravity discover these automatically; the `/scrape` workflow in [.claude/skills/job-scraper/](.claude/skills/job-scraper/) orchestrates them.
4. **opencode Runtime:**
   - opencode natively discovers the skills under `.claude/skills/` and `.agents/skills/`, so they need no copy.
   - [opencode.json](opencode.json) loads the candidate profile ([CLAUDE.md](CLAUDE.md)) as instructions and mirrors the pre-approved tool permissions from [.claude/settings.json](.claude/settings.json).
   - The [.opencode/](.opencode/) directory holds only thin pointers: each `.opencode/command/*.md` wrapper executes its canonical specification under `.claude/` (usually a `.claude/commands/*.md` file; `scrape` and `upskill` point at their `.claude/skills/*/SKILL.md`), and `.opencode/agent/*.md` points at its `.claude/agents/*.md` definition. Nothing here duplicates workflow content - edit `.claude/` and the wrappers follow.
   - Full opencode guide (how to run, commands, skills, troubleshooting): [.opencode/README.md](.opencode/README.md).
