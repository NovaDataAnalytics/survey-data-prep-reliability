# Survey Data Cleaning & Reliability Analysis
### Perceived Supervisor Support, Burnout, and Intention to Leave Among Public Sector Employees in Gauteng

**Nova Data Analytics — Academic Research Support Series | Case Study 02 | Part 1 of 2**

---

> ⚠️ **This is a simulated case study created for educational and training purposes.**  
> The dataset is synthetically generated. Any resemblance to real individuals, organisations, or institutions is purely coincidental. See [DISCLAIMER.md](DISCLAIMER.md) for full terms.

---

## What This Repository Is

This repository accompanies a case study published by [Nova Data Analytics](https://www.novadataanalytics.co.za) demonstrating a complete survey data preparation and measurement quality workflow — the steps that must happen **before** any hypothesis testing, correlation analysis, or structural equation modelling can be considered defensible.

If you are an Honours, Masters, or Doctoral student working with Likert-scale survey data, this repository shows you exactly what to do with your raw data, why each step matters, and how to document every decision in a way that will hold up under examination.

---

## Study Context

A quantitative study examining three constructs among public sector employees in Gauteng:

| Construct | Abbreviation | Items | Scale |
|-----------|-------------|-------|-------|
| Perceived Supervisor Support | PSS | 6 | 5-point Likert |
| Burnout | BO | 6 | 5-point Likert |
| Intention to Leave | ITL | 4 | 5-point Likert |

**Raw sample:** 353 responses | **Clean sample:** 320 responses | **Retention rate:** 90.7%

---

## What Part 1 Covers

This notebook addresses the four questions every researcher must answer before running a single statistical test:

1. **Is the data free of response quality problems?** — Data cleaning across 8 issue types
2. **What does the sample look like?** — Descriptive statistics at item and construct level
3. **Do scores meet normality assumptions?** — Shapiro-Wilk, histograms, Q-Q plots
4. **Do the scales measure their constructs reliably and validly?** — Reliability and validity analysis

---

## Repository Structure

```
wellbeing-survey-analysis/
│
├── nova_wellbeing_survey.csv              # Raw dataset (353 rows, 23 columns)
├── nova_wellbeing_survey_clean.csv        # Clean dataset exported at end of notebook
├── nova_wellbeing_analysis_part1.ipynb    # Full analysis notebook
│
├── README.md                              # This file
├── DISCLAIMER.md                          # Educational use disclaimer
├── CONTRIBUTING.md                        # How to engage with this repository
└── LICENSE                                # Usage rights
```

---

## Notebook Sections

| Section | Content |
|---------|---------|
| 1 | Setup & data loading |
| 2 | Data cleaning — 8 checks including duplicates, out-of-range values, missing data (Little's MCAR test), straightlining, central tendency bias, and acquiescence flagging |
| 3 | Descriptive statistics — demographics, item-level stats, construct boxplots, Likert frequency distributions |
| 4 | Normality assessment — Shapiro-Wilk, histograms with KDE, Q-Q plots, parametric/non-parametric decision |
| 5 | Reliability analysis — Cronbach's α, inter-item correlations, CITC, alpha-if-item-deleted, Spearman-Brown |
| 6 | Validity checks — convergent (AIC), discriminant, common method bias (Harman's), known-groups validity |
| 7 | Part 2 handoff — KMO, Bartlett's test, CFA readiness, clean dataset export |

---

## Key Findings (Part 1)

| Construct | Mean | SD | Cronbach's α | Interpretation |
|-----------|------|-----|-------------|----------------|
| PSS | 3.08 | 0.89 | 0.949 | Excellent |
| Burnout | 3.18 | 0.87 | 0.939 | Excellent |
| ITL | 1.48 | 0.58 | 0.880 | Good |

All corrected item-total correlations exceeded the 0.30 threshold. No item improved alpha if deleted. Common method bias was not a major concern (Harman's first factor < 50%).

---

## Requirements

```bash
pip install pandas numpy matplotlib scipy pingouin factor_analyzer pyampute
```

| Package | Purpose |
|---------|---------|
| `pandas`, `numpy` | Data manipulation |
| `matplotlib` | Visualisation |
| `scipy` | Statistical tests |
| `pingouin` | Reliability analysis (Cronbach's α, CITC, pairwise correlations) |
| `factor_analyzer` | Harman's single factor test, KMO, Bartlett's test |
| `pyampute` | Little's MCAR test |

---

## How to Use This Repository

**If you are a postgraduate researcher:**  
Work through the notebook top to bottom. Every cell includes a markdown explanation of what is being done and why. Use the methodology as a template for your own dissertation's data preparation chapter.

**If you are reviewing Nova's work:**  
The notebook is fully documented and reproducible. Every analytical decision is justified with its rationale and a supporting reference. Run all cells in sequence against the raw dataset to replicate all outputs.

---

## Part 2 — Coming Soon

Part 2 will begin from `nova_wellbeing_survey_clean.csv` and cover:

- **Confirmatory Factor Analysis (CFA)** using `semopy` — testing the pre-specified 3-factor measurement model
- **Model fit indices** — CFI, TLI, RMSEA, SRMR
- **Full convergent and discriminant validity** — AVE, composite reliability, Fornell-Larcker criterion
- **Hypothesis testing** — Spearman correlations with effect sizes
- **Group comparisons** — gender, tenure, department

> **Note on EFA:** Exploratory Factor Analysis is not planned. The three-construct structure is pre-specified by validated theory and established instruments. CFA directly tests the specified measurement model — running EFA before CFA on a theoretically defined instrument treats a confirmatory question as exploratory.

---

## About Nova Data Analytics

[Nova Data Analytics](https://www.novadataanalytics.co.za) is a South African data analytics consultancy providing analytics services, training, and academic research support. Our academic support offering is designed specifically for postgraduate researchers — from data cleaning and statistical analysis to results interpretation and write-up guidance.

If you are working on your own survey study and need support at any stage of the analysis process, we would love to hear from you.

📧 info@novadataanalytics.co.za  
🌐 [novadataanalytics.co.za](https://www.novadataanalytics.co.za)  
💼 [LinkedIn](https://www.linkedin.com/company/novadataanalytics-coza)  
💻 [GitHub](https://github.com/NovaDataAnalytics)

---

## Citation

If you use this dataset or notebook in your own work, please cite as:

```
Nova Data Analytics. (2025). Survey Data Cleaning & Reliability Analysis:
Perceived Supervisor Support, Burnout, and Intention to Leave Among Public
Sector Employees in Gauteng [Educational case study]. 
https://github.com/NovaDataAnalytics/wellbeing-survey-analysis
```

---

## References

- Schafer, J. L., & Graham, J. W. (2002). Missing data: Our view of the state of the art. *Psychological Methods, 7*(2), 147–177.
- Clark, L. A., & Watson, D. (1995). Constructing validity: Basic issues in objective scale development. *Psychological Assessment, 7*(3), 309–319.
- Vallat, R. (2018). Pingouin: Statistics in Python. *Journal of Open Source Software, 3*(31), 1026.
- George, D., & Mallery, P. (2003). *SPSS for Windows step by step* (4th ed.). Allyn & Bacon.
- Little, R. J. A. (1988). A test of missing completely at random for multivariate data with missing values. *Journal of the American Statistical Association, 83*(404), 1198–1202.
