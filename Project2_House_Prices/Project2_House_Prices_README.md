# 🏠 Project 2 — House Price Prediction

## 📌 Problem Statement
Predict the **median house value** of California districts
based on housing and demographic features.

> Banks use this to decide loan amounts!
> Buyers use this to know if price is fair!
> Sellers use this to set correct price!

---

## 📊 Dataset
| Property | Details |
|---|---|
| Source | Kaggle — California Housing Prices |
| Rows | 20,635 districts |
| Features | 11 (after engineering) |
| Target | median_house_value (continuous) |
| Missing Values | 207 in total_bedrooms (1%) |
| Problem Type | Regression |

### Features:
- longitude, latitude
- housing_median_age
- total_rooms, total_bedrooms
- population, households
- median_income
- ocean_proximity (categorical)

---

## 🔧 Feature Engineering

| New Feature | Formula | Why Created |
|---|---|---|
| rooms_per_household | total_rooms / households | Average rooms per house |
| bedrooms_per_room | total_bedrooms / total_rooms | Bedroom ratio |
| population_per_household | population / households | Area crowdedness |

> Feature Engineering improved correlation from 0.049 to 0.256!

---

## 🛠️ Approach

```
Step 1 → Load and explore dataset
Step 2 → Remove ISLAND category (only 5 rows!)
Step 3 → Create 3 new features
Step 4 → Cap outliers at 99th percentile
Step 5 → Build Pipeline (KNNImputer + Scaler + Encoder)
Step 6 → Compare 5 regression models
Step 7 → Select XGBoost (best R²)
Step 8 → Tune with GridSearchCV
Step 9 → Final evaluation
```

---

## 🤖 Models Compared

| Model | R² | RMSE | MAE |
|---|---|---|---|
| Linear Regression | 0.68 | $65,442 | $48,060 |
| Ridge | 0.68 | $65,441 | $48,055 |
| Lasso | 0.68 | $65,442 | $48,060 |
| Random Forest | 0.52 | $79,764 | $52,222 |
| **XGBoost** | **0.79** | **$52,067** | **$35,236** |

---

## 🏆 Final Results (XGBoost — Tuned)

| Metric | Score |
|---|---|
| **R²** | **84.33%** ✅ |
| RMSE | $45,481 |
| MAE | $29,198 |

### Best Parameters Found:
```
learning_rate = 0.1
max_depth     = 7
n_estimators  = 200
```

---

## 💡 Key Learnings

```
1. Linear models (LR, Ridge, Lasso) all got same R²=0.68
   → House prices are NON-LINEAR!
   → Tree based models handle this better!

2. Feature Engineering is crucial!
   → rooms_per_household more useful than total_rooms

3. Outlier capping prevents extreme values
   from affecting predictions!

4. KNNImputer fills missing bedrooms
   based on similar houses → better than mean!

5. CV R² (0.8382) close to Test R² (0.8433)
   → No overfitting! Model generalizes well!
```

---

## 🛠️ Technologies Used
```
Python          → Programming language
Scikit-learn    → ML models and Pipeline
XGBoost         → Best performing model
Pandas/NumPy    → Data manipulation
Matplotlib      → Visualization
```

---

## 📁 Project Structure
```
Project2_House_Prices/
├── house_prices.ipynb    ← Main notebook
├── housing.csv           ← Dataset
└── README.md             ← This file
```

---

## 🚀 How to Run

```bash
# Install required libraries
pip install scikit-learn xgboost pandas numpy matplotlib seaborn

# Open notebook
jupyter notebook house_prices.ipynb
```

---

## 📈 Business Impact
> Model explains **84% of house price variation**!
> Average prediction error of only **$29,198**
> on houses worth $200,000 on average (14% error rate)!
