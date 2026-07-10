# Philippine Regional Poverty Divergence Tracker
**24-Week Data Analytics Foundations Program — Froncoyz Verano**

---

## Project Overview
This project tracks regional poverty convergence across all 17 Philippine regions
using official PSA open data from 2015 to 2023.

**Central question:** Which Philippine regions are closing the poverty gap fastest —
and which ones are being left behind?

A secondary lens follows Caraga (Region XIII), which had one of the highest poverty
incidence rates in 2015 and has since posted significant reductions.

---
## Milestones

| Milestone | Description | Status |
|---|---|---|
| M0 | Problem Statement | ✅ Complete — see M0_README.md |
| M1 | Data Source Discovery & Feasibility Check | ✅ Complete — see M1_README.md |
| M2 | Repo Initialized & Dev Environment Setup | ✅ This week |

---
## Repo Structure

dep-starter-kit/
├── data/
│   ├── raw/          # Unmodified CSV exports from PSA OpenSTAT
│   └── processed/    # Cleaned, analysis-ready files
├── notebooks/        # Jupyter notebooks for exploration and analysis
├── output/           # Chart exports and report outputs
├── scripts/          # Python cleaning and analysis scripts
├── M0_README.md      # Problem statement
├── M1_README.md      # Data source discovery and feasibility check
├── README.md         # This file
└── requirements.txt  # Python dependencies


---

## Data Source
**Primary:** PSA Full Year Official Poverty Statistics
https://openstat.psa.gov.ph/PXWeb/pxweb/en/DB/DB__1E__FY/?tablelist=true

**Fallback:** PSA Philippine Statistical Yearbook, Chapter 2
https://psa.gov.ph/system/files/psy/2_2023.xlsx

---

## Setup
```bash
git clone https://github.com/Froncoyz/dep-starter-kit.git
cd dep-starter-kit
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # Mac/Linux
pip install -r requirements.txt
```
