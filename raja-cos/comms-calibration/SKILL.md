---
name: raja-cos-comms-calibration
description: "M5-level communication drafting for up, down, and sideways audiences. Reviews and calibrates communications to reflect Director-level strategic vision and refinement. Use when: drafting an email to leadership, writing to the team, communicating with peers, calibrating a message for M5 level, upward communication. Triggers: draft email, M5, calibrate, write to CK, write to Baris, communicate up, communicate down, message to my team, upward communication, sideways, cross-functional message."
parent_skill: raja-cos
---

# Comms Calibration — M5-Level Communication

Drafts and calibrates communications for three directions. Applies M5 principles (load from `../references/m5-calibration.md`) to ensure every message reflects strategic vision, not just operational status.

## Workflow

### Step 1: Intake

**Ask user:**
```
1. Direction:
   a) Up — to CK, Baris, William, or other senior leadership
   b) Down — to your team of 3 PMs
   c) Sideways — to peers, partner PMs, engineering leads, field/GTM

2. Audience: [Specific person(s) or group]

3. Topic / context: [What is this about? What's the situation?]

4. What do you want the recipient to do after reading this?
   [Decide / Approve / Be informed / Take action / Change behavior]

5. Do you have a draft, or are we starting from scratch?
```

**⚠️ STOP:** Confirm all 5 inputs before drafting.

### Step 2: Load M5 Calibration Principles

**Load** `../references/m5-calibration.md` before drafting anything.

Apply the direction-specific principles from that reference.

### Step 3: Draft the Communication

Draft based on direction:

**A. Upward (to leadership):**
- Open with strategic insight or recommendation — not status
- 3 bullets maximum if written; 3 sentences maximum for Slack
- Every bullet has a "so what for the business" — not just a task completed
- Close with a single, explicit ask (decide / approve / be informed — pick one)
- No more than 1 risk hedged inline — if you hedge everything, nothing lands

**B. Downward (to your team):**
- Open with the "why" — connect work to area strategy before assigning task
- Acknowledge what they know before adding new context
- One clear expectation per message — avoid laundry lists
- Close with the decision or direction they can act on immediately
- Tone: confident, not directive for its own sake

**C. Sideways (to peers / cross-functional):**
- Open with shared problem or shared opportunity — not "I need you to..."
- Propose a specific path forward — not "let's align"
- Invite their POV explicitly: "What am I missing?" or "Does this match what you're seeing?"
- Close with a concrete next step (meeting / async answer / decision by date)

### Step 4: Self-Critique Pass

After drafting, apply these checks:

```
Critique checklist:
□ Does the first sentence carry the key message? (not buried in bullet 3)
□ Is the ask singular and unambiguous?
□ Would a skeptical VP ask "so what?" after reading this? (if yes: rewrite)
□ Is there any hedge that signals lack of conviction? (remove or own it)
□ Is the length appropriate? (up: short; down: context-rich; sideways: punchy)
□ Does this sound like an M5, or an M4 reporting up?
```

Flag and fix any check that fails before presenting.

### Step 5: Present and Offer Options

Show the draft with the critique summary. Offer:
- **Option A:** Use as-is
- **Option B:** Shorter version (exec Slack format)
- **Option C:** Generate Gmail compose link (via `$gmail-compose` skill) — for email

**Ask:** "Does this land the message you want, or should we adjust the angle/ask?"

## Stopping Points

- ✋ After Step 1: Confirm direction, audience, and desired outcome before drafting
- ✋ After Step 5: Confirm final version before generating Gmail link

## Output

A calibrated draft communication with self-critique summary. Optional Gmail compose link.
