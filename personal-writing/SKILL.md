---
name: personal-writing
description: "Raja's personal writing standard. Apply to ALL written output — docs, emails, Slack messages, PRDs, strategy docs, exec briefs, and any other communication. Use when: writing anything, reviewing any draft, checking tone/framing, fixing a doc, writing an email to leadership, calibrating Director-level voice. Triggers: write this, draft this, review my writing, does this sound right, check this, polish this, how does this read, is this M5, rewrite this."
---

# Personal Writing Standard — Raja Balakrishnan

Apply every rule below to every piece of writing. This is a zero-tolerance standard, not a checklist to partially follow.

---

## Hard Rules — Never Violate

**R1 — No em dashes or double hyphens**
Never use `—`, `--`, or `–` in any sentence. Use a comma, colon, or restructure the sentence.
- ❌ "We launched this feature — customers responded well"
- ✅ "We launched this feature and customers responded well."
- ✅ "We launched this feature: customers responded well."

**R2 — Never justify by executive ask**
Never write that a decision was made because executives asked, will ask, or because it looks good to leadership.
- ❌ "We are tracking this separately because executives will ask about it"
- ❌ "This is indefensible in exec review" / "hard to defend" / "executive scrutiny"
- ✅ State the reason in terms of what is correct for Snowflake and for customers.

**R3 — No defensive or moralistic language**
Never use "honest," "defend," "justify," or "transparent" when explaining a metric or decision. State the model plainly. It speaks for itself.
- ❌ "To be honest about our measurement approach..."
- ✅ "Here's how the measurement works and why it's structured this way."

**R4 — No "management"**
Never write "management has decided," "management wants," or any phrasing that makes it sound like someone else is calling the shots.
- ❌ "Management has set a target of 25%."
- ✅ "We are targeting 25%." / "A 25% growth rate is within reach."

**R5 — No pedagogic tone**
Never over-explain or lecture the reader. State the model, state why, move on. If it takes two paragraphs to explain something simple, simplify it.

**R6 — Never use "deliberate"**
Avoid "deliberate steps," "deliberate action," or similar constructions.
- ❌ "Until customers take deliberate action to enable governance"
- ✅ "Until customers review and take action" / "steps customers need to take"

**R7 — No trial accounts in senior leader or executive documents**
Only Enterprise and Business Critical accounts (and Standard where specifically relevant) are in scope. Never mention trial accounts in documents prepared for senior leaders or executives.

**R8 — No unverified data claims**
Every number, percentage, or market claim must come from a verified source. If unverified, mark it `[UNVERIFIED]` or cut it. Do not round or estimate silently.

**R9 — No conditional framing**
Do not hedge a proposal with "if approved," "if this moves forward," or "pending alignment."
- ❌ "If approved, this would allow us to..."
- ✅ "This allows us to..." (the document is the ask — write with conviction)

---

## Framing Principles

**F1 — Proposal vs. execution framing**
If the initiative is still being proposed, say so explicitly. A proposal asks for a decision; an execution document reports on one.
- ❌ "We are auto-enabling governance features across Enterprise accounts."
- ✅ "We are proposing to auto-enable governance features across Enterprise accounts."

**F2 — Lead with the insight, not the context**
The first sentence must carry the key message. Leadership skims. If the point is buried in bullet 3, it will not land.
- Ask before sending: "If the reader stops after the first sentence, did they get the key point?" If no, rewrite the opening.

**F3 — Lead with wins, not deficiencies**
When current performance is strong, frame problems as opportunities to build on momentum.
- ❌ "Growth is only 18% per quarter. We are below target."
- ✅ "Governance AUM is growing and exceeding targets. The opportunity is to accelerate further."

**F4 — Customer problem before business metric**
Open with customer pain or friction first. Business metrics and growth targets come second.
- ❌ "Our metric growth is slower than target. Customers also experience friction with..."
- ✅ "Customers [specific friction]. This creates a growth opportunity: [metric]."

**F5 — "What's right" beats "what looks good"**
When exec optics conflict with what is correct for Snowflake, always choose correct. Frame accordingly.

**F6 — Framing over wording**
The core issue in most weak documents is the mental model, not the prose. Fix the framing first; line edits come last.

**F7 — Structural changes before line edits**
If a document needs to be merged, restructured, or reframed, do that before any wording changes.

---

## Precision & Specificity

**P1 — Specificity is credibility**
Vague claims signal noise. Named accounts, dates, and numbers signal signal.
- ❌ "Customers have shared concerns about this."
- ✅ "Three T1 accounts (Cisco, ServiceNow, Adobe) raised this in the last 30 days."

**P2 — Name features precisely**
Never use umbrella terms without defining the specific capability. "Auto-governance," "security features," and "AI capabilities" are not feature names.
- ❌ "Auto-governance will scan customer data."
- ✅ "Automatic metadata-based data security monitoring will scan customer schemas for sensitive column patterns."
- Ask: "Could a reader outside my team misinterpret this term?" If yes, replace it.

**P3 — Be precise about distinctions**
Name the exact distinction, not a proxy.
- ❌ "Should auto-enabled objects count alongside customer-governed assets?" (implies different objects)
- ✅ "The objects are the same. The question is whether governance is auto-enabled by Snowflake or actively enabled by the customer."

**P4 — Option descriptions must establish baseline**
Before describing any option, state what the current state is.
- ❌ "Option A: Count auto-governed and customer-governed assets together."
- ✅ "Option A: Expand the current AUM measure — which counts only assets on which a customer has actively taken a governance action — to also include auto-governed objects."

**P5 — Requirements must be scoped**
Requirements must reference real teams, real fiscal years, and real constraints. Never write a generic requirement.
- ❌ "Achievable within the current engineering roadmap"
- ✅ "Achievable within the engineering resourcing available for Data Governance in FY27"

**P6 — Numbers must match scope**
If Phase 1 targets a subset of accounts, cite Phase 1 numbers. Do not cite all-account statistics when the scope is narrower.

**P7 — Concrete example for every abstract concept**
Every abstract concept must have exactly one concrete illustration inline.
- ❌ "Semantic Views encode business logic in a reusable definition."
- ✅ "Semantic Views encode business logic — for example, a Semantic View defines 'revenue' so SQL, a BI dashboard, and a Cortex Analyst agent all calculate it identically."

---

## Structural Rules

**S1 — One ask per communication**
Multiple asks equal no action. Pick the most important one. If you need a decision, an approval, and a resource, send the highest-priority ask.

**S2 — Three bullets maximum for executive communication**
For Slack or async upward communication: ≤3 bullets, ≤3 sentences of body. More signals you have not prioritized.

**S3 — Separate co-located proposals**
If a document contains two distinct proposals, state them sequentially and explicitly. Never blend them in a single sentence or paragraph.
- ✅ "Proposal 1 — What we are enabling: [X]. Proposal 2 — The measurement question this creates: [Y]."
- ❌ "We are proposing X, which creates a measurement question about Y." (blends two decisions)

**S4 — Title telegraphs the recommendation**
The title names the decision and hints at the answer. Avoid vague nouns.
- ❌ "Auto-Governance Success Metrics"
- ✅ "Auto-Governance Proposal: How to Measure Success Without Inflating the Metric"

**S5 — Make a point of view**
Every document must recommend, not just list options and leave the decision to the reader.

**S6 — Keep companion use cases out of senior leader docs**
Do not mention adjacent use cases (data observability, AI guardrails, etc.) in executive or senior leader documents unless the audience is specifically there for that topic. One sentence acknowledging the pattern is extensible is sufficient.

---

## Director-Level (M5) Standards

These separate a sharp Director-level communicator from a Senior IC.

| M4 pattern (avoid) | M5 rewrite (use) |
|---|---|
| Reports what happened | Explains what it means for 12-month strategy |
| Lists accomplishments | Connects accomplishments to business outcomes |
| Asks for permission | Makes a recommendation and asks for alignment |
| "There are some concerns about..." | "We have a problem: [specific]. Here's the mitigation." |
| "There are a few options we could consider..." | "I recommend [option]. Here's why." |
| "Customers have shared feedback that..." | "3 T1 accounts told us in the last 30 days that..." |
| "We want to make sure we're aligned..." | "My ask: confirm by [date] that we're going forward with [X]" |
| "Just following up..." | "I need a decision on [X] by [date] to avoid [consequence]" |
| Shows all the work | Shows the insight — the work is implied |
| Hedges risk | Names the risk, owns it, proposes the mitigation |

**The three self-critique tests — run before every send:**

1. **First-sentence test:** If the reader stops after sentence one, did they get the key point? If no: rewrite.
2. **Skeptical VP test:** Read as a busy VP getting 200 messages a day. Does this earn 30 seconds? If not: tighten.
3. **So-what test:** For each bullet, ask "so what?" If the answer is not obvious, the bullet fails.

---

## Language Preferences

**L1 — Active customer language**
Customers are agents who take action — not passive recipients who react.
- ❌ "until customers have had time to review and respond"
- ✅ "until customers have had time to review and take action"

**L2 — Sharp outcome statements**
Replace generic outcomes with specific user scenarios.
- ❌ "detect issues before they reach the business"
- ✅ "a quality regression in a source table triggers an alert before the downstream dashboard shows wrong numbers"

**L3 — Acronym judgment**
Use acronyms the audience already knows without spelling them out. Only spell out acronyms unfamiliar to the specific audience.
- If writing for the Governance team: AUM, DMF, RBAC need no explanation.
- If writing for cross-functional execs: spell out on first use.

**L4 — Product-led framing**
Auto-enablement narratives show Snowflake acting, not the field team enabling customers.
- ❌ "The field team will work with customers to enable governance features."
- ✅ "Snowflake automatically enables governance features. Customers review and act on what the agent surfaces."

**L5 — Human-in-the-loop framing**
The correct framing for governance automation: the agent suggests, the customer approves.
- ❌ "Snowflake auto-classifies customer data and applies tags."
- ✅ "Snowflake surfaces classification suggestions. Customers confirm and apply protections."

---

## Workflow — Writing Review

When asked to review, rewrite, or check any writing:

### Step 1: Diagnose Framing First
Before touching any word, identify the mental model. Is the framing correct? Are proposals framed as proposals? Is the lead-with-wins principle applied?

### Step 2: Flag Hard Rule Violations
Check R1–R9. Any violation must be fixed before any other editing.
- Flag each with: `[Rule R#] → [what was found] → [suggested fix]`

### Step 3: Apply Framing and Precision Checks
Work through F1–F7 and P1–P7. Flag any issue with the same format.

### Step 4: Run M5 Check
Does this communicate at M5 level? Compare against the M4/M5 table.
- If it reads like an M4 status report: identify the one reframe that will most raise the level.

### Step 5: Run Three Self-Critique Tests
First-sentence test, Skeptical VP test, So-what test.

### Step 6: Output
Present findings in this format:

```
## Writing Review

### Hard Rule Violations (fix first)
[R#] [Quoted text] → [Fix]

### Framing Issues
[F#] [Issue] → [Fix]

### Precision Issues
[P#] [Issue] → [Fix]

### M5 Check
[Pass / Reframe needed]
[If reframe: specific rewrite of the weakest sentence]

### Three Tests
- First-sentence test: [Pass / Fail + rewrite]
- Skeptical VP test: [Pass / Fail + why]
- So-what test: [Pass / Fail + which bullet fails]

### Net Assessment
[Sharp / Solid / Needs work] + one sentence on the highest-priority fix.
```

**⚠️ STOP:** Present findings and wait for approval before rewriting the full document.

---

## Stopping Points

- ✋ After Step 2: Present hard rule violations before any rewriting
- ✋ After Step 6: Present full review before executing any changes

## Output

A prioritized writing review with hard rule violations first, framing issues second, M5 calibration, and three self-critique test results.
