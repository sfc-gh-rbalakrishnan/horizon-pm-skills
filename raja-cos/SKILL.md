---
name: raja-cos
description: "Raja's Chief of Staff skill for area product leadership. Routes to specialized sub-skills for daily PM work, team management, and leadership responsibilities. Use when: starting the day, prepping for customer meeting, reviewing team compliance, reviewing OKRs, reviewing product documents, checking competitive landscape, drafting communications, preparing for PFM meeting, QBR prep. Triggers: good morning, start my day, morning brief, customer prep, prep for meeting, team check, team review, PM compliance, doc review, review this PRD, competitive, OKR update, QBR, draft email, M5, calibrate, PLT check, PFM meeting."
---

# Raja CoS — Area Product Leader Chief of Staff

Router skill for Raja Balakrishnan, Senior Manager PM (Data & AI Governance, Horizon team). Covers IC work, team management (3 PMs), area leadership, and M5 career growth.

## Intent Detection

| User says... | Route to |
|---|---|
| "good morning", "start my day", "morning brief", "PLT check", "PFM meeting", "daily briefing" | `morning-brief/SKILL.md` |
| "prep for [customer]", "customer meeting", "customer call", "pre-read" | `customer-prep/SKILL.md` |
| "team check", "team review", "how is [PM name]", "PM process", "customer cadence", "notes compliance" | `team-review/SKILL.md` |
| "review this", "catch gaps", "PRD review", "before I send", "doc review", "before presenting" | `doc-review/SKILL.md` |
| "competitive", "what is Databricks doing", "Collibra", "Alation", "Monte Carlo", "Atlan", "Purview", "threat", "competitive landscape" | `competitive-intel/SKILL.md` |
| "OKR", "QBR", "quarterly progress", "OKR update", "northstar", "how are we tracking", "OKR report" | `okr-qbr/SKILL.md` |
| "draft email", "M5", "calibrate", "write to", "communicate up", "communicate down", "message to my team", "upward communication" | `comms-calibration/SKILL.md` |

## Routing

1. **Detect** intent from user message using the table above
2. **Load** the matching sub-skill
3. **Follow** that sub-skill's workflow completely

If intent is ambiguous, ask: "Which mode? Morning brief / Customer prep / Team review / Doc review / Competitive intel / OKR-QBR / Comms calibration"

## Foundational Principles

**#1 — M5 lens on every output.** Before presenting any output, check: does this establish strategic insight and a clear recommendation, or does it just report status? Status reports are M4. Strategic framing with "so what + what next" is M5.

**#2 — Sources always.** Every claim cites a source (Jira ticket, customer name + date, Glean result, Snowflake query). Flag gaps explicitly as `[UNVERIFIED]` rather than filling with assumptions.

**#3 — Action-typed outputs.** Every output ends with a typed action list: (A) Communicate now (B) Fix in Jira (C) Roadmap note (D) Escalate (E) No action needed.

## References

- `references/m5-calibration.md` — M5 communication principles
- `references/pm-standards.md` — Team process standards
- `references/area-context.md` — Data & AI Governance area context
