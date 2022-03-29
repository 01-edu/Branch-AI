##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the code that runs the `gridsearch` is (the parameters may change):

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

##### The question 2 is validated if the function is:

```python
def select_model_verbose(gs):

    return gs.best_estimator_, gs.best_params_, gs.best_score_
```

In my case, the `gridsearch` parameters are not interesting. Even if I reduced the over-fitting of the Random Forest, the score on the test is lower than the score on the test returned by the Gradient Boosting in the previous exercise without optimal parameters search.

##### The question 3 is validated if the code used is:

```python
model, best_params, best_score = select_model_verbose(gridsearch)
model.predict(new_point)
```
