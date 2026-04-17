---
name: raja-cos-customer-prep
description: "Customer meeting preparation. Generates pre-reads with account history, feature usage, open asks, and strategic framing. Use when: prepping for a customer call, before a customer meeting, generating a pre-read. Triggers: prep for, customer meeting, customer call, pre-read, before meeting with."
parent_skill: raja-cos
---

# Customer Prep — Meeting Pre-Read

Generates a structured pre-read before any customer meeting. Adds M5-level strategic angle beyond standard account context.

## Workflow

### Step 1: Gather Inputs

**Ask user:**
```
Customer name: [Account name]
Meeting type: Discovery / Check-in / EBC / QBR / Escalation / Other
Who's attending from Snowflake? [Your name + others]
Is this meeting for you directly, or are you prepping a PM on your team?
Any specific topics or known issues to address?
```

**⚠️ STOP:** Confirm inputs before researching.

### Step 2: Research the Account

**Search in parallel:**

1. **Glean — Internal signals:**
   - Search `[Customer name] Snowflake Intelligence feedback` in Slack
   - Search `[Customer name] meeting notes` in Google Drive
   - Search `[Customer name]` in Jira for open tickets/requests

2. **Snowflake Intelligence (SI):**
   - Ask SI: "What is [Customer name]'s usage of [relevant product area] in the last 90 days?"
   - Ask SI: "What are the top feature requests or issues for [Customer name]?"

3. **Glean — Recent comms:**
   - Search for recent emails or Slack threads mentioning the customer

**Compile:**
- Account tier and key contacts
- Current products in use (focus on Data & AI Governance area)
- Known pain points and open asks
- Recent wins or incidents
- Prior meeting notes summary

### Step 3: Generate Pre-Read

**Structure:**

```markdown
## Pre-Read: [Customer Name] — [Meeting Type] | [Date]
**Attending:** [Names] | **Duration:** [X min]

### Account Snapshot
- Tier: [T1/T2/T3] | Primary AE: [Name] | SE: [Name]
- Products in use: [List]
- Relationship health: [Green/Yellow/Red with brief rationale]

### Their Top 3 Asks / Open Items
1. [Ask] — Status: [open/in progress/shipped] | Source: [Jira/Slack/prior meeting, date]
2. [Ask] — Status: ...
3. [Ask] — Status: ...

### What's Changed Since Last Meeting
- [Product update, shipped feature, or incident] — [date]
- [Competitive move they may be aware of]

### Recommended Agenda (suggested)
1. [Topic + time] — goal: [what we want to learn or achieve]
2. [Topic + time]
3. [Topic + time]

### Talk Track Notes
[Key messages to land, objections to anticipate, questions to ask]

### Strategic Angle (M5 lens)
[What does this customer relationship mean for the area roadmap?
What signal from this meeting could validate or invalidate a roadmap bet?
What would a strategic win look like beyond this single meeting?]
```

### Step 4: If Prepping a Team PM

**Add a coaching note:**
```markdown
### Coaching Note for [PM Name]
- Emphasize: [specific thing to land]
- Watch out for: [common pitfall or known sensitivity]
- Bring back signal on: [specific hypothesis we need validated]
- M5 tip: Don't just take the meeting — frame one agenda item as a hypothesis test
```

## Stopping Points

- ✋ After Step 1: Confirm customer name and meeting type before research
- ✋ After Step 3: Present pre-read for review before the meeting

## Output

A pre-read document saved to `<workspace>/pre_read_[customer]_[date].md`
