# Employee Churn Prediction (Google Advanced Data Analytics Capstone)

## Project Overview

Employee attrition is a major business challenge that impacts productivity, increases hiring costs, and affects organizational stability.

The objective of this project is to identify the key factors that lead employees to leave the organization and build a machine learning model that can predict employee attrition.

This project follows the **Google PACE framework (Plan, Analyze, Construct, Execute)** to ensure a structured and business-oriented analytical workflow.

The final model helps HR teams take proactive actions to improve employee satisfaction, optimize workload distribution, and reduce attrition risk.

---

## Business Problem

Organizations need to understand why employees leave and which employees are at risk of attrition.

High attrition leads to:

* increased hiring and training costs
* loss of domain expertise
* reduced team productivity
* lower employee morale

The goal of this project is to:

predict whether an employee will leave the company

and identify the most important factors influencing attrition.

---

## Dataset Information

Total records: 15,000 employees

Target variable:
left → whether the employee left the company (1) or stayed (0)

Features used:

| Variable              | Description                                |
| --------------------- | ------------------------------------------ |
| satisfaction_level    | employee reported satisfaction score (0–1) |
| last_evaluation       | last performance review score (0–1)        |
| number_project        | number of projects handled                 |
| average_monthly_hours | average monthly working hours              |
| time_spend_company    | tenure in company (years)                  |
| Work_accident         | whether employee had workplace accident    |
| promotion_last_5years | promotion status                           |
| Department            | department name                            |
| salary                | salary category                            |

Class distribution:

* Stayed: 83.4%
* Left: 17%

The dataset is slightly imbalanced but still suitable for predictive modeling using F1-score and AUC as evaluation metrics.

---

## Project Methodology (PACE Framework)

### PLAN

Defined the business problem and identified stakeholders.

Stakeholders:

* HR team
* senior management
* workforce planning team

Key objective:
identify drivers of attrition and predict employee churn risk.

Data quality checks:

* missing values check
* duplicate records check
* feature relevance review

---

### ANALYZE (Exploratory Data Analysis)

Key insights from EDA:

* employees working excessive hours are more likely to leave
* employees handling only 2 projects show higher attrition rates
* employees with low salary category show higher attrition
* accounting department shows lowest satisfaction levels
* HR department shows highest attrition rate
* promotions are rare, suggesting possible career stagnation
* management department has highest average tenure
* strong correlation observed between:

  * last_evaluation
  * number_project
  * average_monthly_hours
* satisfaction_level shows strong negative correlation with attrition

There is no strong linear relationship between features and target variable, making tree-based models suitable.

---

### CONSTRUCT (Feature Engineering and Modeling)

Potential data leakage identified:

satisfaction_level may capture post-decision employee sentiment (employees already planning to leave may report lower satisfaction)

To address this issue:

satisfaction_level column was removed.

New feature engineered:

overworked =
1 if employee works more than threshold monthly hours
0 otherwise

Models tested:

* Logistic Regression
* Decision Tree
* Random Forest

Hyperparameter tuning performed using GridSearchCV.

---

### EXECUTE (Results and Business Interpretation)

Final model selected:
Random Forest (after removing leakage)

Performance metrics:

| Model                 | Precision | Recall | F1 Score | Accuracy | AUC    |
| --------------------- | --------- | ------ | -------- | -------- | ------ |
| Decision Tree (final) | 0.8506    | 0.9050 | 0.8768   | 0.9571   | 0.9619 |
| Random Forest (final) | 0.8574    | 0.9015 | 0.8787   | 0.9580   | 0.9673 |

Model performance is strong while maintaining generalization ability.

---

## Key Predictive Features

Top features influencing attrition:

* number_project
* last_evaluation
* tenure
* overworked

Employees working excessive hours show higher likelihood of leaving.

---

## Business Recommendations

Based on model insights:

1. reduce excessive workload for employees handling many projects
2. improve promotion frequency to avoid career stagnation
3. ensure fair distribution of work across departments
4. review HR department attrition drivers
5. improve satisfaction levels through work-life balance initiatives
6. monitor employees with very low or very high project counts
7. implement employee engagement surveys proactively

---

## Tech Stack

Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
Jupyter Notebook

---

## Repository Structure

data → dataset used for analysis
notebooks → Jupyter notebook containing full workflow
models → trained machine learning models
reports → executive summary presentation

---

## How to Run the Project

install dependencies:

pip install -r requirements.txt

open notebook:

jupyter notebook notebooks/employee_churn_analysis.ipynb

---

## Project Highlights

* applied structured ML workflow using PACE framework
* identified and addressed data leakage
* performed feature engineering
* optimized models using GridSearchCV
* translated model insights into business recommendations

---

## Author

Navyadeep Singh Boparai

Data Analyst | Machine Learning | Business Intelligence
