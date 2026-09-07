# Home Credit Default Risk: Gradient Boosted Modeling

This project builds a supervised machine-learning pipeline for predicting credit default risk using the Kaggle Home Credit Default Risk dataset. The goal is primarily risk ranking: assigning higher predicted default-risk scores to applicants who are more likely to experience repayment difficulty.

## Motivation

Credit default prediction is a noisy, imbalanced tabular prediction problem. The dataset includes applicant-level financial information, missing values, categorical variables, and historical credit/repayment tables. This makes it a useful setting for comparing classical baselines with gradient-boosted tree models.

## Data

The project uses the Kaggle Home Credit Default Risk dataset. Raw data are not included in this repository. See `data/README.md` for expected local files.

## Methodology

The pipeline includes:

1. Cleaning and preprocessing application-level features.
2. Handling missing values with imputation and missingness indicators.
3. Engineering financial-burden features such as credit-to-income, annuity-to-income, and income per family member.
4. Aggregating historical credit, previous-application, and installment-payment information to the applicant level.
5. Comparing logistic regression and random forest baselines with XGBoost, LightGBM, and CatBoost.
6. Using stratified cross-validation and a locked holdout set for final evaluation.
7. Ensembling boosted models by averaging predicted probabilities.
8. Interpreting model behavior with XGBoost feature contributions / SHAP-style analysis.
9. Selecting a risk-screening threshold using an F-beta criterion.

## Main results

The final equal-weight ensemble of XGBoost, LightGBM, and CatBoost achieved:

- Holdout ROC AUC: 0.7895
- Holdout average precision: 0.2912

Holdout performance was close to cross-validation performance, suggesting that the pipeline generalized reasonably well rather than overfitting the development set.

## Technical notes

One important implementation issue was that converting XGBoost's sparse feature matrix to a dense representation changed predictions, because absent sparse entries and explicit zeros were not treated identically. To avoid explaining a different input representation, feature contributions were recomputed using XGBoost's native sparse-aware prediction contribution functionality.

## Repository structure

```text
notebooks/
  home_credit_gradient_boosting.ipynb

data/
  README.md

outputs/
  figures/
  tables/