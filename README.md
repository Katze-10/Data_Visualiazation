<div align="left">

# Canadian Data & Analytics Job Market — Visualization Project

**BAM-2053 · Data Visualization · Lambton College Ottawa · Spring 2026**
**Professor:** Robert Decher

![Status](https://img.shields.io/badge/status-in_progress-1a1a2e?style=flat-square)
![Course](https://img.shields.io/badge/course-BAM--2053-efd81d?style=flat-square&labelColor=1a1a2e)
![Dataset](https://img.shields.io/badge/dataset-1796_rows_×_13_fields-16213e?style=flat-square)
![License](https://img.shields.io/badge/license-Academic-475569?style=flat-square)

</div>

---

## Overview

This repository contains the full pipeline for our **BAM-2053 Capstone Project**: a data visualization study of the **Canadian Data & Analytics job market**, built from a Kaggle dataset of **1,796 Indeed.ca job postings**. The goal is to turn raw job-board noise into a dashboard that answers a real business question — *which skills, cities, and seniorities actually pay in Canada right now?* — while applying the design principles taught in the course (cognitive load, data-ink ratio, visual hierarchy, pre-attentive processing).

> The project is evaluated on **both analytical rigor and visual design quality**. Every chart choice in this repo is justified through the 3-Lens Framework (Purpose · Data · Audience).

---

## Repository Structure

```
Data_Visualiazation/
├── Dataset/         Raw and cleaned CSV datasets
├── Proposal/        Capstone proposal Word documents
├── Scripts/         Python cleaning / EDA scripts
├── Agents/          Claude Code custom agents (design + course-specific)
├── Skills/          Claude Code skills (UI/UX, proposal writing, frontend)
└── README.md        You are here
```

| Folder | What's inside | Why it matters |
|---|---|---|
| [`Dataset/`](Dataset/) | `Raw_Dataset.csv`, `Cleaned_Dataset.csv` | Source data + analysis-ready table |
| [`Proposal/`](Proposal/) | `Project_Proposal.docx`, `Project_proposal_2.docx` | Drafts of the May 25 proposal submission |
| [`Scripts/`](Scripts/) | `script.py` | Cleaning, salary parsing, feature engineering |
| [`Agents/`](Agents/) | 5 custom AI agents | Design critique, course expertise, dev support |
| [`Skills/`](Skills/) | 4 skill packs | Reusable design + writing protocols |

---

## The Dataset

**Source:** Kaggle — *Indeed Canada Data Analyst Job Postings*
**Geography:** Canada-wide (all provinces + remote)
**Size:** 1,796 observations · 13 fields after cleaning
**Meets course requirements:** ✓ ≥10 fields · ✓ ≥100 rows

### Cleaned Fields

| Field | Type | Description |
|---|---|---|
| `Job Title` | Categorical | Standardized role family (e.g. *Systems and Data Analysts*) |
| `Job Info` | Text | Original posting title |
| `Position` | Categorical | Specific role (e.g. *Risk Analyst*, *Business Analyst*) |
| `Employer` | Categorical | Company name |
| `City` | Categorical | Posting city (incl. *Remote*) |
| `Province` | Categorical | Province code (`Undef` where missing) |
| `Skill` | Multi-value | Comma-separated tools (Python, SQL, Power BI, Excel...) |
| `Seniority` | Ordinal | Junior · Mid · Senior · ANY |
| `Work Type` | Categorical | Remote · Hybrid · On-site |
| `Industry Type` | Categorical | Sector grouping |
| `Min_Salary` | Numeric (CAD) | Lower bound, annualized |
| `Max_Salary` | Numeric (CAD) | Upper bound, annualized |
| `Avg_Salary` | Numeric (CAD) | Midpoint used for visualizations |

---

## Business Question

> **Which combinations of skills, cities, seniorities, and work modes drive the highest salaries for Data & Analytics roles in Canada — and where are the underserved segments of the market?**

**Target audience:** recent graduates and career-changers in the Ottawa region deciding where to invest learning time. Secondary audience: program advisors at Lambton College.

---

## Planned Visualizations

Each chart is chosen using the **3-Lens Framework** (Purpose · Data · Audience) and respects the **zero-baseline rule** for all magnitude comparisons.

| # | Chart | Purpose | Why this chart |
|---|---|---|---|
| 1 | **KPI / BAN tiles** | Headline metrics (median salary, # postings, top city) | Pre-attentive — big numbers communicate instantly, lowest cognitive load |
| 2 | **Horizontal bar chart** | Top 15 skills by avg. salary | Length is the most accurate pre-attentive attribute for comparison |
| 3 | **Choropleth map** | Postings & salary by province | Geographic dimension is native to the data; color shading reveals clusters |
| 4 | **Box / violin plot** | Salary distribution by seniority | Shows spread, not just averages — protects against misleading means |
| 5 | **Dot / dumbbell plot** | Remote vs. On-site salary gap per role | Two-group comparison without dual-axis pitfalls |
| 6 | **Detail table** | Drill-down at the bottom of the dashboard | Tufte: tables beat charts for exact values |

**Explicitly avoided:** pie charts with >5 slices, dual-axis charts, 3D effects, decorative chartjunk.

---

## Design Principles Applied

This project is graded as much on **design execution** as on analysis. Decisions follow:

- **Cognitive load minimization** — restrained palette, generous whitespace, one accent color (`#efd81d`) reserved for the metric we want the viewer to look at first
- **F-pattern layout** — KPIs top-left, trends top-right, detail tables at the bottom
- **Gestalt grouping** — related filters (geography, role, skill) clustered by proximity
- **Data-ink ratio (Tufte)** — no gridlines unless they aid reading, no shadows on bars, no 3D
- **Accessibility** — ColorBrewer-safe palettes, ≥4.5:1 contrast on text, no color-only encoding
- **Dashboard, not Report** — interactive filtering (province, seniority, work type) so the user explores rather than reads

---

## Project Timeline

| Date | Milestone | Weight |
|---|---|---|
| **May 25, 2026** | Proposal submission (600–800 words) | 10% |
| **May 28, 2026** | Midterm exam | — |
| **June 4, 2026** | MVP presentation (7–10 min, ≥80% functional) | — |
| **June 15, 2026** | Final dashboard + presentation | 30% + 10% |
| **June 18, 2026** | Final exam | — |

---

## Tooling

| Layer | Tool |
|---|---|
| Data cleaning | Python (`pandas`, `numpy`) — see [`Scripts/script.py`](Scripts/script.py) |
| Dashboard | Power BI *(primary)* / Google Data Studio *(fallback)* |
| Document writing | Microsoft Word (proposal in [`Proposal/`](Proposal/)) |
| AI assistance | Claude Code with the agents and skills in [`Agents/`](Agents/) and [`Skills/`](Skills/) |

---

## AI Agents & Skills

Custom Claude Code configurations used to keep the work disciplined and on-brand for the course.

### Agents — [`Agents/`](Agents/)

| Agent | Role |
|---|---|
| [`bam2053-dataviz-expert.md`](Agents/bam2053-dataviz-expert.md) | Course-aligned reviewer — applies 3-Lens Framework, flags scale violations, enforces Tufte |
| [`ui-ux-designer.md`](Agents/ui-ux-designer.md) | Research-backed design critic (NN Group, WCAG, eye-tracking) |
| [`frontend-developer.md`](Agents/frontend-developer.md) | Implementation help for any web-based output |
| [`backend-architect.md`](Agents/backend-architect.md) | Data pipeline guidance |
| [`prompt-engineer.md`](Agents/prompt-engineer.md) | Refines AI workflows used during the project |

### Skills — [`Skills/`](Skills/)

| Skill | Purpose |
|---|---|
| [`proposal-skill/`](Skills/proposal-skill/) | Step-by-step protocol for the BAM-2053 Word proposal |
| [`ui-ux-pro-max/`](Skills/ui-ux-pro-max/) | 50 styles · 21 palettes · 50 font pairings · 20 chart types |
| [`frontend-design/`](Skills/frontend-design/) | Component-level design patterns |
| [`senior-frontend/`](Skills/senior-frontend/) | Performance + architecture reference |

---

## How to Reproduce

```bash
# 1. Clone
git clone <repo-url>
cd Data_Visualiazation

# 2. (When the cleaning script is finalized)
python Scripts/script.py

# 3. Open the dashboard
#    Power BI: open Dashboard/<file>.pbix
#    Data Studio: open the shared link from Proposal/
```

> The cleaning script is currently a stub — it will be filled in during Sprint 1 to take `Raw_Dataset.csv → Cleaned_Dataset.csv` reproducibly (salary range parsing, role-family standardization, province inference from city).

---

## Team

| Name | Role |
|---|---|
| **Sebastián H.S.** | Data prep, dashboard design, proposal writing |
| *(partner, if any)* | *(role)* |

---

## License

Academic use only — coursework for BAM-2053, Lambton College Ottawa, Spring 2026. Dataset retains its original Kaggle license.
