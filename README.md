# credit-risk-classification
### Challenge 20 of UoB Data Analytics bootcamp - Supervised Learning

## Overview of the Analysis
The main purpose of this analysis was to identify the creditworthiness of borrowers. Using a dataset of historical lending activtiy from a peer-to-peer lending service company, I used logistic regression to train and evaluate a model on loan risk. 

The data included information on:
- loan size
- interest rate
- borrower's income
- debt to income
- number of accounts
- derogatory marks 
- total debt 
- loan status (healthy or high-risk)

The model was built to predict loan status. Note that the sample provided was not balanced, containing significantly more instances of healthy loans (75036) than high-risk ones (2500).

In order to predict loan status, data was splitted into training and testing sets. A logistic regression model - which allows us to predict binary outcomes - was fitted to the training sets and used to predict loan status for the test set of data. 

As the sample was unbalanced, a resampling method (with replacement) was used. "Random over-sampling can be used to repeat some samples and balance the number of samples between the dataset" (see more [here](https://imbalanced-learn.org/stable/auto_examples/over-sampling/plot_comparison_over_sampling.html#sphx-glr-auto-examples-over-sampling-plot-comparison-over-sampling-py). Over-sampling resulted in 56277 healthy and 56277 risky data points. A logistic regression model was then fitted to the resampled data and used to predict loan status. 

Both models were evaluated by calculated a balanced accuracy score, as well as by producing a confusion matrix and classification reports, which allow drawing conclusions not only about the model's overall accuracy, but about its precision and recall as well. The resuls of this evaluation are discussed in the section below. 

## Results
- Logistic regression - original data:
  - Computing the logistic regression model on the original data results in high accuracy, with a balanced accuracy score of .94. Note that the balanced accuracy is the average of recall obtained on each class, and has a maximum value of 1.
  - Precision: the model's precision is slightly higher for healthy loans (1) than high-risk loans. Whilst the model's predictions are correct 100% of the times when predicting a healthy-loan, the model correctly predicts high-risk loans 87% of times.
  - Recall: the model correctly identifies 100% of all healthy loans, compared to 89% of high-risk loans.
  
- Logistic regression - resampled data:
  - Resampling the data increased the model's balanced accuracy score to 1, its maximum possible value. 
  - Precision: the model's precision was unaltered when using resampled data: its ability to correctly predict healthy loans remained at 100%, and it still correctly predicted high-risk loans 87% of times.
  - Recall: the model's recall remained at 100% for healthy loans, but increased from 89% to 100% for high-risk loans, meaning that - using the resampled data - the model could now identify 100% of all high-risk loans. 

## Summary
Both logistic regression models perform remarkably well. The model using the over-sampled data is slightly more accurate (1) than the one using the original data (.94), and has a higher recall for high-risk loans (1) compared to the model that uses original data (.87). 

Given that the most important prediction in this case is to accurately identify high-risk loans (we want to avoid false negatives - that is, identifying a high-risk loan as healthy), recall is more important than precision*, and given that the model using over-sampled data leads to both higher accuracy and better recall values, I would recommend the use of that model. 