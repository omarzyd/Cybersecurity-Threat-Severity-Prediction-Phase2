# 🔐 Cybersecurity Threat Severity Prediction — Phase 2 (Kaggle-Style Competition)

> 🏁 _"Not just a machine learning project — a race to the top."_

This was the second and most intense phase of our CSAI 253 Machine Learning course at Zewail City.  
We participated in a **Kaggle-style competition** where teams trained ML models on a shared training set and submitted predictions on a **private test set without labels**. The coordinator alone had the ground truth and returned scores after each submission.

For two weeks, it was a fierce, model-driven battle. Teams competed daily — tuning, submitting, and racing to reach the **lowest RMSE**. Submissions were blind. Feedback was slow. And every percentage point counted.

---

## 🎯 Problem Statement

Build a regression model that predicts the **severity of cybersecurity threats** using real-world telemetry and system data.

- You train on: `train.csv` with labeled threat scores.
- You predict on: `test.csv` without labels.
- You submit predictions to the coordinator.
- You get back: **RMSE score** only.

The team with the **lowest test RMSE** wins.

---

## 🗂️ Dataset Overview

- ~50+ features: numerical + categorical, no context provided
- Target: continuous severity score
- Real-world structure: noise, outliers, missing data, feature drift

---

## 🧪 Our Approach

### 🔹 1. Data Cleaning & Preprocessing

- Imputed missing values (median/mode)
- Encoded categoricals (label + one-hot encoding)
- Standardized and scaled numerical features
- Visualized distributions, outliers, skewness
- Selected top features via:
  - Correlation analysis
  - Tree-based importance (RF/XGB)
  - Recursive Feature Elimination (RFE)

---

### 🔹 2. Modeling & Evaluation

We experimented with:

- **Linear Regression** (baseline)
- **Ridge / Lasso** (regularization)
- **Random Forest** (robust nonlinear model)
- **XGBoost** (high accuracy, flexible)
- **LightGBM** (fastest with high performance)
- **CatBoost** (best with categoricals)

We used:
- 5-fold Cross Validation
- Optuna for hyperparameter tuning (~200 trials per model)
- RMSE as primary metric (Kaggle standard)
- MAE and R² for internal validation
- Residual analysis and prediction drift visualization

---

### 🔹 3. Final Ensemble

```python
final_prediction = (
    0.5 * lgbm_preds +
    0.3 * catboost_preds +
    0.2 * xgb_preds
)
