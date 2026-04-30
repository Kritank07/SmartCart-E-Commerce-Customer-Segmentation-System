# SmartCart – Customer Segmentation Analysis

A machine learning project that segments SmartCart customers into distinct behavioral groups using clustering algorithms, enabling targeted marketing and personalized business strategies.

---

## Overview

This project analyzes customer data from SmartCart to identify meaningful customer segments based on demographics, spending behavior, and purchase patterns. It uses unsupervised learning techniques — KMeans and Agglomerative Clustering — to group customers and derives actionable business insights from each cluster.

---

## Dataset

**File:** `smartcart_customers.csv`

Key features used in the analysis:

| Category | Features |
|---|---|
| Demographics | `Year_Birth`, `Education`, `Marital_Status`, `Income` |
| Household | `Kidhome`, `Teenhome` |
| Spending | `MntWines`, `MntFruits`, `MntMeatProducts`, `MntFishProducts`, `MntSweetProducts`, `MntGoldProds` |
| Engagement | `Recency`, `Response`, `Dt_Customer` |

---

## Tech Stack

- **Python 3.x**
- `pandas` – Data manipulation
- `numpy` – Numerical operations
- `matplotlib` / `seaborn` – Data visualization
- `scikit-learn` – Preprocessing, PCA, KMeans, Agglomerative Clustering, Silhouette Score
- `kneed` – Elbow method / optimal K detection

---

## Project Pipeline
### 1. Data Preprocessing
- Converted `Income` to numeric and filled missing values with the median
- Removed outliers: age > 90 and income > 600,000

### 2. Feature Engineering
- **Age** – Derived from `Year_Birth`
- **Customer Tenure** – Days since first purchase (relative to latest date)
- **Total Spending** – Sum of all product category spend
- **Total Children** – `Kidhome + Teenhome`
- **Education** – Simplified into 3 tiers: `UnderGraduate`, `Graduate`, `PostGraduate`
- **Living_With** – Simplified from marital status into `Partner` or `Alone`

### 3. Exploratory Data Analysis
- Pairplots for key numerical features
- Correlation heatmap

### 4. Feature Encoding & Scaling
- One-Hot Encoding for categorical features (`Education`, `Living_With`)
- StandardScaler for numerical normalization

### 5. Dimensionality Reduction
- PCA reduced features to **3 components** for clustering and 3D visualization

### 6. Clustering
- **Elbow Method** (WCSS) + **Silhouette Score** to determine optimal K
- Compared **KMeans** vs **Agglomerative Clustering (Ward linkage)**
- Agglomerative Clustering selected as the better-performing model

---

## Results – 4 Customer Clusters

| Cluster | Profile | Strategy |
|---|---|---|
| **C0** | Moderate income, family-oriented, partners | Offer **family discounts & bundle deals** |
| **C1** | High income, low children, moderate response | Build **loyalty programs & premium perks** |
| **C2** | Lower income, solo, high web visits | Target with **digital ads & flash sales** |
| **C3** | Highest income, older, best response, max store & catalog purchases | **Golden cluster** – focus for premium services & highest ROI |

> Clusters 1 and 3 are premium customers. Clusters 0 and 2 are budget-conscious segments.
