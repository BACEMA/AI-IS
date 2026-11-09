# AI-IS
# Lab 1: Phishing URL Detection: Regularized Logistic Regression, SHAP & SOC Thresholds

Course: M115 - AI & Intelligent Systems for Cybersecurity (ENSIASD Taroudant)

## Objective
Build and interpret a phishing URL detector on the PhiUSIIL dataset, with
zero-data-leakage preprocessing, five regularization regimes, SHAP explanations
and SOC-oriented threshold tuning.

## Dataset
PhiUSIIL Phishing URL Dataset (235,795 URLs, 49 usable features):
https://www.kaggle.com/datasets/kaggleprollc/phishing-url-websites-dataset-phiusiil

The CSV is not included in this repository (see the Kaggle link above).

## Content
1. Security-oriented EDA: label alignment (IsPhishing = 1 - label), class balance, correlations
2. Stratified 75/25 split and training-only standardization (no data leakage)
3. Logistic Regression: M1 (none), M2 (L2, C=0.001), M3 (L2, C=1), M4 (L1, C=0.01), M5 (balanced)
4. L1 regularization path and Odds Ratio interpretation
5. SHAP explanations: global (bar, beeswarm) and local (waterfall for TP, TN, FP)
6. Threshold tuning: tau = 0.20 / 0.50 / 0.85

## Key results
- M3 (standard L2): F1 = 0.9992 (10 FP, 28 FN)
- M4 (L1, C=0.01): 24 of 49 weights set to zero, F1 = 0.9982
- M5 (balanced): 13 FP, 25 FN
- tau = 0.85: 0 FP, Precision = 1.0000, Recall = 0.9975 (64 FN)

## Links
- Kaggle notebook: <[lien Kaggle](https://www.kaggle.com/code/bacemach/phishing-url-detection)>
- Notebook in this repo: [LAB1.ipynb](./LAB1.ipynb)

## How to run
Open the notebook in Google Colab or Kaggle, load the dataset, then Run All.
