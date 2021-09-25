# D04  Piscine AI - Data Science

# Table of Contents:

# Introduction

Today we will learn how to choose the right Machine Learning metric depending on the problem you are solving and to compute it. A metric gives an idea of how good the model performs. Depending on working on a classification problem or a regression problem the metrics considered are different. It is important to understand that all metrics are just metrics, not the truth.

We will focus on the most important metrics:

- Regression:
  - **R2**, **Mean Square Error**, **Mean Absolute Error**
- Classification:
  - **F1 score**, **accuracy**, **precision**, **recall** and **AUC scores**. Even if it not considered as a metric, the **confusion matrix** is always useful to understand the model performance.

Warning: **Imbalanced data set**

Let us assume we are predicting a rare event that occurs less than 2% of the time. Having a model that scores a good accuracy is easy, it doesn't have to be "smart", all it has to do is to always predict the majority class. Depending on the problem it can be disastrous. For example, working with real life data, breast cancer prediction is an imbalanced problem where predicting the majority leads to disastrous consequences. That is why metrics as AUC are useful.

- https://stats.stackexchange.com/questions/260164/auc-and-class-imbalance-in-training-test-dataset

Before to compute the metrics, read carefully this article to understand the role of these metrics.

- https://www.kdnuggets.com/2018/06/right-metric-evaluating-machine-learning-models-2.html

+ ML models + GS

## Historical

## Rules

## Resources

- https://scikit-learn.org/stable/modules/model_evaluation.html
