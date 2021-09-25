# Exercise 2: Cross validation (k-fold)

The goal of this exercise is to learn how to use cross validation. After reading the articles you should be able to explain why we need to cross-validate the models. We will firstly focus on Linear Regression to reduce the computation time. We will be using `cross_validate` to run the cross validation. Note that `cross_val_score` is similar but the `cross_validate` calculates one or more scores and timings for each CV split.

Preliminary:

- Import California Housing data set and split it in a train set and a test set (10%). Fit a linear regression on the data set. *The goal is to focus on the cross validation, that is why the code to fit the Linear Regression is given.*

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
                                                    random_state=43)
# pipeline 
pipeline = [('imputer', SimpleImputer(strategy='median')),
            ('scaler', StandardScaler()),
            ('lr', LinearRegression())]
pipe = Pipeline(pipeline)
```

1. Cross validate the Pipeline using `cross_validate` with 10 folds. Print the scores on each validation sets, the mean score on the validation sets and the standard deviation on the validation sets. The expected output is:

```console
Scores on validation sets: 
 [0.62433594 0.61648956 0.62486602 0.59891024 0.59284295 0.61307055
 0.54630341 0.60742976 0.60014575 0.59574508]

Mean of scores on validation sets: 
 0.60201392526743

Standard deviation of scores on validation sets: 
 0.0214983822773466

 ```

**Note: It may be confusing that the key of the dictionary that returns the results on the validation sets is `test_score`. Sometimes, the validation sets are called test sets. In that case, we run the cross validation on X_train. It means that the scores are computed on sets in the initial train set. The X_test is not used for the cross-validation.**

- https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_validate.html

- https://machinelearningmastery.com/how-to-configure-k-fold-cross-validation/