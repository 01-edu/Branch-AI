# Exercise 3 Regression

The goal of this exercise is to learn to evaluate a machine learning model using many regression metrics.

Preliminary:

- Import California Housing data set and split it in a train set and a test set (10%). Fit a linear regression on the data set. *The goal is focus on the metrics, that is why the code to fit the Linear Regression is given.*

```python
# imports
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import StandardScaler
from sklearn.impute import SimpleImputer
from sklearn.pipeline import Pipeline
# data
housing = fetch_california_housing()
X, y = housing['data'], housing['target']
# split data train test 
X_train, X_test, y_train, y_test = train_test_split(X,
                                                    y,
                                                    test_size=0.1,
                                                    shuffle=True,
                                                    random_state=13)
# pipeline 
pipeline = [('imputer', SimpleImputer(strategy='median')),
            ('scaler', StandardScaler()),
            ('lr', LinearRegression())]
pipe = Pipeline(pipeline)
# fit
pipe.fit(X_train, y_train)
```

1. Predict on the train set and test set

2. Compute R2, Mean Square Error, Mean Absolute Error on both train and test set