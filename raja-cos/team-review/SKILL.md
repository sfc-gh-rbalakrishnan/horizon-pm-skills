---
name: raja-cos-team-review
description: "Team PM compliance and OKR contribution review. Checks customer meeting cadence, notes hygiene, document health, and each PM's OKR contribution. Use when: reviewing team progress, PM compliance check, customer cadence audit, weekly team health check. Triggers: team check, team review, how is [PM name], PM process, customer cadence, notes compliance, team health."
parent_skill: raja-cos
---

# Team Review — PM Compliance & OKR Contribution

Audits your 3-PM team across process standards, customer engagement, and OKR progress. Surfaces coaching opportunities and risks before they escalate.

## Context

- **Team size:** 3 PMs (ask user for names if not known)
- **Customer meeting target:** ≥ 4 customer meetings per PM per week
- **Notes standard:** Meeting notes must be filed in the centralized Google Drive folder within 48 hours: https://drive.google.com/drive/folders/1_0K6mAf1EeCuOhixDhABGOIOSEbf8JTu
- **OKR source of truth:** https://docs.google.com/spreadsheets/d/1QQqcGUp9o2ebb3j-UCjXP3fQBXVMgzLL963pA_MdRfA/edit?gid=1260102982#gid=1260102982
- See `../references/pm-standards.md` for full standards

## Workflow

### Step 1: Scope the Review

**Ask user:**
```
Review scope:
1. Full team (all 3 PMs) — weekly scorecard
2. Specific PM — deep dive
3. Just OKR contribution check

Which PM names should I track? [Confirm names if not already known]
Time window: This week / Last week / Last 30 days
```

**⚠️ STOP:** Confirm scope before pulling data.

### Step 2: Pull Data Per PM

For each PM in scope:

**A. Customer Meeting Cadence:**
- Search Glean/Google Calendar for customer meetings this week: `from:[PM email] customer meeting site:calendar`
- Search Slack for messages from PM mentioning customer names/meetings
- Count confirmed external customer meetings (not internal syncs)
- Target: ≥ 4/week. Flag if < 4.

**B. Meeting Notes Compliance:**
- Search Google Drive folder (https://drive.google.com/drive/folders/1_0K6mAf1EeCuOhixDhABGOIOSEbf8JTu) for notes filed by this PM in the last 7 days
- Check: notes present for each customer meeting? Filed within 48h?
- Flag: missing notes, stale notes (filed > 48h after meeting), notes with no action items

**C. Document Health:**
- Search Glean Jira for open PLTs/PRDs assigned to this PM
- Check: any docs that are stale (no update in > 2 weeks)? Any blocked PRDs? Any docs scheduled for leadership review without a clear draft?

**D. OKR Contribution:**
- **Load** the OKR spreadsheet: https://docs.google.com/spreadsheets/d/1QQqcGUp9o2ebb3j-UCjXP3fQBXVMgzLL963pA_MdRfA/edit?gid=1260102982#gid=1260102982
- Identify OKR items owned by or contributed to by this PM
- Check status: on track / at risk / behind
- Flag: any OKR item this PM owns that is Yellow or Red with no recent update

### Step 3: Generate Team Scorecard

**Format:**

```markdown
## Team Health Scorecard — [Date Range]

### [PM Name 1]
| Dimension | Status | Detail |
|---|---|---|
| Customer meetings this week | 🟢 5/4 | Met with Cisco, ServiceNow, DoorDash, Medtronic, Red Bull |
| Notes compliance | 🟡 3/5 filed | Missing notes for 2 meetings |
| Document health | 🔴 PRD-X stale 3 weeks | No update since [date] |
| OKR contribution | 🟢 On track | KR2.1 shipping on time |

**Coaching nudge:** [Specific, actionable feedback — not generic]

### [PM Name 2]
...

### [PM Name 3]
...

### Team Aggregate
- Customer meeting rate: X/Y PMs meeting ≥4/week target
- OKR items at risk: N of M items are Yellow/Red
- Top area risk: [Single most important team-level issue to address]
```

### Step 4: Identify Action Type

For each flagged item, type the action:
- **(A) Coaching conversation** — address 1:1 with PM
- **(B) Unblock now** — Raja needs to intervene directly (e.g., escalate blocked doc)
- **(C) Process reminder** — nudge to the team broadly (e.g., notes reminder)
- **(D) Escalate up** — issue is area-level risk requiring leadership awareness

**M5 lens check:** Before presenting — does this scorecard reveal an *area-level pattern* (e.g., 2/3 PMs have low customer cadence = area losing customer signal)? If yes, flag it explicitly as an area risk.

## Stopping Points

- ✋ After Step 1: Confirm PM names and time window
- ✋ After Step 3: Review scorecard before adding coaching nudges
- ✋ Ask: "Do you want me to draft a 1:1 agenda or coaching note for any flagged PM?"

## Output

Team scorecard with per-PM status, coaching nudges, and typed action list.
