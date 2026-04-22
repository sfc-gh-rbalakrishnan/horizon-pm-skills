# How to Use the Horizon Governance Team PM Process Skill

A guide for new and existing PMs on the Horizon Governance team.

---

## What Is This?

This is the Horizon Governance team's own process for building product — from the moment you have an idea to the moment a feature ships to beta. It is **not** a Snowflake-wide standard. It is how **this team** operates.

You interact with it through Cortex Code (CoCo) in plain English. It writes every document for you — product strategy, hypotheses, Heilmeier review, PRD, beta plan — using a structured, opinionated workflow.

You trigger it by saying things like:
- *"Help me write a product strategy for X"*
- *"Derive hypotheses from my product strategy"*
- *"Write a Heilmeier review for H3"*
- *"Write a PRD for prompt injection detection"*
- *"Plan a beta release for Snowguard"*

Or tag it directly with `$horizon-pm-process` followed by your request.

---

## What This Skill Is — and Isn't

This is an AI-powered assistant. Before you rely on it, understand what that means.

**What it does well:**
- Augments the work you were already going to do — faster first drafts, structured templates, research aggregation
- Reduces friction at the stages where PMs typically stall: blank-page strategy docs, hypothesis structuring, Heilmeier formatting
- Flags uncertainty explicitly — every unsourced claim is labeled `[ASSUMPTION — unvalidated]`, and every stopping point reminds you what the skill can't know

**What it doesn't do:**
- It does not replace your judgment on org dynamics, stakeholder politics, or risk tolerance
- It does not know what conversations happened in Slack last week or what your engineering partner is really worried about
- It does not validate your strategy — customers do

**The 70/30 rule:**
Treat every output as 70% done. The remaining 30% is your job: applying context the skill can't access, making calls the skill can't make, and deciding what's true before you share anything externally.

**On uncertainty:**
The skill will tell you when it's operating on assumptions. When it does, that is not a bug — it is the skill being honest. An overconfident AI that fills every gap with plausible-sounding language is more dangerous than one that flags gaps clearly. Treat `[ASSUMPTION — unvalidated]` labels as a checklist of customer conversations you still need to run.

---

## The Principle: Why This Process Exists

Most product teams fail not because they can't ship — but because they ship the wrong thing. They write PRDs from intuition, build features customers never asked for, and launch into silence.

This process enforces one rule above everything else:

> **No feature gets built until a hypothesis is validated in real customer conversations. No feature ships until it has gone through beta with real usage data.**

Every stage has a deliberate gate. The skill stops at each one and asks you to confirm before moving forward. If you feel impatient and want to skip ahead — that impatience is the signal that you need the gate most.

---

## The Five Stages

```
Stage 1: Product Strategy      ← What problem? For whom? Why us?
    ↓
Stage 2: Hypotheses            ← What are our specific bets? Validated?
    ↓ (biweekly customer validation loop)
Stage 3: Heilmeier Review      ← Should engineering commit? Are we ready?
    ↓
Stage 4: PRD (optional)        ← What exactly are we building? What are the flows?
    ↓
Stage 5: Beta Release          ← Did it work in production? GA or not?
    ↓
Feedback → back to Stage 1
```

---

## Stage 1: Product Strategy

**What it produces:** A ≤2 page doc — Problem → Customer Evidence → Approach → Success Metrics.

**The principle:** Executives make decisions on strategy docs, not long decks. If you can't explain the problem, the customer need (with data), what you're building, and why Snowflake uniquely wins — in 2 pages — you don't understand it well enough yet.

**How to use it:** Say *"Help me write a product strategy for AI Guardrails."* The skill researches existing customer evidence from Glean, competitive context, and prior work — and writes the full document.

**Good vs. bad:**

| ❌ | ✅ |
|---|---|
| "Enterprises need AI governance" | "19 named accounts have disabled Cortex entirely because they can't prove AI won't exfiltrate PII" |
| "We will build guardrails" | "We govern what AI can retrieve, return, and do — enforced at the data layer, not the model layer" |
| "Success = shipped" | "5 of 19 blocked accounts re-enabled within 2 quarters" |

**Gate:** You review and approve before anything else starts.

---

## Stage 2: Hypotheses

**What it produces:** A tracker of 5–9 testable bets, each with a solution description, 3 validation questions, and a live status (Not Tested → Validating → Validated / Invalidated).

**The principle:** Your strategy contains assumptions. This stage forces you to make them explicit and testable *before* writing a line of spec. This is also where **JTBD collection starts** — every customer meeting should use the Switch Interview format, listening for situations, triggers, and desired outcomes that become PRD inputs later.

**How to use it:** Say *"Derive hypotheses from my product strategy."* The skill reads your strategy and produces entries like:

> **H3 — CISO Audit Log Requirement**
>
> *Hypothesis:* If we store immutable logs of every AI call in Snowflake, queryable via SQL, then CISOs will approve AI agents for production without requiring a separate SIEM integration.
>
> *Validation Questions:*
> 1. "Does your CISO block AI deployments because there's no audit trail? What would satisfy them?"
> 2. "Would an audit log in Snowflake satisfy compliance, or do they require a SIEM?"
> 3. "How long must you retain AI interaction logs to meet your mandate?"
>
> *Signal Strength:* 🔴 Critical | *Status:* Not Yet Tested

You take this into customer meetings. You test H3 with 2–3 CISOs. You come back and mark it Validated or Invalidated.

**The biweekly cadence:** Every two weeks, update statuses and log what you learned. If ≥2 hypotheses are invalidated in one cycle, you must revise the strategy before continuing — this prevents building on a collapsing foundation.

**Gate:** Hypotheses approved before any engineering conversation begins.

---

## Stage 3: Heilmeier Review

**What it produces:** A ≤2 page doc answering 9 specific questions — designed to drive a build/no-build decision with your engineering partner.

**The principle:** Named after George Heilmeier (DARPA director), these 9 questions force you to be specific about what's new, what the risks are, and what success looks like in concrete, binary terms. This is the engineering conviction doc — not a feature list. It is an argument for why this specific investment is worth making right now.

**How to use it:** Say *"Write a Heilmeier review for H3 — immutable audit logging."* Example output:

> **Q3. What's new and why will it succeed?**
> Every existing solution (Datadog, Splunk, sidecar logging) requires a separate system with separate retention, access control, and query language. Our logs live in Snowflake — governed, retained, and queried exactly like any other table. No CISO has to trust a second system. Structurally impossible for a pure SaaS guardrail vendor to replicate.
>
> **Q6. Risks:**
>
> | Risk | Likelihood | Mitigation |
> |------|-----------|-----------|
> | Customers require SIEM export, not SQL | Medium | Build connector in Phase 2 |
> | Log volume drives unexpected storage costs | Low | Compress + sample low-risk interactions |
> | Competitors ship first | High | Accelerate Phase 1 to beat Bedrock Guardrails GA |

**Gate:** Engineering partner reads this and says yes or no. No PRD until approved.

---

## Stage 4: PRD

**What it produces:** Validated Jobs to Be Done (JTBDs), a JTBD→CUJ coverage map, validated Critical User Journeys (CUJs), and technical requirements.

**The principle:** A PRD has one job — let engineering design and build without a PM in every meeting. That requires two things validated with real customers: **JTBDs** (why the customer needs this) and **CUJs** (how they will use it in practice).

### What is a JTBD?

A Job to Be Done captures the underlying goal a customer is trying to achieve — independent of any product or feature. The format:

```
When [specific situation / trigger],
I want to [motivation — the job, not the feature],
So I can [business-level outcome].
```

**Good vs. bad JTBD:**

| ❌ | ✅ |
|---|---|
| "When I want AI security, I want guardrails so AI is secure" | "When my CISO asks me to prove our AI agents cannot exfiltrate data, I want to show a tamper-proof log of every prompt and response, so I can get production approval in the quarterly security review" |
| "I want to click the guardrails button" | Describes the job, not the UI |

JTBDs are scored by **Importance** (1–10) and **Satisfaction** today (1–10). Opportunity score = Importance + max(Importance − Satisfaction, 0). Anything above 10 is a build priority.

### What is a CUJ?

A Critical User Journey is the step-by-step flow through which a JTBD gets accomplished in your product. Where a JTBD captures *why*, a CUJ captures *how*.

```
CUJ-1a: Security Engineer queries AI audit log after an incident
Actor:   Security Engineer at a Fortune 500 bank, investigating a suspicious retrieval
Trigger: Alert fires from Access History anomaly detection
Goal:    Identify exact prompts and retrieved rows for a suspicious session within 5 minutes

Steps:
1. Engineer navigates to CORTEX_AUDIT_LOG table in Snowsight        [OBSERVED]
2. Engineer queries by session ID and timestamp                      [OBSERVED]
3. System returns all prompts, retrieved documents, and responses    [DESIGNED]
4. Engineer exports results to PDF for CISO review                  [OBSERVED]
```

`[OBSERVED]` = you watched a real customer do this step.
`[DESIGNED]` = new behavior you're introducing — your highest-risk assumption.

**How to collect JTBDs and CUJs:**
- JTBDs come from **Switch Interviews** during hypothesis validation — ask about triggers, timelines, what they tried before
- CUJs come from **walk-through sessions** — watch customers do the actual work today, then write it back to them for confirmation
- Both must be cited to ≥2 real customer conversations before appearing in a PRD

**How to use it:** Say *"Write a PRD for immutable AI audit logging."* The skill will check whether your JTBDs and CUJs are validated before writing. If they aren't, it will tell you what customer work to do first.

**Gate:** Engineering lead signs off on technical requirements before writing starts.

---

## Stage 5: Beta Release Plan

**What it produces:** A structured plan for 3–5 beta accounts — what you're validating, what each account committed to, and the exact GA decision criteria.

**The principle:** Beta is not a soft launch. It is a structured experiment answering three questions:
1. Does the market exist? (Are customers using it at all?)
2. Does the solution work? (Are they completing the CUJs without PM help?)
3. Will the mass market adopt? (Would they pay for it and tell others?)

If any answer is no — you don't GA. You go back to the stage where the assumption failed.

**How to use it:** Say *"Write a beta plan for AI audit logging with JPMorgan, Fidelity, and AstraZeneca."*

> **GA Decision Criteria:** ≥3 of 5 beta accounts query the audit log weekly without PM prompting + NPS ≥ 40 + zero P0 data integrity incidents + at least one CISO meeting where the log was used as evidence in a production approval decision.
>
> **Calibration Protocol:**
> - Only 1 of 5 accounts uses it → market hypothesis wrong; update Product Strategy Section 2
> - Used but can't find what they need → CUJ-1a needs redesign; run new walk-throughs
> - Strong adoption, low NPS → emotional/social job not served; revisit positioning

**Gate:** Accounts must be committed — not just interested. "We'd love to try it" is not a beta commitment.

---

## Quick Reference — What to Say

| Situation | What to say |
|---|---|
| Starting a new product area | *"Write a product strategy for [area]"* |
| Before customer meetings | *"Derive hypotheses from my product strategy"* |
| After customer meetings | *"I just ran 3 customer meetings — update my hypotheses tracker"* |
| Ready for engineering | *"Write a Heilmeier review for [hypothesis]"* |
| Engineering requests a spec | *"Write a PRD for [feature]"* |
| Ready to ship to beta | *"Write a beta plan for [feature] with [accounts]"* |
| Biweekly review | *"Run the biweekly calibration on my hypotheses"* |

---

## The One Rule to Remember

> **Never skip a gate.**

The skill will remind you of each one. Those moments of impatience are exactly when the gates matter most.
