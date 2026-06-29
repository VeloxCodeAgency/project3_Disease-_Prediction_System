# 🏥 Disease Prediction System

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge&logo=python)
![XGBoost](https://img.shields.io/badge/XGBoost-2.0-orange?style=for-the-badge)
![RandomForest](https://img.shields.io/badge/Random_Forest-Ensemble-green?style=for-the-badge)
![SMOTE](https://img.shields.io/badge/SMOTE-Imbalance_Fix-red?style=for-the-badge)
![Colab](https://img.shields.io/badge/Google_Colab-Ready-yellow?style=for-the-badge&logo=google-colab)

**Predicting Diabetes & Heart Disease using Ensemble Machine Learning**  
*Clinical-grade evaluation | SMOTE | Feature Importance | AUC-ROC*

</div>

---

## 🩺 What This Project Does

This system predicts the likelihood of two life-threatening diseases from patient medical data:

| Disease | Dataset | Samples | Features |
|---------|---------|---------|----------|
| 🩸 Diabetes | PIMA Indians Diabetes (UCI) | 768 | 8 clinical |
| ❤️ Heart Disease | Cleveland Heart Disease (UCI) | 303 | 13 clinical |

Three ensemble models are trained, compared, and evaluated using **clinical metrics** — not just accuracy — because in healthcare, a missed diagnosis costs more than a false alarm.

---

## 🧠 Technical Highlights

### Models Used
```
Random Forest      → 200 trees, balanced class weights, Gini importance
XGBoost            → scale_pos_weight for imbalance, 200 estimators
Soft Voting Ensemble → RF + XGB + Logistic Regression (weights: 2:2:1)
```

### Key Techniques

**⚖️ SMOTE — Synthetic Minority Oversampling**  
Class imbalance is a major problem in medical datasets (e.g., only 35% diabetic patients). SMOTE generates synthetic minority samples — applied only on training data to prevent data leakage.

**🔬 Feature Engineering**  
Beyond raw features, clinically meaningful combinations are derived:
- `Glucose × BMI` — combined metabolic risk
- `Insulin / Glucose` — insulin resistance proxy  
- `Glucose Risk Bins` — Normal / Pre-diabetic / Diabetic thresholds
- `High BP Flag`, `High Cholesterol Flag` — clinical cutoff markers

**📊 Clinical Evaluation Metrics**
```
Sensitivity (Recall)  → minimize missed diagnoses  ← MOST CRITICAL
Specificity           → minimize false alarms
PPV (Precision)       → diagnosis trustworthiness
NPV                   → negative result reliability
AUC-ROC               → overall discrimination power
AUC-PR                → performance under class imbalance
```

**🔄 5-Fold Stratified Cross-Validation**  
Ensures class ratio is preserved across all folds — reliable performance estimate.

---

## 📈 Results

### 🩸 Diabetes Prediction

| Model | Accuracy | Recall | AUC-ROC |
|-------|----------|--------|---------|
| Random Forest | ~78% | ~74% | ~0.84 |
| XGBoost | ~79% | ~76% | ~0.85 |
| **Ensemble** | **~80%** | **~77%** | **~0.86** |

### ❤️ Heart Disease Prediction

| Model | Accuracy | Recall | AUC-ROC |
|-------|----------|--------|---------|
| Random Forest | ~82% | ~83% | ~0.89 |
| XGBoost | ~83% | ~84% | ~0.90 |
| **Ensemble** | **~84%** | **~85%** | **~0.91** |

> Actual results may vary slightly due to dataset version and random seed.

---

## 🔍 Key Findings

**Diabetes — Top Predictors (both RF & XGBoost agree):**
1. Glucose level — strongest single predictor
2. BMI — metabolic indicator
3. Age — risk increases significantly after 40
4. Diabetes Pedigree Function — family history encoded

**Heart Disease — Top Predictors:**
1. Chest pain type (cp) — atypical angina most predictive
2. Max heart rate achieved (thalach) — lower = higher risk
3. ST depression (oldpeak) — exercise ECG indicator
4. Number of vessels colored by fluoroscopy (ca)

---

## 🧪 Clinical Interpretation

```
⚕️  Why Recall > Accuracy in medicine:

    Scenario: 100 patients, 30 actually have diabetes
    
    Bad model (high accuracy, low recall):
    → Predicts all as healthy → 70% accuracy but 30 missed diagnoses
    
    Our model (high recall):
    → Catches ~77% of true cases → fewer patients go undiagnosed
    → Some healthy patients flagged (false positives) — confirmed by doctor
```

---

## 🛠️ Tech Stack

```python
Python          3.10
scikit-learn    1.3+
XGBoost         2.0+
imbalanced-learn 0.11+
pandas          2.0+
numpy           1.24+
matplotlib      3.7+
seaborn         0.12+
```

---

## 👩‍💻 Author

**Maryam Saif**  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://linkedin.com/in/your-profile)
[![GitHub](https://img.shields.io/badge/GitHub-saifmaryam-black?style=flat&logo=github)](https://github.com/saifmaryam)
[![HuggingFace](https://img.shields.io/badge/🤗_HuggingFace-maryam--cheema--ai-yellow?style=flat)](https://huggingface.co/maryam-cheema-ai)

---

## 📄 License

This project is open source under the [MIT License](LICENSE).

---

<div align="center">
<i>Built with ❤️ for clinical AI research | Part of AI/ML Internship Portfolio</i>
</div>
