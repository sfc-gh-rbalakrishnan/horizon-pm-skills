---
name: raja-cos-okr-qbr
description: "OKR progress tracking and QBR preparation. Reads from the Horizon OKR spreadsheet and Northstar dashboard. Generates G/Y/R grades, executive narrative, and QBR-ready bullets. Use when: checking OKR status, generating OKR report, preparing for QBR, quarterly review prep, checking how we are tracking. Triggers: OKR, QBR, quarterly progress, how are we tracking, OKR update, northstar, OKR report, quarterly review."
parent_skill: raja-cos
---

# OKR / QBR — Progress Tracking & Executive Narrative

Pulls current OKR status from source-of-truth systems and generates G/Y/R grades, risk flags, and QBR-ready narrative. Also surfaces OKR contribution per PM for team accountability.

## Data Sources

- **OKR Spreadsheet (source of truth):** https://docs.google.com/spreadsheets/d/1QQqcGUp9o2ebb3j-UCjXP3fQBXVMgzLL963pA_MdRfA/edit?gid=1260102982#gid=1260102982
- **Northstar Dashboard:** https://app.snowflake.com/sfcogsops/snowhouse_aws_us_west_2/#/streamlit-apps/SNOWSCIENCE.STREAMLIT_APPS.NORTHSTAR

## Workflow

### Step 1: Scope the Request

**Ask user:**
```
Mode:
1. Quick check — current G/Y/R status summary
2. Full OKR report — complete narrative with evidence
3. QBR prep — slides-ready bullets + risks + asks
4. Team OKR contribution — which PM owns what and how they're tracking

Also: Should I fetch the latest OKR targets from you, or use whatever is in the spreadsheet?
(OKR numbers change quarterly — confirm the current targets)
```

**⚠️ STOP:** Confirm mode before proceeding.

### Step 2: Pull OKR Data

1. **Read the OKR spreadsheet** using `mcp_glean_read_document` on the URL above. Pull: Objective text, KR text, KR owner, current value, target value, and status (G/Y/R).

2. **If asked about Northstar dashboard metrics**, open the dashboard URL and read the current values for area-relevant metrics.

3. **If OKR numbers are unclear or outdated**, ask user: "Can you confirm the current targets for [specific KR]?" — do not invent numbers.

4. **Cross-reference with Jira**: For KRs tied to PLT delivery milestones, search Jira for the linked PLTs and check their current status/TED.

### Step 3: Grade Each KR

Apply this grading rubric:

| Grade | Criteria |
|---|---|
| 🟢 Green | On track — current progress % ≥ expected % for this point in quarter AND no blocking risks |
| 🟡 Yellow | At risk — behind pace OR has a known blocker OR TED slipping but recoverable |
| 🔴 Red | Off track — significantly behind, blocker not resolving, or TED already past |

For each KR:
```
KR[N]: [KR text]
Owner: [PM name]
Current: [value] / Target: [value] ([X%])
Grade: 🟢/🟡/🔴
Evidence: [PLT ticket, data point, or named source]
Risk: [If Y/R: what is the specific risk]
Mitigation: [If Y/R: what is the recovery path]
```

### Step 4: Generate the Output (mode-specific)

**Mode 1 — Quick check:**
```markdown
## OKR Snapshot — [Date]
Objective: [Title]
🟢 N KRs on track  |  🟡 N at risk  |  🔴 N off track

KR1 [🟢] — [brief status]
KR2 [🟡] — [brief status + risk in one line]
...
```

**Mode 2 — Full OKR Report:**
```markdown
## OKR Report: [Objective Title] | Q[N] FY[YY] | [Date]

### Executive Summary
[2-3 sentences: overall trajectory, biggest risk, and what we need to land]

### KR Progress
[Full grade table with evidence and mitigation per KR — see Step 3 format]

### Top 3 Risks
1. [Risk] — [Impact if not resolved] — [Action owner] — [Timeline]
2. ...

### Asks / Decisions Needed
[Anything requiring leadership input to unblock a 🟡 or 🔴 KR]
```

**Mode 3 — QBR Prep:**
```markdown
## QBR Bullets — [Objective Title]

### What We Set Out to Do
[One-sentence objective framing]

### What We Delivered
- ✅ [KR1 green: specific achievement, with number]
- ✅ [KR2 green: ...]

### What's At Risk
- ⚠️ [KR3 yellow: what happened, why, what we're doing]

### What We Need
[Asks from leadership — be specific: decision / unblock / resource]

### Strategic Insight
[M5 lens: what does this quarter's progress tell us about the area strategy?
Are we validating the right bets? What should we do differently next quarter?]
```

**Mode 4 — Team OKR Contribution:**
```markdown
## OKR Contribution by PM — [Date]

| PM | KRs Owned | Status | Risk |
|---|---|---|---|
| [PM 1] | KR1, KR3 | 🟢 KR1, 🟡 KR3 | KR3 blocker: [detail] |
| [PM 2] | KR2 | 🟢 | None |
| [PM 3] | KR4, KR5 | 🔴 KR4, 🟢 KR5 | KR4 TED already past |

Coaching priority: [PM name] — KR[N] needs intervention
```

### Step 5: M5 Lens Check

Before presenting any report, add:
```
M5 Lens: [Does this progress confirm or challenge our area strategy?
What should we do *differently* next quarter based on what we learned?
What's the insight that only the area leader can see from this data?]
```

## Stopping Points

- ✋ After Step 1: Confirm mode and whether to validate OKR targets with user
- ✋ After Step 2: If any OKR targets are unclear, pause and ask user to confirm numbers
- ✋ After Step 4: Present report before adding M5 lens

## Output

OKR status report or QBR bullets, graded with evidence, in the requested format.
