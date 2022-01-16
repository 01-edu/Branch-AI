# Exercise 5 Machine Learning models

The goal of this exercise is to have an overview of the existing Machine Learning models and to learn to call them from scikit learn.
We will focus on:

- SVM/SVC
- Decision Tree
- Random Forest (Ensemble learning)
- Gradient Boosting (Ensemble learning, Boosting techniques)

All these algorithms exist in two versions: regression and classification. Even if the logic is similar in both classification and regression, the loss function is specific to each case.

It is really easy to get lost among all the existing algorithms. This article is very useful to have a clear overview of the models and to understand which algorithm use and when. https://towardsdatascience.com/how-to-choose-the-right-machine-learning-algorithm-for-your-application-1e36c32400b9

Preliminary:

- Import California Housing data set and split it in a train set and a test set (10%). Fit a linear regression on the data set. *The goal is to focus on the metrics, that is why the code to fit the Linear Regression is given.*

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
# fit
pipe.fit(X_train, y_train)

```

1. Create 5 pipelines with 5 different models as final estimator (keep the imputer and scaler unchanged):
    1. Linear Regression
    2. SVM
    3. Decision Tree (set `random_state=43`)
    4. Random Forest (set `random_state=43`)
    5. Gradient Boosting  (set `random_state=43`)

Take time to have basic understanding of the role of the basic hyperparameter and their default value.

- For each algorithm, print the R2, MSE and MAE on both train set and test set.