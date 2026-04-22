# Jobs to Be Done — Reference Guide

## What Is a Job to Be Done?

A Job to Be Done (JTBD) is the underlying goal a customer is trying to achieve — independent of any product, feature, or solution. The key insight:

> **Products come and go. Jobs don't change.**

Theodore Levitt put it simply: "People don't want a quarter-inch drill. They want a quarter-inch hole." The drill is the solution. The hole is the job. Customers "hire" your product to get a job done. When it stops doing the job better than alternatives, they fire it.

---

## Two Schools of JTBD (Know Both)

### School 1: Outcome-Driven Innovation (Tony Ulwick / Strategyn)

**Focus:** What does the customer need to accomplish? How do they measure success?

The job is defined by the job executor and the job itself. Customers evaluate success using **desired outcome statements** — measurable criteria for how well the job gets done.

**Outcome statement format:**
```
[Direction] + [metric] + [object of control] + [context/clarifier]

Example:
"Minimize the time it takes to identify which agent is causing anomalous data access."
"Minimize the risk of a PII field being returned in an AI response."
```

**When to use:** When you need to prioritize across many possible features. Quantitative — you can survey customers on importance vs. satisfaction to find unmet outcomes.

### School 2: Switch / Situation Interviews (Bob Moesta & Clayton Christensen)

**Focus:** What situation triggered the customer to seek a new solution? What were they doing before?

Structured as a **Job Story**:
```
When [situation / trigger],
I want to [motivation / what I'm trying to do],
So I can [expected outcome / goal].
```

**Example:**
```
When my CISO asks me to prove our AI agents cannot be weaponized against customer data,
I want to show a complete audit trail of every prompt, retrieval, and response,
So I can get sign-off to move the AI project to production.
```

**When to use:** When you're trying to understand why customers are (or aren't) switching to your product, or when exploring new problem spaces through interviews.

---

## Three Dimensions of Every Job

Every job has three layers. Write at least one JTBD per layer for each major customer segment.

| Layer | Definition | Example |
|-------|-----------|---------|
| **Functional** | The practical task to accomplish | "Detect and block prompt injection attacks before they reach my data" |
| **Emotional** | How the customer wants to feel (or avoid feeling) | "Feel confident telling my board that AI is safe to deploy" |
| **Social** | How the customer wants to be perceived by others | "Be seen as the security leader who enabled AI — not the one who blocked it" |

The functional job is what you build. The emotional and social jobs determine how you position and sell it.

---

## How to Collect JTBDs: The Interview Playbook

### Before the Interview
- Pick one customer segment (CISO, compliance lead, data engineer — not all at once)
- Recruit 5-8 customers who have recently made a relevant decision (bought, evaluated, or rejected a solution)
- Do not show mockups or features — you are listening, not validating

### Interview Structure (45–60 min)

**Part 1: Timeline (15 min) — the Switch Interview**
Ask about the last time they faced this problem:
1. "Walk me through the last time you had to [address this problem area]. What happened?"
2. "What triggered that? What changed?"
3. "What did you try first? Why wasn't that good enough?"
4. "How long had this been a problem before you decided to act?"
5. "Who else was involved in the decision?"

**Part 2: Job Definition (20 min) — what are they actually trying to do?**
1. "When this problem surfaced, what were you ultimately trying to accomplish?"
2. "How do you know when you've done this well? What does success look like?"
3. "What's the worst outcome if this goes wrong?"
4. "If this were completely solved, what would be different about your day?"

**Part 3: Desired Outcomes (15 min) — ranking and gaps**
1. "On a scale of 1–10, how important is [outcome] to you?"
2. "On a scale of 1–10, how satisfied are you with how well current solutions deliver [outcome]?"
3. (Calculate opportunity score: Importance + max(Importance − Satisfaction, 0) — gaps > 10 are high priority)

**Closing:**
- "What would make you drop everything to try a new solution?"
- "Who else should I talk to who has this problem even worse?"

### After the Interview
- Write the JTBD statement within 24 hours, in the customer's own language
- Do not paraphrase into PM language — preserve the vocabulary
- Tag it with: Segment | Functional/Emotional/Social | Importance (1–10) | Satisfaction (1–10)

---

## JTBD Statement Quality Rubric

| Criterion | Pass | Fail |
|-----------|------|------|
| **Situation is specific** | "When my CISO asks for a production AI approval" | "When I want to use AI" |
| **Motivation is the job, not the feature** | "I want to prove no data was exfiltrated" | "I want to see audit logs" |
| **Outcome is business-level** | "Get AI approved for production" | "AI is safe" |
| **Product-agnostic** | Could be solved by multiple approaches | Describes a specific UI or button |
| **Validated** | Heard from ≥2 customers in their words | Written by PM from intuition |

**Quick test:** If you read the JTBD to a customer and they say "yes, that's exactly my problem," it's good. If they say "sure, I guess so," it's too vague.

---

## Prioritizing JTBDs: The Opportunity Matrix

After collecting desired outcomes from ≥5 customers, plot them:

```
Importance (1–10) vs. Satisfaction (1–10)

High Importance + Low Satisfaction  → OVER-SERVED: customers pay premium, highest priority
High Importance + High Satisfaction → WELL-SERVED: do not disrupt; defend
Low Importance + Low Satisfaction  → NON-ISSUE: ignore
Low Importance + High Satisfaction → TABLE STAKES: don't over-invest
```

Build features only for **over-served** jobs (high importance, low satisfaction).

---

## JTBD Anti-Patterns

| Anti-Pattern | What It Looks Like | Fix |
|---|---|---|
| **Feature JTBD** | "I want to click the guardrails toggle" | Describe the goal, not the UI |
| **Circular JTBD** | "When I want AI security, I want guardrails, so AI is secure" | The situation and outcome must be different things |
| **Too broad** | "I want my data to be secure" | Add a specific situation and measurable outcome |
| **Too narrow** | "I want the PII redaction rule to apply in < 1 hour" | That's a technical requirement, not a job |
| **Assumed JTBD** | Written without customer interviews | Always validate with ≥2 real conversations |
| **Single-layer** | Only functional jobs written | Add emotional + social layers before writing CUJs |

---

## JTBD → PRD Connection

Each JTBD in the PRD should:
1. Map to at least one validated CUJ (the "how" of the job)
2. Cite the customer interviews that validated it (name, date)
3. Be ordered by opportunity score (most over-served first)

See `references/cuj_guide.md` for how to translate JTBDs into validated Critical User Journeys.
