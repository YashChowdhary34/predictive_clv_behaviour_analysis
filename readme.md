# Predictive Customer - Lifetime Value, Spend Probability and Behaviour Analysis

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
#### Features
- Customer ID
- Purchase Date
- Purchase Quantity
- Order Value

## Table of Contents
- [Feature Engineering]
- [Models]
  - [CLV Model]
  - [Churn Probability Model]
- [Analysis]
  - [Dataset Analysis]
  - [Cohort Analysis]
  - [RFM Analysis]
  - [CLV Analysis]
  - [Churn Probability Analysis]
  - [Timeseries and Forecasting]
 
## Feature Engineering

## Objectives
- Create features that summarize customer interactions and purchasing behavior.
- Normalize and scale data for improved model performance.
- Perform time-based splits to simulate real-world forecasting scenarios.
  
### 1. Temporal Data Splitting
- **Rationale:** To mimic real-world use cases, where predictions are made based on past data for future periods.
- **Implementation:** Data is split into training and testing sets based on transaction dates. The training set contains earlier transactions, while the testing set includes later ones.

### 2. Derived Features
Recency, Frequency, and Monetary Value (RFM): Captures the core of customer behavior:

**Recency:** Days since the last transaction.
**Frequency:** Total number of transactions in a given period.
**Monetary:** Value: Total spend amount.
