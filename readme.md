![monthly_revenue_trends](https://github.com/user-attachments/assets/458ad152-f99b-416d-97af-a65559120e9c)# Predictive Customer - Lifetime Value, Spend Probability and Behaviour Analysis

## Introduction

This project delves into analyzing and predicting Customer Lifetime Value (CLV) by examining customer purchasing patterns, behavior trends, and engagement metrics. 
Using a real-world dataset, we analyze and derive insights to improve customer retention strategies and forecast future revenue streams.

## Business Problems That We'll Be Answering
- Which customers have the highest spending probability in the next 90 days (clv - 90days)
- Which customers have recently purchased but are unlikely to buy (survival analysis)
- Which customers were predicted to purchase but didn't (missed opportunities)

## Dataset
We are working with CDNow Dataset, CDNow was a Dot-Com company that went bust in the early 2000s. They then donated the dataset, it's highly reliable, realistic,
and perfect for our particular use case.
**Features**
- Customer ID
- Purchase Date
- Purchase Quantity
- Order Value

## Table of Contents
- [Feature Engineering](#Feature-Engineering)
- [Models]
  - [CLV Model](#Spend-Amount-Prediction-Model)
  - [Churn Probability Model](#Spend-Probability-Prediction-Model)
- [Analysis]
  - [Dataset Analysis]
  - [Cohort Analysis]
  - [RFM Analysis]
  - [CLV Analysis]
  - [Churn Probability Analysis]
  - [Timeseries and Forecasting]
 
## 1. Feature Engineering

The **Feature Engineering** notebook focuses on transforming raw customer data into meaningful features suitable for machine learning models. Key steps include:

### Objectives
- Process and clean raw transactional data.
- Extract features encapsulating customer behavior, such as recency, frequency, and monetary value (RFM).
- Generate advanced predictors like average spending, purchase trends, and customer segmentation metrics.

### Key Features Created
- **Recency**: Days since the last purchase.
- **Frequency**: Total number of purchases.
- **Monetary Metrics**: 
  - `price_sum`: Total spend across transactions.
  - `price_mean`: Average spend per transaction.
- **spend_90_total**: Predicted customer lifetime value (CLV) for the next 90 days.

### Methods
- Data aggregation and grouping based on `customer_id`.
- Handling missing data and outliers.
- Normalization and scaling of numerical features for model compatibility.

---

## 2. Spend Amount Prediction Model

The **Spend Amount Prediction Model** notebook develops a regression model to estimate the total spend by customers over the next 90 days. This forms the cornerstone of CLV predictions.

### Objectives
- Train a model to predict `spend_90_total` using features derived from the Feature Engineering phase.
- Evaluate and optimize model performance.

### Methodology
- **Model Used**: Gradient Boosting Regressor (e.g., XGBoost, LightGBM).
- **Feature Selection**:
  - Recency, Frequency, Monetary metrics, and additional behavioral features.
- **Evaluation Metrics**:
  - Mean Absolute Error (MAE)
  - Root Mean Square Error (RMSE)

### Workflow
1. **Data Splitting**: Stratified train-test split.
2. **Hyperparameter Tuning**: Using grid search and cross-validation.
3. **Performance Analysis**: Visualizing predictions versus actual spend values to ensure reliability.

### Outcomes
- Model achieves robust prediction accuracy with MAE and RMSE within acceptable thresholds.
- Feature importance analysis highlights key drivers of customer spending behavior.

---

## 3. Spend Probability Prediction Model

The **Spend Probability Prediction Model** notebook focuses on predicting the likelihood of a customer purchasing within the next 90 days. This complements the spend amount model to provide a holistic view of customer behavior.

### Objectives
- Build a classification model to predict `spend_90_flag` (a binary indicator of future purchases).
- Combine predictions with spending amounts to prioritize high-value customers.

### Methodology
- **Model Used**: Random Forest Classifier or Logistic Regression.
- **Features**: Same as the Spend Amount Prediction Model.
- **Evaluation Metrics**:
  - Accuracy
  - Precision, Recall, and F1-Score
  - Area Under the Receiver Operating Characteristic (ROC-AUC) Curve

### Workflow
1. **Label Encoding**: Transform `spend_90_flag` to a binary variable.
2. **Model Training**: Employ robust training techniques to handle class imbalance.
3. **Threshold Tuning**: Adjust decision thresholds to maximize business-specific metrics.

### Outcomes
- High accuracy and ROC-AUC scores ensure reliable probability predictions.
- Predictions integrated with spend amount estimates enable targeted marketing and retention strategies.

## Dataset Analysis

### Revenue Contribution by Top Customers
![revenue_contribution_by_top_10_customers](https://github.com/user-attachments/assets/38620e82-8745-4cf4-be90-921e4e421316)

### Monthly Revenue Trends
![monthly_revenue_trends](https://github.com/user-attachments/assets/ff44be4a-7c0a-4c42-a54c-da5724a8e210)

### Order Frequency Analysis
![order_frequency_analysis](https://github.com/user-attachments/assets/056fb078-561a-467e-bc09-0e65a7fe951f)

### Revenue By Product Price
![revenue_by_product_price](https://github.com/user-attachments/assets/47b6f5d2-6f4f-433a-8620-b46e1c9ca3b4)

---

## Cohort Analysis

---

## RFM Analysis

### Distribution of RFM Metrics
![rfm_metrics_distribution](https://github.com/user-attachments/assets/a22a8345-1b78-45c4-bec2-0901e900eed6)

### Relationship Between RFM metrics
![rfm_relationship_heatmap](https://github.com/user-attachments/assets/7a4aee8d-a5a5-4de1-b536-4d331e8189f6)

### Customer Spread based on Recency and Frequency
![rfm_recency_vs_frequency](https://github.com/user-attachments/assets/55826e12-f4d9-4ea2-aea7-d0c66ea64780)

### Customer Spread based on Monetary Value and Frequency
![rfm_frequency_vs_monetary](https://github.com/user-attachments/assets/feb2954b-ce1c-48c9-b2f4-dcee22f5c983)

---

## Prediction Analysis

---


