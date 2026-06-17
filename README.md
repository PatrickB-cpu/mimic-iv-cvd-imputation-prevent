# MIMIC-IV Cardiovascular Risk Prediction:
## Evaluating Missing Data Imputation Strategies Using the AHA PREVENT Equation

![R](https://img.shields.io/badge/Language-R-276DC3)
![Database](https://img.shields.io/badge/Data-MIMIC--IV-blue)
![Methods](https://img.shields.io/badge/Methods-MICE%20%7C%20missForest%20%7C%20Median-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## Project Overview

Missing data is one of the most common challenges in clinical research and electronic health record (EHR) analysis.

This project evaluates how different imputation strategies influence cardiovascular risk prediction performance using the MIMIC-IV critical care database and the American Heart Association (AHA) PREVENT risk equation.

The analysis compares three commonly used imputation approaches:

- Median Imputation
- Multiple Imputation by Chained Equations (MICE)
- Random Forest Imputation (missForest)

across multiple missingness mechanisms and missingness levels.

The objective was to determine which method best preserved prediction accuracy, discrimination, and calibration in a large real-world clinical dataset.

---

## Research Question

How do different missing data imputation methods affect cardiovascular risk prediction performance when applied to large-scale EHR data?

---

## Data Source

### MIMIC-IV

Medical Information Mart for Intensive Care (MIMIC-IV) is a publicly available critical care database containing detailed clinical information from over 65,000 ICU patients.

Variables were extracted from:

- Laboratory tables
- Vital signs
- Medication records
- Diagnostic codes
- Demographic information

Physiologic plausibility filters and exclusion criteria were applied to create an analysis-ready cohort.

---

## Study Design

### Workflow

```text
MIMIC-IV Database
        ↓
Cohort Construction
        ↓
Missingness Simulation
        ↓
MCAR / MAR / MNAR
        ↓
5% and 30% Missingness
        ↓
Imputation
(Median | MICE | missForest)
        ↓
AHA PREVENT Risk Calculation
        ↓
Performance Evaluation
```

---

## Missingness Mechanisms

Three missingness mechanisms were evaluated.

### MCAR
Missing Completely At Random

Missing values occur independently of observed and unobserved variables.

### MAR
Missing At Random

Missingness depends on observed patient characteristics.

### MNAR
Missing Not At Random

Missingness depends on the underlying value itself.

---

## Imputation Methods

### Median Imputation

Simple deterministic replacement using the median value of each variable.

Advantages:

- Fast
- Easy to implement

Limitations:

- Underestimates variability
- Can bias estimates

---

### MICE

Multiple Imputation by Chained Equations

- Iterative conditional modeling
- Generates multiple plausible datasets
- Widely used in clinical research

Package:

```r
mice
```

---

### missForest

Random Forest-Based Imputation

- Nonparametric
- Handles nonlinear relationships
- Captures complex interactions

Package:

```r
missForest
```

---

## Cardiovascular Risk Prediction

Risk estimates were generated using the:

### AHA PREVENT Equation

The PREVENT equation is a contemporary cardiovascular disease risk prediction model developed by the American Heart Association.

Predicted risk scores were calculated following imputation and compared across methods.

---

## Performance Metrics

Imputation performance was evaluated using:

### Error Metrics

- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)

### Discrimination

- C-Index
- ROC Analysis

### Calibration

- Calibration Curves
- Calibration Assessment Statistics

---

## Key Findings

### Overall Performance Ranking

1. missForest
2. MICE
3. Median Imputation

### Major Findings

- missForest consistently produced the lowest prediction error.
- Random forest imputation preserved nonlinear relationships between variables.
- MICE performed well but showed slightly greater prediction error.
- Median imputation demonstrated reduced calibration performance.
- Application of the PREVENT equation to ICU populations revealed structural calibration limitations, highlighting challenges when applying outpatient-derived risk models to critically ill patients.

---

## Example Outputs

### Cohort Flow Diagram

*Insert Figure*

### Missingness Simulation Design

*Insert Figure*

### Calibration Curves

*Insert Figure*

### ROC Curves

*Insert Figure*

### Method Comparison

*Insert Figure*

---

## Repository Structure

```text
mimic-iv-cvd-imputation-prevent/
│
├── data/
├── code/
│   ├── 01_cohort_construction.R
│   ├── 02_missingness_simulation.R
│   ├── 03_imputation.R
│   ├── 04_prevent_equation.R
│   ├── 05_evaluation.R
│
├── output/
│   ├── figures/
│   ├── tables/
│
├── manuscript/
│
└── README.md
```

---

## Skills Demonstrated

- Electronic Health Record Analysis
- Clinical Data Engineering
- Missing Data Methodology
- Predictive Modeling
- Model Validation
- Cardiovascular Risk Prediction
- Statistical Programming in R
- Reproducible Research
- Data Visualization

---

## Future Work

Potential extensions include:

- Deep learning imputation methods
- XGBoost imputation
- External validation cohorts
- Time-dependent prediction models
- Survival-based cardiovascular risk prediction

---

## References

Johnson AEW et al. MIMIC-IV Clinical Database.

Khan SS et al. PREVENT Equations for Cardiovascular Disease Risk Prediction.

Van Buuren S. Flexible Imputation of Missing Data.

Stekhoven DJ. missForest: Nonparametric Missing Value Imputation for Mixed-Type Data.
