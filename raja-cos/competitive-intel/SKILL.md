---
name: raja-cos-competitive-intel
description: "Proactive competitive monitoring for Data & AI Governance. Tracks Databricks Unity Catalog, Collibra, Alation, Monte Carlo, Atlan, and Microsoft Purview. Generates action-typed responses. Use when: checking competitive landscape, researching a competitor, responding to competitive threat, updating roadmap based on competition. Triggers: competitive, what is Databricks doing, Collibra update, Alation, Monte Carlo, Atlan, Purview, competitive threat, competitive action, competitive landscape, market update."
parent_skill: raja-cos
---

# Competitive Intel — Data & AI Governance Watchlist

Proactive competitive monitoring for the 6 primary competitors in the Data & AI Governance space. Every output ends with typed actions (not just information).

## Watchlist

| Competitor | Area | Primary threat to |
|---|---|---|
| Databricks Unity Catalog | Data governance / catalog / lineage | Horizon Catalog, Lineage, Classification |
| Collibra | Enterprise data governance | Catalog, Policy, Access |
| Alation | Data catalog and governance | Catalog, Search, Semantic Views |
| Monte Carlo | Data observability / quality | Data Quality, DMF |
| Atlan | Active metadata / modern governance | Catalog, Discovery, Collaboration |
| Microsoft Purview | Azure-native data governance | Classification, Policy, Cross-cloud |

## Workflow

### Step 1: Scope the Query

**Ask user:**
```
1. Specific competitor: [Name]  OR  "full landscape sweep"
2. Focus area: product announcements / pricing / customer wins / partnerships / all
3. Time window: last 7 days / last 30 days / last quarter
4. Why are you asking? (customer asked / roadmap decision / exec question / proactive monitoring)
```

**⚠️ STOP:** Confirm scope before research.

### Step 2: Research

**For each competitor in scope, run in parallel:**

1. **Web search** (use web_search tool): `"[Competitor] product announcement [month year]"` and `"[Competitor] data governance new feature [year]"`

2. **Glean internal search**: `[Competitor] competitive analysis` — look for internal decks, battlecards, or Slack discussions

3. **Glean Slack**: Search for recent mentions of the competitor in product and field channels

4. **Customer signal**: Search Glean for any customer feedback mentioning the competitor (e.g., "customer said they're evaluating Collibra")

**Collect per competitor:**
- What's new (last 30 days): product announcements, pricing changes, partnerships
- What customers are saying: evaluation, switching signals, comparisons
- What Snowflake's current response is: battlecard status, known differentiators

### Step 3: Synthesize

**For each competitor with notable changes:**

```markdown
### [Competitor Name]
**What changed:** [1-2 sentences — specific announcement or move]
**Source:** [URL or internal doc, date]

**Why it matters to our roadmap:**
[Which Horizon feature area is most affected?
Does this close a gap we had? Open a new gap?
Does it change customer conversations in the next 90 days?]

**Customer impact:**
[Are any current customers evaluating this? Any at-risk signals?]

**Snowflake's current position:**
[What's our differentiated answer today? Where are we behind?]
```

### Step 4: Recommend Typed Actions

For each material change, assign an action type:

| Type | Description | Example |
|---|---|---|
| **(A) Communicate now** | Field/SEs need to know this week | Update battlecard, send to #competitive-intelligence |
| **(B) Roadmap note** | Affects upcoming planning cycle | Add to area roadmap review input |
| **(C) Customer talking point** | At-risk customer needs a response | Draft message for AE to send |
| **(D) Exec escalation** | Leadership needs to know (major threat) | Summarize for Baris/William |
| **(E) Monitor** | Watch but no action yet | Revisit in 30 days |

**M5 lens:** For any (B) or (D) action, frame as: "This changes our 12-month strategy because [specific reason]" — not just "they shipped a feature."

### Step 5: Generate Communication (if Action A or C)

**If (A) — field communication:**
Draft a short Slack message for #competitive-intelligence or #[relevant channel]:
```
🔍 Competitive Update — [Competitor]: [Date]
[What happened in 1 sentence]
[Why it matters to customer conversations]
[Recommended talking point or battlecard link]
cc: @[SE lead] @[Field lead]
```

**If (C) — customer talking point:**
Draft a message for the AE to send to the at-risk customer:
```
[Personalized opening]
[Acknowledge competitive context without being defensive]
[Snowflake's differentiated value in 2-3 sentences]
[Clear next step]
```

## Stopping Points

- ✋ After Step 2: Present raw research before synthesis (especially if limited data found)
- ✋ After Step 4: Confirm action types with user before drafting communications

## Output

Competitive summary per competitor + typed action list + optional draft communications.
