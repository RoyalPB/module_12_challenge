# module_12_challenge## Overview of the Analysis

This analysis explores the best means of investigating an imbalanced dataset of loans, healthy vs. high-risk. The vast majority of loans are healthy, and therefor it is easy to create a model with a high level of accuracy to predict healthy loans. However, the prediction accuracy for high-risk loans, being much smaller in number, is much lower. The goal is to find a model that is able to predict both healthy and high-risk loans with a high level of accuracy.

![Separating features from targets](/Images/1.PNG)

![Target value counts](/Images/2.PNG)

As shown in the above sections of code, the features and targets were separated and target values counted to provide insight on the overall makeup of the data set:

Healthy loans:   96.78%
High-risk loans:  3.22%

You can see that these metrics make it very easy to guess that a loan will be healthy, but far less likely to identify high-risk loans. To begin the analysis, the data was split into training and testing components, and a logistic regression model was fit to the raw training data. Then the model was used to predict the `y` outcomes and compared against the `y` test data.

![Train test split](/Images/3.PNG)

![Raw data model](/Images/4.PNG)

![Raw data prediction](/Images/5.PNG)

Because the value counts between the healthy and high-risk loans are so imbalanced, the data was resampled using a RandomOverSampler instance and the training data was fit to this model to create resampled training components, producing equal value counts.

![Resampled value counts](/Images/6.PNG)

Using the equally weighted training data, a logistic regression model was fit and used to predict the `y` value again.

![Resampled prediction](/Images/7.PNG)

## Results

* Machine Learning Model 1:
  * Accuracy      95%
  * Precision
    * Healthy    100%
    * High-Risk   85%
  * Recall 
    * Healthy     99%
    * High-Risk   91%

![Model 1 results](/Images/8.PNG)

* Machine Learning Model 2:
  * Accuracy      99%
  * Precision
    * Healthy    100%
    * High-Risk   84%
  * Recall 
    * Healthy     99%
    * High-Risk   99%
  
![Model 2 results](/Images/9.PNG)

## Summary

As evidenced in the results above, both models were near perfect in predicting healthy loans. However, what really matters for this analysis is the ability to predict the smaller data set of high-risk loans. Although the raw data model also did quite well at predicting these, with slightly better precision, the resampled data's recall and accuracy scores were much better, leading me to recommend the oversampled model for future loan-risk analysis.
