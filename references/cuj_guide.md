# Critical User Journeys (CUJs) — Reference Guide

## What Is a Critical User Journey?

A **Critical User Journey (CUJ)** is the step-by-step flow through which a validated Job to Be Done gets accomplished in your product. It is the operational translation of a JTBD.

> **JTBD = the WHY** (what the customer is trying to achieve)
> **CUJ = the HOW** (the specific path through your product to achieve it)

A CUJ is "critical" because it represents a path where failure has serious consequences — either the customer cannot accomplish their goal, or they accomplish it in a way that creates risk (wrong result, data exposed, audit gap, etc.).

**Key distinctions:**

| Concept | Scope | Product-Specific? | Validated By |
|---------|-------|-------------------|-------------|
| JTBD | The goal / motivation | No — product-agnostic | Customer interviews |
| CUJ | The end-to-end path through the product | Yes | Customer walk-throughs |
| User Story | A single interaction step | Yes | Designer / PM assumption |
| Journey Map | Entire customer lifecycle (purchase → onboard → expand) | Sometimes | Research + analytics |

A CUJ is **narrower than a journey map** (it covers one key workflow, not the entire lifecycle) and **wider than a user story** (it covers the complete flow, not one click).

---

## Anatomy of a CUJ

Every CUJ has six components:

```
CUJ-[N]: [Short Title]
JTBD:     [The job this CUJ accomplishes — link to JTBD statement]
Actor:    [Who is doing this — specific persona with role + context]
Trigger:  [What causes this journey to start]
Goal:     [What success looks like at the end — observable, binary]
Validated by: [Customer name + date of walk-through]

Steps:
1. [Actor] [action verb] [object] in [surface/context]
2. [System] responds with [observable outcome]
3. [Actor] [decision or next action]
...
N. [Actor] reaches [goal state] — journey complete.

Failure States:
- If [condition], then [what goes wrong] → [expected system behavior]
- If [condition], then [what goes wrong] → [expected system behavior]

Performance Requirements:
- [Step N] must complete in < [X]ms at P99
- [Step N] must return results within [X] seconds
```

---

## How to Collect CUJs: The Walk-Through Protocol

### Step 1: Start from Validated JTBDs
Do not write CUJs before you have validated JTBDs. Each CUJ is anchored to a specific job. If you don't know the job, you don't know what "critical" means.

Prioritize CUJs for the **top 3 over-served JTBDs** (highest importance, lowest satisfaction from the opportunity matrix).

### Step 2: Recruit the Right Customers
- Pick customers who have this job today — not potential customers
- Prefer customers who are actively doing this job in production (not evaluating)
- 3–5 customers per CUJ is sufficient; aim for variation in company size and use case

### Step 3: The Walk-Through Session (60 min)

**Do not show mockups in the first 30 minutes.**

**Part 1: How they do it today (30 min)**
1. "Can you show me how you [accomplish the job] today? Walk me through exactly what you do."
2. Watch and take notes. Do not interrupt. Note every tool, system, and workaround.
3. "Where do you get stuck? What takes the longest? What do you have to do manually?"
4. "What does it feel like when this goes wrong? What's the worst that has happened?"
5. "Who else is involved? Do you need approval from anyone?"

**Part 2: Define success (15 min)**
1. "How do you know this went well? What does the output look like?"
2. "What would make you trust this result enough to act on it?"
3. "What would cause you to re-do this workflow?"

**Part 3: Prototype reaction (15 min)** *(only if you have something to show)*
1. Show the CUJ you've drafted. "Does this match how you think about this?"
2. "What's missing? What would cause this to fail in your environment?"
3. "Where would you expect this to be 10x faster / more accurate / more transparent?"

### Step 4: Synthesize into a CUJ
Within 48 hours of each walk-through:
1. Write the CUJ in the standard format above
2. Use the customer's vocabulary (the words they used, not PM abstraction)
3. Mark every step as: **Observed** (customer actually does this today) or **Designed** (new behavior we are introducing)
4. Flag all "designed" steps — these are your highest-risk assumptions and need the most validation

---

## Validation Protocol

A CUJ is not validated until:

| Gate | Criteria |
|------|---------|
| **G1: Observed** | The job has been watched being done by ≥2 customers |
| **G2: Agreed** | Customer reviewed your CUJ write-up and said "yes, this is how I would do it" |
| **G3: Scoped** | Failure states have been confirmed ("what happens if X" answered with real examples) |
| **G4: Prioritized** | Customer confirmed this is one of their top 3 most frequent or highest-stakes workflows |

Mark each CUJ in the PRD with its validation status:
- `[OBSERVED]` — you watched it happen
- `[AGREED]` — customer reviewed the written CUJ
- `[SCOPED]` — failure states confirmed
- `[VALIDATED]` — all four gates passed

Do not build a CUJ that is not at least `[AGREED]`.

---

## CUJ Coverage Map

Before writing the PRD, map your CUJs to confirm you have covered the right surface area:

```
JTBD-1: [job statement]
  └── CUJ-1a: Happy path — [title]         [VALIDATED]
  └── CUJ-1b: Failure path — [condition]   [AGREED]
  └── CUJ-1c: Escalation path — [condition] [OBSERVED]

JTBD-2: [job statement]
  └── CUJ-2a: ...
```

**Rule:** Every JTBD in the PRD must have at least one validated CUJ. If a JTBD has no CUJ, either the job is not ready to build or the discovery work is not done.

---

## CUJ Anti-Patterns

| Anti-Pattern | Example | Fix |
|---|---|---|
| **UI-level CUJ** | "User clicks 'Enable Guardrails' button" | Start from the trigger (why are they here?), not the click |
| **Happy-path only** | CUJ has no failure states | Ask customers "when does this break?" — failure states drive the hardest engineering decisions |
| **Assumed flow** | Written by PM without walk-throughs | Every step must be observed or confirmed — mark "designed" steps explicitly |
| **Missing actor context** | "The user enables redaction" | Specify: "The Security Engineer configuring Cortex Agents for production deployment enables..." |
| **No success state** | Journey just ends | Define observable, binary success: "Agent outputs contain no raw PII fields" |
| **Too many CUJs** | 20 CUJs for one feature | Focus on ≤5 critical paths. If you have more, you haven't prioritized. |
| **Conflated JTBDs** | One CUJ tries to accomplish multiple jobs | Each CUJ serves one JTBD. Split if the customer's goal changes mid-flow. |

---

## CUJ Template (copy-paste ready)

```markdown
### CUJ-[N]: [Short Title]
**JTBD:** [Link to the job this CUJ satisfies]
**Actor:** [Role] at [company type/size] who is [specific context]
**Trigger:** [What causes this journey to start]
**Goal:** [Observable, binary success state]
**Validated by:** [Customer name] ([date]); [Customer name] ([date])
**Validation status:** [OBSERVED / AGREED / SCOPED / VALIDATED]

#### Steps
1. Actor [action] in [surface]
2. System [observable response]
3. Actor [decision or next action]
4. ...
N. Actor reaches goal state: [description]

#### Failure States
| Condition | Expected Behavior |
|-----------|------------------|
| [If X happens] | [System does Y] |
| [If Z is missing] | [System does W] |

#### Performance Requirements
| Step | Requirement |
|------|-------------|
| Step N | < [X]ms at P99 |
```

---

## The JTBD → CUJ → Engineering Chain

```
JTBD (validated interview)
  ↓
CUJ (validated walk-through)
  ↓
Engineering spec (technical requirements, latency, error handling)
  ↓
Design prototype (CUJ steps become screens/interactions)
  ↓
Beta test (does customer complete CUJ without PM help?)
```

The test of a good CUJ: a designer should be able to build a prototype, and an engineer should be able to write a technical spec, **without a PM in the room**. If they need to ask questions, the CUJ is not specific enough.
