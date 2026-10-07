# Machine Learning Assignment - Polynomial Regression

## Overview

This repository contains the implementation and report for **Machine Learning Assignment 1**.

The assignment involves predicting a continuous target variable using polynomial regression for two personalised datasets:

- **VAR1:** 6 input features (`x1`–`x6`)
- **VAR2:** 3 input features (`x1`–`x3`)

Each problem contains 1,000 training samples and 1,000 test samples.

## Methodology

The modelling pipeline consists of:

1. Polynomial feature expansion using `PolynomialFeatures`
2. Feature standardisation using `StandardScaler`
3. Regularised regression

Model selection was performed using **5-fold cross-validation** with `random_state=42`.

Initially, ordinary polynomial regression was evaluated across different polynomial degrees and feature subsets. Regularised models were then explored to control overfitting and allow higher-degree polynomial representations.

The regularisation methods considered were:

- Ridge Regression
- Lasso Regression
- Elastic Net
- Relaxed Lasso

The final models were selected based on cross-validation performance while considering model simplicity.

## Final Models

| Problem | Model | Degree | Regularisation | Validation MSE | Validation R² |
|---|---|---:|---|---:|---:|
| VAR1 | Relaxed Lasso | 5 | Lasso α=0.02, Ridge refit α=0.1 | 0.3134 | 0.9693 |
| VAR2 | Ridge | 11 | α=1.23285 | 0.2517 | 0.9942 |

### VAR1

The final VAR1 model uses a degree-5 polynomial expansion followed by Relaxed Lasso.

Lasso is first used for feature selection, retaining **91 of the 461 polynomial terms**. A Ridge refit is then performed on the selected terms.

### VAR2

The final VAR2 model uses a degree-11 polynomial expansion followed by Ridge regression with **α = 1.23285**.

Elastic Net achieved a slightly lower cross-validation MSE of 0.2512, compared with 0.2517 for Ridge. Ridge was selected because the difference is very small and Ridge provides a simpler regularisation structure.

## Cross-Validation

A **5-fold shuffled cross-validation** strategy was used throughout model selection.

The best plain polynomial models achieved:

| Problem | Best Plain Polynomial | CV MSE |
|---|---|---:|
| VAR1 | Degree 4 | 0.8351 |
| VAR2 | Degree 8 | 0.2948 |

Regularisation improved the cross-validation performance to:

| Problem | Final Model | CV MSE | Improvement |
|---|---|---:|---:|
| VAR1 | Relaxed Lasso, Degree 5 | 0.3134 | ~62% |
| VAR2 | Ridge, Degree 11 | 0.2517 | ~15% |

The final models were retrained using all 1,000 training samples before generating predictions for the hidden test datasets.

## Prediction Files

The repository contains the two required prediction files:

- `IMT2023555_pred_var1.csv`
- `IMT2023555_pred_var2.csv`

Each file contains 1,000 predictions in a single column named `y`.

The prediction files were validated to ensure:

- 1,000 predictions
- Correct column name (`y`)
- No missing values
- Finite numerical values
- Predictions are in the same order as the corresponding test datasets

## Repository Contents

```text
ML_Assignment/
├── ML_Assignment.ipynb
├── ML_Assignment_report.pdf
├── IMT2023555_pred_var1.csv
├── IMT2023555_pred_var2.csv
├── README.md
├── Dataset/
│   ├── IMT2023555_train_var1.csv
│   ├── IMT2023555_test_var1.csv
│   ├── IMT2023555_train_var2.csv
│   └── IMT2023555_test_var2.csv
└── figures/
    └── Figures used in the report
