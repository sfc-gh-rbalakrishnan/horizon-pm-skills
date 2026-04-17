---
name: raja-cos-doc-review
description: "Product document gap analysis. Reviews PRDs, QBR slides, strategy docs, and exec communications before they go up. Use when: reviewing a PRD, catching gaps before leadership, reviewing before sending to CK/Baris/William, QBR slide review. Triggers: review this, catch gaps, PRD review, before I send, before presenting, doc review, review this PRD, review this doc."
parent_skill: raja-cos
---

# Doc Review — Catch Gaps Before They Escalate

Structured gap analysis tuned to document type. Checks both content quality and M5 framing (does this reflect strategic thinking, or just status reporting?).

## Workflow

### Step 1: Intake

**Ask user:**
```
1. Doc URL or paste the content here
2. Document type:
   a) PRD
   b) QBR slide / OKR update
   c) Strategy / Heilmeier doc
   d) Launch plan / release note
   e) Exec email or Slack message
   f) Other
3. Who is the intended audience? (e.g., CK, Baris, William, engineering partner, all-hands)
4. When does it go out / get presented?
```

**⚠️ STOP:** Confirm doc type and audience before analysis.

### Step 2: Load the Doc

- If URL: use `mcp_glean_read_document` to fetch content
- If pasted: use directly
- If Google Slides: request a text export or screenshot

### Step 3: Apply Doc-Type Gap Analysis

**A. PRD:**
- [ ] Is the problem statement grounded in customer evidence? (named accounts, N=, or % signal)
- [ ] Is there a clear "why now" (urgency beyond "customers want it")?
- [ ] Is the success metric observable and binary (not "improve experience")?
- [ ] Is competitive context addressed? (what does Databricks/Collibra do here?)
- [ ] Is scope explicitly bounded? (what is OUT of scope)
- [ ] Is there a JTBDs section with validated job stories?
- [ ] Are CUJs present and validated (≥2 customer walk-throughs)?
- [ ] Does it land a point of view, or just describe options?

**B. QBR Slide / OKR Update:**
- [ ] Is OKR alignment explicit? (which KR does each bullet serve?)
- [ ] Is every Green/Yellow/Red grade defensible with evidence?
- [ ] Are risks surfaced proactively (not just at-risk items buried)?
- [ ] Is there a "so what" for leadership (impact, not just progress)?
- [ ] Is the narrative arc clear: where we were → what happened → where we're going?
- [ ] Are any surprises that would embarrass you in the room missing?

**C. Strategy / Heilmeier Doc:**
- [ ] Does it name the specific problem (not a category)?
- [ ] Is the "why Snowflake" section specific and differentiated (not generic cloud story)?
- [ ] Is the competitive risk table present and honest?
- [ ] Are success metrics binary and time-bound?
- [ ] Does it make a recommendation, or just list options?

**D. Launch Plan / Release Note:**
- [ ] Is the customer value proposition in the first sentence?
- [ ] Are GA criteria documented (not just "when eng says ready")?
- [ ] Is a rollback plan present for P0 risks?
- [ ] Is the support enablement checklist complete?

**E. Exec Email / Message:**
→ **Load** `../references/m5-calibration.md` before evaluating
- [ ] Does it lead with strategic insight, not status?
- [ ] Is there a single clear ask or recommendation?
- [ ] Is it ≤ 5 sentences (for Slack) or ≤ 3 bullets (for email)?
- [ ] Does it anticipate the exec's most likely question?
- [ ] Would this embarrass you if forwarded to the next level up?

### Step 4: Output Gap Report

```markdown
## Doc Review: [Title] | Audience: [Name] | [Date]

### Gap Summary
🔴 Blocking: N issues (must fix before sharing)
🟡 Important: N issues (should fix if time allows)
🟢 Style/polish: N issues (nice to have)

### 🔴 Blocking Gaps
1. [Gap] — [Why it matters] — [Suggested fix]

### 🟡 Important Gaps
1. [Gap] — [Suggested fix]

### 🟢 Polish
1. [Suggestion]

### M5 Check
[Does this doc establish strategic thinking and a point of view?
Or does it report status?
Specific reframe suggestion if needed.]

### Recommended Edit
[If ≤3 blocking gaps: offer to draft the fix inline]
```

### Step 5: Draft Fixes (if requested)

**Ask:** "Do you want me to draft the fix for any of the blocking gaps inline?"

If yes: rewrite only the flagged sections. Do not rewrite the whole doc.

## Stopping Points

- ✋ After Step 1: Confirm doc type before analysis
- ✋ After Step 4: Present gap report before drafting fixes

## Output

Gap report with typed priorities, M5 check, and optional inline fix drafts.
