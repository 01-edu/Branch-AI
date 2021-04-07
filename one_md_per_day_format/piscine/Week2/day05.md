# D04  Piscine AI - Data Science 


# Table of Contents:


# Introduction

If you finished yesterday's exercises you should be able to train several Machine Learning algorithms and to choose one returned by GridSearchCV.
GridSearchCV returns the model that gives the best score on the test set. Yesterday, as I told you, I changed the **cv** parameter to compute the GridSearch with a train set and a test set. 
It means that the selected model is based on one single measure. What if, by luck, we predict correctly on that section ? What if the best model is bad ? What if I could have selected a better model ? 

We will answer these questions today ! The topics we will cover are the one of the most important in Machine Learning. 
Must read before to start the exercises: 

    - Biais-Variance trade off; aka Underfitting/Overfitting.
        -  https://machinelearningmastery.com/gentle-introduction-to-the-bias-variance-trade-off-in-machine-learning/

        - https://jakevdp.github.io/PythonDataScienceHandbook/05.03-hyperparameters-and-model-validation.html

    - Cross-validation
        - https://algotrading101.com/learn/train-test-split/

- 

## Rules

## Ressources 


# Exercise 1: K-Fold

The goal of this exercise is to learn to use `KFold` to split the data set in a k-fold cross validation. Most of the time you won't use this function to split your data because this function is used by others as `cross_val_score` or `cross_validate` or `GridSearchCV` ... . But, this allows to understand the splitting and to create a custom one if needed.  

```
X = np.array(np.arange(1,21).reshape(10,-1))
y = np.array(np.arange(1,11))
```

1. Using `KFold`, perform a 5-fold cross validation. For each fold, print the train index and test index. The expected output is: 

    ```
    Fold:  1
    TRAIN: [2 3 4 5 6 7 8 9] TEST: [0 1]

    Fold:  2
    TRAIN: [0 1 4 5 6 7 8 9] TEST: [2 3]

    Fold:  3
    TRAIN: [0 1 2 3 6 7 8 9] TEST: [4 5]

    Fold:  4
    TRAIN: [0 1 2 3 4 5 8 9] TEST: [6 7]

    Fold:  5
    TRAIN: [0 1 2 3 4 5 6 7] TEST: [8 9]
    ```


## Correction 

1. This question is validated if the output of the 5-fold cross validation is: 


    ```
    Fold:  1
    TRAIN: [2 3 4 5 6 7 8 9] TEST: [0 1]

    Fold:  2
    TRAIN: [0 1 4 5 6 7 8 9] TEST: [2 3]

    Fold:  3
    TRAIN: [0 1 2 3 6 7 8 9] TEST: [4 5]

    Fold:  4
    TRAIN: [0 1 2 3 4 5 8 9] TEST: [6 7]

    Fold:  5
    TRAIN: [0 1 2 3 4 5 6 7] TEST: [8 9]
    ```

    

# Exercise 2: Cross validation (k-fold)

The goal of this exercise is to learn how to use cross validation. After reading the articles you should be able to explain why we need to cross-validate the models. We will firstly focus on Linear Regression to reduce the computation time. We will be using `cross_validate` to run the cross validation. Note that `cross_val_score` is similar bu the `cross_validate` calculates one or more scores and timings for each CV split.

Preliminary: 

- Import California Housing data set and split it in a train set and a test set (10%). Fit a linear regression on the data set. *The goal is to focus on the cross validation, that is why the code to fit the Linear Regression is given.* 



```
#imports
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import StandardScaler
from sklearn.impute import SimpleImputer
from sklearn.pipeline import Pipeline

#data
housing = fetch_california_housing()
X, y = housing['data'], housing['target']
#split data train test 
X_train, X_test, y_train, y_test = train_test_split(X,
                                                    y,
                                                    test_size=0.1,
                                                    shuffle=True,
                                                    random_state=43)
#pipeline 
pipeline = [('imputer', SimpleImputer(strategy='median')),
            ('scaler', StandardScaler()),
            ('lr', LinearRegression())]
pipe = Pipeline(pipeline)
```



1. Cross validate the Pipeline using `cross_validate` with 10 folds. Print the scores on each validation sets, the mean score on the validation sets and the standard deviation on the validation sets. The expected output is: 

```
Scores on validation sets: 
 [0.62433594 0.61648956 0.62486602 0.59891024 0.59284295 0.61307055
 0.54630341 0.60742976 0.60014575 0.59574508]

Mean of scores on validation sets: 
 0.60201392526743

Standard deviation of scores on validation sets: 
 0.0214983822773466

 ```

**Note: It may be confusing that the key of the dictionnary that returns the results on the validation sets is `test_score`. Sometimes, the validation sets are called test sets. In that case, we run the cross validation on X_train. It means that the scores are computed on sets in the initial train set. The X_test is not used for the cross-validation.**

https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_validate.html
https://machinelearningmastery.com/how-to-configure-k-fold-cross-validation/

## Correction 

1. This question is validated if the output is: 

```
Scores on validation sets: 
 [0.62433594 0.61648956 0.62486602 0.59891024 0.59284295 0.61307055
 0.54630341 0.60742976 0.60014575 0.59574508]

Mean of scores on validation sets: 
 0.60201392526743

Standard deviation of scores on validation sets: 
 0.0214983822773466

```

The model is consistent across folds: it is stable. That's a first sign that the model is not overfitted. The average R2 is 60% that's a good start ! To be improved. 



# Exercise 3 GridsearchCV

The goal of this exercise is to learn to use GridSearchCV to run a grid search, predict on the test set and score on the test set. 

Preliminary: 

- Import California Housing data set and split it in a train set and a test set (10%). Fit a linear regression on the data set. *The goal is to focus on the gridsearch, that is why the code to fit the Linear Regression is given.* 


```
#imports
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import StandardScaler
from sklearn.impute import SimpleImputer
from sklearn.pipeline import Pipeline

#data
housing = fetch_california_housing()
X, y = housing['data'], housing['target']
#split data train test 
X_train, X_test, y_train, y_test = train_test_split(X,
                                                    y,
                                                    test_size=0.1,
                                                    shuffle=True,
                                                    random_state=43)
#pipeline 
pipeline = [('imputer', SimpleImputer(strategy='median')),
            ('scaler', StandardScaler()),
            ('lr', LinearRegression())]
pipe = Pipeline(pipeline)
```


1. Run `GridSearchCV` on all CPUs with 5 folds, MSE as score, Random Forest as model with:

    - max_depth between 1 and 20 (at least 3 values)
    - n_estimators between 1 and 100 (at least 3 values)

This may take few minutes to run. 

*Hint*: The name of the metric to put in the parameter `scoring` is `neg_mean_squared_error`. The smaller the MSE is, the better the model is. At the contrary, The greater the R2 is the better the model is. `GridSearchCV` chooses the best model by selecting the one that maximized the score on the validation sets. And, in mathetmatic, maximzing a function or minimzing its opposite is equivalent. More details: 
https://stackoverflow.com/questions/21443865/scikit-learn-cross-validation-negative-values-with-mean-squared-error


2. Extract the best fitted estimator, print its params, print its score on the validation set and print `cv_results_`.

3. Compute the score the test set.  


WARNING: If the score used in classification is the AUC, there is one rare case where the AUC may return an error or a warning: The fold contains only one class. In that case it can't be computed, by definition. 


## Correction

1. This question is validated if the code that runs the grid search is similar to: 

    ```
    parameters = {'n_estimators':[10, 50, 75],
                'max_depth':[4, 7, 10]}

    rf = RandomForestRegressor()
    gridsearch = GridSearchCV(rf,
                            parameters,
                            cv = 5,
                            n_jobs=-1,
                            scoring='neg_mean_squared_error')

    gridsearch.fit(X_train, y_train)

    ```
    The answers that uses another list of parameters are accepted too ! 

2. This question is validated if you called this attributes: 

    ```
    print(gridsearch.best_score_)
    print(gridsearch.best_params_)
    print(gridsearch.cv_results_)
    ```
    The best score is -0.29028202683007526, that means that the MSE is ~0.29, it doesn't give any information since this metric is arbitrary. This score is the average of `neg_mean_squared_error` on all the validation sets. 

    The best models params are `{'max_depth': 10, 'n_estimators': 75}`. 

    As you may must have a different parameters list than this one, you should have different results. 

3. This question is validated if you used the fitted estimator to compute the score on the test set: `gridsearch.score(X_test, y_test)`. The MSE score is ~0.27. The score I got on the test set is close to the score I got on the validation sets. It means the models is not overfitted. 

    

# Exercise 5 Validation curve and Learning curve 

The goal of this exercise is to learn to analyse the models' performance with two tools:
- Validation curve
- Learning curve 

For this exercise we will use a dataset of 100k data points to give you an idea of the computation time you can expect during projects. 

Preliminary: 

- Using make_classification from sklearn, generate a binary data set with 100k data points and with 30 features. 

    ```
    X, y = make_classification(n_samples=100000,
                            n_features= 30,
                            n_informative=10,
                            flip_y=0.2 )
    ```



1. Plot the validation curve, using all CPUs, with 5 folds. The goal is to focus again on max_depth between 1 and 20. 
You may need to increase the window (example: between 1 and 50 ) if you notice that other values of max_depth could have returned better results. This may take few minutes. 

I do not expect that you implement all the plot from scratch, you'd better leverage the code here: 
https://scikit-learn.org/stable/auto_examples/model_selection/plot_validation_curve

The plot should look like this: 

![alt text][logo_ex5q1]

[logo_ex5q1]: images/day5/ex5/w2_day5_ex5_q1.png "Validation curve "

The interpretation is that from max_depth=10, the train score keeps increasing but the test score (or validation score) reaches a plateau. It means that choosing max_depth = 20 may lead to have an overfitted model. 

Note: Given the time computation is is not possible to plot the validation curve for all parameters. It is useful to plot it for parameters that control the overfitting the most. 

More details: https://chrisalbon.com/machine_learning/model_evaluation/plot_the_validation_curve/


2. Let us assume the gridsearch returned `clf = RandomForestClassifier(max_depth=12)`. Let's check if the models underfits, overfit or fits correctly. Plot the learning curve. These two ressources will help you a lot to understand how to analyse the learning curves and how to plot them: 

    - https://machinelearningmastery.com/learning-curves-for-diagnosing-machine-learning-model-performance/
    - https://scikit-learn.org/stable/auto_examples/model_selection/plot_learning_curve.html#sphx-glr-auto-examples-model-selection-plot-learning-curve-py


- **Re-use the function in the second ressource**, change the cross validation to a classic 10-folds, run the learning curve data computation on all CPUs and plot the three plots as shown below.

![alt text][logo_ex5q2]

[logo_ex5q2]: images/day5/ex5/w2_day5_ex5_q2.png "Learning curve "

- **Note Plot Learning Curves**: The learning curves is detailed in the first ressource. 
- **Note Plot Scalibility of the model**: This plot shows the relationship between the time to train the model and the number of rows in the data. In that case the relationship is linear. 
- **Note Performance of the model**: This plot shows wether it worths increasing the training time by adding data to increase the score. It would worth to add data to increase the score if the curve hasn't reach a plateau yet. In that case, increasing the training time by 10 units increases the score by less than 0.001. 
## Correction 

1. This question is validated if the outputted plot looks like: 
![alt text][logo_ex5q1]

[logo_ex5q1]: images/day5/ex5/w2_day5_ex5_q1.png "Validation curve "

The code that generated the data in the plot is: 


```
from sklearn.model_selection import validation_curve

clf = RandomForestClassifier()
param_range = np.arange(1,30,2)
train_scores, test_scores = validation_curve(clf,
                                            X,
                                            y,
                                            param_name="max_depth",
                                            param_range=param_range,
                                            scoring="roc_auc",
                                            n_jobs=-1)

```

2. This question is validated if the ouput is 

![alt text][logo_ex5q2]

[logo_ex5q2]: images/day5/ex5/w2_day5_ex5_q2.png "Learning curve "


