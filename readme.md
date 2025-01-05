# **Predictive - Customer Lifetime Value, Spend Probability, and Behaviour Analysis**

## Introduction
Customer behavior analysis is a vital process that can provide businesses with valuable insights into their customers' behaviors and preferences. In this project, I analized the CDNOW dataset to determine customer buying patterns based on Recency, Frequency, and Monetary Value (RFM).

- Using Python, I performed RFM analysis to determine each customer's Recency, Frequency, and Monetary Value based on their transaction history. This analysis will help us understand how recently and how often customers make purchases, as well as the average amount they spend.

- Next, I used the K-Means algorithm to segment customers into groups based on their RFM scores. This segmentation will help identify distinct customer groups and tailor marketing strategies and promotions to each group's specific needs and preferences.

- I also developed a machine learning model to predict the probability of customer purchase and the likely purchase amount using XGBRegressor and XGBClassifier. By predicting customer behavior, businesses can better understand their customers' needs and preferences and adjust their marketing strategies accordingly.

- Finally, I conducted cohort analysis to determine customer lifetime value (CLV) and measure the effectiveness of our marketing strategies. By analyzing customer behavior over time, we can gain insights into how our customer base changes and adapt our strategies to meet their evolving needs.

Overall, this project will provide valuable insights into customer behavior, allowing businesses to improve customer engagement, retention, and revenue.

---

## Business Problems That We'll Be Answering
- **Which customers have the highest spending probability in the next 90 days?**
- **Which customers have recently purchased but are unlikely to buy again?** (Survival Analysis)
- **Which customers were predicted to purchase but didn't?** (Missed Opportunities)

---

## Dataset
We are working with the **CDNow Dataset**, which was donated after the company went bankrupt in the early 2000s. The dataset is highly reliable, realistic, and well-suited for our use case.

### Features
- **Customer ID**: Unique identifier for each customer.
- **Purchase Date**: Date of each purchase.
- **Purchase Quantity**: Number of items purchased.
- **Order Value**: Total value of each transaction.

---

## Table of Contents
- [Feature Engineering](#feature-engineering)
- **Models**
  - [CLV Model](#spend-amount-prediction-model)
  - [Churn Probability Model](#spend-probability-prediction-model)
- **Visualizations**
  - [Dataset Analysis](#dataset-analysis)
  - [RFM Analysis](#rfm-analysis)
  - [CLV Analysis](#clv-analysis)
  - [Churn Probability Analysis](#churn-probability-analysis)
  - [Timeseries and Forecasting](#timeseries-and-forecasting)

---

## Feature Engineering

### Objectives
- Create features encapsulating customer behavior, such as recency, frequency, and monetary value (RFM).
- Generate advanced predictors like average spending, purchase trends, and segmentation metrics.

### Key Features Created
- **Recency**: Days since the last purchase.
- **Frequency**: Total number of purchases.
- **Monetary Metrics**:
  - `price_sum`: Total spend across all transactions.
  - `price_mean`: Average spend per transaction.
- **spend_90_total**: Predicted customer lifetime value (CLV) for the next 90 days.

### Methods
- Aggregation and grouping based on `customer_id`.
- Handling missing data and outliers.
- Normalization and scaling of numerical features to enhance model performance.

---

## Spend Amount Prediction Model

### Objectives
- Train a model to predict `spend_90_total` using features derived from the Feature Engineering phase.
- Evaluate and optimize model performance.

### Methodology
- **Model Used**: Gradient Boosting Regressor (e.g., XGBoost, LightGBM).
- **Feature Selection**:
  - Recency, frequency, monetary metrics, and other behavioral features.
- **Evaluation Metrics**:
  - Mean Absolute Error (MAE)
  - Root Mean Square Error (RMSE)

### Workflow
1. **Data Splitting**: Stratified train-test split.
2. **Hyperparameter Tuning**: Using grid search and cross-validation.
3. **Performance Analysis**: Visualizing predictions versus actual spend values.

### Outcomes
- The model achieves robust prediction accuracy with MAE and RMSE within acceptable thresholds.
- Feature importance analysis highlights the key drivers of customer spending behavior.

### Model Performance
- **Mean Absolute Error (MAE)**: Predictions are off by about 9.65 units, equivalent to 9-10 dollars.

### Feature Importance
![CLV Feature Importance](https://github.com/user-attachments/assets/d676e09f-63f2-48fa-aaed-9935c30b58cf)

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
2. **Model Training**: Employ robust techniques to handle class imbalance.
3. **Threshold Tuning**: Adjust decision thresholds to maximize business-specific metrics.

### Outcomes
- High accuracy and ROC-AUC scores ensure reliable probability predictions.
- Predictions integrated with spend amount estimates enable targeted marketing and retention strategies.

### Model Performance
- **ROC-AUC**: 0.84

### Feature Importance
![Churn Feature Importance](https://github.com/user-attachments/assets/515473e8-bc91-4b20-9593-8f94c36b5c90)

---

## Visualizations

### Customer Activity
![customer_activity_trendline](https://github.com/user-attachments/assets/04a0d6ba-65e0-4c73-9514-e9ad955d5595)

### Parallel Coordinates for All Customer Metrics
![customer_metrics_predicted_clv_parallelcoords](https://github.com/user-attachments/assets/0ca7fd93-f1a8-4912-ba08-7d38d499d010)

### Dataset Analysis
- **Revenue Contribution by Top Customers**  
![Revenue Contribution](https://github.com/user-attachments/assets/38620e82-8745-4cf4-be90-921e4e421316)

- **Monthly Revenue Trends**  
![Monthly Revenue Trends](https://github.com/user-attachments/assets/ff44be4a-7c0a-4c42-a54c-da5724a8e210)

- **Order Frequency Analysis**  
![Order Frequency Analysis](https://github.com/user-attachments/assets/056fb078-561a-467e-bc09-0e65a7fe951f)

- **Revenue by Product Price**  
![Revenue by Product Price](https://github.com/user-attachments/assets/47b6f5d2-6f4f-433a-8620-b46e1c9ca3b4)

---

### RFM Analysis
- **Distribution of RFM Metrics**  
![RFM Metrics Distribution](https://github.com/user-attachments/assets/a22a8345-1b78-45c4-bec2-0901e900eed6)

- **Relationship Between RFM Metrics**  
![RFM Heatmap](https://github.com/user-attachments/assets/7a4aee8d-a5a5-4de1-b536-4d331e8189f6)

- **Customer Spread by Recency and Frequency**  
![Recency vs Frequency](https://github.com/user-attachments/assets/55826e12-f4d9-4ea2-aea7-d0c66ea64780)

- **Customer Spread by Monetary Value and Frequency**  
![Frequency vs Monetary](https://github.com/user-attachments/assets/feb2954b-ce1c-48c9-b2f4-dcee22f5c983)

---

### CLV Analysis
- **Predicted Spend vs Features**  
![Predicted Spend](https://github.com/user-attachments/assets/85a53bb8-954e-4100-a72b-95d6ee628719)

- **Correlation Heatmap**  
![Correlation Heatmap](https://github.com/user-attachments/assets/994b20bd-b73a-4cfd-8660-36d2fca818a8)

- **Customer Spending Distribution**  
![Spending Distribution](https://github.com/user-attachments/assets/b271b7dd-0ad3-4ed5-8e1d-887cd2323cf5)

- **Relationship Between Frequency and Predicted Spend**
![relationship_btw_predicted_spend_and_frequency](https://github.com/user-attachments/assets/68708b66-dcc0-4294-86db-5f593811c14a)

- **Customer Segmentation by Value and Frequency**
![segmentation_by_value_frequency](https://github.com/user-attachments/assets/e6eb459d-7a8c-4629-968b-ba5b70842164)

- **Correlation Heatmap of RMF and Predicted Spend**
![rmf_predicted_spend_correlation_heatmap](https://github.com/user-attachments/assets/aef017ef-fb14-4868-a622-e13697cf37fa)

---

### Churn Probability Analysis
- **Purchase Probability Distribution**  
![Purchase Probability](https://github.com/user-attachments/assets/42e4847b-0c39-445a-a681-aedae2032b94)

- **Purchase Probability over RFM**  
![Purchase vs RFM](https://github.com/user-attachments/assets/1c1f2fe1-05b9-40d7-a5fe-dac94e3b5c4b)

- **Predicted Churn Probability Correlation Heatmap**
![churn_correlation_heatmap](https://github.com/user-attachments/assets/fa7418cc-fdee-46f6-bafe-c3a106c765d4)

---

### Timeseries and Forecasting
- **Spend Trends Over Time**  
![Spend Over Time](https://github.com/user-attachments/assets/75ab2bb3-f60a-4446-b06f-a0996feba4b2)

- **Avg Spend over Month and DayofWeek**
![avg_spend_by_month](https://github.com/user-attachments/assets/6bbb174a-cfd3-49b9-87c7-8e636ac605fa)
![avg_spend_by_dayofweek](https://github.com/user-attachments/assets/0df86520-2f5b-49fd-8eb7-f3faf6ff0a4c)

- **Revenue with Moving Averages**
![total_spend_with_moving_avg](https://github.com/user-attachments/assets/70bee57f-dd1a-4f97-87f9-0bd741e68ce9)

- **Customer Spend over Time Density Heatmap**
![customer_spend_over_time_heatmap](https://github.com/user-attachments/assets/e1436c66-0e1d-4535-9ec4-39f315a03940)

- **Forecast for Next 90 Days**  
![90-Day Forecast](https://github.com/user-attachments/assets/05ddb976-5842-4175-b40d-47ca892346d6)

---

## Conclusion
This project demonstrates the power of predictive analytics in customer behavior analysis. By accurately forecasting CLV and spend probabilities, businesses can enhance retention strategies and revenue growth. The analyses reinforce the importance of leveraging data-driven insights for tailored customer engagement.
