# Sparkify Customer Churn Prediction with PySpark
### Table of Contents

1. [Description](#description)
2. [Files Descriptions](#files)
3. [Dataset](#dataset)
4. [Strategy](#strategy)
5. [Methodology](#Methodology)

## Description <a name="description"></a>
Predict customer churn with PySpark for an imaginary digital music service called Sparkify. Sparkify has a free-tier and a premium subscription plan. Users can upgrade, downgrade or cancel their service at any time. Churn means downgradding from premium to free tier or cancelling the service. If we can predict users who will churn, the company can offer them discounts and incentives to entice them to stay.

## Files Description <a name="files"></a>
1. Sparkify.ipynb: The original prototype of the customer churn model trained on the local machine with the small instance of the dataset.
2. Results : a folder containing the exported plots as png 

## Dataset <a name="dataset"></a>
The dataset is a .json file that keeps track of timestamped events of the following actions performed on the digital music service:
1. play a song
2. login
3. listening to an advertisement
4. downgrading subscription
5. cancelling subscription
6. ...

## Strategy <a name="strategy"></a>
In order to solve the problems. The whole analysis is performed using *PySpark*. We woud like to predict the **probability of user churn** There, our strategy to solve the problem is to firstly build and select supervised learning models on a mini dataset. And then it can be deployed onto cloud platforms such as IBM Watson Studio or AWS for a larger dataset.

## Methodology <a name="methodology"></a>
Please refer to my notebook file for detailed analysis, the whole analysis is divided into several parts
- Define Target Variable (churn) and Exploratory Analysis
- Feature Engineering (Create New Feature and Transformation)
- Modeling (Here i used three different models **logistic regression, SVM and gradient boosting tree**)
- Evaluation (Pick up the best model and report result on **validation set**)
