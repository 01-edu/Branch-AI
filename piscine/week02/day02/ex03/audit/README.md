##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the outputted plot looks like this:

![alt text][ex3q1]

[ex3q1]: ../w2_day2_ex3_q1.png "Scatter plot"

##### The question 2 is validated if the coefficient and the intercept of the Logistic Regression are:

```console
Intercept:  [-0.98385574]
Coefficient:  [[1.18866075]]
```

##### The question 3 is validated if the plot looks like this:

![alt text][ex3q2]

[ex3q2]: ../w2_day2_ex3_q3.png "Scatter plot"

##### The question 4 is validated if `predict_probability` outputs the same probabilities as `predict_proba`. Note that the values have to match one of the class probabilities, not both. To do so, compare the output with: `clf.predict_proba(X)[:,1]`. The shape of the arrays is not important.

##### The question 5 is validated if `predict_class` outputs the same classes as `cfl.predict(X)`. The shape of the arrays is not important.

##### The question 6 is validated if the plot looks like the plot below. As mentioned, it is not required to shift the class prediction to make the plot easier to understand.

![alt text][ex3q6]

[ex3q6]: ../w2_day2_ex3_q5.png "Scatter plot + Logistic regression + predictions"

##### The question 7 is validated if the plot looks like this:

![alt text][ex3q7]

[ex3q7]: ../w2_day2_ex3_q6.png "Logistic regression decision boundary"
