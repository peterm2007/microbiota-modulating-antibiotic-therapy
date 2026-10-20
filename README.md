# microbiota-modulating-antibiotic-therapy

# Microbiota-Modulating Antibiotic Therapy in ICUs: Results of a Retrospective Data and Prospective Pilot Study in Patients With Intra-Abdominal Infections

This repository contains the official Python implementation for the statistical analysis and predictive modeling presented in the paper: **"Microbiota-Modulating Antibiotic Therapy in ICUs: Results of a Retrospective Data and Prospective Pilot Study in Patients With Intra-Abdominal Infections"** (Chernevskaya et al., 2025).

## Overview

The study evaluates whether a preventive microbiota-modulating antibiotic strategy (utilizing bacterial protein synthesis and transcription inhibitors like doxycycline, gentamicin, and clarithromycin) improves clinical outcomes in critically ill patients with severe intra-abdominal infections (IAI). 

The analysis pipeline provided in this repository covers data preprocessing and advanced biostatistical modeling for **Stage 2 (Prospective Pilot Cohort, N=56)**.

### Analysis Pipeline
1. **Data Preprocessing & KNN Imputation:** Handling missing continuous clinical/laboratory covariates (BWI, ALT, AST, Creatinine, INR, WBC, PLT, Lactate, ICU LOS) using a \(K\)-Nearest Neighbors (KNN) algorithm to preserve data variance and internal structures.
2. **Propensity Score (PS) Calculation:** Estimating individual propensity scores via binomial logistic regression based on baseline clinical severity confounders: SOFA score, serum lactate, mechanical ventilation, septic shock, and malignancy.
3. **Multivariate Logistic Regression:** Evaluating the adjusted effect of microbiota modulation on the primary endpoint (**in-hospital mortality**) using the continuous propensity score as a covariate.
4. **Competing Risk Analysis (Fine-Gray Model):** Modeling the time from ICU admission to successful live discharge, treating ICU mortality as a competing risk event.

## Repository Structure

```text
├── README.md               # Repository documentation
├── requirements.txt        # Required Python libraries and versions
├── analysis.py             # Main Python script containing the full analysis pipeline
└── data.xlsx               # De-identified clinical dataset (Stage 2 pilot cohort)
```

## Getting Started

### Prerequisites

The analysis was executed using Python 3.14. 

The core libraries required are:
* `pandas` (>= 3.0.6)
* `numpy` (>= 2.5.0)
* `scikit-learn` (>= 1.6.0)
* `statsmodels` (>= 0.15.0)
* `lifelines` (>= 0.30.3)

### Running the Analysis

To perform the preprocessing, KNN imputation, propensity score adjustments, and competing risk regressions, execute the main script:

```bash
python analysis.py
```

## Key Statistical Outputs

* **Table 5 Replacement:** Multivariate logistic regression for in-hospital mortality demonstrating a pronounced clinical trend toward reduced adjusted odds of death in the Modulation Group (OR = 0.2219, 95% CI: 0.0399–1.2345, \(p = 0.0855\)).
* **Table 6 Replacement:** Fine-Gray subdistribution hazard regression establishing a descriptive, statistically null effect on time to live ICU discharge (adjusted SHR = 0.7985, 95% CI: 0.3393–1.8792, \(p = 0.6063\)), properly accounting for ICU mortality as a competing risk.

## Citation

If you use this code or dataset in your research, please cite our paper:

```text
Chernevskaya, E., Getsina, M., Burnatsev, K., Tsakoev, R., Meinarovich, P., Yakunina, E., & Beloborodova, N. (2025). Microbiota-Modulating Antibiotic Therapy in ICUs: Results of a Retrospective Data and Prospective Pilot Study in Patients With Intra-Abdominal Infections. (To be updated upon final publication).
```
