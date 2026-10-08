# COVID-19, Economic Disparity, Vaccination, and Case Fatality Rate Analysis

An undergraduate public health data analysis project examining the empirical relationships between national economic level (`gdp_per_capita`), vaccine rollout dynamics, diagnostic surveillance disparities, and Case Fatality Rates (CFR) across 80 countries using panel data from Our World in Data (OWID).

---

## Overview

This study examines associations between national income levels and reported pandemic-response indicators and outcomes across countries. Countries were stratified into the top 20% (High-GDP) and bottom 20% (Low-GDP) based on each country's maximum observed `gdp_per_capita`. The analysis compares vaccination indicators, reported cases and deaths, testing-data missingness, and country-level Case Fatality Rates (CFR). These are descriptive comparisons and do not establish causal effects.

---

## Research Questions

1. Vaccination Disparity: How did population vaccination completion rates and daily rollout speeds differ between High-GDP and Low-GDP countries?
2. Surveillance & Case Data: How did testing-data missingness differ between GDP groups, and how should reported case figures be interpreted in light of those differences?
3. Clinical Outcome Disparity: How did cumulative Case Fatality Rate (CFR) differ between the two economic cohorts when evaluating fatal outcomes among confirmed cases?

---

## Data & Cohort Definition

All analyses were conducted using historical country-level panel data from the **Our World in Data (OWID)** COVID-19 repository:

- Economic Stratification: Countries were segmented using national per capita GDP (`gdp_per_capita`) quantiles:
  - High-GDP Cohort (Top 20%): Per capita GDP $\ge \$33,132.32$ (40 nations).
  - Low-GDP Cohort (Bottom 20%): Per capita GDP $\le \$3,364.93$ (40 nations).
  - Intermediate Cohort: Intermediate 60% of countries were excluded to focus on extreme economic contrast cohorts ($N=80$ total nations analyzed).
- Core Variables: `gdp_per_capita`, `people_fully_vaccinated_per_hundred`, `new_vaccinations_smoothed_per_million`, `new_cases_per_million`, `total_deaths_per_million`, `total_cases`, `total_deaths`, and `new_tests_per_thousand`.

---

## Analytical Workflow

```mermaid
flowchart LR
    A["OWID Panel Data"]
    --> B["GDP Quantile Stratification<br/>(Top 20% vs. Bottom 20%)"]
    --> C["Vaccination Response Analysis<br/>(Completion Rate & Pace)"]
    --> D["Reported Case & Mortality Audit<br/>(Superficial Paradox)"]
    --> E["Testing Missingness Diagnostic<br/>(Surveillance Bias)"]
    --> F["Case Fatality Rate (CFR) Analysis"]
    --> G["Longitudinal Visualization"]
```

---

## Key Findings

1.Vaccination Completion Disparity: High-GDP countries achieved an average vaccination completion rate of 61.60%, compared to 14.45% in Low-GDP countries (~4.3-fold disparity).
2. Vaccination Rollout Pace: The mean daily smoothed vaccination rate across retained country-date observations was 2,578.40 vaccinations per million per day in the High-GDP group and 821.19 per million per day in the Low-GDP group. These are pooled observation means, not equal-weighted means of country-level rates. The analysis first excludes rows missing `total_cases` or `total_deaths`; pandas omits missing values in the vaccination-rate column when calculating each mean.
3. Reported Cases, Deaths, and Testing Missingness: Mean reported daily new cases were 242.87 vs. 9.13 per million in High- vs. Low-GDP groups. The maximum observed cumulative deaths per million among retained country-date observations was 3,693.61 in High GDP and 579.72 in Low GDP. Testing data were missing in 65.76% of High-GDP observations and 91.18% of Low-GDP observations; these descriptive differences warrant caution when interpreting reported case figures.
4. Case Fatality Rate (CFR): The mean country-level CFR was 0.51% for High-GDP and 2.01% for Low-GDP countries in the stored CFR table. This table includes 78 countries after the code's data-availability filters: 38 High-GDP and 40 Low-GDP countries.

---

## Selected Visualizations

"results/figures/09_longitudinal_vaccination_trajectory.png" : illustrating the rapid coverage plateau in High-GDP nations versus the delayed, lower-ceiling rollout in Low-GDP nations.

"results/figures/08_cfr_distribution_boxplot.png" 
"results/figures/06_missing_rate_testing_data.png": National Case Fatality Rate (CFR) distributions, showing tightly bounded low mortality in High-GDP nations versus wider interquartile range and high-fatality outliers in Low-GDP nations. // Missing value rates in diagnostic testing data, highlighting severe surveillance gaps (>91% missing) in Low-GDP nations.

"results/figures/07_avg_case_fatality_rate.png": Comparison of mean Case Fatality Rate (CFR) between High-GDP (0.51%) and Low-GDP (2.01%) cohorts.


---

## Limitations

- Ecological Study Design: Aggregate country-level comparisons cannot account for individual-level patient risks, comorbidities, or clinical trajectories.
- Unmeasured Demographic Confounders: Differences in national population age structures (such as higher median age in high-income nations) were not adjusted for.
- Historical Surveillance Missingness: High missingness in historical testing and hospitalization variables limits direct modeling of daily healthcare utilization.
- Dataset and CFR coverage: Numerical values reflect the dataset snapshot used to generate the stored outputs. The source data are absent from this repository, so the analysis cannot be independently rerun from the repository alone. The CFR calculation takes the maximum observed `total_cases` and maximum observed `total_deaths` separately for each country before calculating the ratio; those maxima are not guaranteed to come from the same date.

---

## Contribution

This project was conducted as an individual undergraduate data analysis study:
- Formulated the research scope, analytical questions, and cohort stratification methodology.
- Implemented quantile-based economic cohort selection and data cleaning workflows using pandas.
- Evaluated vaccination rollout velocity and population-level completion rates.
- Conducted the diagnostic testing missingness audit to investigate the apparent case-count paradox.
- Computed national cumulative Case Fatality Rates (CFR) and analyzed distribution metrics.
- Designed publication-style visualizations using Matplotlib and Seaborn and exported quantitative summary tables.

---

## Tools

- Programming: Python 3.9+
- Data Manipulation: pandas, NumPy
- Visualization: Matplotlib, Seaborn
- Environment: Jupyter Notebook

---

