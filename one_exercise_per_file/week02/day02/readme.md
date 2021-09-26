# W2D02  Piscine AI - Data Science

## Classification with Scikit Learn

The goal of this day is to understand practical classification. 

Today we will learn a different approach in Machine Learning: the classification which is a large domain in the field of statistics and machine learning. Generally, it can be broken down in two areas:

- **Binary classification**, where we wish to group an outcome into one of two groups.
- **Multi-class classification**, where we wish to group an outcome into one of multiple (more than two) groups.

You may wonder why the approach is different from regression and why we don't use regression and define a threshold from where the class would 1 else 0 - in binary classification.
The main reason is that the linear regression is sensitive to outliers, hence the treshold would vary depending on the outliers in the data. The article mentioned explains this reason with plots. To keep things simple, we can say that the output needed in classification is a probability to belong to one of the classes. So, by definition the value output by the classification model has to be between 0 and 1. The linear regression can't satisfy this constraint.

In mathematics, there are functions with nice properties that take as input a real (-inf, inf) and output a value between 0 and 1, the most popular of them is the **sigmoid** - which is the inverse function of the logit, hence the name logistic regression.

Let's take a small example to have a better understanding of the steps needed to perform a logistic regression on a binary data. Let's assume that we want to predict the gender given the people' size (height).

Logistic regression steps:

- Fit a sigmoid on the training data
- Compute sigmoid(size)=0.7 because the sigmoid returns values between 0 and 1
- Return the class: 0.7 > 0.5 => class 1. Thus, the gender is male

For the linear regression exercises, the loss (Mean Square Error - MSE) is minimized with an algorithm called **gradient descent**. In the classification, the loss MSE  can't be used because the output of the model is 0 or 1 (for binary classification).

The **logloss** or **cross entropy** is the loss used for classification. Similarly, it has some nice mathematical properties. The minimization of the **logloss** is not covered in the exercises. However, since it is used in most machine learning models for classification, I recommend to spend some time reading the related article. 


## Exercises of the day

- Exercise 1 Logistic regression with Scikit-learn
- Exercise 2 Sigmoid
- Exercise 3 Decision boundary
- Exercise 4 Train test split
- Exercise 5 Breast Cancer prediction
- Bonus: Exercise 6 Multi-class - **Optional**


## Virtual Environment 
- Python 3.x
- NumPy
- Pandas
- Matplotlib
- Scikit Learn
- Jupyter or JupyterLab

*Version of Scikit Learn I used to do the exercises: 0.22*. I suggest to use the most recent one. Scikit Learn 1.0 is finally available after ... 14 years. 

## Ressources

### Logistic regression

- https://towardsdatascience.com/understanding-logistic-regression-9b02c2aec102

### Logloss

- https://towardsdatascience.com/cross-entropy-for-classification-d98e7f974451

- https://medium.com/swlh/what-is-logistic-regression-62807de62efa