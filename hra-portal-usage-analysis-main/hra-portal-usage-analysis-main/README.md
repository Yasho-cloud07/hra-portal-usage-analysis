# HRA Portal Usage Analysis
### Analyzing & Visualizing Usage for Human Reference Atlas User Interfaces Using Amazon CloudFront Logs

**Course:** E538/E438 — Information Visualization | Indiana University Bloomington | Spring 2026  
**Client:** Rishi Mulkutkar · HRA UI Dev Team / CNS Center, Indiana University  
**GitHub:** https://github.com/Yasho-cloud07/hra-portal-usage-analysis  
**Data (Google Drive):** https://drive.google.com/drive/folders/14KixFe93ZxHf0ps8mBA-hKYqCJHoiRvG  
**Code & Notebooks (Google Drive):** https://drive.google.com/drive/u/1/folders/12W2j2jBTXdcyVI4CiuY4FO9p3f6Rnmd0

---

## Team

| Name | Role |
|---|---|
| Yashoneel Bingley | Team Lead |
| Sahej Vasandi | Trends & Time-Series Analysis |
| Pratham Mody | Geography & CDE Analysis |
| Nachiket Kulkarni | Data Pipeline (DuckDB) |
| Shreyash Nadgouda | RUI & EUI Product Analysis |

---

## Project Overview

The Human Reference Atlas (HRA) Portal is a NIH-funded biomedical research platform at Indiana University, providing three user interfaces for researchers worldwide:

- **RUI** — Registration User Interface (3D tissue block spatial registration)
- **EUI** — Exploration User Interface (anatomical structure browsing)
- **CDE** — Cell Data Explorer (cell-level dataset analysis)

This project delivers the **first structured behavioral analytics study** of the HRA Portal, transforming **12.7 million raw Amazon CloudFront HTTP log records** spanning **28 months (October 2023 – January 2026)** into actionable UX insights for the development team.

### Key Numbers at a Glance

| Metric | Value |
|---|---|
| Raw CloudFront records | 12.7 million |
| Interaction events analyzed | 6,870,577 |
| Coverage window | Oct 2023 – Jan 2026 (28 months) |
| Countries reached | 209 |
| Bot / AI traffic filtered | 37.3% |
| Genuine human events | 4.31M (62.7%) |

---

## Repository Structure

```
hra-portal-usage-analysis/
│
├── README.md                        ← You are here
├── HOW_TO.md                        ← Full setup and usage guide
│
├── data/                            ← Cleaned CSV datasets (4 files)
│   ├── monthly_usage.csv            ← 106 rows: events + unique users per month per interface
│   ├── feature_frequency.csv        ← 81,138 rows: per-endpoint event counts
│   ├── traffic_summary.csv          ← 3 rows: human / bot / AI crawler totals
│   └── geography_summary.csv        ← 209 rows: per-country event + user counts
│
├── notebooks/                       ← Jupyter analysis notebooks
│   ├── HRA_RUI_EUI_Analysis.ipynb   ← RUI & EUI usage trends
│   ├── HRA_Visualization.ipynb      ← All 7 publication-quality figures
│   ├── HRA_Info_Vis.ipynb           ← Full information visualization pipeline
│   └── HRA_insights_Analysis.ipynb  ← CDE deep dive + intelligence dashboard
│
├── report/                          ← Final deliverables (open in browser)
│   ├── HRA_Analysis_Report.html     ← Main interactive report
│   └── HRA_insights_Report.html     ← CDE & intelligence dashboard report
│
├── outputs/                         ← All generated figures (PNG)
│   ├── fig2_usage_trends.png
│   ├── fig3_feature_distribution.png
│   ├── fig4_bot_traffic.png
│   ├── fig5_global_reach.png
│   ├── fig6_cde_analysis.png
│   └── fig7_intelligence_dashboard.png
│
└── scripts/                         ← Standalone Python scripts
    ├── pipeline.py                  ← DuckDB-on-Parquet data pipeline
    ├── bot_classification.py        ← User-Agent string classifier
    └── visualizations.py            ← Figure generation scripts
```

---

## Quick Start — View Results (No Setup Required)

The fastest way to explore the project is to open the pre-built HTML reports directly in your browser. No Python, no Jupyter, no installation needed.

```
1. Download or clone this repository
2. Open  report/HRA_Analysis_Report.html  in any browser
3. Open  report/HRA_insights_Report.html  for CDE and dashboard analysis
```

Everything is self-contained in the HTML files.

---

## Key Findings Summary

### RUI — 818,780 Events
- November 2024 spike: **189,235 events (~10× average monthly volume)** driven by a HuBMAP Consortium release
- Tissue Collision Check endpoint dominates: **436,343 events (53% of all RUI traffic)** — every 3D mouse drag fires a real-time collision API call
- Bot-adjusted genuine human events: ~513,000

### EUI — The Growth Story
- **+200% year-over-year unique user growth**: ~450/month (early 2024) → ~2,900/month (Dec 2025)
- Surpasses RUI in monthly unique users by December 2025
- Bot-adjusted genuine human events: ~380,000

### CDE — Critical Finding
- **78% home-page bounce rate**: users land and leave without exploring
- October 2024 HuBMAP demo spike: 772 new users, **zero lasting retention**
- Only 95 events ever reached `/cde/visualize` (the core tool) across 28 months
- Structural onboarding intervention required — not new feature development

### Traffic & Geography
- **37.3% non-human traffic**: 32.5% traditional bots + 4.8% AI crawlers (GPTBot, ClaudeBot, CCBot)
- Platform reaches **209 countries**; US contributes 74.7% of events
- Singapore (9.9× events/user ratio): strongest legitimate international research hub

---

## Tools & Technologies

| Tool | Purpose |
|---|---|
| Python 3.x | Core analysis language |
| **DuckDB** | High-performance SQL queries on Parquet files (replaced pandas — see HOW_TO.md) |
| Pandas | Data manipulation post-query |
| Matplotlib + Seaborn | Static visualization (Figs 2–7) |
| Plotly | Interactive dashboard elements |
| Jupyter Notebooks | Analysis and exploration environment |
| Amazon CloudFront | Source of raw server-side log data |

---

## License & Citation

This project was completed as part of the E538/E438 Information Visualization course at Indiana University Bloomington, Spring 2026. All data belongs to the HRA UI Dev Team and CNS Center, Indiana University. Code is available for academic and research reference.

For questions, contact the team via the GitHub repository.
