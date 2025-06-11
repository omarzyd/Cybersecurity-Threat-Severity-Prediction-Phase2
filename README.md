# 🔐 Cybersecurity Threat Severity Prediction — Phase 2 (Kaggle-Style Competition)

> 🏁 "Not just a machine learning project its a race for accuracy."

This was the second and most intense phase of our Machine Learning course at Zewail City.  
We participated in a **Kaggle-style competition**, where teams were given a shared training set and a **test set with hidden labels**. The twist?  
**You don’t get to evaluate your model** — only the instructor holds the test labels.

We trained, predicted, and submitted our results blindly. The coordinator returned a single number: **accuracy**.  
And the team with the highest accuracy… **won**.

---

## 🎯 Problem Statement

We were challenged to build a regression model that predicts the **severity of cybersecurity threats** based on system/network telemetry.

- You train your model on a labeled dataset.
- You predict on an unlabeled test dataset.
- You submit your predictions.
- The instructor returns an **accuracy score**.
- The team with the **highest accuracy wins**.

---

## 🗂️ Dataset Overview

- Input: ~50 features (categorical + numerical, many unnamed)
- Target: continuous score representing threat severity
- Provided: `train.csv` (with `y_train`) and `test.csv` (without `y_test`)
- Ground truth for test set was only known to the instructor

---

## ⚔️ The Competition Format

- Each team had access to the same training and test files.
- No team knew the actual test labels.
- We submitted `.csv` prediction files to the instructor.
- We received back a **single float** our **accuracy score**.
- **Leaderboards changed daily.** Everyone iterated until the deadline.

> 🧠 Every prediction mattered. Every point counted.  
> 📈 We tuned, ensembled, and experimented until the final minutes.

---

## 🧪 Our Approach

### 🔹 1. Data Preprocessing
- Missing value imputation
- Label + one-hot encoding for categorical features
- Standard scaling and MinMax scaling
- Feature selection via:
  - Correlation matrix
  - Feature importance from tree models
  - Recursive Feature Elimination (RFE)

---

### 🔹 2. Models We Trained

| Model         | Description |
|---------------|-------------|
| Linear Regression | Simple baseline |
| Ridge/Lasso    | Regularization, less overfitting |
| Random Forest  | Strong out-of-the-box |
| **XGBoost**    | Excellent performance, fine-tuned |
| **LightGBM**   | Fastest with great accuracy |
| **CatBoost**   | Best with categorical data |
| **Ensemble**   | Final model – weighted average of top 3 |

Each model was tuned using:
- 5-fold cross-validation on training data
- **Optuna** for automated hyperparameter optimization
- Accuracy tracked on validation sets

---

## 🌟 Final Submission Strategy

We created a final ensemble model by blending our top three:

final_prediction = (
    0.5 * lightgbm_preds +
    0.3 * catboost_preds +
    0.2 * xgboost_preds
)

---
## 📈 Model Performance (Local CV Accuracy)

> ⚠️ Note: These are cross-validation results on the training data.  
> The actual ranking was based on **test accuracy** provided by the instructor on the hidden test set.

| Model         | CV Accuracy |
|---------------|-------------|
| LightGBM      | 92.1%       |
| CatBoost      | 91.8%       |
| XGBoost       | 91.5%       |
| **Ensemble**  | **92.7%** ✅ |

Our final ensemble was built by blending predictions from LightGBM, CatBoost, and XGBoost with optimized weights.

---

## 🤔 Reflections

This challenge was more than a project — it was a **real-world simulation** of:
- Blind model evaluation
- Hyperparameter tuning under pressure
- Competitive ML teamwork
- Dealing with feedback delays and uncertainty

Even though we didn’t win, we gained deep experience in:
- Building robust pipelines
- Understanding model generalization
- Thinking like practitioners, not just students

---

## 👥 Team Collaboration

Our team consisted of four members:

- **Malak** 🧪 – Data cleaning, preprocessing, feature scaling
- **Azza** 📊 – Exploratory Data Analysis, feature engineering, visualization  
- **Farida** 🤖 – Model training, validation, ensemble development  
- **Omar (me)** ⚙️ – Hyperparameter tuning, model optimization, final pipeline assembly

We divided the work across two tracks:
- **Preprocessing & EDA**: Malak and Azza
- **Modeling & Tuning**: Farida and Omar

Throughout the project, we collaborated via shared notebooks, coordinated submissions, and cross-reviewed each other's contributions to ensure a robust and unified pipeline.

> 💬 _"Every improvement in accuracy was a result of shared effort and constant iteration."_  

---

## 🏆 Competition Results

At the end of the challenge, the instructor revealed the **official leaderboard**, ranking all teams by their accuracy on the hidden test set.

> 📌 Our team, **TeamML**, achieved a final test accuracy of **91.6653%**, placing us **9th overall** in a highly competitive field.

The gap between the top and our position was narrow, less than **0.003 in accuracy**. It was a race of fine-tuning, experimentation, and resilience.

![image](https://github.com/user-attachments/assets/79ffaca6-6df9-48e1-9b05-ffa29eb7c2b8)

Even though we didn’t land at the very top, we pushed our models to the limit, explored diverse strategies, and came away with **battle-tested skills** in:
- Blind evaluation
- Ensemble modeling
- Hyperparameter tuning
- High-pressure iteration

This wasn’t just a class project, it was a simulation of **real-world model deployment** under uncertainty.

---
