# Credit Card Fraud Detection (Imbalanced Classification)

Overview

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
