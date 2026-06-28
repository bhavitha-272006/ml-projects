# 💳 Project 5 — Credit Card Fraud Detection

## 📌 Problem Statement
Detect **fraudulent credit card transactions**
from millions of normal transactions in real time.

> Global card fraud losses → $32 billion/year!
> Missing ONE fraud = money lost!
> ML model checks every transaction in milliseconds!

---

## 📊 Dataset
| Property | Details |
|---|---|
| Source | Synthetic (based on real fraud patterns) |
| Rows | 10,100 transactions |
| Features | 10 (after engineering) |
| Target | Class (0=Normal, 1=Fraud) |
| Missing Values | None |
| Class Balance | Highly imbalanced (99% normal, 1% fraud!) |

### Features:
- amount (transaction amount)
- hour (time of transaction)
- v1-v5 (anonymized transaction features)
- is_night (engineered — night transactions!)
- high_amount (engineered — suspicious amounts!)
- amount_log (engineered — log transformed amount)

---

## 🔧 Feature Engineering

| New Feature | Logic | Why Created |
|---|---|---|
| is_night | hour <= 6 → 1 else 0 | Fraud happens at night! |
| high_amount | amount > 95th percentile → 1 | Fraudsters spend more! |
| amount_log | log(1 + amount) | Reduces outlier impact |

### Feature Effectiveness:
```
high_amount:
→ Normal transactions  → 5% have high amount
→ Fraud transactions   → 52% have high amount
→ 10x difference! → Very useful feature! ✅

is_night:
→ Normal → 12% at night
→ Fraud  → 2% at night
→ Less useful alone but combined with high_amount!
```

---

## ⚖️ Handling Extreme Imbalance

```
99% normal vs 1% fraud!
→ Much worse than typical imbalanced datasets!

If model predicts everything as normal:
→ Accuracy = 99% ← looks amazing!
→ Catches 0 fraud! ← completely useless! ❌

Solution: SMOTE
→ 81 fraud cases in training
→ After SMOTE → ~7,999 fraud cases
→ Model learns fraud patterns properly! ✅
```

---

## 🛠️ Approach

```
Step 1 → Create synthetic fraud dataset
Step 2 → Feature engineering (3 new features)
Step 3 → Train Test Split (stratified)
Step 4 → Build Pipeline with SMOTE
Step 5 → Compare 3 models
Step 6 → Select best model (Logistic Regression)
Step 7 → Final evaluation on test set
```

> Note: Used only 3 models (excluded KNN and SVM)
> → Too slow on large datasets!
> → KNN calculates distance to every point!

---

## 🤖 Models Compared

| Model | Recall | F1 | ROC-AUC |
|---|---|---|---|
| **Logistic Regression** | **0.9875** | **0.9586** | **1.0000** |
| Random Forest | 0.9147 | 0.9484 | 0.9999 |
| XGBoost | 0.9632 | 0.9579 | 0.9998 |

---

## 🏆 Final Results (Logistic Regression)

| Metric | Score |
|---|---|
| Accuracy | 99.90% |
| **Recall** | **100%** ✅ |
| F1 | 95% |
| ROC-AUC | 100% |

### Confusion Matrix:
```
Actual\Predicted  Normal  Fraud
Normal              1999      2   ← 2 false alarms
Fraud                  0     19   ← 0 fraud missed! 🎯
```

---

## 💡 Key Learnings

```
1. Accuracy is misleading for fraud detection!
   → 99% accuracy by predicting everything normal!
   → Always use Recall for fraud!

2. SMOTE is critical for extreme imbalance!
   → Only 81 fraud cases to learn from!
   → SMOTE creates realistic synthetic fraud!

3. Feature Engineering caught fraud patterns:
   → high_amount → 52% of fraud has high amount!
   → Simple features can be very powerful!

4. Simple models can be best for fraud:
   → Logistic Regression beat Random Forest!
   → Fraud patterns are often linear!

5. ROC-AUC = 1.0 in synthetic data is expected!
   → Real fraud data → 0.85-0.95 more realistic!
   → Synthetic data has obvious patterns!
```

---

## 🛠️ Technologies Used
```
Python            → Programming language
Scikit-learn      → ML models and Pipeline
imbalanced-learn  → SMOTE for extreme imbalance
Pandas/NumPy      → Data manipulation
Matplotlib        → Visualization
Seaborn           → Statistical plots
```

---

## 📁 Project Structure
```
Project5_Fraud_Detection/
├── fraud_detection.ipynb    ← Main notebook
└── README.md                ← This file
```

---

## 🚀 How to Run

```bash
# Install required libraries
pip install scikit-learn imbalanced-learn pandas numpy matplotlib seaborn

# Open notebook
jupyter notebook fraud_detection.ipynb
```

---

## 📈 Business Impact
> Model catches **100% of fraudulent transactions**!
> Zero fraud cases missed in testing!
> Only 2 false alarms out of 2,020 transactions!
> Bank saves millions by detecting all fraud instantly!
