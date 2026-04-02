# Credit Card Default Prediction (NUS Capstone Project)

## Project Overview

Financial institutions must evaluate the risk of customers defaulting on credit card payments in order to minimize financial losses and make informed lending decisions.

The objective of this project is to develop machine learning models that predict whether a credit card customer will default on their next payment.

The dataset contains 30,000 customer records with demographic, financial, and repayment behaviour features.

The project emphasizes:

feature selection using statistical techniques
handling multicollinearity
model comparison for imbalanced classification
business interpretation of model results

---

## Business Problem

Credit card default prediction is a critical risk management problem.

Incorrect predictions have business consequences:

False Positive (FP):
predicting a customer will default when they actually will not
→ leads to rejecting good customers and losing business

False Negative (FN):
predicting a customer will not default when they actually will
→ leads to financial losses due to unpaid credit

Therefore, model evaluation focuses on:

precision
recall
F1 score

instead of accuracy alone.

---

## Dataset Information

Dataset size:
30,000 rows × 25 columns

Target variable:
default.payment.next.month

1 = default
0 = non-default

Key feature groups:

### Demographic features

SEX
EDUCATION
MARRIAGE
AGE

### Credit information

LIMIT_BAL (remaining credit balance)

### Repayment behaviour

PAY_0 to PAY_6
repayment delay status for past 6 months

### Bill amounts

BILL_AMT1 to BILL_AMT6
monthly bill amounts

### Payment amounts

PAY_AMT1 to PAY_AMT6
payments made in previous months

Train dataset used for model fitting
Test dataset used for evaluation.

---

## Exploratory Data Analysis (EDA)

Key observations:

LIMIT_BAL and AGE show right-skewed distributions

majority customers are university educated

majority customers are single

repayment status variables PAY_0 to PAY_6 are concentrated around 0 (paid duly)

bill amounts and payment amounts are right skewed

payment amounts generally lower than bill amounts indicating partial payments

class imbalance present:

77.9% non-defaulters
22.1% defaulters

---

## Multicollinearity Analysis

Variance Inflation Factor (VIF) and correlation heatmaps were used to evaluate relationships between variables.

Observations:

BILL_AMT1 to BILL_AMT6 show high multicollinearity (VIF > 10)

PAY_AMT1 to PAY_AMT6 also correlated with each other

LIMIT_BAL highly correlated with several variables

BILL_AMT1 to BILL_AMT6 show high correlation among themselves

PAY_AMT1 to PAY_AMT6 show correlation among themselves

multicollinearity can lead to unstable coefficient estimates and reduced model interpretability

---

## Feature Selection Strategy

Features excluded from model building:

LIMIT_BAL

BILL_AMT1 to BILL_AMT6

PAY_AMT1 to PAY_AMT6

Reason:

high multicollinearity

weak influence on target variable

risk of unstable model coefficients

features retained include demographic variables and repayment status variables.

Feature selection decisions were supported using:

correlation heatmap

Variance Inflation Factor (VIF)

---

## Models Implemented

The following models were evaluated:

Logistic Regression
Random Forest
Support Vector Machine (SVM)
Artificial Neural Network (ANN)

---

## Model Performance Comparison

| Model               | Accuracy | Precision | Recall | F1 Score |
| ------------------- | -------- | --------- | ------ | -------- |
| Logistic Regression | 0.7795   | 0.50      | 0.556  | 0.526    |
| Random Forest       | 0.8072   | 0.649     | 0.273  | 0.384    |
| SVM                 | 0.7767   | 0.440     | 0.046  | 0.084    |
| ANN                 | 0.7775   | 0.25      | 0.004  | 0.008    |

---

## Key Insights

bill amount variables show strong correlation with each other indicating redundancy

payment amount variables also show correlation among themselves

accuracy alone is not sufficient for evaluating imbalanced classification problems

F1-score provides better balance between precision and recall

Logistic Regression provides a better balance between precision and recall compared to other models evaluated

---

## Final Model Selection

Champion model: Logistic Regression

Performance:

Accuracy: 77.9%
Precision: 50%
Recall: 55.6%
F1 Score: 52.6%

Although Random Forest achieved slightly higher accuracy, Logistic Regression provided better balance between precision and recall for identifying defaulters.

---

## Business Impact

model can help financial institutions:

identify customers with higher likelihood of default

support data-driven credit approval decisions

reduce financial risk exposure

improve risk management strategy

balancing false positives and false negatives is important to avoid rejecting good customers while also minimizing credit losses.

---

## Project Structure

data/
Train.csv
Test.csv
CC_Default.csv

notebooks/
credit_default_analysis.ipynb

---

## Tech Stack

Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn

---

## Future Improvements

handle class imbalance using resampling techniques

experiment with additional feature engineering

hyperparameter tuning

test ensemble methods

improve recall without significantly reducing precision

---

## Author

Navyadeep Singh Boparai

Machine Learning | Data Analytics | Predictive Modeling
