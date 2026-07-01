# Philippine Regional Poverty Divergence Tracker
### 24-Week Data Analytics Program — Phase 1: Foundations | Milestone 1

---

## Problem Statement (Summary)

I want to answer: **"Which Philippine regions are closing the poverty gap fastest from 2015 to 2023 — and which ones are being left behind?"**

*(Full problem statement, audience, KPIs, and dashboard design are in M0_README.md)*

---

## Data Source Notes

### Primary Source

- **Name:** PSA Full Year Official Poverty Statistics — OpenSTAT Portal
- **URL:** https://openstat.psa.gov.ph/PXWeb/pxweb/en/DB/DB__1E__FY/?tablelist=true
- **Format:** CSV / XLSX — exported directly from the PX-Web portal table viewer; no login or registration required
- **Coverage:** All 17 Philippine regions and their provinces; survey years 2015, 2018, 2021, and 2023; national, regional, provincial, and highly urbanized city (HUC) level; last updated September 2024
- **Why it fits the problem:** This is the PSA's authoritative source for official poverty incidence, poverty thresholds, income gaps, and magnitude of poor families by region and province. Every KPI in the problem statement — incidence rate, threshold, income gap, poverty gap, and magnitude of poor — is directly published in this portal and exportable as a flat CSV, covering all four survey cycles needed to track regional convergence over time.
- **Known limitations:**
  - The 2015 tables use a 2006-based CPI while 2018 onward use a 2012-based CPI — poverty thresholds in peso terms are not directly comparable across cycles; only incidence rates and gap percentages are.
  - Provincial estimates for very small provinces carry coefficients of variation above 20%, which the PSA flags as unreliable for ranking; cluster groupings must be used instead of point rankings.
  - Tables 5 and 6 (magnitude of poor families and population) are currently published up to 2021 only on the portal — the 2023 magnitude figures exist in the official PDF but have not yet been added to the OpenSTAT tables.
  - HUC-level breakdowns (Table 1a) are available from 2018 onward only, not 2015.
  - BARMM and Sulu 2021 figures were revised post-release due to food price corrections — always download from the portal, not from cached older files.

---

### Fallback Source

- **Name:** PSA Philippine Statistical Yearbook (PSY) — Chapter 2: Income and Prices
- **URL:** https://psa.gov.ph/philippine-statistical-yearbook
- **Direct file:** https://psa.gov.ph/system/files/psy/2_2023.xlsx
- **Format:** XLSX — single workbook, direct download, no portal interaction needed
- **Coverage:** National and regional level; multi-year poverty and income tables; published annually; the 2023 PSY edition consolidates data through the 2021 FIES cycle (2023 FIES data will appear in the 2024 PSY edition)
- **Why it could still work:** The PSY Chapter 2 compiles the most critical regional poverty tables — incidence, threshold, income gap, and magnitude — into one pre-formatted Excel file. If the OpenSTAT portal is inaccessible, changes its table structure, or requires login at any point during the project, this file provides the same regional-level data through a completely different access method: a static direct download with no dependency on the PX-Web system.
- **Known limitations:**
  - Provincial-level detail for Caraga's five provinces is incomplete — the PSY prioritizes regional summaries, so the Caraga deep-dive work requires Source 1 to be restored.
  - The Excel workbook uses merged cells, inline footnote rows, and inconsistent region-code formatting that require preprocessing before analysis — more cleaning effort than the OpenSTAT CSV export.
  - The 2023 PSY still reflects 2021 poverty figures; the 2024 PSY edition incorporating 2023 FIES data was not yet available at the time of writing.
  - This source has the same underlying data weakness as Source 1 only in that both are PSA — but the access method, file format, and hosting location are entirely different, so a portal outage or URL change on one does not affect the other.

---

## Repository Structure

```
poverty-divergence-tracker/
│
├── data/
│   ├── raw/                        # Unmodified exports from PSA OpenSTAT
│   │   ├── psa_table1_families_incidence_2015_2023.csv
│   │   ├── psa_table2_population_incidence_2015_2023.csv
│   │   ├── psa_table5_magnitude_families.csv
│   │   ├── psa_table6_magnitude_population.csv
│   │   ├── psa_table10_income_gap.csv
│   │   └── psa_table11_poverty_gap.csv
│   │
│   └── processed/                  # Cleaned, merged files (Week 3+)
│
├── notebooks/
│   └── 01_data_inspection.ipynb    # Initial field check and row counts
│
├── scripts/
│   └── clean_psa_exports.py        # Schema normalization for OpenSTAT CSVs
│
├── requirements.txt
└── README.md
```

---

## Requirements

```
pandas==2.2.2
openpyxl==3.1.2
matplotlib==3.8.4
seaborn==0.13.2
plotly==5.22.0
jupyter==1.0.0
numpy==1.26.4
```

---

## Submission Self-Check

| # | Check | Status |
|---|---|---|
| 1 | Repo has required folder structure — `data/raw/`, `data/processed/`, `scripts/`, `notebooks/` | ✅ Initialized — raw PSA CSV files placed in `data/raw/` |
| 2 | `requirements.txt` exists at the repo root | ✅ Seven dependencies listed; install via `pip install -r requirements.txt` |
| 3 | README describes the problem, data source, and project goal | ✅ Problem statement in `M0_README.md`; source notes, coverage checks, and limitations in this file |
| 4 | Commit hash points to the latest submission snapshot | ⬜ Fill in after final `git commit` — run `git log --oneline -1` and paste hash below |

**Commit hash:** `________________________________________`

---

*Milestone 0 — Problem Statement | Complete*
*Milestone 1 — Data Source Discovery & Feasibility Check | Complete*
*24-Week Data Analytics Foundations Program*
