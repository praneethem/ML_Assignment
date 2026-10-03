# Machine Learning Assignment - Polynomial Regression

## Overview

This repository contains the implementation and report for Machine Learning Assignment 1.

The assignment involves predicting a continuous target variable using **polynomial regression** for two personalised datasets:

- **VAR1:** 6 input features (`x1`–`x6`)
- **VAR2:** 3 input features (`x1`–`x3`)

Each problem contains 1,000 training samples and 1,000 test samples.

## Methodology

The models use the following pipeline:

1. Polynomial feature expansion using `PolynomialFeatures`
2. Feature standardisation using `StandardScaler`
3. Ordinary Least Squares regression using `LinearRegression`

Model selection was performed using **5-fold cross-validation**.

The search considered:

- Polynomial degrees 1–10 for VAR1
- Polynomial degrees 1–20 for VAR2
- All non-empty feature subsets

Only polynomial regression was used. No Ridge, Lasso, ensemble, or other model types were used.

## Final Models

| Problem | Features | Degree | Validation MSE | Validation R² |
|---|---|---:|---:|---:|
| VAR1 | x1–x6 | 4 | 0.835 | 0.919 |
| VAR2 | x1–x3 | 8 | 0.295 | 0.993 |

The final models were refitted using all 1,000 training samples before generating predictions for the test datasets.

## Prediction Files

The repository contains the two required prediction files:

- `IMT2023555_pred_var1.csv`
- `IMT2023555_pred_var2.csv`

Each file contains 1,000 predictions in a single column named `y`.

## Repository Contents

```text
ML_Assignment/
├── ML_Assignment.ipynb
├── ML_Assignment_report.pdf
├── IMT2023555_pred_var1.csv
├── IMT2023555_pred_var2.csv
├── README.md
└── figures/
    ├── SVG figures
    └── PNG figures
