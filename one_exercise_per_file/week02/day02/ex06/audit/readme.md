##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if each classifier has as input a binary data as below:

```python
def train(X_train, y_train):
       clf = LogisticRegression()
       clf1 = LogisticRegression()
       clf2 = LogisticRegression()
       
       clf.fit(X_train, y_train == 0)
       clf1.fit(X_train, y_train == 1)
       clf2.fit(X_train, y_train == 2)
       
       return clf, clf1, clf2
```

##### The question 2 is validated if the predicted classes on the test set are:

```console
array([0, 0, 2, 1, 2, 0, 2, 1, 1, 1, 0, 1, 2, 0, 1, 1, 0, 0, 2, 2, 0, 0,
       0, 2, 2, 2, 0, 1, 0, 0])
```

Even if I had this warning `ConvergenceWarning: lbfgs failed to converge (status=1):` I noticed that `LogisticRegression` returns the same output.
