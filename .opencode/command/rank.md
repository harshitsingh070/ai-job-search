---
description: Triage scraped jobs into a ranked shortlist
---

Read `.claude/commands/rank.md` and execute it exactly as written. It is the canonical specification and the single source of truth for this workflow - follow its steps in order without skipping, reordering, or reinterpreting them.

In opencode, wherever the specification says to dispatch agents with the **Agent tool** (e.g. `general-purpose` scoring agents), use the `task` tool with `subagent_type: general`.

User input for this run - substitute it wherever the specification references `$ARGUMENTS`:

$ARGUMENTS
