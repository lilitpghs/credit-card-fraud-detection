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

### Precision–Recall Trade-off (Logistic Regression)

![PR Logistic](figures/pr_logistic.png)

**Insight:**  
Logistic Regression achieves very high recall across a wide range of thresholds, meaning it is effective at detecting fraudulent transactions. However, precision remains low at default thresholds, indicating a high number of false positives.

This highlights a common challenge in fraud detection: while linear models can identify risky patterns, they often lack the discriminative power needed to reduce false alerts without sacrificing recall. As a result, Logistic Regression serves as a strong baseline but is insufficient as a standalone production model.
