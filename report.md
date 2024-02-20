# Loan Risk Analysis

## Overview of the Analysis

This project focuses on loan risk analysis using logistic regression models. The dataset contains information about loans classified as healthy (0) and high-risk (1). The dataset contains financial information related to loan applications. Here's a brief explanation of each column:

* loan_size: The size or amount of the loan requested by the borrower.
* interest_rate: The interest rate associated with the loan.
* borrower_income: The income of the borrower, providing insight into their financial capacity.
* debt_to_income: The ratio of the borrower's debt to their income, indicating their ability to manage debt payments.
* num_of_accounts: The number of accounts the borrower holds, reflecting their credit history and financial stability.
* derogatory_marks: The presence of derogatory marks on the borrower's credit report, which can impact creditworthiness.
* total_debt: The total debt amount owed by the borrower.

The goal is to predict the likelihood of a high-risk loan, where 1 represents a high-risk loan (2,500 instances), and 0 represents a healthy loan (75,036 instances). 

## Stages of the Machine Learning Process:

* 1. Data Exploration and Understanding: Analyzing the structure and characteristics of the dataset.
Understanding the distribution of the target variable.

* 2. Model Selection: Choosing a suitable machine learning algorithm for binary classification.

* 3. Model Training: Splitting the dataset into training and testing sets. Training the selected model on the training set. Resampling (in the second model): Addressing class imbalance by using RandomOverSampler on the training set.

* 4. Model Evaluation: Evaluating the model's performance on the testing set using relevant metrics.

Two different approaches were taken to evaluate the model's performance.

## Results

* Model 1: Original Dataset. In this approach, the original dataset with 75,036 instances of healthy loans and 2,500 instances of high-risk loans was used. The resulting model showed an impressive 99% accuracy. However, examining more detailed metrics reveals a discrepancy between precision and recall for the two labels:
  * Precision for healthy loans (0): 1.0
  * Precision for high-risk loans (1): 0.86
  * Recall for healthy loans (0): 1.0
  * Recall for high-risk loans (1): 0.91

* Precision indicates the proportion of correct predictions among those classified as positive, while recall represents the proportion of actual positives that were correctly classified. The discrepancy suggests a bias toward the majority class.

* Model 2: Balanced Dataset. To address the imbalance, RandomOverSampler was applied to the training set to equalize the number of instances for both classes. Although the resulting model still achieved 99% accuracy, detailed metrics revealed notable changes:
  * Precision for healthy loans (0): 1.0
  * Precision for high-risk loans (1): 0.85
  * Recall for healthy loans (0): 0.99
  * Recall for high-risk loans (1): 0.99

* While the recall for high-risk loans improved significantly, precision slightly decreased. This trade-off could be attributed to the generation of synthetic instances, which, although enhancing the model's ability to identify the minority class, also introduce some noise.

## Summary

Both models achieved remarkable accuracy, indicating their proficiency in classifying loan risk. However, the choice between them depends on the problem's specific requirements.

* If the emphasis is on accurately predicting high-risk loans (1), Model 2 is recommended due to its higher recall for the 1 class (0.99).
* If an overall balanced performance is desired, Model 1 is also a strong contender with high precision and recall for both classes.

In conclusion, the selection should align with the specific goals of the project, emphasizing whether precision, recall, or a balanced trade-off is more crucial for successful loan risk classification.
