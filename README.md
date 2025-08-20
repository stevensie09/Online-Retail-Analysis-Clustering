# Online Retail Customer Segmentation using RFM and K-Means Clustering

## 📖 Project Overview
This project focuses on analyzing a transnational online retail dataset to understand customer purchasing behavior. The goal is to segment customers into distinct groups using a combination of RFM (Recency, Frequency, Monetary) analysis and the K-Means clustering algorithm. This segmentation allows for targeted marketing strategies, customer retention programs, and personalized customer experiences.

**Keywords**: Customer Segmentation, RFM Analysis, K-Means Clustering, Unsupervised Machine Learning, Marketing Analytics, E-commerce

## 📊 Dataset
**Source**: [UCI Machine Learning Repository - Online Retail II Data Set](https://archive.ics.uci.edu/ml/datasets/Online+Retail+II)

**Description**: The dataset contains all transactions occurring between 01/12/2009 and 09/12/2011 for a UK-based online retail store. The company primarily sells unique all-occasion gifts.

**Contents**:
- **InvoiceNo**: Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction. If this code starts with the letter 'C', it indicates a cancellation.
- **StockCode**: Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.
- **Description**: Product (item) name. Nominal.
- **Quantity**: The quantities of each product (item) per transaction. Numeric.
- **InvoiceDate**: Invoice date and time. Numeric, the day and time when each transaction was generated.
- **UnitPrice**: Unit price. Numeric, product price per unit in sterling.
- **CustomerID**: Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.
- **Country**: Country name. Nominal, the name of the country where each customer resides.

## 🎯 Objective
To clean and preprocess the raw transactional data, engineer meaningful features based on the RFM framework, and apply K-Means clustering to identify homogenous groups of customers with similar purchasing behaviors.

## 🛠️ Methodology & Technical Steps
### 1. Data Exploration & Cleaning
The initial phase involved a thorough exploration and cleaning of the data to ensure its quality for analysis:
- Handled missing values, primarily in the `Stock Code` column.
- Removed entries with negative `Quantity` and zero `Price`, which typically represent cancelled orders, returns, or administrative adjustments.
- Filtered out non-product entries (e.g., postage charges, bank fees, manual adjustments) by standardizing `StockCode` and `Invoice` formats.
- The cleaning process retained approximately 77% of the original records, resulting in a robust dataset for analysis.

### 2. Feature Engineering (RFM Analysis)
The core customer features were created using the RFM framework:
- **Recency (R)**: The number of days since a customer's last purchase. (Lower values are better)
- **Frequency (F)**: The total number of unique invoices (transactions) per customer. (Higher values are better)
- **Monetary Value (M)**: The total amount of money spent by a customer (`Quantity` * `UnitPrice`). (Higher values are better)
These three metrics provide a composite view of customer value and engagement.

### 3. Machine Learning: K-Means Clustering
- **Algorithm**: The K-Means clustering algorithm, an unsupervised learning method, was used to group customers based on their RFM scores.
- **Preprocessing**: The RFM features were standardized using `StandardScaler` to ensure each feature contributes equally to the distance calculations.
- **Optimal Clusters (k)**: The Elbow Method and Silhouette Score were used to determine the optimal number of clusters, balancing interpretability and cluster quality.

## 📈 Results
After applying K-Means clustering, customers were segmented into distinct groups. While the exact number of clusters is determined in the notebook, typical segments include:
- **Champions**: Best customers (high R, F, M).
- **Loyal Customers**: Make regular purchases (high F, good M and R).
- **At-Risk Customers**: Customers who were once good but haven't purchased recently (low R, but historically good F/M).
- **New Customers**: Recent purchasers who haven't bought frequently yet (high R, low F).
- **Lost Customers**: Worst customers (low R, F, M).

These segments allow for targeted business strategies:
- **Champions**: Reward them, ask for reviews, offer loyalty programs.
- **Loyal Customers**: Upsell higher-value products and keep them engaged.
- **At-Risk Customers**: Send win-back campaigns and renewal offers.
- **New Customers**: Provide onboarding support and introductory offers.

## 📁 Project Structure
```
online-retail-segmentation/
├── data/
│   └── online_retail_II.xlsx          # Raw dataset (not included in repo)
├── notebooks/
│   └── online-retail-data-clustering.ipynb  # Main analysis Jupyter notebook
├── README.md                          # This file
└── requirements.txt                   # Python dependencies
```

## 📚 References
- Chen, D., Sain, S.L., and Guo, K. (2012). Data mining for the online retail industry: A case study of RFM model-based customer segmentation using data mining. *Journal of Database Marketing & Customer Strategy Management*, Vol. 19, No. 3, pp. 197–208. [https://link.springer.com/article/10.1057/dbm.2012.17](https://link.springer.com/article/10.1057/dbm.2012.17)
- Dua, D. and Graff, C. (2019). UCI Machine Learning Repository. Irvine, CA: University of California, School of Information and Computer Science.

