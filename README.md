# 🛒 Customer Personality Analysis: Dimensionality Reduction Battle (PCA vs. Full Features)

## 📋 Project Overview
This repository implements an industry-standard dimensionality reduction pipeline. By using **Principal Component Analysis (PCA)** on complex customer demographic and behavioral data, this project demonstrates how to compress **29 high-dimensional features** into a **2D visual map** without losing significant information.

The goal is to move from "Raw Data" to "Market Segments," allowing a business to target high-value customers with mathematical precision.

---

## 🏗️ Systematic Workflow

### 1. Data Processing & Realistic Cleaning
* **Feature Engineering:** Combined redundant columns like `Kidhome` and `Teenhome` into a single `Children` metric and calculated `Total_Spending` as the primary target for visualization.
* **Missing Value Strategy:** Implemented listwise deletion for missing `Income` values to ensure statistical integrity.
* **Feature Scaling:** Applied `StandardScaler` to ensure PCA isn't biased toward features with larger magnitudes (like Income vs. Kid Count)—a **mechanical necessity** for Eigen-decomposition.

### 2. The Dimensionality Reduction Battle
To identify the most efficient way to represent our customers, I compared the raw high-dimensional space against the PCA-reduced space:

* **Raw Dataset:** 29 Dimensions (Impossible to visualize, high computational cost).
* **PCA Space:** 2 Dimensions (Projected via the top two Eigenvectors).

---

## 📊 Performance Metrics (Final Results)

The project focused on **Explained Variance** and **Model Efficiency**. By reducing dimensions, we achieved a clearer separation of customer "tribes."

| Metric | Raw Features (29) | PCA Reduced (2) |
| :--- | :--- | :--- |
| **Visualizable?** | No | **Yes (2D Scatter)** |
| **Total Variance Explained** | 100% | **~58.79%** |
| **Complexity** | High (29 features) | **Low (2 features)** |
| **Key Insight Captured** | Noise + Signal | **Pure Spending Patterns** |

### Visual Insights
* **The Spending Gradient:** The 2D projection reveals a clear horizontal flow (PC1) where low-spenders (Purple) are mathematically separated from the High-Value "Whales" (Yellow).
* **Outlier Detection:** PCA successfully isolated an anomalous customer (Income outlier) at $PC1 \approx 12$, who would have otherwise skewed a standard marketing model.

---

## ⚙️ Configuration & Hyperparameters

Following the **Industry Checklist**, these parameters provided the most stable projection:

* **Scaling:** `StandardScaler` (Mean=0, Var=1).
* **PCA Components:** $n=2$ (Selected for 2D visual interpretability).
* **Convergence:** Deterministic SVD solver was used to ensure stable principal axes.

---

## 🚀 Deployment & Running Instructions

### Option 1: Google Colab (Recommended)
1. Open the `Customer_PCA_Analysis.ipynb` in Colab.
2. Run the first cell; it will prompt you to upload the dataset.
3. Upload `marketing_campaign.csv`.
4. The pipeline will automatically handle cleaning, scaling, and generate the 2D cluster map.

### Option 2: Local Environment
1. Clone the repo: `git clone https://github.com/shivirivastava0212/pca-feature-reduction-analysis.git`
2. Install dependencies: `pip install pandas scikit-learn seaborn matplotlib`
3. Run: `python pca_analysis.py`

---

## 🧠 Lessons Learned
* **Signal over Noise:** I learned that 29 features contain a lot of "noise." Reducing them to 2 components makes the **Business Logic** (Who spends more?) immediately obvious.
* **Scaling is King:** Without standardization, the "Income" feature (values in thousands) completely dominated the PCA, making the results useless.
* **Visualization as a Tool:** PCA isn't just for models; it's for **stakeholders**. A CEO can't read a 29D matrix, but they can understand a 2D cluster map.

---

## 👨‍💻 Author
**Shivi Srivastava** Aspiring AI Engineer | Amity University Uttar Pradesh  
[LinkedIn Profile](https://www.linkedin.com/in/shivi-srivastava-8a5086310/) | [GitHub Portfolio](https://github.com/shivisrivastava0212)
