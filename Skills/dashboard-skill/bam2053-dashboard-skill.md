# 📊 SKILL: BAM-2053 Dashboard Design (Power BI / Google Data Studio)
**Trigger:** User is designing, building, or reviewing a dashboard in Power BI or Google Data Studio
**Covers:** Layout, chart selection, color, scales, UX/UI, interactivity, and delivery checklist

---

## SKILL PROTOCOL — STEP BY STEP

### STEP 1 — DASHBOARD INTAKE (confirm before designing)

```
Tool:           [ ] Power BI   [ ] Google Data Studio
Dataset:        _______________
Audience:       _______________  (executives / analysts / public)
Primary KPIs:   _______________ (top 3 metrics that matter most)
Time dimension: [ ] Yes  [ ] No
Geography:      [ ] Yes  [ ] No
Stage:          [ ] Planning  [ ] MVP (80%)  [ ] Final (100%)
```

---

### STEP 2 — INFORMATION ARCHITECTURE FIRST

Before touching any tool, define the structure:

```
LEVEL 1 — Overview Page
  └── KPI cards (BANs) — top 3-5 metrics
  └── Primary trend chart (line/bar)
  └── One map (if geographic data)

LEVEL 2 — Drill-Down Page(s)
  └── Detailed breakdowns (bar charts by category)
  └── Scatter plot (if correlation to show)
  └── Table/Matrix for exact values

LEVEL 3 — Filters & Controls
  └── Date slicer
  └── Category filter
  └── Geographic filter (if applicable)
```

**Rule:** Put the most important insight where the eye lands first — top-left.
**F-Pattern:** Critical KPIs → top bar; supporting charts → left column; details → right/bottom.

---

### STEP 3 — CHART SELECTION RULES

For each data question, apply the 3-Lens Framework:

| Question Type | Recommended Chart | Avoid |
|--------------|-------------------|-------|
| Compare categories | Bar or Column chart | Pie with >5 slices |
| Show trend over time | Line chart | 3D charts |
| Show proportion of whole | Donut / Pie (≤5 slices) | 3D pie |
| Show correlation | Scatter plot | Dual-axis |
| Show geographic distribution | Choropleth map | Dot maps for large areas |
| Show single critical metric | KPI / BAN card | Gauge charts |
| Show frequency distribution | Histogram | Bar chart (different concept!) |
| Compare two groups | Dumbbell dot plot | Stacked bar (hard to read differences) |
| Show detail / exact values | Matrix / Table | Pie chart |

---

### STEP 4 — COLOR SYSTEM

#### Choose ONE of these palette types:
- **Categorical** — Different colors for different categories (max 6-7 hues)
- **Sequential** — Light to dark of one hue (for quantities: low → high)
- **Diverging** — Two hues from center (for data with a meaningful midpoint: below/above target)

#### Application rules:
- **1 accent color** for the most important metric
- **Gray** for context / background data
- **Never** use red/green together (7-10% of men have color blindness)
- If using red/green, add patterns or labels as backup
- Match brand colors if a company is the client

#### Power BI color tip:
```
Format pane → Data colors → "fx" button → Conditional formatting
Use field value for sequential coloring
Use rules for diverging (above/below threshold)
```

---

### STEP 5 — QUANTITATIVE SCALE CHECKLIST

Before finalizing any chart, check for the **6 Common Scale Problems:**

| Problem | Check | Fix |
|---------|-------|-----|
| 1. Unequal intervals | Y-axis gaps consistent? | Set custom intervals: 1, 2, 5, 10, 20, 50... |
| 2. Ambiguous units | Axis title says exactly what the number is? | "Revenue (CAD $000s)" not just "Revenue" |
| 3. Mixed units on same axis | Only one unit per axis? | Split into separate charts |
| 4. Dual-axis | Using two Y-axes? | Use merged/side-by-side charts instead |
| 5. Broken scale | Y-axis starts at non-zero for bar chart? | **Bar charts MUST start at zero** |
| 6. Inconsistent decimals | "1.5, 2, 3.75" on same axis? | Pick one decimal standard throughout |

#### Zero-Baseline Rule:
- **Bar / Column charts:** Y-axis MUST start at 0 — always
- **Line charts:** Can start at non-zero if the variation is the story
- **Never** truncate a bar chart to exaggerate differences

---

### STEP 6 — UX / UI LAYOUT PRINCIPLES

#### Structure (UX):
```
┌─────────────────────────────────────────────┐
│  TITLE + Subtitle + Date filter             │  ← top bar
├──────────┬──────────┬──────────┬────────────┤
│  KPI 1   │  KPI 2   │  KPI 3   │  KPI 4    │  ← BAN row
├──────────┴──────────┴──────────┴────────────┤
│                                              │
│     PRIMARY CHART (line or bar — main story)│  ← center/left
│                                             │
├────────────────────┬────────────────────────┤
│   Secondary chart  │   Map / breakdown      │  ← supporting
├────────────────────┴────────────────────────┤
│         Detail Table (optional)             │  ← bottom
└─────────────────────────────────────────────┘
```

#### Visual Design (UI):
- **Background:** Off-white or very light gray — never pure white
- **Font:** 1 typeface only; 2 max (one for titles, one for data labels)
- **Spacing:** Use consistent padding — white space is not wasted space
- **Grid lines:** Light and minimal; horizontal only
- **Borders:** Avoid heavy borders on chart panels
- **Titles:** Every chart needs one — specific, not generic ("Revenue by Region Q1 2025" not "Revenue")

---

### STEP 7 — INTERACTIVITY CHECKLIST (Power BI specific)

- [ ] **Slicers:** Date range, category, region — placed consistently (left panel or top)
- [ ] **Cross-filtering:** Test that clicking one chart filters others correctly
- [ ] **Tooltips:** Add context without cluttering (show % of total, comparison vs. prior period)
- [ ] **Drill-through:** Link summary → detail page
- [ ] **Bookmarks:** Save specific filter views for the presentation
- [ ] **Mobile layout:** Check if required (Power BI has separate mobile view)

---

### STEP 8 — MVP vs FINAL DELIVERY STANDARDS

| Criterion | MVP (June 4 — 80%) | Final (June 15 — 100%) |
|-----------|-------------------|----------------------|
| Pages | At least 1 functional page | Full structure (overview + detail) |
| Charts | Core charts working | All charts + interactivity |
| Filters | At least date filter | All filters + drill-through |
| Color | Consistent palette applied | Polished, accessible palette |
| Titles | Chart titles present | All titles + subtitles + source |
| Presentation | 7–10 min, show it live | 7–15 min via Teams, 100% complete |

---

### STEP 9 — EVALUATION ALIGNMENT (Final Product 30%)

Map every design decision to the rubric:

| Rubric Criterion | How to satisfy it |
|-----------------|-------------------|
| **Data Relevance & Chart Selection** | Every chart justified with 3-Lens Framework |
| **Visual Design & Usability** | Low cognitive load, consistent palette, F-pattern layout |
| **Functionality & Features** | Filters, tooltips, drill-through working |
| **Alignment with Business Goals** | KPIs match the business question from the proposal |

---

## COMMON DASHBOARD ERRORS (from course) — SELF-AUDIT

Run this before any submission:

- [ ] ❌ Too much clutter — remove anything that doesn't serve the insight
- [ ] ❌ Too many colors — max 6-7 categorical hues; use gray for non-focus
- [ ] ❌ Lack of context — every chart has a title and labeled axes
- [ ] ❌ Bad data-viz pairing — verify each chart type matches the data question
- [ ] ❌ Careless arrangement — F-pattern applied, hierarchy is clear
- [ ] ❌ Unnecessary variety — don't use 8 different chart types just to "show variety"
- [ ] ❌ Bad design — run the cognitive load check; would a manager understand this in 30 seconds?
