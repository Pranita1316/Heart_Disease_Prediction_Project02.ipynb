[README.md](https://github.com/user-attachments/files/29211710/README.md)
# Project 02 — Heart Disease Prediction


A machine learning project that predicts the presence of heart disease from patient
clinical data, comparing three classification algorithms: **Logistic Regression**,
**Random Forest**, and **K-Nearest Neighbors (KNN)**.

## 📊 Dataset

This project uses the classic **UCI Cleveland Heart Disease** dataset (303 patients,
14 clinical attributes) — the same underlying data referenced by the assignment's
suggested Kaggle dataset, [`johnsmith88/heart-disease-dataset`](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset).
The notebook loads it directly from a public CSV mirror
([source](https://raw.githubusercontent.com/mrdbourke/zero-to-mastery-ml/master/data/heart-disease.csv))
so it runs end-to-end with no Kaggle API key required. The exact 1025-row Kaggle CSV
can be swapped in instead with no code changes — all columns match.

**Target:** `target` — 1 = heart disease present, 0 = absent

## 🔧 What This Notebook Does

1. **Load, Explore & Preprocess** — checks for missing values (none found), one-hot
   encodes nominal categorical columns (`cp`, `restecg`, `slope`, `thal`), splits data
   80/20 into train/test sets (stratified by target).
2. **Feature Engineering** — correlation analysis against the target + Random Forest
   feature importance; drops `fbs` (fasting blood sugar), which showed near-zero
   correlation (-0.03) and the lowest importance score.
3. **Train 3 Models** — Logistic Regression and KNN trained on scaled features
   (`StandardScaler`); Random Forest trained on unscaled features (tree-based models
   don't need scaling).
4. **Evaluate & Compare** — Accuracy, Precision, Recall, and F1-Score for all 3 models
   in a single comparison table + bar chart.
5. **Best Model Analysis** — confusion matrix for the best-performing model, plus a
   written conclusion.

## 📈 Results

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---|---|---|---|
| **Logistic Regression** | **0.8361** | **0.8108** | **0.9091** | **0.8571** |
| Random Forest | 0.7541 | 0.7250 | 0.8788 | 0.7945 |
| KNN (k=7) | 0.7541 | 0.7500 | 0.8182 | 0.7826 |

**Best model: Logistic Regression**

### Why Logistic Regression Won
The relationship between these clinical features (chest pain type, max heart rate, ST
depression, etc.) and heart disease is largely linear and additive — exactly what
Logistic Regression captures well. With only 303 total rows, Random Forest's extra
flexibility doesn't pay off and KNN suffers from the curse of dimensionality across 18
features. Logistic Regression's high recall (~91%) on the disease class also matters
clinically: it misses very few real heart-disease cases.

## 🗂️ Files

- `Heart_Disease_Prediction_Project02.ipynb` — full notebook (Colab-ready, already executed
  with outputs visible)

## ▶️ How to Run

1. Open the notebook in Google Colab (`File → Open notebook → GitHub` and paste this
   repo's URL, or use the Colab badge/link below).
2. Run all cells top to bottom — no setup, API keys, or file uploads required.

## 🔗 Links

- **Google Colab Notebook:** https://colab.research.google.com/drive/1Cgm6_H5pf5EIQN-c0KEYsZT95usKApO9?usp=sharing
- **Dataset reference (assignment-specified):** https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset
- **Dataset source used (no-auth mirror):** https://raw.githubusercontent.com/mrdbourke/zero-to-mastery-ml/master/data/heart-disease.csv
