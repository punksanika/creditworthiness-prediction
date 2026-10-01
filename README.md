# Creditworthiness Prediction Using Machine Learning

## Overview

This project develops a machine learning-based classification system to predict whether an individual is likely to default based on historical financial information.

The project focuses on building an end-to-end machine learning workflow, including exploratory data analysis, feature engineering, classification, class-imbalance handling, cross-validation, hyperparameter tuning, and model evaluation.

## Objective

The objective is to predict an individual's credit default status using financial and demographic information.

The target variable is:

- `Default = 0` → Non-Default
- `Default = 1` → Default

## Dataset

The dataset contains 100 observations and the following variables:

| Feature | Description |
|---|---|
| Age | Age of the individual |
| Income | Income of the individual |
| LoanAmount | Loan amount |
| CreditScore | Credit score |
| EmploymentYears | Number of years employed |
| Default | Target variable indicating default status |

The target distribution contains:

- 77 non-default cases
- 23 default cases

Because the target classes are not equally distributed, class imbalance was considered during model development.

## Machine Learning Workflow

The project follows these steps:

1. Dataset loading
2. Data inspection
3. Exploratory data analysis
4. Class distribution analysis
5. Correlation analysis
6. Feature engineering
7. Feature scaling
8. Baseline Logistic Regression
9. Decision Tree classification
10. Random Forest classification
11. Class imbalance handling
12. Stratified 5-fold cross-validation
13. ROC curve analysis
14. Feature importance analysis
15. Random Forest hyperparameter tuning
16. Classification threshold analysis
17. Final model comparison

## Feature Engineering

Feature engineering was applied to derive additional information from the available financial variables.

The engineered features were incorporated into the model development process and compared with the original feature set.

## Models Used

### Logistic Regression

Used as a baseline classification model and provides a linear approach to predicting default probability.

### Decision Tree

Used to capture non-linear relationships between the financial variables and the target.

### Random Forest

An ensemble of decision trees used to model non-linear relationships while reducing dependence on an individual decision tree.

### Tuned Random Forest

Grid Search with stratified cross-validation was used to explore different Random Forest hyperparameter combinations.

The tuning process optimized F1-score because the dataset contains fewer default cases than non-default cases.

## Evaluation Metrics

The models were evaluated using:

### Accuracy

Measures the overall proportion of correctly classified observations.

### Precision

Measures how many observations predicted as default were actually default cases.

### Recall

Measures how many actual default cases were correctly identified.

### F1-Score

Provides a balance between Precision and Recall.

### ROC-AUC

Measures the model's ability to distinguish between the two classes across classification thresholds.

## Model Results

The final cross-validated comparison produced the following results:

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Balanced Logistic Regression | 0.530 | 0.206 | 0.340 | 0.255 | 0.508 |
| Balanced Random Forest | 0.730 | 0.250 | 0.130 | 0.168 | 0.494 |
| Tuned Random Forest | 0.750 | 0.400 | 0.174 | 0.242 | 0.521 |

The results show that model performance varies considerably depending on the evaluation metric. In particular, identifying default cases remains challenging, as reflected by the relatively low recall values.

## ROC Analysis

ROC curves were generated to examine the ability of the classification models to distinguish between default and non-default cases across different probability thresholds.

## Feature Importance

Random Forest feature importance was calculated to examine the relative contribution of the available features to the model's predictions.

The resulting feature importance values are available in:

`results/credit_feature_importance.csv`

## Threshold Analysis

The classification threshold was varied to examine its effect on:

- Precision
- Recall
- F1-Score

The results are available in:

`results/credit_threshold_analysis.csv`

## Project Structure

```text
creditworthiness-prediction/
│
├── data/
│   └── credit_data.csv
│
├── results/
│   ├── credit_model_results.csv
│   ├── credit_feature_importance.csv
│   └── credit_threshold_analysis.csv
│
├── creditworthiness_prediction.ipynb
│
└── README.md
