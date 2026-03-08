# Power BI Fraud Dashboard

A **Power BI dashboard** to analyze financial fraud transactions using a synthetic dataset. The dashboard includes key metrics and visualizations to identify fraud patterns.

## Dataset

- **Source:** [Synthetic Financial Fraud Dataset on Kaggle](https://www.kaggle.com/datasets/umitka/synthetic-financial-fraud-dataset)  
- **Description:** The dataset contains synthetic transaction data, including user IDs, transaction amounts, and a fraud indicator (`is_fraud`).

## Data Preparation

A new column `Fraud_Label` was added to categorize transactions:

``DAX
Fraud_Label = IF('synthetic_fraud_dataset'[is_fraud] = 1, "Fraud", "Legit")

## Measures
1- Fraud Rate = DIVIDE(SUM('synthetic_fraud_dataset'[is_fraud]), COUNTROWS('synthetic_fraud_dataset')).

2- Total Fraud = SUM('synthetic_fraud_dataset'[is_fraud]).

3- Avg Fraud Amount = CALCULATE(
    AVERAGE('synthetic_fraud_dataset'[amount]), 
    'synthetic_fraud_dataset'[is_fraud] = 1
).

4- Fraud Count per User = CALCULATE(
    COUNTROWS('synthetic_fraud_dataset'),
    'synthetic_fraud_dataset'[is_fraud] = 1
). 

## Dashboard Features

Interactive visuals for fraud analysis

Metrics: Fraud Rate, Total Fraud Transactions, Average Fraud Amount

User-level fraud tracking
