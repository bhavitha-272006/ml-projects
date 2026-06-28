# 📱 Project 3 — Customer Churn Prediction

## 📌 Problem Statement
Predict whether a telecom customer will **leave (churn)**
or **stay** based on their usage patterns and contract details.

> Losing a customer costs 5x more than keeping one!
> Early churn prediction → company can offer deals → save customer!

---

## 📊 Dataset
| Property | Details |
|---|---|
| Source | Telco Customer Churn (Kaggle) |
| Rows | 7,043 customers |
| Features | 19 (after cleaning) |
| Target | Churn (0=Stay, 1=Leave) |
| Missing Values | 11 spaces in TotalCharges |
| Class Balance | Imbalanced (73% stay, 27% churn) |

### Key Features:
- tenure (months with company)
- Contract type (Month-to-month, One year, Two year)
- MonthlyCharges, TotalCharges
- Internet Service, Online Security
- Payment Method, Paperless Billing

---

## 🔧 Data Cleaning

```
Issue Found: TotalCharges stored as text (object)!
→ 11 spaces causing dtype issue
→ Fixed: Replace spaces → NaN → convert to float → fill median

Churn column: 'Yes'/'No' → converted to 1/0
CustomerID: dropped (not useful for prediction)
```

---

## 🛠️ Approach

```
Step 1 → Load and explore dataset
Step 2 → Fix TotalCharges dtype issue
Step 3 → Convert Churn to 0/1
Step 4 → Identify column types (numerical/categorical/binary)
Step 5 → Build Pipeline with SMOTE
Step 6 → Compare 5 models
Step 7 → Select Logistic Regression (best Recall)
Step 8 → Tune with GridSearchCV
Step 9 → Final evaluation
```

---

## ⚖️ Handling Imbalanced Data

```
Problem: 73% stay vs 27% churn
→ Model might just predict everyone stays!
→ Gets 73% accuracy but catches 0 churners!

Solution: SMOTE (Synthetic Minority Oversampling)
→ Creates synthetic churn examples
→ Balances dataset to 50/50
→ Model learns both classes equally!
```

---

## 🤖 Models Compared

| Model | Recall | F1 | ROC-AUC |
|---|---|---|---|
| **Logistic Regression** | **0.79** | **0.63** | **0.84** |
| KNN | 0.74 | 0.56 | 0.76 |
| SVM | 0.72 | 0.62 | 0.83 |
| Random Forest | 0.57 | 0.58 | 0.82 |
| XGBoost | 0.57 | 0.59 | 0.82 |

---

## 🏆 Final Results (Logistic Regression — Tuned)

| Metric | Score |
|---|---|
| Accuracy | 73.74% |
| **Recall** | **79.14%** ✅ |
| F1 | 61.54% |
| ROC-AUC | 84.06% |

### Best Parameters Found:
```
C       = 1.0
penalty = l1 (Lasso regularization)
solver  = liblinear
```

### Confusion Matrix:
```
Actual\Predicted  Stay   Churn
Stay               743    292
Churn               78    296   ← caught 79% of churners!
```

---

## 💡 Key Learnings

```
1. Simple model (Logistic Regression) beat complex ones!
   → Churn patterns are mostly LINEAR!

2. SMOTE must be applied ONLY on training data!
   → Test data must reflect real distribution!

3. Recall is most important for churn:
   → Missing a churner = losing a customer = losing money!

4. L1 penalty won in GridSearchCV:
   → Removes useless features automatically!
   → 19 features → some were not useful!
```

---

## 🛠️ Technologies Used
```
Python            → Programming language
Scikit-learn      → ML models and Pipeline
imbalanced-learn  → SMOTE for class balancing
Pandas/NumPy      → Data manipulation
Matplotlib        → Visualization
```

---

## 📁 Project Structure
```
Project3_Customer_Churn/
├── customer_churn.ipynb    ← Main notebook
├── telco_churn.csv         ← Dataset
└── README.md               ← This file
```

---

## 🚀 How to Run

```bash
# Install required libraries
pip install scikit-learn imbalanced-learn pandas numpy matplotlib seaborn

# Open notebook
jupyter notebook customer_churn.ipynb
```

---

## 📈 Business Impact
> Model identifies **79% of customers who will leave**!
> Company can offer targeted deals to these customers!
> Retaining even 50% of predicted churners
> saves significant revenue!
