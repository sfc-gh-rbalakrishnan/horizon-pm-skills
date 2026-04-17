---
name: raja-cos-morning-brief
description: "Daily PLT audit and PFM meeting readiness check. Use when: starting the day, checking PLT health, preparing for PFM meeting. Triggers: good morning, morning brief, PLT check, PFM meeting, daily briefing, start my day."
parent_skill: raja-cos
---

# Morning Brief — PLT Health & PFM Readiness

Audits all PLT Jira tickets against required fields and flags issues before the next PFM meeting (bi-weekly, every other Monday).

## Context

**PFM Meeting:** Bi-weekly, every other Monday. All PLTs reviewed for status, TED, and Green/Yellow/Red health by leadership.

**Required fields for each PLT** (from the standard reporting checklist):
1. Project Status (Green / Yellow / Red)
2. Project Status Note
3. Target End Date (TED)
4. Target Availability
5. Feature Tier
6. Launch Event
7. Customer Commitment
8. Committed Delivery Date
9. Available Clouds
10. Available Geo Regions

## Workflow

### Step 1: Fetch PLT Jiras

**Actions:**

1. **Search** Jira for all PLT project tickets that are active/in-flight. Use `mcp_glean_search` with `app: jira` and query: `"PLT project:PLT status != Done"`. Also search `"PLT assignee:rbalakrishnan OR PLT horizon governance"` to capture team tickets.

2. **Parse** each ticket and collect: ticket key, summary, assignee, Project Status, Project Status Note (and its last-updated date), Target End Date, Target Availability, Feature Tier, Launch Event, Customer Commitment, Committed Delivery Date, Available Clouds, Available Geo Regions.

3. **If Glean Jira search returns insufficient detail**, ask user: "Should I open the Jira dashboard directly, or do you want to paste the PLT ticket list here?"

**Output:** Raw list of PLT tickets with field values.

### Step 2: Apply Health Rules

For each PLT ticket, apply these checks in order:

**🔴 CRITICAL — Immediate action required:**
- TED is **in the past** AND Project Status Note was not updated within the last **7 days**
- Any of the 10 required fields is **completely missing** (null/empty)
- Project Status is **Red** with no status note

**🟡 WARNING — Action needed before next PFM:**
- TED is **within 14 days** AND Project Status Note not updated within the last **7 days**
- Project Status is **Yellow** with no status note updated in the last **7 days**
- Target Availability, Feature Tier, or Launch Event is missing while TED is within 30 days
- Customer Commitment or Committed Delivery Date is missing on a customer-committed PLT

**🟢 GREEN — No action needed:**
- All 10 fields present, Project Status Note updated within the last 7 days, TED is more than 14 days out

**Output per ticket:**
```
[STATUS] PLT-XXXX: [Summary] | Assignee: [Name]
  Issues: [list of specific field gaps or rule violations]
  Last status note: [date]
  TED: [date] ([X days away / X days overdue])
```

### Step 3: Generate PFM Readiness Report

**Compute:**
- Days until next PFM meeting (next Monday on the bi-weekly cycle — ask user to confirm if uncertain)
- Count: 🔴 Critical / 🟡 Warning / 🟢 Green tickets

**Format the report:**

```markdown
## PLT Health — [Today's Date] | Next PFM: [Date] ([N days away])

### Summary
🔴 Critical: N  |  🟡 Warning: N  |  🟢 Green: N

### 🔴 Critical — Fix Before PFM
[PLT-XXXX] [Summary] — [specific issue]
  Action: [Exact field to update / note to write]

### 🟡 Warning — Should Fix Before PFM
[PLT-XXXX] [Summary] — [specific issue]
  Action: [Exact field to update]

### 🟢 Green — No Action Needed
[PLT-XXXX] [Summary] ✓
```

### Step 4: Draft Status Note Templates (if requested)

**Ask:** "Do you want me to draft a status note update for any of the 🔴 or 🟡 PLTs?"

If yes, for each selected PLT:
- Ask: "What's the current state in one sentence?"
- Draft a status note in the standard format:
  ```
  [Date] — [Status]: [What's complete]. [What's in progress]. [Blocker if any]. 
  TED [on track / at risk / slipping to X] because [reason].
  ```

## Stopping Points

- ✋ After Step 2: Present health summary to user before generating full report
- ✋ After Step 3: Ask if status note drafts are needed

## Output

A PFM-ready PLT health report with:
- Color-coded ticket list with specific field gaps
- Prioritized action list (what to fix today vs. this week)
- Optional: draft status notes for flagged tickets
