# CDNow

### Dot-Com company that went bust in the early 2000s

## Business problems what we'll be solving

- 1. Which customers have the highest spend probility in next 90-days (clv - 90days)
- 2. Which customers have recently purchased but are unlikely to buy (survival analysis)
- 3. Which customers were predicted to purchase but didn't (missed opportunities)

## Dataset

### \* Transaction History

- 66k transactions
- 25k customers

### \* Launch of 19 New Products

### \* Covers New Customers that never made a purchase before

## Goals: Understand which customers to focus on

- Prediction Task
  - How much will they spend in the future
  - What probability is that they will make another purchase in the future

## Customer Lifetime Value (CLV)

Companies use this as a metirc to gauge profitability and to focus on which customers. CLV is the profit from estimated by the future relationship with a customer. There are many different approaches to model CLV but we are going to use ml approach

## Steps Involved

### 1.Subset a Cohort

We are looking for customers or group of customers that made their first purchase around the same period of time so that we can be sure that they were exposed to the same marketing or acquisition tactic

### 2.Temporal Splitting

We'll split the dataset by time 90days/rest

### 3.RFM Features

Feature engineer RMF features for training split 80% rest 20% will be used to come up with the target in our case the clv (90 days)

### 4.2 Predictive Models

- Predict how much a customer will spend in the next N-days (regression)
- What probability a customer will purchase in next N-days (classification)
