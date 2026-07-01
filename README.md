# Philippine Regional Poverty Divergence Tracker
### 24-Week Data Analytics Program — Phase 1: Foundations


## Problem Statement
I want to answer: 
**"Which Philippine regions are closing the poverty gap fastest from 2015 to 2023 — and which ones are being left behind?"**

More specifically: across four survey cycles (2015, 2018, 2021, 2023), how have poverty incidence, poverty thresholds, and income gaps shifted across all 17 regions? Are the improvements evenly distributed, or is the gap between the richest and poorest regions widening over time?

A secondary lens: **Where does Caraga (Region XIII) stand in this national picture?** In 2015, Caraga had the second-highest poverty incidence in the country at 39.1 percent. By 2021, it had dropped to 24.1 percent among families. By 2023, Caraga was among the regions that posted statistically significant decreases. Understanding whether this improvement is genuinely converging with national averages — or simply recovering from a deeper baseline — is the local question this project will answer.


## Audience
This project is for three audiences, each with a different use for the findings:
- **Regional planners and LGU policy staff (Caraga and comparable regions)** — need to understand whether poverty reduction programs are working faster or slower than the national trend, and which provinces within the region are leading or lagging.
- **National policymakers and researchers (NEDA, DSWD, academic institutions)** — need a clear cross-regional comparison to identify convergence or divergence patterns that inform budget allocation and social protection targeting.
- **The developer (me)** — needs a reproducible descriptive analytics project built entirely on verified PSA open data, demonstrating data wrangling, trend analysis, and chart-based storytelling for a portfolio.


## KPI or Key Metric
The primary metric is the **Poverty Incidence Rate (%) among families**, tracked per region across four survey years:

```
Poverty Incidence = (Number of Poor Families ÷ Total Families) × 100
```

Supporting metrics:
| Metric | What it measures |
|---|---|
| Poverty Incidence among Population (%) | Share of poor individuals, not just families |
| Annual Per Capita Poverty Threshold (PhP) | The income floor to escape poverty, adjusted by region |
| Income Gap (%) | How far below the threshold the average poor family falls |
| Poverty Gap (%) | Average shortfall as a share of the poverty threshold |
| Magnitude of Poor Families ('000) | Absolute headcount, not just rates |
| Point Change in Poverty Incidence | How many percentage points each region improved across periods |

The **convergence question** — whether poor regions are catching up to rich ones — is answered by plotting the point-change in poverty incidence against the starting poverty level. Regions that started poorest and improved fastest show convergence. Regions that started poorest and improved slowest show divergence.


## Likely Data Source
I will use the **PSA Full Year Official Poverty Statistics**, published through OpenSTAT and the PSA Poverty Statistics page.
Data is publicly available and covers 2015, 2018, 2021, and 2023 at national, regional, and provincial levels.

**Primary access points:**
- PSA OpenSTAT — Full Year Poverty Statistics: https://openstat.psa.gov.ph/PXWeb/pxweb/en/DB/DB__1E__FY/?tablelist=true
- PSA Poverty Statistics main page: https://psa.gov.ph/statistics/poverty
- PSA Poverty Statistical Tables: https://psa.gov.ph/statistics/poverty/stat-tables
- 2023 Full Year Poverty Statistics publication (PDF): https://psa.gov.ph/sites/default/files/phdsd/2023%20FY%20Official%20Poverty%20Statistics%20Publication_15August2024.pdf

**Tables to be used:**
- Table 1: Annual Per Capita Poverty Threshold and Poverty Incidence Among Families, by Region and Province (2018, 2021, 2023)
- Table 2: Poverty Incidence Among Population, by Region and Province (2018, 2021, 2023)
- Table 5 & 6: Magnitude of Poor Families and Population, by Region and Province
- Income Gap and Poverty Gap tables (2018, 2021, 2023)
- Updated 2015 and 2018 tables (accessible separately via PSA stat-tables page)



## Possible Final Output
The final output is a **semi-automated refresh dashboard** — a web-based visualization built so that when PSA releases new FIES-based poverty data (approximately every three years), replacing the source CSV file is all it takes for every chart to update automatically. No chart rebuilding, no code rewriting.

This is the appropriate architecture for this dataset. Because the PSA's FIES-based poverty statistics update on a fixed survey cycle rather than continuously, a real-time live dashboard is not meaningful here — the data simply does not change between cycles. What matters instead is that the dashboard is **designed to absorb the next data release (2026) with zero structural changes**.

**How the refresh works:**
```
PSA releases new FIES cycle data (e.g., 2026)
        ↓
Download updated CSV exports from PSA OpenSTAT
        ↓
Replace source CSV files in the project data folder
        ↓
Dashboard reads the new files on next load — all charts update automatically
        ↓
No code changes required
```

**Planned dashboard views:**
1. **Regional Poverty Incidence Heatmap** — All 17 regions across all available survey years in a matrix view, color-coded from deep red (high poverty) to light green (low poverty). New survey years appear as new columns automatically when the source CSV is updated.

2. **Convergence Scatter Plot** — X-axis: poverty incidence in the earliest available year. Y-axis: total percentage-point drop to the most recent year. Each dot is a region. The chart redraws with the new baseline and endpoint whenever new data is loaded.

3. **Caraga Province-Level Breakdown** — Bar charts for Agusan del Norte, Agusan del Sur, Surigao del Norte, Surigao del Sur, and Dinagat Islands across all survey years. Shows which provinces drive Caraga's regional improvement and which are lagging.

4. **Poverty Threshold vs. Poverty Incidence** — Line chart by region showing whether the cost of meeting basic needs is rising faster in poorer regions — a proxy for whether poverty is becoming harder or easier to escape over time.

5. **Income Gap Trend Lines** — How far below the poverty threshold the average poor family remains, by region, across all survey years. A declining income gap signals shallower poverty, not just fewer poor people.

**Stretch goal (post-Week 16):** Automate the CSV download step by querying the PSA OpenSTAT PX-Web API directly, so replacing the source file happens programmatically on each dashboard load rather than manually.


## Scope Note
This project covers all 17 Philippine regions, provincial-level breakdowns for Caraga specifically, and four FIES-based survey cycles: 2015, 2018, 2021, and 2023 — with the architecture ready to absorb the 2026 cycle. Analysis is descriptive; no predictive modeling is in scope. The goal is a clear, chart-driven answer to one question: are the poorest regions catching up, and where does Caraga stand in that story?

*Milestone 0 — Problem Statement*
*24-Week Data Analytics Foundations Program
