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

![PR Logistic](images/output_34_0.png)

**Insight:**  

    - Logistic Regression achieves very high recall across a wide range of thresholds, meaning it is effective at detecting fraudulent transactions. 
      However, precision remains low at default thresholds, indicating a high number of false positives.

    - This highlights a common challenge in fraud detection: while linear models can identify risky patterns, they often lack the discriminative power 
    needed to reduce false alerts without sacrificing recall. As a result, Logistic Regression serves as a strong baseline but is insufficient 
    as a standalone production model.

### Feature Importance (Random Forest)

![RF Importance](images/output_47_0.png)

**Insight:**  

      - The Random Forest model identifies a small subset of features—particularly V14, V4, and V10—as dominant drivers of fraud predictions. 
        These variables correspond to latent transaction patterns rather than surface-level attributes such as transaction amount.

      - This suggests that fraudulent behavior is better characterized by complex feature interactions than by individual transaction magnitudes, 
       reinforcing the need for non-linear models in fraud detection.

### Precision–Recall Trade-off (Random Forest)

![PR RF](figures/output_50_0.png)

**Insight:**  

      - Compared to Logistic Regression, Random Forest achieves a more favorable precision–recall balance. Precision improves substantially at moderate 
        thresholds while recall remains relatively high.
      - This indicates that tree-based models are better suited to capture non-linear interactions that distinguish fraudulent from legitimate transactions, reducing         false positives without severely compromising fraud detection rates.

### Global Model Explainability (SHAP)

![SHAP Summary](images/output_60_0.png)

**Insight:**  

      - The SHAP summary plot reveals that a small number of features—most notably V14, V4, and V12—dominate the model’s predictions. 
        The color gradients show that  extreme values in these features push predictions strongly toward fraud or legitimacy.

      - This asymmetric behavior highlights how fraud detection depends on specific combinations of latent transaction characteristics rather 
        than uniform linear effects.

### Average Feature Impact (SHAP)

![SHAP Bar](images/output_61_0png)

**Insight:**  

      - The mean absolute SHAP values confirm that V14 and V4 consistently exert the largest influence on model output across transactions. 
        This consistency indicates that the model’s decision logic is stable rather than driven by noise or rare edge cases.

### Local Explanation (Single Transaction)

![SHAP Waterfall](images/output_66_0.png)

**Insight:**  

      - The SHAP waterfall plot decomposes the prediction for a single transaction into individual feature contributions. 
        Features such as V14 and V11 significantly push the prediction toward fraud, while others mitigate risk.

      - This level of transparency is critical in financial systems where model decisions must be explainable to auditors, regulators, and risk teams.

### Local Decision Patterns

![SHAP Force](images/output_71_0.png)

**Insight:**  

     - Local explanation plots further illustrate how combinations of feature values jointly influence predictions, 
       providing intuitive insight into how fraud risk accumulates across multiple signals.





      
