# Microbiota-Modulating Antibiotic Therapy in ICUs: Results of a Retrospective Data and Prospective Pilot Study in Patients With Intra-Abdominal Infections

This repository contains the official Jupyter Notebook implementation for the statistical analysis and predictive modeling presented in the paper: **"Microbiota-Modulating Antibiotic Therapy in ICUs: Results of a Retrospective Data and Prospective Pilot Study in Patients With Intra-Abdominal Infections"** (Chernevskaya et al., 2026).

## Overview

The study evaluates whether a preventive microbiota-modulating antibiotic strategy (utilizing bacterial protein synthesis and transcription inhibitors like doxycycline, gentamicin, and clarithromycin) improves clinical outcomes in critically ill patients with severe intra-abdominal infections. 

The primary analysis pipeline provided in this interactive notebook covers data preprocessing and advanced biostatistical modeling for **Stage 2 (Prospective Pilot Cohort, N=56)**.

### Analysis Pipeline
1. **Categorical & Continuous Baseline Analysis:** Performing baseline cohort comparisons using the two-sided Mann-Whitney U test (for continuous data) and Fisher's exact test (for categorical variables).
2. **Data Preprocessing & KNN Imputation:** Handling missing continuous clinical/laboratory covariates using a K-Nearest Neighbors (KNN) algorithm with global seed setting to ensure strict computational reproducibility.
3. **Propensity Score (PS) Calculation:** Estimating individual propensity scores via multivariable binomial logistic regression based on clinical confounders (SOFA score, serum lactate, mechanical ventilation, septic shock, and malignancy).
4. **Multivariate Logistic Regression:** Evaluating the adjusted effect of microbiota modulation on the primary endpoint (**in-hospital mortality**) using the continuous propensity score as a covariate.
5. **Competing Risk Analysis (Fine-Gray Model):** Modeling the time from ICU admission to successful live discharge, properly treating ICU mortality as a competing risk event, and plotting the Cumulative Incidence Functions (CIF).

## Repository Structure

```text
├── README.md               # Repository documentation
├── requirements.txt        # Required Python libraries and versions
├── modulation.ipynb        # Main Jupyter Notebook containing the full analysis pipeline
└── Supplementary data.xlsx # De-identified clinical dataset (Stage 2 pilot cohort)
```

## Getting Started

### Running in Google Colab / Local Jupyter Environment

The interactive notebook `modulation.ipynb` is pre-configured to run seamlessly in Google Colab or a local Jupyter interface. 

To ensure reproducibility, the first cells of the notebook automatically handle the installation of required dependencies and suppress environment-specific technical warnings.

### Prerequisites

The analysis was executed using Python 3.14. To set up your local environment, install the exact dependencies listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

Core libraries required (2026 Stable Stack):
* `pandas` (==3.0.6)
* `numpy` (==2.5.0)
* `scikit-learn` (==1.6.0)
* `scipy` (==1.18.1)
* `statsmodels` (==0.15.0)
* `lifelines` (==0.30.3)
* `matplotlib` (==3.11.0)
* `openpyxl` (==3.1.5)

## Key Statistical Outputs & Figures

* **Table 5 Updates:** Multivariate logistic regression for in-hospital mortality demonstrating a pronounced clinical trend toward reduced adjusted odds of death in the Modulation Group (OR = 0.2219, 95% CI: 0.0399–1.2345, p = 0.0855).
* **Table 6 Updates:** Fine-Gray subdistribution hazard regression establishing a descriptive, statistically null effect on time to live ICU discharge (adjusted SHR = 0.7985, 95% CI: 0.3393–1.8792, p = 0.6063), properly accounting for ICU mortality as a competing risk.
* **Figure 2 Generation:** The notebook automatically exports a high-resolution, publication-ready plot (`ICU_discharge_competing_risks.png`, 300 DPI) representing the Cumulative Incidence Functions aligned up to a strict 30-day follow-up horizon.

## Citation

If you use this code or dataset in your research, please cite our paper:

```text
Chernevskaya, E., Getsina, M., Burnatsev, K., Tsakoev, R., Meinarovich, P., Yakunina, E., & Beloborodova, N. (2025). Microbiota-Modulating Antibiotic Therapy in ICUs: Results of a Retrospective Data and Prospective Pilot Study in Patients With Intra-Abdominal Infections. (To be updated upon final publication).
```

