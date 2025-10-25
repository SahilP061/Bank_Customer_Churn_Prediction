# Bank_Customer_Churn_Prediction
## Predicting Customer Churn in Retail Banking
## Overview
Customer churn occurs when a client stops doing business with a company and in this case, when a bank customer closes their account. Predicting churn allows the bank to identify at-risk customers early and take proactive steps to retain them.
The goal of this project is to build and evaluate machine-learning models that predict whether a customer is likely to leave the bank based on demographic and financial features such as credit score, balance, and product usage. The project also uses explainable AI to uncover which factors most strongly influence churn.

## Exploratory Data Analysis
The dataset included customer demographic, financial, and behavioural information.
Before modelling:
Missing values were checked and none were found.
Categorical features (e.g., Geography, Gender) were one-hot encoded.
Numerical features were standardised for consistent scaling.

To explore feature–target relationships, three violin plots were created, each with Exited (0 = No, 1 = Yes) on the x-axis and Estimated Salary, Balance, and Tenure on the y-axes.
These plots revealed subtle patterns for instance, customers with very high balances appeared more likely to exit, hinting at behavioural or satisfaction differences between retained and lost customers.

## Feature Engineering & Modelling
Five machine-learning models were initially trained:
* Logistic Regression
* Random Forest
* Gradient Boosting
* Support Vector Machine
* K-Nearest Neighbours

Model performance was compared using ROC-AUC curves across cross-validation folds. Gradient Boosting and Random Forest emerged as top performers.
To refine performance, Randomized Search was used for hyperparameter tuning of these two models, although if processing power allows a Grid Search is recommended. The optimised models were then retrained and evaluated on the test set using the following metrics: Accuracy, Precision, Recall, F1-score, and ROC-AUC.

Results were summarised in a comparison table for clarity.

## Model Evaluation
All evaluation metrics were visualised in a comparative bar chart. Both models performed strongly, though Gradient Boosting slightly outperformed Random Forest across most metrics.

Confusion matrices revealed that:
* The model correctly identified the majority of customers who stayed.
* It detected around 44 % of customers who exited.
* Only about 4 % of retained customers were incorrectly classified as churned.

This trade-off is often acceptable in business settings, where the cost of wrongly targeting a few loyal customers is lower than missing those about to leave.

## Model Interpretation (SHAP)

Since Gradient Boosting delivered the best results, SHAP (SHapley Additive exPlanations) was used to interpret its predictions.
The SHAP summary and beeswarm plots revealed that Number of Products and Age were the most influential factors driving churn predictions.
Customers with higher age or larger balances were more likely to churn.
The number of products had a non-linear effect, high product counts could indicate either high loyalty or high churn risk, depending on accompanying factors like balance.
Interactions showed that customers with high balances and multiple products were particularly likely to leave, suggesting disengagement among high-value clients.

## Conclusion & Business Implications

The Gradient Boosting model achieved strong predictive performance, accurately identifying at-risk customers. SHAP interpretation highlighted Age, Balance, and Product Engagement as key churn drivers.

Business insights:
* Monitor customers with multiple products and high balances, as they represent the most valuable yet vulnerable group.
* Launch targeted retention campaigns for these segments — e.g., personalised offers or relationship-management follow-ups.
* Enhance multi-product satisfaction, perhaps via integrated services or loyalty incentives.

Overall, this project demonstrates how predictive modelling and explainable AI can inform customer-retention strategies and reduce churn in the banking sector.
