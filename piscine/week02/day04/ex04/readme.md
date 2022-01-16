# Exercise 4 Classification

The goal of this exercise is to learn to evaluate a machine learning model using many classification metrics.

Preliminary:

- Import Breast Cancer data set and split it in a train set and a test set (20%). Fit a logistic regression on the data set. *The goal is focus on the metrics, that is why the code to fit the logistic Regression is given.*

```python
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import load_breast_cancer
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

X , y = load_breast_cancer(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.20)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
classifier = LogisticRegression()
classifier.fit(X_train_scaled, y_train)
```

1. Predict on the train set and test set

2. Compute F1, accuracy, precision, recall, roc_auc scores on the train set and test set. Print the confusion matrix on the test set results.

**Note: AUC can only be computed on probabilities, not on classes.**

3. Plot the AUC curve for on the test set using roc_curve of scikit learn. There many ways to create this plot. It should look like this:

![alt text][logo_ex4]

[logo_ex4]: ./w2_day4_ex4_q3.png "ROC AUC "

- https://scikit-learn.org/stable/modules/generated/sklearn.metrics.plot_roc_curve.html