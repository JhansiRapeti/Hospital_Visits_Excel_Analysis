Cleaned and analyzed 600 hospital visits, built an operations dashboard
Hospital Visits Analysis (Excel)

Project Overview
The Director of Hospital Operations asked for a review of patient visits for
**July–September 2026** across six departments. The data came directly from the
hospital system and contained several data quality issues. I cleaned the data,
answered 8 business questions, and built a one-page operations dashboard.


Business Questions
1. What are total visits, total billing, and average bill per visit?
2. Which department has the most visits, and which brings the most billing?
3. What is the average length of stay (ALOS) for each department?
4. How are visits trending month to month?
5. What is the payer mix (billing by insurance type)?
6. Which day of the week is busiest for the Emergency department?
7. Which age group (Child, Adult, Senior) has the highest average bill?
8. Which doctors see the most patients?

Dataset
| Sheet | Rows | Description |
|---|---|---|
| Visits | 615 (raw) → 600 (clean) | Visit ID, patient ID, age, department, doctor, insurance, admit/discharge dates, bill |
| Doctors | 22 | Doctor ID, name, department, years of experience |

Data Cleaning Steps
- Kept an untouched **raw copy** before making changes
- Removed **15 duplicate** visits (615 → 600)
- Standardized department and insurance names with **TRIM** and **PROPER**
- Found look-alike values: **"Self Pay" vs "Self-Pay"** — merged them with Find & Replace
- Converted **bill amounts stored as text** to numbers
- Flagged **6 missing bill amounts** instead of guessing values
- Found **2 visits with discharge before admission** (negative length of stay) — dates were reversed, so I swapped them and logged the change
- Found **4 visits with blank age** — classified them as "Unknown" instead of letting them fall into "Child"
- Kept a **cleaning log** of every change

Analysis Steps
- Calculated **Length of Stay** (Discharge − Admit), **Month**, and **Day of Week**
- Created **Age Groups** with **IFS**: Child (<18), Adult (18–64), Senior (65+), Unknown (blank)
- Used **XLOOKUP** on Doctor_ID to bring in doctor names
- Built **pivot tables** with Sum, Count, Average and % of Total
- Built a **dashboard** with KPIs, pivot charts and key insights

Key Results
| KPI | Value |
|---|---|
| Total Visits | 600 |
| Total Billing | $2,904,580 |
| Average Bill per Visit | $4,890 |

Key Insights
- **Emergency has the most visits (171)** but brings only $206,160 in billing.
  **Cardiology has fewer visits (98) but brings $1,084,470 — 37% of all billing.**
- **Cardiology patients stay the longest (ALOS 3.1 days)**; Emergency patients usually
  go home the same day (ALOS 0.6 days).
- **Visits declined** from July (209) to September (184) — still lower even per day
  (6.7 → 6.1 visits/day), so the drop is real.
- **Payer mix:** Private insurance 43% of billing, Medicare 25%, Medicaid 24%, Self-Pay 8%.
- **Sunday is the busiest day for Emergency** (40 visits vs 18 on Thursday) — possibly
  because regular clinics are closed on weekends.
- **Seniors have the highest average bill ($5,869)**, compared to Adults ($5,489) and
  Children ($2,716). Seniors make up most Cardiology patients, the highest-billing department.
- **Dr. Linda Shah (D03, Emergency)** sees the most patients (47).

Recommendations
- **Add Emergency staff on Sundays** to handle the weekend peak.
- **Plan Cardiology bed capacity** — it brings the most billing and has the longest stays.
- **Investigate the Q3 visit decline** before the next quarter.
- **Monitor Self-Pay accounts** for payment follow-up.
- **Improve data entry**: add date checks (discharge ≥ admit) and dropdown lists for
  insurance types to prevent look-alike values.

What I Learned
- **Look-alike values** ("Self Pay" vs "Self-Pay") can't be fixed by TRIM or PROPER — check every filter list.
- **Sanity-check calculated columns** — a negative length of stay revealed reversed dates.
- **Blanks in IFS count as 0** — always test for blanks first.
- **Group by ID, not name** — two different doctors shared the same name ("Dr. Mary Iyer"),
  and grouping by name merged them into one.
- Separate **what the data shows** from **possible explanations**.

Tools & Skills
Excel · Data Cleaning · TRIM / PROPER · Find & Replace · XLOOKUP · IFS · COUNTIFS ·
Date calculations · Pivot Tables · Pivot Charts · Dashboard Design

Files
- `Hospital_Project_Jhansi.xlsx` — full workbook (raw data, cleaned data, pivots, dashboard)
- `dashboard.png` — screenshot of the final dashboard

Dashboard
![Dashboard](dashboard.png)

Author
**Jhansi Rapeti** — Aspiring Data Analyst
