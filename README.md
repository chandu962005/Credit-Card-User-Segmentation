# Bank Customer Profiling and Segmentation

<p align="center">
  <img src="https://user-images.githubusercontent.com/39597515/214297948-3f5e8cae-730f-476f-a955-ea650baf405b.png" width="800"/>
</p>

## Project Overview

In this personal project, I performed **customer segmentation for a bank** using real-world credit card data. The goal was to help the marketing team **launch targeted ad campaigns** by grouping customers into at least 3 distinctive clusters based on behavior and transactions.  

This project focuses on **understanding customer needs** through data science and ML techniques to **maximize marketing campaign conversion rates**.

---

## What I Did

- Explored **6 months of customer data**, including transactions, balance, credit usage, and tenure.  
- Performed **data cleaning, preprocessing, and feature engineering** to extract meaningful metrics.  
- Applied **clustering techniques (K-Means, PCA, Hierarchical)** to segment customers into distinct groups.  
- Evaluated clusters using metrics like **Silhouette Score, Inertia, ARI, and NMI** to ensure meaningful segmentation.  

---

## Table of Contents

| Sr No | Topic |
| ------| ----- |
| 1. | Data Preparation Pipeline |
| 2. | Feature Engineering |
| 3. | Feature Selection |
| 4. | K-Means Clustering and PCA |
| 5. | Hierarchical Clustering |
| 6. | Advanced Clustering |
| 7. | Key Learnings / Takeaways |

---

## Data Description

**Data Source:** [Kaggle – Credit Card Data](https://www.kaggle.com/arjunbhasin2013/ccdata)  

Key Features:

- `CUSTID` – Customer ID  
- `BALANCE / PURCHASES / CASH_ADVANCE` – Account balances, transaction amounts  
- Frequency Features – How often transactions occur (0–1 scale)  
- `CREDIT_LIMIT / PAYMENTS / MINIMUM_PAYMENTS` – Credit usage and payments  
- `TENURE` – Duration of credit card usage  

---

## 1. Data Preparation Pipeline

### Data Analysis & Insights

- Mean BALANCE: $1,564 | Avg PURCHASES: ~$1,000 | TENURE: ~11 years  
- Full payment rate (`PRC_FULL_PAYMENT`) low (~15%)  
- Outliers: One-off purchase $40,761, Cash advance $47,137  

### Data Cleaning & Visualization

- Handled missing values in `MINIMUM_PAYMENTS` and `CREDIT_LIMIT` using **mean imputation**  
- Created distribution plots and correlation heatmaps  
- Dropped irrelevant columns (`CUST_ID`) and removed duplicates  
- Scaled features using **StandardScaler**  

---

## 2. Feature Engineering

Created new features to capture customer behavior:

| Feature | Description |
| ------- | ----------- |
| BALANCE_USAGE_RATIO | Balance used vs credit limit |
| ONEOFF_PURCHASE_RATIO | One-off purchases / total purchases |
| INSTALLMENT_PURCHASE_RATIO | Installment purchases / total purchases |
| TOTAL_PURCHASES | Sum of one-off + installment purchases |
| PURCHASES_PER_TRX | Avg amount per purchase transaction |
| CASH_ADVANCE_PER_TRX | Avg cash advance per transaction |
| PAYMENT_RATIO | Total payments / credit limit |
| MINIMUM_PAYMENT_RATIO | Min payments / credit limit |
| FULL_PAYMENT_FLAG | 1 if full payments always made, else 0 |
| UTILIZATION_RATIO | Total spent / credit limit |

<p align="center">
  <img src="https://github.com/adiag321/Bank-Customer-Profiling-and-Segmentation/blob/main/Images/Feature_Engineering.png?raw=true" width="600"/>
</p>

---

## 3. Feature Selection

- Applied **Recursive Feature Elimination (RFE)** and **Lasso Regressor** to identify key features.

<p align="center">
  <img src="https://user-images.githubusercontent.com/39597515/214297262-5a24f94d-0d76-4929-892b-7eb0a8abf262.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/39597515/214297527-b3845ca5-0ac3-435e-a589-11a7c741d298.png" width="500"/>
</p>

---

## 4. Clustering Techniques – K-Means & PCA

- Applied **K-Means clustering** to group customers based on behavior.  
- Used **Elbow Method** to determine optimal number of clusters.  
- Applied **PCA** for dimensionality reduction and better cluster interpretability.

**PCA Highlights:**

- 14 components retained >90% variance  
- 3 components used for visualization and low-dimensional clustering  

| Approach | Silhouette | Inertia | ARI | NMI |
| -------- | ---------- | ------- | --- | --- |
| Original | 0.241 | 125,665.82 | — | — |
| PCA (14) | 0.393 | 105,474.41 | 0.569 | 0.687 |
| PCA (3)  | 0.480 | 25,465.82 | 0.338 | 0.456 |

---

## 5. Hierarchical Clustering

- Explored hierarchical clustering to identify nested clusters and validate K-Means results.  

---

## 6. Advanced Clustering

- Applied techniques like **DBSCAN** and **Gaussian Mixture Models (GMM)** for comparison.  

---

## 7. Key Learnings / Takeaways

- **PCA** improved clustering by reducing noise and redundancy.  
- **Silhouette Score** was key for evaluating natural separation of clusters.  
- **ARI and NMI** helped evaluate alignment with original clusters.  
- Final recommendation: **Use PCA with 3 components** for best cluster separation while maintaining interpretability.  

---

## Resources

- [Analytics Vidhya – Customer Profiling and Segmentation](https://www.analyticsvidhya.com/blog/2021/03/customer-profiling-and-segmentation-an-analytical-approach-to-business-strategy-in-retail-banking/)

