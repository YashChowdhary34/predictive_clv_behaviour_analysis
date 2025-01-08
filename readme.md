# **Predictive - Customer Lifetime Value, Spend Probability, and Behaviour Analysis**

## Introduction

Customer behavior analysis is a vital process providing businesses with valuable insights into their customers' behaviors and preferences. In this project, I analyzed the CDNOW dataset to determine customer buying patterns based on Recency, Frequency, and Monetary Value (RFM).

- Using Python, I performed RFM analysis to determine each customer's Recency, Frequency, and Monetary Value based on their transaction history. This analysis will help us understand how recently and how often customers make purchases and the average amount they spend.

- Next, I used the K-Means algorithm to segment customers into groups based on their RFM scores. This segmentation will help identify distinct customer groups and tailor marketing strategies and promotions to each group's specific needs and preferences.

- I also developed a machine learning model using XGBRegressor and XGBClassifier to predict the probability of customer purchase and the likely purchase amount. By predicting customer behavior, businesses can better understand their customers' needs and preferences and adjust their marketing strategies accordingly.

- Finally, I conducted cohort analysis to determine customer lifetime value (CLV) and measure the effectiveness of our marketing strategies. By analyzing customer behavior over time, we can gain insights into how our customer base changes and adapt our strategies to meet their evolving needs.

Overall, this project provides valuable insights into customer behavior, allowing businesses to improve customer engagement, retention, and revenue.

---

## Business Problems That We'll Be Answering

- **Which customers have the highest spending probability in the next 90 days?**
- **Which customers have recently purchased but are unlikely to buy again?** (Survival Analysis)
- **Which customers were predicted to purchase but didn't?** (Missed Opportunities)

---

## Table of Contents

- [Feature Engineering](#feature-engineering)
- [Customer Segmentation](#customer-segmentation)
- **Models**
  - [Spend Amount Prediction Model](#spend-amount-prediction-model)
  - [Spend Probability Prediction Model](#spend-probability-prediction-model)
- **Analysis**
  - [Dataset Analysis](#dataset-analysis)
  - [RFM Analysis](#rfm-analysis)
  - [CLV Analysis](#clv-analysis)
  - [Churn Probability Analysis](#churn-probability-analysis)
  - [Timeseries and Forecasting](#timeseries-and-forecasting)
- [Answers to Business Problems](#Answering-Business-Questions)
- [Tech Stack](#tech-stack)

- [Conclusion](#conclusion)

---

## Feature Engineering

### Objectives

- Create features encapsulating customer behavior, such as recency, frequency, and monetary value (RFM).
- Generate advanced predictors like average spending, purchase trends, and segmentation metrics.
- Create datetime features for timeseries analysis.

### Key Features Created

- **Recency**: Days since the last purchase.
- **Frequency**: Total number of purchases.
- **Monetary Metrics**:
  - `price_sum`: Total spend across all transactions.
  - `price_mean`: Average spend per transaction.
- **spend_90_total**: Predicted customer lifetime value (CLV) for the next 90 days.
- **spend_90_flag**: Predicted customer spend probability over the next 90 days.
- **dayofweek**: Purchase by day of week to identify weekly purchasing patterns.

---

## Customer Segmentation

Customer segmentation helps in grouping customers based on similarities, allowing businesses to gain a broad view of their customer base and answer critical business questions effectively. Here, we employ RFM (Recency, Frequency, Monetary) analysis and K-Means clustering for segmentation.

Using Principal Component Analysis (PCA), we reduced the dimensions of the dataset for visualization. The clusters were plotted to reveal the distinct groupings. Now we have identified different groups to which each customer belongs and can therefore develop specific marketing strategies suitable for each group.

### K-Means Clustering

We use the K-Means clustering algorithm to identify distinct customer groups. The optimal number of clusters is determined using the Elbow Method, which plots inertia values against different K-values. For this analysis, we chose **K=4**.

### Cluster Insights

Each cluster was analyzed based on the average RFM metrics:

- **Cluster 0**: Average Customers
- **Cluster 1**: Losing Customers
- **Cluster 2**: Loyal Customers
- **Cluster 3**: VIP Customers

These labels were assigned based on the clustering results, enabling targeted strategies for each group. The segmentation allows businesses to focus on retaining valuable customers, improving loyalty, and reducing churn.

This segmentation framework provides actionable insights to tailor marketing efforts and improve customer relationship management.

---

## Models

### Spend Amount Prediction Model

#### What do customers spend in the next 90 days? (Regression)

- Train a model to predict `spend_90_total` using features derived from the Feature Engineering phase.
- Evaluate and optimize model performance.

#### Methodology

- **Model Used**: Gradient Boosting Regressor (XGBRegressor)
- **Feature Selection**:
  - Recency, frequency, monetary metrics.
- **Evaluation Metrics**:
  - Mean Absolute Error (MAE)
  - Root Mean Square Error (RMSE)

#### Workflow

1. **Data Splitting**: Stratified train-test split.
2. **Hyperparameter Tuning**: Using grid search and cross-validation.
3. **Performance Analysis**: Visualizing predictions versus actual spend values.

#### Outcomes

- The model achieves robust prediction accuracy with MAE and RMSE within acceptable thresholds.
- Feature importance analysis highlights the key drivers of customer spending behavior.

#### Model Performance

- **Mean Absolute Error (MAE)**: Predictions are off by about 9.65 units, equivalent to 9-10 dollars.

#### Feature Importance

<p align="center">
  <img src="https://github.com/user-attachments/assets/d676e09f-63f2-48fa-aaed-9935c30b58cf" alt="CLV Feature Importance" width="70%">
</p>

### Spend Probability Prediction Model

#### What is the probability of a customer to purchase in the next 90 days? (Classification)

- Build a classification model to predict `spend_90_flag` (a binary indicator of future purchases).
- Combine predictions with spending amounts to prioritize high-value customers.

#### Methodology

- **Model Used**: Gradient Boosting Classifier (XGBClassifier)
- **Features**: Same as the Spend Amount Prediction Model.
- **Evaluation Metrics**:
  - Precision, Recall, and F1-Score
  - Area Under the Receiver Operating Characteristic (ROC-AUC) Curve

#### Workflow

1. **Data Splitting**: Stratified train-test split.
2. **Hyperparameter Tuning**: Using grid search and cross-validation.
3. **Performance Analysis**: Visualizing predictions versus actual spend values.

#### Outcomes

- High accuracy and ROC-AUC scores ensure reliable probability predictions.
- Predictions integrated with spend amount estimates enable targeted marketing and retention strategies.

#### Model Performance

- **ROC-AUC**: 0.84

#### Feature Importance

<p align="center">
  <img src="https://github.com/user-attachments/assets/515473e8-bc91-4b20-9593-8f94c36b5c90" alt="Churn Feature Importance" width="70%">
</p>

---

## Analysis

### Customer Activity

Trendline shows that we have growth both in the number of orders and the order amount.
![customer_activity_trendline](https://github.com/user-attachments/assets/04a0d6ba-65e0-4c73-9514-e9ad955d5595)

### Parallel Coordinates for All Customer Metrics

This plot shows the correlation between all the customer metrics.
![customer_metrics_predicted_clv_parallelcoords](https://github.com/user-attachments/assets/0ca7fd93-f1a8-4912-ba08-7d38d499d010)

### Dataset Analysis

- **Revenue Contribution by Top Customers**
  We can see the revenue contribution of top 10 customers, these are our VIP customers and can develop strategies to oversell them.
  ![Revenue Contribution](https://github.com/user-attachments/assets/38620e82-8745-4cf4-be90-921e4e421316)

- **Monthly Revenue Trends**
  Monthly revenue trends show a decline which makes sense for the dataset that we are working with.
  ![Monthly Revenue Trends](https://github.com/user-attachments/assets/ff44be4a-7c0a-4c42-a54c-da5724a8e210)

- **Order Frequency Analysis**  
  Most customers aren't repeat buyers; we need to develop specific marketing strategies to make customers repurchase.
  ![Order Frequency Analysis](https://github.com/user-attachments/assets/056fb078-561a-467e-bc09-0e65a7fe951f)

- **Revenue by Product Price**
  We can take a look at revenue per product price which could be useful in developing pricing strategies to increase revenue during a specific time period by upselling or rolling out price drops.  
   ![Revenue by Product Price](https://github.com/user-attachments/assets/47b6f5d2-6f4f-433a-8620-b46e1c9ca3b4)

---

### RFM Analysis

- **Distribution of RFM Metrics**  
  ![RFM Metrics Distribution](https://github.com/user-attachments/assets/a22a8345-1b78-45c4-bec2-0901e900eed6)

- **Relationship Between RFM Metrics**  
  As we expect frequency and price_sum are positively correlated.
  ![RFM Heatmap](https://github.com/user-attachments/assets/7a4aee8d-a5a5-4de1-b536-4d331e8189f6)

- **Customer Spread by Recency and Frequency**  
  This shows increase in purchasing.
  ![Recency vs Frequency](https://github.com/user-attachments/assets/55826e12-f4d9-4ea2-aea7-d0c66ea64780)

- **Customer Spread by Monetary Value and Frequency**  
  As we saw previously the positive correlation between frequency and price_sum this resonates with that, plus we can see the customer spread along these features.
  ![Frequency vs Monetary](https://github.com/user-attachments/assets/feb2954b-ce1c-48c9-b2f4-dcee22f5c983)

---

### CLV Analysis

- **Predicted Spend vs Features**

  - The spend prediction is higher for more recent customers.
  - More customers belong in the low frequency and low spend segments.
  - Budget buyers are predicted to spend more.

  ![Predicted Spend](https://github.com/user-attachments/assets/85a53bb8-954e-4100-a72b-95d6ee628719)

- **Customer Spending Distribution**

  - We have more customers in the low purchase value segment.

  ![Spending Distribution](https://github.com/user-attachments/assets/b271b7dd-0ad3-4ed5-8e1d-887cd2323cf5)

- **Relationship Between Frequency and Predicted Spend**

  ![Relationship Between Frequency and Predicted Spend](https://github.com/user-attachments/assets/68708b66-dcc0-4294-86db-5f593811c14a)

- **Customer Segmentation by Value and Frequency**

  - Budget buyers are predicted to spend more comparatively.

  ![Segmentation by Value and Frequency](https://github.com/user-attachments/assets/e6eb459d-7a8c-4629-968b-ba5b70842164)

---

### Churn Probability Analysis

- **Purchase Probability Distribution**

  - The purchase probability distribution aligns with the dataset characteristics.

  ![Purchase Probability](https://github.com/user-attachments/assets/42e4847b-0c39-445a-a681-aedae2032b94)

- **Purchase Probability over RFM**

  ![Purchase Probability over RFM](https://github.com/user-attachments/assets/1c1f2fe1-05b9-40d7-a5fe-dac94e3b5c4b)

- **Predicted Churn Probability Correlation Heatmap**

  ![Churn Correlation Heatmap](https://github.com/user-attachments/assets/fa7418cc-fdee-46f6-bafe-c3a106c765d4)

---

### Timeseries and Forecasting

- **Spend Trends Over Time**

  - Revenue peaked between January and April 1997.

  ![Spend Over Time](https://github.com/user-attachments/assets/75ab2bb3-f60a-4446-b06f-a0996feba4b2)

- **Average Spend over Month and Day of Week**

  ![Average Spend by Month](https://github.com/user-attachments/assets/6bbb174a-cfd3-49b9-87c7-8e636ac605fa)

  ![Average Spend by Day of Week](https://github.com/user-attachments/assets/0df86520-2f5b-49fd-8eb7-f3faf6ff0a4c)

- **Revenue with Moving Averages**

  ![Total Spend with Moving Average](https://github.com/user-attachments/assets/70bee57f-dd1a-4f97-87f9-0bd741e68ce9)

- **Customer Spend over Time Density Heatmap**

  ![Customer Spend Over Time Heatmap](https://github.com/user-attachments/assets/e1436c66-0e1d-4535-9ec4-39f315a03940)

- **Forecast for Next 90 Days**

  ![90-Day Forecast](https://github.com/user-attachments/assets/05ddb976-5842-4175-b40d-47ca892346d6)

---

### Answering Business Questions

#### **1. Which customers have the highest spending probability in the next 90 days?**

Customers with a high `spend_90_flag` value, predicted by the classification model, and a high `spend_90_total` (predicted spend) are identified as having the highest spending probability. These customers are prioritized for retention and upselling strategies.

#### **2. Which customers have recently purchased but are unlikely to buy again?**

Customers with low `spend_90_flag` and high recency values are identified as at risk of churn. Retention efforts like personalized offers or loyalty rewards can be targeted at this group.

#### **3. Which customers were predicted to purchase but didn’t?**

By comparing actual purchases with predictions, customers with high `spend_90_flag` but no transactions during the period are flagged as missed opportunities. Re-engagement campaigns or follow-up strategies can focus on these customers.

---

### Tech Stack

- **Programming Language**: Python
- **Data Visualization**: Matplotlib, Seaborn, Plotly
- **Machine Learning**: Scikit-learn, XGBoost
- **Database**: MySQL
- **Data Manipulation**: Pandas, NumPy
- **Model Evaluation**: Precision, Recall, F1-Score, RMSE, MAE
- **Timeseries Analysis**: Statsmodels, Prophet
- **Clustering and Segmentation**: K-Means, PCA
- **Forecasting and Predictions**: Gradient Boosting (XGBRegressor, XGBClassifier)
- **IDE/Environment**: Jupyter Notebook, VSCode

---

## Conclusion

This project demonstrates the power of predictive analytics in customer behavior analysis. By accurately forecasting CLV and spend probabilities, businesses can enhance retention strategies and revenue growth. The analyses reinforce the importance of leveraging data-driven insights for tailored customer engagement.
