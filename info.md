# CDNow

### Dot-Com Company That Went Bust in the Early 2000s

## Business Problems We Will Be Solving

1. **Which customers have the highest spend probability in the next 90 days?** (CLV - 90 days)
2. **Which customers have recently purchased but are unlikely to buy again?** (Survival analysis)
3. **Which customers were predicted to purchase but didn’t?** (Missed opportunities)

## Dataset

### Transaction History
- 66k transactions
- 25k customers

### Product Launch Data
- Includes the launch of 19 new products
- Covers new customers who have never made a purchase before

## Goals: Understand Which Customers to Focus On

### Prediction Tasks
1. **How much will customers spend in the future?**
2. **What is the probability that they will make another purchase in the future?**

## Customer Lifetime Value (CLV)

Customer Lifetime Value (CLV) is a metric used to gauge profitability by estimating the future relationship with a customer. Companies use this metric to identify which customers to focus on for retention and marketing efforts.

### Why CLV Matters
- Helps prioritize high-value customers.
- Informs tailored marketing strategies.
- Supports long-term profitability and planning.

### Our Approach
We will use a machine learning (ML) approach to model CLV.

---

## Steps Involved

### 1. Subset a Cohort
- Identify customers or groups of customers who made their first purchase around the same period.
- This ensures exposure to similar marketing or acquisition tactics, making comparisons fair.

### 2. Temporal Splitting
- Split the dataset into two segments:
  - **90 days**: Used for short-term CLV predictions.
  - **Remaining period**: Used for training and evaluation.

### 3. RFM Features
- Feature engineer **Recency**, **Frequency**, and **Monetary (RFM)** metrics from the data.
- Use 80% of the dataset for training and 20% for testing.
- Target variable: Predicted CLV over 90 days.

### 4. Predictive Models

#### a) Regression
- Predict how much a customer will spend in the next N days.

#### b) Classification
- Predict the probability that a customer will make a purchase in the next N days.

---

This structured approach ensures data-driven insights for effective customer prioritization and strategic decision-making.

