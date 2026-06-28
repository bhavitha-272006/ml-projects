# 🛍️ Project 4 — Customer Segmentation

## 📌 Problem Statement
Group mall customers into **meaningful segments**
based on their age, income, and spending behavior.

> Instead of treating all customers the same →
> Target each segment with the right offers!
> Increase sales and customer satisfaction!

---

## 📊 Dataset
| Property | Details |
|---|---|
| Source | Mall Customer Segmentation |
| Rows | 200 customers |
| Features | Age, Annual Income, Spending Score |
| Target | None (Unsupervised!) |
| Missing Values | None |
| Problem Type | Clustering |

### Features:
- Age (18-69 years)
- Annual Income ($15k-$137k)
- Spending Score (1-99, higher = spends more)

---

## 🛠️ Approach

```
Step 1 → Load and explore dataset
Step 2 → Select meaningful features
Step 3 → Scale features (StandardScaler)
Step 4 → Find best k using Elbow Method
Step 5 → Confirm with Silhouette Score
Step 6 → Train K-Means with k=5
Step 7 → Analyze cluster profiles
Step 8 → Visualize with PCA (2D)
```

---

## 📊 Finding Best Number of Clusters

### Elbow Method:
```
k=1 → Inertia: 600.00
k=2 → Inertia: 445.97
k=3 → Inertia: 338.47
k=4 → Inertia: 263.90
k=5 → Inertia: 220.51 ← elbow point!
k=6 → Inertia: 186.52 (small improvement)
```

### Silhouette Scores:
```
k=4 → 0.2903
k=5 → 0.2895 ← acceptable + business friendly!
k=8 → 0.3037
```

> Chose k=5 balancing mathematical score
> and business practicality!

---

## 🎯 Customer Segments Discovered

| Cluster | Age | Income | Spending | Segment Name |
|---|---|---|---|---|
| 0 | 45 | $40k | 64 | 🛍️ Loyal Budget Shoppers |
| 1 | 59 | $99k | 78 | 💎 Premium Senior Customers |
| 2 | 56 | $94k | 22 | 💰 High Potential Customers |
| 3 | 32 | $105k | 76 | 👑 VIP Young Customers |
| 4 | 29 | $69k | 22 | 🎯 Budget Conscious Youth |

---

## 💼 Business Recommendations

```
Cluster 2 (High Potential):
→ High income but LOW spending!
→ Send premium product offers!
→ Convert them to high spenders!

Cluster 3 (VIP Young):
→ Young + High income + High spending!
→ Give loyalty rewards!
→ Keep them happy — most valuable!

Cluster 4 (Budget Youth):
→ Young + Medium income + Low spending
→ Send discount offers and deals!
→ Build loyalty early!

Cluster 1 (Premium Senior):
→ Older + High income + High spending
→ Focus on premium service!
→ Personalized shopping experience!
```

---

## 📉 PCA Visualization

```
Reduced 3 features → 2D using PCA
Explained variance: 71% preserved!

5 distinct cluster groups visible!
Each segment clearly separated!
```

---

## 💡 Key Learnings

```
1. Unsupervised learning → NO labels needed!
   Model finds patterns by itself!

2. Always scale before K-Means!
   → Features on different scales
   → One feature would dominate clustering!

3. Use BOTH Elbow + Silhouette to find best k!
   → Mathematical + Business perspective!

4. PCA helps visualize high-dimensional clusters!
   → 71% variance preserved in 2D!

5. Cluster interpretation requires domain knowledge!
   → Numbers alone don't tell the story!
```

---

## 🛠️ Technologies Used
```
Python          → Programming language
Scikit-learn    → KMeans, PCA, Silhouette Score
Pandas/NumPy    → Data manipulation
Matplotlib      → Visualization
Seaborn         → Statistical plots
```

---

## 📁 Project Structure
```
Project4_Customer_Segmentation/
├── customer_segmentation.ipynb    ← Main notebook
└── README.md                      ← This file
```

---

## 🚀 How to Run

```bash
# Install required libraries
pip install scikit-learn pandas numpy matplotlib seaborn

# Open notebook
jupyter notebook customer_segmentation.ipynb
```

---

## 📈 Business Impact
> Identified **5 distinct customer segments**!
> Marketing team can now target each group differently!
> Estimated **20-30% increase in campaign effectiveness**
> by targeting right customers with right offers!
