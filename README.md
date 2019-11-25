# Sparkify Customer Churn Prediction with PySpark
### Table of Contents

1. [Description](#description)
2. [Files Descriptions](#files)
3. [Dataset](#dataset)
4. [Strategy](#strategy)
5. [Methodology](#methodology)
6. [Implementation](#implementation)
7. [Tuning](#tuning)
8. [Conclusion](#conclusion)

## Description <a name="description"></a>
Predict customer churn with PySpark for an imaginary digital music service called Sparkify. Sparkify has a free-tier and a premium subscription plan. Users can upgrade, downgrade or cancel their service at any time. Churn means downgrading from premium to free tier or cancelling the service. If we can predict users who will churn, the company can offer them discounts and incentives to entice them to stay.

## Files Description <a name="files"></a>
1. Sparkify.ipynb: The churn model trained on the local machine with the small instance of the dataset.
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
In order to solve the problems. The whole analysis is performed using *PySpark*. We woud like to predict the **probability of user churn**. The strategy is to solve the problem is to firstly build and select supervised learning models on a mini dataset. And then it can be deployed onto cloud platforms such as IBM Watson Studio or AWS for a larger dataset.

## Methodology <a name="methodology"></a>
Please refer to my notebook file for detailed analysis, the whole analysis is divided into several parts
- Define Target Variable (churn) and Exploratory Analysis
- Feature Engineering (Create New Feature and Transformation)
- Modeling (Here i used three different models **logistic regression, SVM and gradient boosting tree**)
- Evaluation (Pick up the best model and report result on **validation set**)

## Implementation <a name="implementation"></a>
1. Step1: Split the dataset into 80% training set, 20% valdiation set 
2. Step2: Train the training set on three different models: logistic regression, svm and gradient boosting tree Initial Parameters:
    + LogisticRegression(maxIter=10,regParam=0.0)
    + GBTClassifier(maxDepth=5,maxIter=10,seed=42)
    + LinearSVC(maxIter=10, regParam=0.01) 
3. Step3: Evaluate the three models use the 3-fold cross validation Respective f1 score:
    + logistic regression (f1 score 0.7570)
    + gradient boosted tree ( f1 score 0.7028)
    + supported vector machine (best f1 score 0.6700)
## Tuning <a name="tuning"></a>
Here I tried multiple grid-searches, tuning different hyperparamater:
Several hyperparameters have been tried but  it turned out that the initial ones were the best.

+ logistic regression (logistic_reg.regParam, [0.0, 0.05, 0.1])
+ gradient boosted tree (gbt.maxDepth, [5, 10])
+ supported vector machine (svm.regParam, [0.01, 0.05, 0.5]) 
## Conclusion <a name="conclusion"></a>
**Summary of Solution** 

To summarize the whole analysis, I built a machine learning model using pyspark to predict the user churn based on their log activity. By aggregating the data down to user-level engineering different features, training different machine learning models, tunining hyperparameter and cross validation to pick the best models, I finally picked the GBT models (maxDepth=5, maxIter=10) (Accuracy: 0.7567, F1 Score: 0.7609). Feature Importances were reported in the end.

the project was interesting because it's my first time to use spark. And I now realize how many data records of an individual could be. A user could have hundreds of log records and therefore distributed computing is necessary. However, after we aggregate the data to user level. The size of the user sample actually is not very big. Therefore, it rely on us to use more robust evaluation to train the model.