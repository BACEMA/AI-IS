Lab 2: Static Malware Detection: PE Forensics, Multi-Model Evaluation, TreeSHAP & SOC Cost Optimization

Course: M115 - AI & Intelligent Systems for Cybersecurity (ENSIASD Taroudant)

Objective
Build a leakage-safe static detector for Windows PE files for the fictional company AtlasPay: compare five model families, explain predictions with TreeSHAP, and choose a SOC threshold from explicit costs while keeping a lockbox test set.

Dataset
Deterministic synthetic EMBER-inspired dataset (6,000 PE files, 12 usable features), generated inside the notebook (seed 42). It is not AtlasPay telemetry and not the EMBER benchmark, so no CSV is needed.

Content

1. Forensic audit: class balance, missing values, identifier (SHA256_File_ID), post-scan leakage (VT_PostScan_Detections), parser sentinel (99999.0)
2. Stratified 80/20 development/lockbox split, imputation and scaling inside the CV pipeline
3. 5-fold CV: Logistic Regression, deep Decision Tree, Random Forest, LightGBM, Stacking
4. Error forensics: LR vs LightGBM disagreement, SHAP (beeswarm, waterfall, dependence plot)
5. SOC costs (FP = 25, FN = 500; blocking FP = 2,000): thresholds chosen on out-of-fold predictions, frozen, evaluated once on the lockbox
6. CISO recommendation

Key results

* Deep Decision Tree overfits: train F1 = 1.000, validation F1 = 0.830
* Logistic Regression, Random Forest, LightGBM and Stacking are tied: validation PR-AUC 0.903 to 0.909
* Triage, Logistic Regression, tau = 0.28: 10 FP, 34 FN, Precision = 0.966, Recall = 0.894, cost = 17,250
* Blocking (FP = 2,000), Logistic Regression, tau = 0.50: 8 FP, 36 FN, cost = 34,000
* 298 alerts for 1,200 test files (24.8%), so the 120 alerts/day target cannot be validated on this synthetic prevalence

Links

* Notebook in this repo: [Lab2_Template.ipynb](https://github.com/BACEMA/AI-IS/blob/main/lab2-models/Lab2_Template.ipynb)

How to run
Open the notebook in Google Colab or Kaggle, install lightgbm and shap, then Run All.
