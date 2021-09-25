1. This question is validated if the fitted logistic regression returns:

```python
LogisticRegression(C=1.0, class_weight=None, dual=False, fit_intercept=True,
                   intercept_scaling=1, l1_ratio=None, max_iter=100,
                   multi_class='auto', n_jobs=None, penalty='l2',
                   random_state=0, solver='lbfgs', tol=0.0001, verbose=0,
                   warm_start=False)
```

2. This question is validated if the predicted class is `0`.

3. This question is validated if the predicted probabilities are `[0.61450526 0.38549474]`

4. This question is validated if the output is:

```console
Coefficient: 
 [[0.81786797]]
Intercept: 
 [-0.87522391]
Score: 
 0.7142857142857143
```