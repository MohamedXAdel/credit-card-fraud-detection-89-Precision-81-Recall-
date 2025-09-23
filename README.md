# Credit Card Fraud Detection (≈ 89% Precision, ≈ 81% Recall)

This project builds a machine learning pipeline to detect fraudulent credit card transactions.  
The main challenge is **extreme class imbalance** — fraud cases are very rare compared to legitimate ones.  
By combining resampling techniques with ensemble models (Random Forest, XGBoost), we achieved about **89% precision** and **81% recall**.

---

## 📌 Table of Contents
1. [Business Problem](#business-problem)  
2. [Dataset](#dataset)  
3. [Approach](#approach)  
4. [Evaluation Metrics](#evaluation-metrics)  
5. [Results](#results)  
6. [Conclusions](#conclusions)  
7. [Limitations & Future Work](#limitations--future-work)  
8. [How to Run](#how-to-run)  
9. [Dependencies](#dependencies)  

---

## 💼 Business Problem

Credit card fraud causes **billions of dollars in losses** annually.  
Detecting fraud is tricky because:

- Fraud cases are **rare** (heavily imbalanced dataset).  
- False positives (legitimate transactions marked as fraud) are costly — customer dissatisfaction, wasted investigations.  
- False negatives (frauds missed) are also costly — direct financial losses.  

👉 The goal: **maximize fraud detection (recall)** while keeping **false alarms low (high precision)**.

---

## 📊 Dataset

- Based on a credit card transaction dataset (highly imbalanced).  
- Fraudulent transactions are less than 1% of all records.  
- Features are numerical (often anonymized PCA components, plus `Time` and `Amount`).  
- Preprocessing steps include:
  - Feature scaling (for `Amount` and `Time`).  
  - Train/test split with **stratification**.  
  - Resampling methods to rebalance classes.  

---

## ⚙️ Approach

### 1. Exploratory Data Analysis (EDA)
- Distribution of features, class imbalance check.  
- Correlations and visualization of fraud vs non-fraud behavior.  

### 2. Handling Imbalanced Data
- **Random undersampling / oversampling**.  
- **SMOTE** (Synthetic Minority Oversampling Technique).  
- **Hybrid methods** like SMOTEENN for better class balance.  

### 3. Models Used
- **Random Forest Classifier**  
- **XGBoost Classifier**  
- Baseline logistic regression for comparison.  

---

## 📏 Evaluation Metrics

Since accuracy is misleading with imbalanced data, we focus on:

- **Precision**: % of predicted frauds that are actual frauds.  
- **Recall (Sensitivity)**: % of actual frauds that were detected.  
- **F1-Score**: harmonic mean of precision and recall.  
- **Confusion Matrix**: to visualize false positives & false negatives.  
- **ROC-AUC & PR-AUC curves**.  

---

## 🏆 Results

- **Best Model Performance**:  
  - Precision ≈ **0.89**  
  - Recall ≈ **0.81**  
  - F1-Score ≈ **0.85**  

- **Interpretation**:  
  - 89% of flagged frauds are correct (few false positives).  
  - 81% of real frauds are detected (some still missed).  

- **Trade-off**: Slightly higher recall lowers precision, and vice versa. The chosen threshold balances both.  

---

## ✅ Conclusions

- Fraud detection is **feasible** with high precision and recall using ensemble models + resampling.  
- Handling class imbalance is critical — without it, models mostly predict the majority class (non-fraud).  
- Random Forest and XGBoost significantly outperform simple baselines.  
- Achieving **89% precision and 81% recall** is a strong result for such an imbalanced domain.  

---

## ⚠️ Limitations & Future Work

- **False negatives remain** — ~19% of frauds are still missed.  
- **False positives exist** — though reduced, still cause customer inconvenience.  
- **Fraud evolves over time** → models need periodic retraining (concept drift).  
- **Future directions**:
  - Use advanced resampling (ADASYN, Borderline-SMOTE).  
  - Apply anomaly detection / deep learning (autoencoders, LSTMs).  
  - Use explainability tools (SHAP, LIME) to understand decisions.  
  - Deploy in real-time pipelines with monitoring.  

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/MohamedXAdel/credit-card-fraud-detection-89-Precision-81-Recall-
   cd credit-card-fraud-detection-89-Precision-81-Recall-
