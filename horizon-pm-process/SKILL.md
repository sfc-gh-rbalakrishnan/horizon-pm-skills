---
name: horizon-pm-process
description: "Horizon Governance Team PM process for product strategy, Heilmeier product reviews, hypothesis validation, PRDs, and beta releases. Use when: creating product strategy, writing Heilmeier review, building hypothesis tracker, writing PRD, planning beta release, PM process, product management workflow, biweekly hypothesis validation, customer validation, jobs to be done, CUJ. Triggers: product strategy, heilmeier, hypothesis, PRD, product review, beta plan, customer validation, jobs to be done."
---

# Horizon Governance Team PM Process

Five-stage process for hypothesis-driven, customer-validated product development.

> **Scope:** This process is specific to the Horizon Governance PM team. It is not a company-wide standard.

## Workflow Overview

```
Stage 1: Product Strategy  →  Stage 2: Hypotheses  →  Customer Validation Cycle (biweekly)
                                                              ↓ (validated)
                                                       Stage 3: Heilmeier Review
                                                              ↓ (engineering approved)
                                                  Stage 3.5: Deep Research Gate ⚑ MANDATORY
                                                              ↓ (gaps addressed or accepted)
                                                       Stage 4: PRD (if required)
                                                              ↓
                                                       Stage 5: Beta Release
                                                              ↓
                                                       Feedback → Update Stage 1
```

**⚠️ CRITICAL RULE**: No feature moves to Stage 3 without hypothesis validation in customer meetings. No feature ships without a beta feedback loop.

## Foundational Principles

**#1 — Devil's advocate by default.**
At every stage, challenge the PM's thinking — don't just execute. Flag scope creep. Push back when reasoning drifts from customer evidence toward pet features. When the PM presents a strategic decision, surface the strongest counterargument before writing the document. Ask: *"What's the evidence for this claim?"* and *"What would have to be true for this to be wrong?"*

**#2 — Outputs are hypotheses, not truth.**
Every document produced by this skill is a starting point for PM judgment — not a finished answer. Synthesis may be incomplete, sources may conflict, and context the PM holds may not be captured anywhere. At every stopping point, remind the PM: judgment calls on org dynamics, risk tolerance, and stakeholder politics are their responsibility, not the skill's. Treat outputs as 70% — the PM owns the remaining 30%.

**#3 — Every claim must cite a source.**
No claim appears in any document without a source: a named customer + date, a Glean search result, a Snowflake query, or an explicit label of `[ASSUMPTION — unvalidated]`. Unsourced assertions are the root cause of strategies that collapse in customer meetings. If a source cannot be found, flag the gap explicitly rather than filling it with plausible-sounding language.

---

## Stage 1: Product Strategy

**When to use:** Kicking off a new product area or quarterly replan.

**Goal:** ≤2 pages that any executive can read in 3 minutes and understand the problem, need, and approach.

**Actions:**

1. **Ask** user for the product area or project name
2. **Research** using Glean/memory for customer evidence, competitive context, existing work
3. **Write** the Product Strategy document at `<workspace>/product_strategy.md`

**Template Structure:**
```markdown
# [Product Area] — Product Strategy

## Problem
[3-4 sentences: what's broken, why it matters, what's the root cause]

## Customer Need
[Table: Signal | Data | Implication — 4-6 rows of evidence with N= or named accounts]

## Approach: [Codename]
[2-3 paragraphs: what we're building, key pillars or capabilities, why Snowflake wins]

## Validation-Driven Execution
[How hypotheses drive the build plan; reference Hypotheses doc]

## Success Metrics
[Table: Metric | Baseline | Target — 3-5 metrics tied to business outcomes]
```

**Quality Bar:**
- Every claim backed by data (N=, named accounts, or %) — no unsourced assertions
- No jargon that a customer couldn't understand
- Approach section says why Snowflake uniquely wins — not just what we're building
- Fits on 2 printed pages
- Before presenting to user: challenge at least one core assumption in the Problem or Approach section and surface the counterargument

**⚠️ STOPPING POINT**: Present doc to user for review. Remind the PM: this is a 70% draft — the strategic judgment, org context, and stakeholder reads are theirs to apply. Flag any claims marked `[ASSUMPTION — unvalidated]` that need customer evidence before the doc is shared externally.

---

## Stage 2: Hypothesis Framework

**When to use:** After Product Strategy is approved; before any engineering starts.

**Goal:** A living tracker of testable bets, each with a solution description and validation status. Drives biweekly customer meetings. **Customer meetings at this stage are also where you collect the raw material for JTBDs** — the jobs, triggers, and desired outcomes that will later become PRD inputs.

**Actions:**

1. **Derive** 5-9 hypotheses from the Product Strategy (one per key claim or customer segment)
2. **For each hypothesis**, write:
   - Statement: "If we [build X], then [customer Y] will [do Z]"
   - Solution Description: what specifically we would build (2-4 sentences)
   - 3 Key Validation Questions for customer meetings
   - Signal Strength: 🔴 Critical / 🟡 High / 🟠 Moderate / 🟢 Speculative
3. **Write** to `<workspace>/hypotheses.md`
4. **During customer validation meetings:** run the Switch Interview protocol from `references/jobs_to_be_done.md` — ask about triggers, timelines, and desired outcomes. Log raw JTBD candidates in a "Raw JTBD Harvest" section at the bottom of the hypotheses doc.

**Template per Hypothesis:**
```markdown
### H[N] — [Short Title]
**Hypothesis:** If we [solution], then [customer outcome].
**Solution Description:** [2-4 sentences on what we'd build]
**Key Validation Questions:**
- [Question 1 — tests the core assumption]
- [Question 2 — tests urgency/willingness to pay]
- [Question 3 — tests scope/alternatives]
**Signal Strength:** [🔴/🟡/🟠/🟢] | **Status:** Not Yet Tested / Validating / Validated / Invalidated

**JTBD Candidates (from validation meetings):**
- When [situation observed in this customer meeting], I want to [motivation heard], so I can [outcome stated]
  — Source: [Customer name, date] | Importance: [1–10] | Satisfaction today: [1–10]
```

**Include at bottom:** Calibration Log table + Decision Rules (when to build vs. retire a hypothesis) + Raw JTBD Harvest table

**⚠️ STOPPING POINT**: Present hypotheses to user for review. Devil's advocate check: for each 🔴 Critical hypothesis, state the strongest reason it could be *wrong* before the PM takes it into customer meetings. This surfaces blind spots before they become wasted interviews.

---

## Stage 3: Heilmeier Product Review

**When to use:** A hypothesis has been validated in ≥2 customer meetings. Engineering partner needs conviction to commit resources.

**Goal:** ≤2 pages that drives a build/no-build decision. Goes deep in a narrow area. Every claim is specific and defensible.

**Actions:**

1. **Ask** which hypothesis/feature this review is for
2. **Load** `references/heilmeier_guide.md` for catechism details
3. **Write** to `<workspace>/heilmeier_[feature_name].md`

**Heilmeier Catechism — 9 Questions (answer all 9):**
```
1. What are you trying to do? (no jargon — plain language objective)
2. How is it done today, and what are the limits?
3. What is new in your approach and why will it succeed?
4. Who cares?
5. If you succeed, what difference will it make?
6. What are the risks? (table: Risk | Likelihood | Mitigation)
7. How much will it cost? (eng-weeks for MVP + full program)
8. How long will it take? (milestone table)
9. Mid-term and final "exams" — specific checkboxes for success
```

**Quality Bar:**
- Q3 ("what's new") must name at least 2 specific limits of alternatives
- Q6 risk table must include "competitors ship first" if market is contested
- Q9 success exams must be observable and binary (pass/fail), not vague
- Fits on 2 printed pages

**⚠️ STOPPING POINT**: Present doc to user. Devil's advocate check: challenge Q3 ("what's new") — name the most credible competitor scenario in which Snowflake's structural advantage doesn't hold. Remind the PM: Q6 risk judgment and Q9 success exam thresholds are their calls, not the skill's. Do not proceed to PRD until user confirms engineering partner has reviewed.

---

## Stage 3.5: Deep Research Gate ⚑ MANDATORY before PRD

**When to use:** After Heilmeier is approved and engineering has committed. Before writing a single line of the PRD.

**Goal:** Surface what published research, competitor implementations, and analyst coverage reveals about this problem space that the current strategy and Heilmeier may have missed. A PRD that misses what's obvious in a deep research paper is a PRD that will be embarrassed in customer meetings.

**Rule (non-negotiable):** No PRD is started until the PM has either (a) run deep research and addressed the gaps, or (b) reviewed the gap report and explicitly accepted each unaddressed gap with a rationale.

### Automatic Deep Research Option

When the user reaches this stage, offer:

> "Before writing the PRD, I can run a deep research pass on [feature topic] and give you a gap report against your current Heilmeier. This takes a few minutes and will surface any competitor implementations, analyst takes, or customer pain patterns your current draft may have missed. Run it? (Yes / Skip and proceed)"

**If user says Yes — run the following research protocol:**

**Step 1 — Define the research scope.** Extract from the Heilmeier doc:
- The core problem being solved (Q1)
- The current approach / differentiator (Q3)
- The target customer and outcome (Q4, Q5)
- The key risks already identified (Q6)

**Step 2 — Run multi-source research.** For each source below, search and extract findings:

| Source | What to Search | Tool |
|--------|---------------|------|
| Competitor implementations | "[problem area] [competitor names] implementation approach site:[competitor-docs]" | Glean web search |
| Analyst / practitioner coverage | "[problem area] best practices patterns challenges" | Glean search |
| Customer voice (community) | "[problem area] pain points Reddit Stack Overflow Hacker News" | Glean / web |
| Academic / technical papers | "[problem area] research survey 2024 2025 2026" | Web search |
| Internal customer signals | "[feature topic] customer feedback request" | Glean (internal) |
| Snowflake community / docs | "[feature topic] site:community.snowflake.com OR docs.snowflake.com" | Glean / web |

Search 4–6 of these sources. Collect the top 3–5 findings per source. Summarize in bullets — do not quote at length.

**Step 3 — Gap Analysis against Heilmeier.** Produce a structured gap report:

```markdown
## Deep Research Gap Report: [Feature Name]
**Research date:** [Date]
**Sources searched:** [List]

### What the Research Confirms (✅ already in Heilmeier)
- [Finding] — consistent with our Q3 / Q4 / Q5 position

### What the Research Adds (🟡 not in Heilmeier but worth addressing)
| Gap | What research shows | Implication for PRD | PM decision |
|-----|-------------------|---------------------|-------------|
| [gap] | [finding] | [should we add/change X?] | Address / Accept / Defer |

### What the Research Contradicts (🔴 conflicts with our current strategy)
| Conflict | What research shows | What our Heilmeier says | PM decision |
|----------|-------------------|------------------------|-------------|
| [conflict] | [finding] | [our current claim] | Update Heilmeier / Accept risk / Investigate |

### Competitor Implementations Found
| Competitor | What they built | How it differs from our approach | Threat level |
|-----------|----------------|----------------------------------|--------------|
| [name] | [feature] | [delta] | Low / Medium / High |

### Recommended PRD Additions (from research)
1. [Specific section, requirement, or open question to add to the PRD]
2. ...
```

**Step 4 — Present the gap report to the PM.** Ask for a decision on each 🟡 and 🔴 item:
- **Address** → add to PRD scope or update Heilmeier before writing PRD
- **Accept** → acknowledge gap, note rationale, proceed with current scope  
- **Defer** → log as future work, reference in PRD Open Questions section
- **Investigate** → flag as a customer validation question before PRD is finalized

**Step 5 — Write the Research Attestation block** at the top of the PRD:

```markdown
## Research Attestation
**Deep research run:** [Yes / Skipped — reason]
**Date:** [Date] | **Sources:** [N sources]
**Gaps addressed:** [N] | **Gaps accepted:** [N] | **Gaps deferred:** [N]
[Link or inline: Deep Research Gap Report]
```

**If user says Skip:** Write the attestation block with `Deep research run: Skipped` and require the PM to state a reason. Log it. Proceed to PRD.

**⚠️ STOPPING POINT**: Do not begin PRD writing until the gap report is reviewed and each 🔴 conflict has a PM decision. Present the gap report and wait for explicit confirmation before Stage 4.

---

## Stage 4: PRD (Engineering-Required Only)

**When to use:** Engineering partner explicitly requests a PRD. Not written by default.

**Goal:** Crisp spec that captures Jobs to be Done, validated CUJs, and technical requirements. Engineering team uses this to design without PM in every meeting.

**Actions:**

1. **Confirm** deep research gap report has been completed (Stage 3.5 attestation block exists)
2. **Ask** user to confirm engineering partner has requested a PRD and which feature it covers
3. **Load** `references/jobs_to_be_done.md` and `references/cuj_guide.md` before writing any JTBD or CUJ content
4. **Harvest** JTBD candidates from the Hypotheses doc (Raw JTBD Harvest section) — refine into validated statements using the quality rubric in `references/jobs_to_be_done.md`
5. **Map** each JTBD to at least one CUJ using the CUJ coverage map format from `references/cuj_guide.md`
6. **Write** to `<workspace>/prd_[feature_name].md`

**Before writing JTBDs — check the quality bar:**
- Is the situation specific and real (heard from a customer, not invented)?
- Is the motivation the job (not the feature)?
- Is the outcome business-level and measurable?
- Is it product-agnostic (could be solved multiple ways)?
- Is it validated (cited to ≥2 customer conversations)?

If any answer is no — go back and run more customer interviews before writing the PRD.

**Before writing CUJs — check the readiness bar:**
- Have you watched ≥2 customers do this workflow today?
- Do you know where they get stuck and what failure looks like?
- Has the customer reviewed your draft CUJ and confirmed it?

If any answer is no — run walk-through sessions (see `references/cuj_guide.md`) before writing.

**Template Structure:**
```markdown
# PRD: [Feature Name]
**Status:** Draft | **Engineering Partner:** [Name] | **Date:** [Date]

## Jobs to be Done
<!--
Write 3–5 validated JTBD statements. Each must cite the customer conversations
that validated it. Order by opportunity score (most over-served first).
Use the Job Story format: When [situation], I want to [motivation], so I can [outcome].
See references/jobs_to_be_done.md for quality rubric and anti-patterns.
-->

| # | JTBD Statement | Type | Importance | Satisfaction | Opportunity | Source |
|---|---------------|------|-----------|-------------|-------------|--------|
| J1 | When [situation], I want to [motivation], so I can [outcome] | Functional | X/10 | X/10 | X | [Customer, date] |

## JTBD → CUJ Coverage Map
<!--
Each JTBD must map to at least one validated CUJ.
This table ensures no JTBD is left without an implementable flow.
-->
| JTBD | CUJ-Happy Path | CUJ-Failure Path | Validation Status |
|------|---------------|-----------------|------------------|
| J1   | CUJ-1a        | CUJ-1b          | [VALIDATED]       |

## Critical User Journeys (CUJs)
<!--
Use the CUJ template from references/cuj_guide.md.
Each CUJ must be AGREED or VALIDATED before inclusion.
Mark each step as [OBSERVED] or [DESIGNED].
See references/cuj_guide.md for full format and anti-patterns.
-->

### CUJ-1a: [Happy Path Title]
**JTBD:** J1
**Actor:** [Role + context]
**Trigger:** [What starts this journey]
**Goal:** [Observable, binary success state]
**Validated by:** [Customer, date]; [Customer, date]
**Validation status:** [VALIDATED]

Steps:
1. [Actor] [action] in [surface] [OBSERVED]
2. [System] responds with [outcome] [DESIGNED]
...

Failure States:
| Condition | Expected Behavior |
|-----------|------------------|
| [If X] | [System does Y] |

## Out of Scope
[Explicit list — saves engineering debate time]

## Technical Requirements
| Requirement | Target | Notes |
|------------|--------|-------|
| Latency (P99) | <Xms | |
| Throughput | X RPS | |
| Availability | X% | |
| Data retention | X days | |

## Open Questions
[Unresolved decisions that need eng/design input]

## Validation Evidence
| Customer | Date | Method | JTBDs Validated | CUJs Validated |
|---------|------|--------|----------------|---------------|
| [Name]  | [Date] | Switch interview | J1, J2 | — |
| [Name]  | [Date] | Walk-through | — | CUJ-1a, CUJ-1b |
```

**⚠️ STOPPING POINT**: Confirm with user that technical requirements have been reviewed by engineering lead.

**When to use:** Feature is ready to ship to limited customers. Validates whether the market exists, solution works, and mass market will adopt.

**Goal:** Ship fast to 3-5 accounts. Learn before GA. Calibrate Stage 1 and Stage 2 based on results.

**Actions:**

1. **Ask** user for the feature and target beta accounts (3-5 names)
2. **Write** to `<workspace>/beta_plan_[feature_name].md`

**Template Structure:**
```markdown
# Beta Plan: [Feature Name]
**Beta Window:** [Start] – [End] | **Target Accounts:** [3-5 names]

## What We Are Validating
| Question | Success Signal | Failure Signal |
|----------|---------------|----------------|
| Does the market exist? | [observable] | [observable] |
| Does solution solve the problem? | [observable] | [observable] |
| Will mass market adopt? | [observable] | [observable] |

## Beta Customer Commitments
[What each account has agreed to: usage, feedback sessions, NPS]

## Feedback Mechanism
[How we collect: weekly call, in-product survey, Slack channel, usage telemetry]

## GA Decision Criteria
[Specific: ≥X of Y accounts use feature weekly + NPS ≥ Z + zero P0 incidents]

## Calibration Protocol
- If market doesn't exist → update Product Strategy Section 2 (Customer Need)
- If solution doesn't fit → update Heilmeier Q3 (new approach), re-validate hypotheses
- If adoption is low → update PRD CUJs, run new customer interviews
```

**⚠️ STOPPING POINT**: Confirm beta accounts are committed (not just interested) before proceeding.

---

## Biweekly Cadence Protocol

Every two weeks:
1. Review Hypotheses tracker — update Status for each tested hypothesis
2. Log findings in Calibration Log table
3. **If validated** → move to Stage 3 queue
4. **If invalidated** → retire hypothesis, update Product Strategy if core assumption is wrong
5. **Reprioritize** remaining hypotheses by signal strength

**Rule:** If ≥2 hypotheses are invalidated in a single cycle → mandatory Product Strategy revision before continuing.

---

## References

- `references/heilmeier_guide.md` — Full Heilmeier catechism background
- `references/jobs_to_be_done.md` — JTBD: two schools, three job types, interview playbook, quality rubric, opportunity matrix, anti-patterns
- `references/cuj_guide.md` — CUJ: definition, anatomy, walk-through protocol, validation gates, coverage map, anti-patterns, copy-paste template

## Stopping Points

- ✋ Stage 1: Product Strategy approved by user
- ✋ Stage 2: Hypotheses approved before customer outreach
- ✋ Stage 3: Heilmeier reviewed by engineering partner
- ⚑ Stage 3.5: Deep Research gap report reviewed; each 🔴 conflict has a PM decision
- ✋ Stage 4: PRD technical requirements signed off
- ✋ Stage 5: Beta accounts confirmed (committed, not just interested)

## Output

All documents written to `<workspace>/<project_name>/` directory:
- `product_strategy.md`
- `hypotheses.md`
- `heilmeier_<feature>.md`
- `deep_research_gap_<feature>.md` (Stage 3.5 output)
- `prd_<feature>.md` (if required)
- `beta_plan_<feature>.md`
