# W2D04  Piscine AI - Data Science

## Train and evaluate Machine Learning models

Today we will learn how to train and evaluate a machine learning model. You'll learn how tochoose the right Machine Learning metric depending on the problem you are solving and to compute it. A metric gives an idea of how good the model performs. Depending on working on a classification problem or a regression problem the metrics considered are different. It is important to understand that all metrics are just metrics, not the truth.

We will focus on the most important metrics:

- Regression:
  - **R2**, **Mean Square Error**, **Mean Absolute Error**
- Classification:
  - **F1 score**, **accuracy**, **precision**, **recall** and **AUC scores**. Even if it not considered as a metric, the **confusion matrix** is always useful to understand the model performance.

Warning: **Imbalanced data set**

Let us assume we are predicting a rare event that occurs less than 2% of the time. Having a model that scores a good accuracy is easy, it doesn't have to be "smart", all it has to do is to always predict the majority class. Depending on the problem it can be disastrous. For example, working with real life data, breast cancer prediction is an imbalanced problem where predicting the majority leads to disastrous consequences. That is why metrics as AUC are useful. Before to compute the metrics, read carefully this article to understand the role of these metrics.

You'll learn to train other types of Machine Learning models than linear regression and logistic regression. You're not supposed to spend time understanding the theory. I recommend to do that during the projects. Today, read the Scikit-learn documentation to have a basic understanding of the models you use. Focus on how to use correctly those Machine Learning models with Scikit-learn. 

You'll also learn what is a grid-search and how to use it to train your machine learning models. 

## Exercises of the day

- Exercise 0 Environment and libraries
- Exercise 1 MSE Scikit-learn 
- Exercise 2 Accuracy Scikit-learn
- Exercise 3 Regression
- Exercise 4 Classification
- Exercise 5 Machine Learning models
- Exercise 6 Grid Search


## Virtual Environment 
- Python 3.x
- NumPy
- Pandas
- Matplotlib
- Scikit Learn
- Jupyter or JupyterLab

*Version of Scikit Learn I used to do the exercises: 0.22*. I suggest to use the most recent one. Scikit Learn 1.0 is finally available after ... 14 years. 

## Ressources

### Metrics

- https://www.kdnuggets.com/2018/06/right-metric-evaluating-machine-learning-models-2.html

### Imbalance datasets

- https://stats.stackexchange.com/questions/260164/auc-and-class-imbalance-in-training-test-dataset

### Gridsearch

- https://medium.com/fintechexplained/what-is-grid-search-c01fe886ef0a

# Exercise 0 Environment and libraries

The goal of this exercise is to set up the Python work environment with the required libraries.

**Note:** For each quest, your first exercice will be to set up the virtual environment with the required libraries. 

I recommend to use:

- the **last stable versions** of Python. 
- the virtual environment you're the most confortable with. `virtualenv` and `conda` are the most used in Data Science.
- one of the most recents versions of the libraries required

1. Create a virtual environment named `ex00`, with a version of Python >= `3.8`, with the following libraries: `pandas`, `numpy`, `jupyter`, `matplotlib` and `scikit-learn`.

