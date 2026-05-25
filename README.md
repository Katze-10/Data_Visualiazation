<div align="left">

# Canadian Analyst Job Market — Salary & Demand Dashboard

**BAM-2053 · Data Visualization · Lambton College Ottawa · Spring 2026**
**Professor:** Robert Decher · **Team:** Northbound Analytics

![Course](https://img.shields.io/badge/course-BAM--2053-1A1A2E?style=flat-square)
![Proposal](https://img.shields.io/badge/proposal-v3_submitted-0F766E?style=flat-square)
![Dataset](https://img.shields.io/badge/dataset-1,796_rows_×_13_fields-B88A00?style=flat-square)
![Primary Tool](https://img.shields.io/badge/built_with-Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Secondary Tool](https://img.shields.io/badge/mirror-Looker_Studio-4285F4?style=flat-square&logo=googleanalytics&logoColor=white)

</div>

---

## Overview

This repository contains the full pipeline for our **BAM-2053 Capstone Project**: a data visualization study of the **Canadian Analyst job market**, built from a Kaggle dataset of **1,796 cleaned Indeed.ca job postings**. The goal is to turn raw job-board noise into an interactive dashboard that answers a real career question — *which combinations of skill, city, seniority, and work mode pay best in Canada right now?* — while applying every design principle the course emphasizes (cognitive load, data-ink ratio, F-pattern, pre-attentive processing, Gestalt grouping).

> The project is evaluated on **both analytical rigor and visual design quality**. Every chart choice in this repo is justified through the **3-Lens Framework** (Purpose · Data · Audience).

---

## Repository Structure

```
Data_Visualiazation/
├── Dataset/         Raw and cleaned CSV datasets
├── Proposal/        Capstone proposal (v1, v2, v3 + PDF)
├── Scripts/         Python cleaning / EDA scripts
├── Agents/          Claude Code custom agents (design + course-specific)
├── Skills/          Claude Code skills (UI/UX, proposal, dashboard, frontend)
└── README.md        You are here
```

| Folder | What's inside |
|---|---|
| [`Dataset/`](Dataset/) | `Raw_Dataset.csv`, `Cleaned_Dataset.csv` — source + analysis-ready data |
| [`Proposal/`](Proposal/) | `Project_Proposal_v1.docx`, `_v2.docx`, **`_v3.docx`** (current), `_v3.pdf` |
| [`Scripts/`](Scripts/) | `script.py` — cleaning / feature engineering (in progress) |
| [`Agents/`](Agents/) | 5 custom AI agents |
| [`Skills/`](Skills/) | 5 skill packs |

---

## Project Status

| Milestone | Date | Weight | Status |
|---|---|---|---|
| Proposal submission (600–800 words) | **May 25, 2026** | 10% | ✅ **submitted — v3** |
| Midterm exam | May 28, 2026 | — | ⏳ |
| MVP presentation (7–10 min, ≥80% functional) | June 4, 2026 | — | ⏳ |
| Final dashboard + presentation | June 15, 2026 | 30% + 10% | ⏳ |
| Final exam | June 18, 2026 | — | ⏳ |

---

## The Dataset

**Source:** [Kaggle — Data Analyst Job Roles in Canada](https://www.kaggle.com/datasets/amanbhattarai695/data-analyst-job-roles-in-canada)
**Geography:** Canada-wide (14 provinces + remote)
**Size:** 1,796 observations · 13 fields after cleaning
**Meets course requirements:** ✓ ≥10 fields · ✓ ≥100 rows

### Headline statistics

| Field | Key statistics |
|---|---|
| **Province** | 14 provinces · Ontario 53%, BC 14%, Alberta 11% |
| **Job Title** | 10 categories · top: Senior Supply Chain (262), BI Analysts (229) |
| **Seniority** | ANY 76% · Senior 20% · Mid 2% |
| **Work Type** | In-Person 91% · Remote 8% · Hybrid 1% |
| **Industry** | 22 types · Technology 19% · Healthcare 7% · Others 53% |
| **Skills** | 1,057 unique tags · top: Excel, Python, SQL, Power BI |
| **Salary (Avg)** | Mean **$78,435** · range $43,720–$158,640 · σ $18,027 |

### Cleaned fields

| Field | Type | Description |
|---|---|---|
| `Job Title` | Categorical | Standardized role family (e.g. *Systems and Data Analysts*) |
| `Job Info` | Text | Original posting title |
| `Position` | Categorical | Specific role (e.g. *Risk Analyst*, *Business Analyst*) |
| `Employer` | Categorical | Company name |
| `City` | Categorical | Posting city (incl. *Remote*) |
| `Province` | Categorical | Province code (`Undef` where missing) |
| `Skill` | Multi-value | Comma-separated tools (Python, SQL, Power BI, Excel…) |
| `Seniority` | Ordinal | Junior · Mid · Senior · ANY |
| `Work Type` | Categorical | Remote · Hybrid · On-site |
| `Industry Type` | Categorical | Sector grouping |
| `Min_Salary` | Numeric (CAD) | Lower bound, annualized |
| `Max_Salary` | Numeric (CAD) | Upper bound, annualized |
| `Avg_Salary` | Numeric (CAD) | Midpoint used for visualizations |

---

## Business Question

> **Which combinations of skill, city, seniority, and work mode pay best in Canada right now — and where are the underserved segments of the market?**

### Five concrete questions the dashboard must answer

1. Which province offers the highest median salary for entry-level analyst roles?
2. Do remote roles pay differently than on-site roles within the same job family?
3. Which skill combinations correlate with salaries above the 75th percentile?
4. How does seniority affect salary range spread within each industry?
5. Which cities concentrate the most analyst demand outside Ontario?

### Target audience

**Primary:** recent graduates and career-changers in Ottawa deciding which roles to pursue.
**Secondary:** Lambton program advisors guiding placement, and recruiters benchmarking compensation. The dashboard assumes no SQL or BI background — it must work for a first-year student in the first ten seconds with the file.

---

## Planned Visualizations

Each chart is chosen using the **3-Lens Framework** (Purpose · Data · Audience) and respects the **zero-baseline rule** for all magnitude comparisons.

### Market Overview
| Chart | Why this chart |
|---|---|
| **KPI / BAN tiles** | Pre-attentive numerals — median salary, postings, top province communicate instantly |
| **Choropleth map by province** | Geography is native to the data; color shading exposes regional clusters |
| **Horizontal bar · job title × seniority** | Length is the most accurate pre-attentive attribute for comparison |

### Salary Analysis
| Chart | Why this chart |
|---|---|
| **Box plots · salary by job title** | Show spread, not just averages — protects against misleading means |
| **Grouped bar · work type × province** | Zero-baseline anchored; one accent highlights the top combination |
| **Scatter · min vs. max salary by industry** | Reveals band spread; explicit caveat: correlation ≠ causation |

### Skills & Interactivity
| Chart | Why this chart |
|---|---|
| **Treemap · top skills** | Area reads more reliably than typographic size in a word cloud |
| **Global filter panel** | Province · seniority · work type · industry · salary, grouped by proximity (Gestalt) |
| **Detail table** | Tufte: tables beat charts for exact values; placed last as reference material |

**Explicitly avoided:** pie charts with >5 slices, dual-axis charts, 3D effects, decorative chartjunk, color as the sole encoding.

---

## Design Principles Applied

This project is graded as much on **design execution** as on analysis. Decisions follow:

- **Data-ink ratio (Tufte)** — no gridlines unless they aid reading, no shadows on bars, no 3D
- **Single accent color** — one color reserved for the metric we want the audience to notice first
- **F-pattern layout** — KPIs top-left where attention concentrates, comparative charts middle, detail table at the bottom
- **Pre-attentive processing** — length, color hue, and position used deliberately to direct the eye
- **Gestalt grouping** — related filters clustered by proximity, not floating separately
- **Hick's Law** — interactivity limited to five filters; fewer controls, better decisions
- **Accessibility** — ColorBrewer-safe palettes, ≥4.5:1 contrast on text, color never the sole encoding
- **Dashboard, not Report** — interactive filtering (province, seniority, work type, industry, salary) so the user explores rather than reads

---

## Reference Example

We benchmarked our concept against the **[Robert Half 2025 Canada Salary Guide](https://www.roberthalf.com/ca/en/insights/salary-guide)**, which publishes compensation ranges for Canadian analytics roles by city and seniority. It is a static PDF with no skill, work-type, or industry filtering. Our dashboard adds the multi-dimensional filtering and skill-frequency layer Robert Half cannot provide.

---

## Tooling

| Layer | Tool | Why |
|---|---|---|
| Data cleaning | **Python** (`pandas`, `numpy`) | Reproducible pipeline in [`Scripts/script.py`](Scripts/script.py) |
| Dashboard (primary) | **Power BI** | Handles dataset, treemap, and multi-filter interactivity natively; both team members already use it from BAM-2024 |
| Dashboard (secondary) | **Google Looker Studio** | Publishes via URL — no Microsoft account needed for the student audience |
| Document writing | Microsoft Word | Proposal in [`Proposal/`](Proposal/) |
| AI assistance | Claude Code | Agents and skills in [`Agents/`](Agents/) and [`Skills/`](Skills/) |

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
| [`proposal-skill/`](Skills/proposal-skill/) | Step-by-step protocol for the BAM-2053 Word proposal (used for v3) |
| [`dashboard-skill/`](Skills/dashboard-skill/) | Protocol for building the Power BI / Looker Studio dashboard |
| [`ui-ux-pro-max/`](Skills/ui-ux-pro-max/) | 50 styles · 21 palettes · 50 font pairings · 20 chart types |
| [`frontend-design/`](Skills/frontend-design/) | Component-level design patterns |
| [`senior-frontend/`](Skills/senior-frontend/) | Performance + architecture reference |

---

## Proposal History

| Version | File | What changed |
|---|---|---|
| v1 | [`Project_Proposal_v1.docx`](Proposal/Project_Proposal_v1.docx) | First draft — basic sections, no design styling |
| v2 | [`Project_proposal_v2.docx`](Proposal/Project_proposal_v2.docx) | Reformatted, consolidated content |
| **v3** | **[`Project_proposal_v3.docx`](Proposal/Project_proposal_v3.docx)** | **Submitted version.** Editorial layout, navy + gold + teal palette, all 8 rubric items covered: team name (*Northbound Analytics*), purpose & objectives, 5 key questions, target audience, data sources + limitations, 8 visualizations + wireframe sketch, reference example (Robert Half), tool justification (Power BI + Looker Studio) |
| v3 PDF | [`Project_proposal_v3.pdf`](Proposal/Project_proposal_v3.pdf) | PDF export of v3 for submission portal |

---

## How to Reproduce

```bash
# 1. Clone
git clone <repo-url>
cd Data_Visualiazation

# 2. Run cleaning pipeline (when finalized)
python Scripts/script.py

# 3. Open the dashboard
#    Power BI:        Dashboard/<file>.pbix
#    Looker Studio:   shared link in Proposal/Project_proposal_v3.docx
```

> The cleaning script is currently a stub. It will be filled in during Sprint 1 to take `Raw_Dataset.csv → Cleaned_Dataset.csv` reproducibly (salary range parsing, role-family standardization, province inference from city).

---

## Team — Northbound Analytics

| Name | Student ID | Role |
|---|---|---|
| **Andrés Camilo Cepeda Pedraza** | C0967286 | Dashboard build, data cleaning, presentation |
| **Juan Sebastián Herrera Sanchez** | C0965669 | Design system, proposal writing, narrative |

---

## License

Academic use only — coursework for BAM-2053, Lambton College Ottawa, Spring 2026. Dataset retains its original Kaggle license.
