##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the code that runs the grid search is similar to:

```python
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

##### The question 2 is validated if these attributes were used:

```python
print(gridsearch.best_score_)
print(gridsearch.best_params_)
print(gridsearch.cv_results_)
```

The best score is -0.29028202683007526, that means that the MSE is ~0.29, it doesn't give any information since this metric is arbitrary. This score is the average of `neg_mean_squared_error` on all the validation sets.

The best models params are `{'max_depth': 10, 'n_estimators': 75}`.

Note that if the parameters used are different, the results should be different. 

##### The question 3 is validated if the fitted estimator was used to compute the score on the test set: `gridsearch.score(X_test, y_test)`. The MSE score is ~0.27. The score I got on the test set is close to the score I got on the validation sets. It means the models is not over fitted.
