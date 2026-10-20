---
description: Find new job postings matching your profile via the installed portal-search CLIs
---

Read `.claude/skills/job-scraper/SKILL.md` and execute it exactly as written. It is the canonical specification and the single source of truth for this workflow - follow its steps in order without skipping, reordering, or reinterpreting them. The skill's own directory is `.claude/skills/job-scraper/` - files it references as "this directory" (e.g. `search-queries.md`) live there.

In opencode, wherever the specification says to dispatch agents with the **Agent tool** (e.g. parallel portal CLI searches), use the `task` tool with `subagent_type: general`.

User input for this run - substitute it wherever the specification references `$ARGUMENTS` (a focus area like "data science", "broad", or "health"; empty for a default run):

$ARGUMENTS
