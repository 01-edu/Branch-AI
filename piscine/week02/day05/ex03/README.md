# Exercise 3 GridsearchCV

The goal of this exercise is to learn to use GridSearchCV to run a grid search, predict on the test set and score on the test set.

Preliminary:

- Import California Housing data set and split it in a train set and a test set (10%). Fit a linear regression on the data set. *The goal is to focus on the gridsearch, that is why the code to fit the Linear Regression is given.*

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

1. Run `GridSearchCV` on all CPUs with 5 folds, MSE as score, Random Forest as model with:

- max_depth between 1 and 20 (at least 3 values)
- n_estimators between 1 and 100 (at least 3 values)

This may take few minutes to run.

*Hint*: The name of the metric to put in the parameter `scoring` is `neg_mean_squared_error`. The smaller the MSE is, the better the model is. At the contrary, The greater the R2 is the better the model is. `GridSearchCV` chooses the best model by selecting the one that maximized the score on the validation sets. And, in mathematic, maximizing a function or minimizing its opposite is equivalent. More details:

- https://stackoverflow.com/questions/21443865/scikit-learn-cross-validation-negative-values-with-mean-squared-error

2. Extract the best fitted estimator, print its params, print its score on the validation set and print `cv_results_`.

3. Compute the score the test set.

**WARNING: If the score used in classification is the AUC, there is one rare case where the AUC may return an error or a warning: The fold contains only one class. In that case it can't be computed, by definition.**