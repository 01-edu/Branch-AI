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

# Exercise 1 MSE Scikit-learn 

The goal of this exercise is to learn to use `sklearn.metrics` to compute the mean squared error (MSE).

1. Compute the MSE using `sklearn.metrics` on `y_true` and `y_pred` below:

```python
y_true = [91, 51, 2.5, 2, -5]
y_pred = [90, 48, 2, 2, -4]
```

## Correction

1. This question is validated if the MSE outputted is **2.25**.

# Exercise 2 Accuracy Scikit-learn

The goal of this exercise is to learn to use `sklearn.metrics` to compute the accuracy.

1. Compute the accuracy using `sklearn.metrics` on `y_true` and `y_pred` below:

```python
y_pred = [0, 1, 0, 1, 0, 1, 0]
y_true = [0, 0, 1, 1, 1, 1, 0]
```

## Correction

1. This question is validated if the accuracy outputted is **0.5714285714285714**.

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

## Correction

1. This question is validated if the predictions on the train set and test set are:

   ```console
    # 10 first values Train
    array([1.54505951, 2.21338527, 2.2636205 , 3.3258957 , 1.51710076,
        1.63209319, 2.9265211 , 0.78080924, 1.21968217, 0.72656239])
    ```

    ```console
    #10 first values Test

    array([ 1.82212706,  1.98357668,  0.80547979, -0.19259114,  1.76072418,
            3.27855815,  2.12056804,  1.96099917,  2.38239663,  1.21005304])
    ```

2. This question is validated if the results match this output:

    ```console
    r2 on the train set:  0.3552292936915783
    MAE on the train set:  0.5300159371615256
    MSE on the train set:  0.5210784446797679

    r2 on the test set:  0.30265471284464673
    MAE on the test set:  0.5454023699809112
    MSE on the test set:  0.5537420654727396
    ```

This result shows that the model has slightly better results on the train set than the test set. That's frequent since it is easier to get a better grade on an exam we studied than an exam that is different from what was prepared. However, the results are not good: r2 ~ 0.3. Fitting non linear models as the Random Forest on this data may improve the results. That's the goal of the exercise 5.

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

[logo_ex4]: images/day4/ex4/w2_day4_ex4_q3.png "ROC AUC "

- https://scikit-learn.org/stable/modules/generated/sklearn.metrics.plot_roc_curve.html

## Correction

1. This question is validated if the predictions on the train set and test set are:

    ```console
    # 10 first values Train
    array([1, 0, 1, 1, 1, 0, 0, 1, 1, 0])

    # 10 first values Test
    array([1, 1, 0, 0, 0, 1, 1, 1, 0, 0])
    ```

2. This question is validated if the results match this output:

    ```console
    F1 on the train set:  0.9911504424778761
    Accuracy on the train set:  0.989010989010989
    Recall on the train set:  0.9929078014184397
    Precision on the train set:  0.9893992932862191
    ROC_AUC on the train set:  0.9990161111794368


    F1 on the test set:  0.9801324503311258
    Accuracy on the test set:  0.9736842105263158
    Recall on the test set:  0.9866666666666667
    Precision on the test set:  0.9736842105263158
    ROC_AUC on the test set:  0.9863247863247864
    ```

    The confusion matrix on the test set should be:

    ```console
    array([[37,  2],
           [ 1, 74]])
    ```

3. The ROC AUC plot should look like:

![alt text][logo_ex4]

[logo_ex4]: images/day4/ex4/w2_day4_ex4_q3.png "ROC AUC "

Having a 99% ROC AUC is not usual. The data set we used is easy to classify. On real data sets, always check if there's any leakage while having such a high ROC AUC score.

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

## Correction

1. Some of the algorithms use random steps (random sampling used by the `RandomForest`). I used `random_state = 43` for the Random Forest, the Decision Tree and the Gradient Boosting. This question is validated of the scores you got are close to:

    ```console
    # Linear regression 

    TRAIN
    r2 on the train set:  0.34823544284172625
    MAE on the train set:  0.533092001261455
    MSE on the train set:  0.5273648371379568

    TEST
    r2 on the test set:  0.3551785428138914
    MAE on the test set:  0.5196420310323713
    MSE on the test set:  0.49761195027083804


    # SVM 

    TRAIN
    r2 on the train set:  0.6462366150965996
    MAE on the train set:  0.38356451633259875
    MSE on the train set:  0.33464478671339165

    TEST
    r2 on the test set:  0.6162644671183826
    MAE on the test set:  0.3897680598426786
    MSE on the test set:  0.3477101776543003


    # Decision Tree

    TRAIN
    r2 on the train set:  0.9999999999999488
    MAE on the train set:  1.3685733933909677e-08
    MSE on the train set:  6.842866883530944e-14

    TEST
    r2 on the test set:  0.6263651902480918
    MAE on the test set:  0.4383758696244002
    MSE on the test set:  0.4727017198871596


    # Random Forest

    TRAIN
    r2 on the train set:  0.9705418471542886
    MAE on the train set:  0.11983836612191189
    MSE on the train set:  0.034538356420577995

    TEST
    r2 on the test set:  0.7504673649554309
    MAE on the test set:  0.31889891600404635
    MSE on the test set:  0.24096164834441108


    # Gradient Boosting

    TRAIN
    r2 on the train set:  0.7395782392433273
    MAE on the train set:  0.35656543036682264
    MSE on the train set:  0.26167490389525294

    TEST
    r2 on the test set:  0.7157456298013534
    MAE on the test set:  0.36455447680396397
    MSE on the test set:  0.27058170064218096

    ```

It is important to notice that the Decision Tree over fits very easily. It learns easily the training data but is not able to extrapolate on the test set. This algorithm is not used a lot.

However, Random Forest and Gradient Boosting propose a solid approach to correct the over fitting (in that case the parameters `max_depth` is set to None that is why the Random Forest over fits the data). These two algorithms are used intensively in Machine Learning Projects.

# Exercise 6 Grid Search

The goal of this exercise is to learn how to make an exhaustive search over specified parameter values for an estimator. This is very useful because the hyperparameter which are the parameters of the model impact the performance of the model.

The scikit learn object that runs the Grid Search is called GridSearchCV. We will learn tomorrow about the cross validation. For now, let us set the parameter **cv** to `[(np.arange(18576), np.arange(18576,20640))]`.
This means that GridSearchCV splits the data set in a train and test set.

Preliminary:

- Load the California Housing data set. As precised, this time, there's no need to split the data set in train set and test set since GridSearchCV does it.

You will have to run a Grid Search on the Random Forest on at least the hyperparameter that are mentioned below. It doesn't mean these are the only hyperparameter of the model. If possible, try at least 3 different values for each hyperparameter.

1. Run a Grid Search with `n_jobs` set to `-1` to parallelize the computations on all CPUs. The hyperparameter to change are: n_estimators, max_depth, min_samples_leaf. It may take

Now, let us analyse the grid search's results in order to select the best model.

2. Write a function that takes as input the Grid Search object and that returns the best model **fitted**, the best set of hyperparameter and the associated score:

    ```python
    def select_model_verbose(gs):

        return trained_model, best_params, best_score
    ```

3. Use the trained model to predict on a new point:

```python
new_point = np.array([[3.2031, 52., 5.47761194, 1.07960199, 910., 2.26368159, 37.85, -122.26]])
```

How do we know the best model returned by GridSearchCV is good enough and stable ? That is what we will learn tomorrow !

**WARNING: Some combinations of hyper parameters are not possible. For example using the SVM, the kernel linear has no parameter gamma.**

**Note**:

- GridSearchCV can also take a Pipeline instead of a Machine Learning model. It is useful to combine some Imputers or Dimension reduction techniques with some Machine Learning models in the same Pipeline.
- It may be useful to check on Kaggle if some Kagglers share their Grid Searches.

Ressources:

- https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html

- https://stackoverflow.com/questions/38555650/try-multiple-estimator-in-one-grid-search

- https://medium.com/fintechexplained/what-is-grid-search-c01fe886ef0a

- https://elutins.medium.com/grid-searching-in-machine-learning-quick-explanation-and-python-implementation-550552200596

- https://scikit-learn.org/stable/auto_examples/model_selection/plot_grid_search_digits.html

## Correction

1. This question is validated if the code that runs the `gridsearch` is (the parameters may change):

```python
parameters = {'n_estimators':[10, 50, 75],
            'max_depth':[3,5,7],
            'min_samples_leaf': [10,20,30]}

rf = RandomForestRegressor()
gridsearch = GridSearchCV(rf,
                        parameters,
                        cv = [(np.arange(18576), np.arange(18576,20640))],
                        n_jobs=-1)
gridsearch.fit(X, y)
```

2. This question is validated if the function is:

```python
def select_model_verbose(gs):

    return gs.best_estimator_, gs.best_params_, gs.best_score_
```

In my case, the `gridsearch` parameters are not interesting. Even if I reduced the over fitting of the Random Forest, the score on the test is lower than the score on the test returned by the Gradient Boosting in the previous exercise without optimal parameters search.

3. This question is validated if the code used is:

```python
model, best_params, best_score = select_model_verbose(gridsearch)
model.predict(new_point)
```
