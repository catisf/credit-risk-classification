# credit-risk-classification
### Challenge 20 of UoB Data Analytics bootcamp - Supervised Learning

## Overview of the Analysis
The main purpose of this analysis was to identify the loan risk. Using a dataset of historical lending activtiy, logistic regression was used to train and evaluate a model on loan risk. 

The data included information on:
- loan size
- interest rate
- borrower's income
- debt to income
- number of accounts
- derogatory marks 
- total debt 
- loan status (healthy or high-risk)

The model was built to predict loan status, with 0 = healthy loan and 1 = high-risk loan. Note that the sample provided was unbalanced, containing significantly more instances of healthy loans (75036) than high-risk ones (2500).

In order to predict loan status, data was splitted into training and testing sets. A logistic regression model - which predicts binary outcomes - was fitted to the training sets and used to predict loan status for the test set. 

As the sample was unbalanced, a resampling method ([random over-sampling](https://imbalanced-learn.org/stable/auto_examples/over-sampling/plot_comparison_over_sampling.html#sphx-glr-auto-examples-over-sampling-plot-comparison-over-sampling-py)) was used. Over-sampling resulted in 56277 healthy and 56277 risky data points. A logistic regression model was then fitted to the resampled data and used to predict loan status. 

Both models were evaluated by calculating their balanced accuracy score, as well as by producing a confusion matrix and classification reports. The resuls of this evaluation are discussed in the section below. 

## Results
- Logistic regression - original data:
  - Balanced accuracy score: computing the logistic regression model on the original data results in high accuracy, with a balanced accuracy score of 94%. Note that the balanced accuracy is the average of recall obtained on each class, and has a maximum value of 1.
  - Precision: the model's precision is slightly higher for healthy loans than high-risk loans. Whilst the model's predictions are correct 100% of the times when predicting a healthy-loan, the model correctly predicts high-risk loans 87% of times.
  - Recall: the model correctly identifies 100% of all healthy loans, compared to 89% of high-risk loans.
  
- Logistic regression - resampled data:
  - Balanced accuracy score: resampling the data increased the model's balanced accuracy score to 1, its maximum possible value. 
  - Precision: the model's precision was unaltered when using resampled data: its ability to correctly predict healthy loans remained at 100%, and it still correctly predicted high-risk loans 87% of times.
  - Recall: the model's recall remained at 100% for healthy loans, but increased from 89% to 100% for high-risk loans, meaning that - using the resampled data - the model could now identify 100% of all high-risk loans. 

## Summary
Both logistic regression models perform remarkably well. I would, however recommend the use of the second model (over-sampling model). The reasoning for it being:
- the second model outperforms the first in terms of overall (balanced) accuracy, with a performance of 100% vs 94%
- the model using over-sampling data has a higher recall for high-risk loans (100%) compared to the model using original data (87%). This is particularly important, as the most important prediction this model should make is to accurately identify high-risk loans. That is, we want to avoid false negatives (identifying a high-risk loan as healthy) and the second model does so more accurately. 
