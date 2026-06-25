# Suspension Bracket FEA Multi-Variant Analysis

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Tableau](https://img.shields.io/badge/Tableau-Public-orange)
![Domain](https://img.shields.io/badge/Domain-CAE%20%7C%20Mechanical%20Engineering-green)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## Problem Statement

A mechanical engineering team runs FEA simulations on **4 design variants**
of an automotive suspension bracket. This project analyzes simulation results
to identify the best performing design and critical failure zones using a
complete data analytics pipeline.

> **Business Question:** Which suspension bracket design variant should
> the engineering team proceed with for prototype development?

---

## Tools & Technologies

| Category | Tools |
|---|---|
| Data Cleaning | Python, pandas, numpy |
| Visualization | matplotlib, seaborn |
| Statistical Analysis | scipy, statsmodels, scikit-learn |
| Dashboard | Tableau Public |
| Report | reportlab (PDF) |
| Domain | CAE, FEA, Mechanical Engineering |

---

## Dataset

- **Source:** Synthetic FEA simulation dataset
- **Size:** 1,800+ nodes × 16 columns (after cleaning)
- **Variants:** Variant A, B, C, D
- **Load Cases:** Static, Dynamic, Fatigue
- **Zones:** Mounting Hole, Weld Joint, Bracket Arm, Rib Section, Base Plate
- **Key variables:** Von Mises Stress, Displacement, Safety Factor,
  Stress Ratio, Performance Score, Failure Risk

---

## Project Structure

```
structural-fea-dashboard/
│
├── data/
│   ├── raw/
│   │   └── fea_simulation_raw.csv       ← messy dataset 
│   └── processed/
│       └── Simulation_data_Cleaned_with_pandas.csv     ← cleaned dataset
│
├── notebooks/
│   ├── Simulation_Variant_Analysis.ipynb            ← Data Cleaning, EDA, Statistical Analysis
│   
├── reports/
│   ├── FEA_Findings_Report.pdf          ← 2-page findings summary
│
└── README.md
```

---

## Key Findings

### Recommended Design: Variant D

| Metric | Variant A | Variant B | Variant C | **Variant D** |
|---|---|---|---|---|
| Mean Stress (MPa) | 136.9 | 141.0 | 147.2 | **138.5** |
| Median Stress (MPa) | 124.2 | 129.2 | 133.3 | **126.8** |
| IQR (MPa) | 95.88 | 100.39 | 107.30 | **93.99 ✅** |
| Mean Safety Factor | 3.99 | 3.69 | 6.36 | **4.16 ✅** |
| % High Risk Nodes | 26.1% | 28.0% | 29.5% | **25.6% ✅** |
| Performance Score | 0.465 | 0.443 | 0.424 | **0.477 ✅** |

**Variant D recommended** — lowest IQR (most consistent design),
highest safety factor, lowest % high-risk nodes, best performance score.
ANOVA confirms differences are statistically significant (p < 0.05).

---

### Critical Zone Analysis

| Zone | Mean Stress | Risk Level |
|---|---|---|
| Mounting Hole | 212.2 MPa | 🔴 Critical |
| Weld Joint | 194.3 MPa | 🔴 Critical |
| Bracket Arm | 129.3 MPa | 🟡 Moderate |
| Rib Section | 98.1 MPa | 🟢 Low |
| Base Plate | 75.1 MPa | 🟢 Safe |

Mounting Hole and Weld Joint require priority redesign attention.

---

### Load Case Impact

| Load Case | Mean Stress | vs Static |
|---|---|---|
| Dynamic | 165.5 MPa | +30% ⚠️ |
| Fatigue | 130.2 MPa | +2.4% |
| Static | 127.3 MPa | Baseline |

Dynamic loading is the primary design driver — 30% higher stress
than static loading across all variants.

---

## Statistical Validation

| Test | Result | Conclusion |
|---|---|---|
| ANOVA | p < 0.05 | Variant differences are statistically real |
| Tukey HSD | Variant C significantly different | A and D perform similarly |
| Regression R² | Moderate fit | Stress ratio is strongest SF predictor |
| Pareto (80/20) | 2 zones = majority of failures | Focus on Mounting Hole and Weld Joint |

---

## Engineering Recommendations

1. **Proceed with Variant D** for physical prototype development
2. **Redesign Mounting Hole** — increase fillet radius (212.2 MPa average)
3. **Review Weld Joint geometry** — second most critical zone (194.3 MPa)
4. **Prioritize dynamic load cases** in next simulation batch
5. **Use Steel** for production — cost-effective with SF = 2.31 (above 1.5 threshold)
6. **Avoid Cast Iron** — SF of only 1.84, too close to minimum threshold

---

## Dashboard

**Live Tableau Dashboard:**
[View on Tableau Public](https://public.tableau.com/app/profile/vishnu.priya.kapu/viz/Suspension_Bracket_FEA_Multi_Variant_Analysis/01_Executive_Summary)

Dashboard includes 4 pages:
- Executive Summary (KPIs + recommendation)
- Variant Comparison (box plots, bar charts)
- Zone Analysis (heatmap, risk breakdown)
- Simulation Performance (mesh vs solve time)

---

## How to Run

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn jupyter
```

### Steps
```bash
# Clone the repository
git clone https://github.com/[your-username]/structural-fea-dashboard.git
cd structural-fea-dashboard

# Run notebooks in order
jupyter notebook notebooks/01_data_generation.py
jupyter notebook notebooks/02_data_cleaning.ipynb
jupyter notebook notebooks/03_eda.ipynb
jupyter notebook notebooks/04_statistical_analysis.ipynb
```

---

## Findings Report

Full 2-page findings report available in the `reports/` folder:
- [FEA_Findings_Report.pdf](reports/FEA_Findings_Report.pdf)
- [FEA_Findings_Report.docx](reports/FEA_Findings_Report.docx)

---

## About This Project

This project demonstrates a complete data analytics workflow applied to
a CAE engineering domain — combining mechanical engineering domain knowledge
with data analysis skills including data cleaning, EDA, statistical analysis,
and interactive dashboard building.

**Domain:** Automotive CAE / Structural Analysis
**Analyst:** Vishnu priya Kapu
**Year:** 2025
