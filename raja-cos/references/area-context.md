# Data & AI Governance Area Context

Reference for Raja's product area. Used by all sub-skills to ground outputs in area-specific context.

---

## What We Own

**Area:** Data & AI Governance, Horizon team at Snowflake

**Products / Feature Areas:**
- Horizon Catalog — metadata management, object tagging, search, discoverability
- Data Classification — automated PII/sensitive data detection and tagging
- Data Policy — masking policies, row access policies, projection policies
- Access Governance — RBAC, privilege management, trust center
- Data Lineage — column-level and object-level lineage
- Data Quality / DMF — Data Metric Functions for automated quality monitoring
- Semantic Views / Cortex Analyst — semantic annotation layer for LLM-ready data
- Data & AI Governance (broader) — governance for AI workloads, model lineage, AI policy

---

## Why This Area Matters

Data & AI Governance is the trust layer for enterprise Snowflake. The core proposition:
- If you can't govern your data, you can't trust your AI
- As AI workloads on Snowflake grow, governance becomes the unlock — not an afterthought
- Regulatory environment (GDPR, CCPA, EU AI Act) is accelerating buyer urgency
- Every T1/T2 account has an active governance conversation today

The area's strategic position: governance that is *native to where the data lives* is structurally superior to bolt-on governance from Collibra, Alation, or Purview. This is the "Snowflake wins" story.

---

## Primary Competitors

| Competitor | Primary threat | Snowflake's differentiation |
|---|---|---|
| Databricks Unity Catalog | End-to-end data + AI governance for Databricks shops | Snowflake native; cross-cloud; enterprise security |
| Collibra | Enterprise governance / catalog with compliance depth | Platform-native; no separate tool; unified data + governance |
| Alation | Data catalog, search, and stewardship | Semantic Views + Cortex for AI-native catalog |
| Monte Carlo | Data observability and quality | DMF is native, not a separate pipeline |
| Atlan | Modern active metadata / collaboration | Snowflake is the platform, not a metadata overlay |
| Microsoft Purview | Azure-native governance | Multi-cloud; Snowflake-first |

---

## Key Leadership Stakeholders

- **CK** (Chetan Kapoor) — Head of Product, Horizon
- **Baris** (Baris Gultekin) — Head of AI, Snowflake
- **William** — Director/VP in chain (confirm current name with Raja if uncertain)

---

## Key Processes & Cadences

| Cadence | Frequency | Relevance |
|---|---|---|
| PFM Meeting | Bi-weekly (every other Monday) | All PLTs reviewed for status, TED, Green/Yellow/Red |
| OKR Check-in | Weekly / Bi-weekly (confirm with Raja) | KR status updates from each PM |
| QBR | Quarterly | Area-level OKR report to leadership; requires QBR prep (okr-qbr sub-skill) |
| Customer meeting target | Weekly | ≥4 customer meetings/PM; Raja's team tracked weekly |
| Competitive sweep | Monthly (minimum) | Full watchlist check via competitive-intel sub-skill |

---

## Current Quarter OKR Focus

> **Note:** OKR targets change quarterly. Always load current numbers from the OKR spreadsheet before generating any OKR output.
>
> OKR spreadsheet: https://docs.google.com/spreadsheets/d/1QQqcGUp9o2ebb3j-UCjXP3fQBXVMgzLL963pA_MdRfA/edit?gid=1260102982#gid=1260102982
>
> Northstar Dashboard: https://app.snowflake.com/sfcogsops/snowhouse_aws_us_west_2/#/streamlit-apps/SNOWSCIENCE.STREAMLIT_APPS.NORTHSTAR

---

## Agentic AI Tools in Use

- **CoCo (Cortex Code):** Snowflake's agentic AI assistant — used for document generation, gap analysis, morning briefs, and all PM work
- **Snowflake Intelligence (SI):** Natural language data agent — used for customer usage analysis, data exploration, and OKR metric lookup
- **Glean MCP:** Gives CoCo access to Slack, Google Drive, Jira, GitHub for internal research
- **Snowwork:** Snowflake's browser-control agentic product (Research Preview) — used for tasks requiring access outside Snowflake systems

---

## Useful Links

| Resource | URL |
|---|---|
| OKR Spreadsheet | https://docs.google.com/spreadsheets/d/1QQqcGUp9o2ebb3j-UCjXP3fQBXVMgzLL963pA_MdRfA/edit?gid=1260102982#gid=1260102982 |
| Northstar Dashboard | https://app.snowflake.com/sfcogsops/snowhouse_aws_us_west_2/#/streamlit-apps/SNOWSCIENCE.STREAMLIT_APPS.NORTHSTAR |
| Team Notes (Google Drive) | https://drive.google.com/drive/folders/1_0K6mAf1EeCuOhixDhABGOIOSEbf8JTu |
| GitHub Skills Repo | https://github.com/sfc-gh-rbalakrishnan/horizon-pm-skills |
