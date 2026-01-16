# Credit Card Fraud Detection (Imbalanced Classification)

## Overview

This project focuses on building and evaluating machine learning models for credit card fraud detection, a critical real-world problem in finance and cybersecurity characterized by extreme class imbalance and asymmetric decision costs.

Rather than optimizing for accuracy alone, the project treats fraud detection as a decision-making problem, where correct handling of imbalance, appropriate evaluation metrics, threshold selection, and model explainability are all essential. The goal is to demonstrate how predictive performance and interpretability can be combined to support reliable and auditable fraud detection systems.

## Dataset

- Name: [Credit Card Fraud Dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud) (Kaggle - ULB)

- Size: 284,807 transactions

- Fraud Rate: ~0.17%

- Features:

      - V1–V28: anonymized PCA components

      - Time, Amount

- Target: Class (1 = fraud, 0 = legitimate)


## Why use a well-known dataset?

Although the dataset is widely used, it was selected deliberately for the following reasons:

1. Realistic problem structure
  
         Fraud represents less than 0.2% of all transactions, closely mirroring real-world fraud detection scenarios.

2. Industry relevance
  
         Credit card fraud detection is a core use case in banking, payments and cybersecurity, making this directly applicable to applied ML and risk analytics roles.

3. Focus on methodology over memorization
  
         Because features are anonymized PCA components, the project emphasizes:
  
        - handling severe class imbalance
        - choosing appropriate evaluation metrics
        - comparing models under realistic constraints
        - threshold optimization and explainability

4. Meaningful benchmarking
  
         A standard dataset enables clear interpretation of results while leaving room for original modeling, evaluation strategy, and explanation design.

Originality in this project lies in end-to-end decision framing, not proprietary data.

## Project Objectives

This project demonstrates the ability to:

- Handle highly imbalanced classification problems correctly

- Build and compare multiple models with increasing complexity:

  - Logistic Regression

  - Random Forest

  - XGBoost

- Evaluate models using precision, recall, ROC-AUC, and PR-AUC, rather than accuracy

- Perform threshold tuning to reflect real operational trade-offs

- Explain model behavior using SHAP at both global and local levels

## Modeling Approach

**Pipeline:**

**1.** Exploratory analysis with explicit focus on class imbalance

**2.** Stratified train/test split

**3.** Logistic Regression as an interpretable baseline

**4.** Random Forest to capture non-linear interactions

**5.** XGBoost for industry-grade performance

**6.** Evaluation using ROC-AUC and PR-AUC

**7.** Threshold tuning for operational decision-making

**8.** Model explainability using SHAP 

## Key Results

This analysis produced several consistent and practically relevant findings:

1. Accuracy is not a meaningful metric under extreme imbalance

Models with high accuracy can still perform poorly in fraud detection. Precision–Recall analysis proved essential for understanding true model behavior.

2. Linear models detect risk but over-flag transactions

Logistic Regression achieves very high recall but low precision, resulting in excessive false positives. This makes it a strong baseline but insufficient as a standalone production model.

3. Tree-based models materially reduce false positives
   
Random Forest and XGBoost achieve a more favorable precision–recall balance, maintaining strong fraud detection while significantly improving precision.

4. Fraud signal concentrates in a small subset of features
   
Across feature importance and SHAP analyses, a small number of latent variables—most notably V14, V4, V10, and V12—consistently dominate predictions. This indicates stable, non-random fraud patterns.

5. Transaction amount is not a primary fraud driver
   
Fraudulent behavior is better characterized by latent behavioral patterns than by transaction size alone.

6. Model decisions are explainable at global and local levels
    
SHAP analysis reveals stable global importance patterns and provides transparent, transaction-level explanations suitable for audit and regulatory contexts.

7. Threshold selection defines operational performance
    
Optimal model behavior depends on explicitly tuning decision thresholds to balance fraud detection rates against false alert volume.

## Model Insights & Visual Analysis

### Precision–Recall Trade-off (Logistic Regression)

![PR Logistic](images/output_34_0.png)

**Insight:**  

    - Logistic Regression achieves very high recall but low precision across most thresholds. This confirms that while linear models can detect risky patterns, they lack sufficient discriminative power to control false positives.

### Feature Importance (Random Forest)

![RF Importance](images/output_47_0.png)

**Insight:**  

      - A small subset of features—particularly V14, V4, and V10—dominates model decisions. These latent components capture complex transaction patterns rather than surface-level attributes.

### Precision–Recall Trade-off (Random Forest)

![PR RF](figures/output_50_0.png)

**Insight:**  

      - Random Forest substantially improves precision while maintaining high recall, demonstrating the value of non-linear models in fraud detection.
      
### Global Model Explainability (SHAP)

![SHAP Summary](images/output_60_0.png)

**Insight:**  

      - SHAP confirms that fraud predictions are driven by extreme values in a small number of latent features, with asymmetric effects pushing transactions strongly toward fraud or legitimacy.
      
### Average Feature Impact (SHAP)

![SHAP Bar](images/output_61_0png)

**Insight:**  

      - Mean absolute SHAP values show consistent dominance of V14 and V4, indicating stable decision logic rather than noise-driven behavior.
      
### Local Explanation (Single Transaction)

The waterfall plot explains a single transaction by decomposing the model’s prediction into additive feature contributions:

- The model starts from a baseline prediction (average model output)

- Each feature pushes the prediction toward fraud (red) or toward legitimacy (blue)

- The final position represents the model’s output for this transaction

![SHAP Waterfall](images/output_66_0.png)

**Insight:**  

      - The waterfall plot decomposes a single prediction into additive feature contributions, clearly showing how individual signals combine to produce a fraud decision.
      
### Local Decision Patterns

The force plot visualizes the same prediction but displays all individual feature contributions:

- Features pushing the prediction higher are shown in red

- Features pushing the prediction lower are shown in blue

- The final prediction results from the balance of all opposing forces

Unlike the waterfall plot, no aggregation is performed, which can make the visualization more detailed but less compact.

![SHAP Force](images/output_71_0.png)

**Insight:**  

     - Force plots visualize how multiple features jointly push predictions toward fraud or legitimacy, offering intuitive insight into cumulative risk formation.

## Key Takeaway

Fraud detection is not merely a prediction task. It is a cost-sensitive decision problem where evaluation metrics, thresholds, and explainability matter as much as model accuracy.

This project demonstrates how combining robust models with careful evaluation and transparent explanations leads to fraud detection systems that are not only effective, but also trustworthy and operationally viable.

## Tools & Technologies

- Python, Pandas, NumPy

- Scikit-learn

- XGBoost

- SHAP

- Matplotlib

## Repository Structure

```text
├── images/
│   └── *.png                               # Saved visualizations 
├── README.md             # Project documentation
├── credit_card_fraud_detection.ipynb   # Main analysis notebook (static, non-executable)
```
> **Note:**  
> The notebook is provided as-is for transparency and methodological review.  
> Datasets and execution artifacts are not included.
      
## Keywords

Fraud Detection · Imbalanced Classification · Financial Risk Analytics · Machine Learning · XGBoost · Logistic Regression · Random Forest · SHAP · Model Interpretability · Decision Support · Credit Card Transactions

## Author

Lilit Poghosyan — Background in Industrial Engineering, Business Intelligence, and Data Analytics, with a focus on improving decision quality in complex operational systems.
