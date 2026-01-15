# Credit Card Fraud Detection (Imbalanced Classification)

# Overview

This project focuses on credit card fraud detection, a real-world machine learning problem defined by extreme class imbalance, asymmetric error costs and the need for model interpretability. Instead of optimizing for accuracy, the project exemines fraud-appropriate metrics, threshold tuning and explainable models, reflecting how fraud systems are built in production environments.

## Dataset

- Name: [Credit Card Fraud Dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud)

- Size: 284,807 transactions

- Fraud Rate: ~0.17%

- Features:

      - V1–V28: anonymized PCA components

      - Time, Amount

- Target: Class (1 = fraud, 0 = legitimate)


### Why use a well-known dataset?

- This dataset is widely used because it:

- Accurately reflects real-world fraud imbalance

- Forces correct metric selection (PR-AUC, recall)

- Removes domain shortcuts via anonymized features

- Enables focus on methodology and decision logic

Originality in this project comes from modeling choices, evaluation strategy, threshold analysis, and interpretability, not from proprietary data.

### Class Imbalance

Insight:

    - Fraud accounts for less than 0.2% of transactions, making accuracy misleading.
    - A naive model could achieve >99% accuracy while detecting no fraud at all.

### Modeling Approach

**Pipeline:**

**1.** Exploratory analysis with imbalance focus

**2.** Stratified train/test split

**3.** Logistic Regression (baseline, interpretable)

**4.** Random Forest (non-linear interactions)

**5.** XGBoost (industry-grade performance)

**6.** Evaluation using ROC-AUC & PR-AUC

**7.** Threshold tuning for operational trade-offs

**8.** Model explainability using SHAP    

### Model Comparison

Insight:

      - Tree-based models outperform Logistic Regression by capturing non-linear transaction patterns.
      - XGBoost achieves the best Precision–Recall trade-off, making it suitable for high-risk screening.

### Precision–Recall Trade-off

Insight:

      - Lower thresholds increase fraud recall but raise false positives.
      - This reflects a real operational trade-off between fraud loss prevention and customer friction.

### Explainability with SHAP

Global Feature Importance

Insight:
       - SHAP highlights which features most strongly influence fraud predictions 
         and how extreme values push decisions toward fraud or legitimacy.

Local Explanation (Single Transaction)

Insight:
      - Each prediction can be decomposed into additive feature contributions, 
        supporting transparency and auditability in regulated environments.
    
