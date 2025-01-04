![clv_feature_importance](https://github.com/user-attachments/assets/4d6787fe-afdf-4c1e-9b4b-3d9949af96ed)# Predictive - Customer Lifetime Value, Spend Probability, and Behaviour Analysis

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
- [Visualizations]
  - [Dataset Analysis](#Dataset-Analysis)
  - [RFM Analysis](#RFM-Analysis)
  - [CLV Analysis](#CLV-Analysis)
  - [Churn Probability Analysis](#Churn-Probability-Analysis)
  - [Timeseries and Forecasting](#Timeseries-and-Forecasting)

---

## Feature Engineering

### Objectives
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

## Spend Amount Prediction Model

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

### Model Performance
**Model’s predictions are off by about 9.65 units which for out particular dataset evaluates to 9-10 dollars**

### Feature Importance
![clv_feature_importance](https://github.com/user-attachments/assets/d676e09f-63f2-48fa-aaed-9935c30b58cf)

---

## Spend Probability Prediction Model

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

### Model Performance
**ROC-AUC: 0.84**

### Feature Importance
![churn_feature_importance](https://github.com/user-attachments/assets/515473e8-bc91-4b20-9593-8f94c36b5c90)

---

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

## CLV Analysis

### Predicted Spend over Recency, Frequency, Avg Spend, Total Spend
![predicted_spend_vs_features](https://github.com/user-attachments/assets/85a53bb8-954e-4100-a72b-95d6ee628719)

### Correlation Heatmap between all the Features and Predicted Spend
![predicted_clv_correlation_heatmap](https://github.com/user-attachments/assets/994b20bd-b73a-4cfd-8660-36d2fca818a8)

### Distribution of Customer Spending
![distribution_of_customer_spending](https://github.com/user-attachments/assets/b271b7dd-0ad3-4ed5-8e1d-887cd2323cf5)

### Relationship Between Frequency and Predicted Spend
![relationship_btw_predicted_spend_and_frequency](https://github.com/user-attachments/assets/497dfdc8-4e37-4f8f-8c5e-f7ec5f8370b9)

### Customer Segmentation by Value and Frequency
![segmentation_by_value_frequency](https://github.com/user-attachments/assets/2a7a180b-ff8b-471b-8d21-b9a59fcb90f8)

### Correlation Heatmap of RMF and Predicted Spend
![rmf_predicted_spend_correlation_heatmap](https://github.com/user-attachments/assets/28b5fbf1-b29f-4d7f-925c-e0f6c8f58b2a)

---

## Churn Probability Analysis

### Distribution of Predicted Purchase Probability
![purchase_and_churn_probability_distribution](https://github.com/user-attachments/assets/42e4847b-0c39-445a-a681-aedae2032b94)

### Purchase Probability over RFM Features
![purchase_prob_over_rfm](https://github.com/user-attachments/assets/1c1f2fe1-05b9-40d7-a5fe-dac94e3b5c4b)

### Predicted Churn Probability Correlation Heatmap
![churn_correlation_heatmap](https://github.com/user-attachments/assets/0fdecf9f-ec8d-4579-88f7-de405caa1f49)

---

## Timeseries and Forecasting

### Total Spend over Time
![total_spend_over_time](https://github.com/user-attachments/assets/75ab2bb3-f60a-4446-b06f-a0996feba4b2)

### Avg Spend over Month and DayofWeek
![avg_spend_by_month](https://github.com/user-attachments/assets/c57016a7-9725-4253-a7fb-e004b2d2836e)
![avg_spend_by_dayofweek](https://github.com/user-attachments/assets/e6415916-b02f-4bde-a4a4-9062a05a6c15)

### Revenue with Moving Averages
![total_spend_with_moving_avg](https://github.com/user-attachments/assets/a60d14e8-ac77-4956-94b3-380480c7ab86)

### Customer Spend over Time Density Heatmap
![customer_spend_over_time_heatmap](https://github.com/user-attachments/assets/e34baa06-99cf-434f-9a1c-9d1031780985)

### Spend Forecast for the Next 90 days
![spend_forecast_for_next_90_days](https://github.com/user-attachments/assets/05ddb976-5842-4175-b40d-47ca892346d6)

---

## Conclusion

Through meticulous feature engineering and model development, this project successfully predicts Customer Lifetime Value, providing valuable insights for strategic decision-making in customer relationship management. The analyses underscore the importance of tailored marketing strategies to enhance customer retention and profitability.

---

