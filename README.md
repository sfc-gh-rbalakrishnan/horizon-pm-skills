# horizon-pm-skills

Cortex Code (CoCo) skills for the **Horizon Governance PM team**.

## Skills

| Skill | Description |
|---|---|
| `horizon-pm-process` | Five-stage PM process: product strategy, hypotheses, Heilmeier review, PRD, and beta plan. Team-specific — not a Snowflake-wide standard. |

## Setup

Add the following to `~/.snowflake/cortex/skills.json` on your machine:

```json
{
  "remote": [
    {
      "source": "https://github.com/raja-balakrishnan_snow/horizon-pm-skills",
      "ref": "main",
      "skills": [
        { "name": "horizon-pm-process" }
      ]
    }
  ]
}
```

Then restart CoCo. The skill will be available automatically.

## Usage

Trigger by saying things like:
- *"Write a product strategy for X"*
- *"Derive hypotheses from my product strategy"*
- *"Write a Heilmeier review for H3"*
- *"Write a PRD for [feature]"*
- *"Write a beta plan for [feature]"*

Or tag it directly: `$horizon-pm-process write a product strategy for AI Guardrails`
