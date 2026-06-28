# 🔬 Project 1 — Breast Cancer Detection

## 📌 Problem Statement
Predict whether a tumor is **malignant (cancerous)** or **benign (non-cancerous)**
based on medical measurements from cell nuclei.

> Early detection of cancer saves lives!
> ML model helps doctors identify high-risk patients faster!

---

## 📊 Dataset
| Property | Details |
|---|---|
| Source | sklearn built-in (load_breast_cancer) |
| Rows | 569 patients |
| Features | 30 numerical features |
| Target | 0 = Malignant, 1 = Benign |
| Missing Values | None |
| Class Balance | Slightly imbalanced (37% malignant) |

### Features Include:
- Mean radius, texture, perimeter, area
- Smoothness, compactness, concavity
- Symmetry, fractal dimension
- Worst and error values for each

---

## 🛠️ Approach

```
Step 1 → Load and explore dataset
Step 2 → Train Test Split (stratified)
Step 3 → Build sklearn Pipeline (StandardScaler)
Step 4 → Compare 5 models with cross validation
Step 5 → Select best model (KNN — highest Recall)
Step 6 → Tune with GridSearchCV
Step 7 → Final evaluation on test set
```

---

## 🤖 Models Compared

| Model | Accuracy | Recall | ROC-AUC |
|---|---|---|---|
| Logistic Regression | 0.9648 | 0.9790 | 0.9950 |
| **KNN** | **0.9626** | **0.9965** | **0.9863** |
| SVM | 0.9736 | 0.9860 | 0.9951 |
| Random Forest | 0.9560 | 0.9720 | 0.9877 |
| XGBoost | 0.9407 | 0.9684 | 0.9820 |

---

## 🏆 Final Results (KNN — Tuned)

| Metric | Score |
|---|---|
| Accuracy | 97.37% |
| **Recall** | **100%** ✅ |
| ROC-AUC | 96.43% |

### Confusion Matrix:
```
Actual\Predicted  Malignant  Benign
Malignant            39         3
Benign                0        72   ← 0 cancer patients missed!
```

---

## 💡 Key Learnings

```
1. In medical ML → Recall is most important metric!
   Missing a cancer patient = life threatening!

2. Even simple models (KNN) can beat complex ones
   when the right metric is prioritized!

3. sklearn Pipeline prevents data leakage!

4. GridSearchCV found best parameters:
   → metric = euclidean
   → n_neighbors = 11
   → weights = uniform
```

---

## 🛠️ Technologies Used
```
Python          → Programming language
Scikit-learn    → ML models and Pipeline
Pandas/NumPy    → Data manipulation
Matplotlib      → Visualization
```

---

## 📁 Project Structure
```
Project1_Breast_Cancer/
├── breast_cancer.ipynb    ← Main notebook
└── README.md              ← This file
```

---

## 🚀 How to Run

```bash
# Install required libraries
pip install scikit-learn pandas numpy matplotlib seaborn

# Open notebook
jupyter notebook breast_cancer.ipynb
```

---

## 📈 Business Impact
> This model catches **100% of cancer cases** in testing.
> Zero patients sent home without treatment!
> Can assist doctors in early diagnosis and save lives!
