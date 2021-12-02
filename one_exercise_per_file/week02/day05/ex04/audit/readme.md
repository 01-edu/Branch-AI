1. This question is validated if the outputted plot looks like:

![alt text][logo_ex5q1]

[logo_ex5q1]: ../w2_day5_ex5_q1.png "Validation curve "

The code that generated the data in the plot is:

```python
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

2. This question is validated if the output is

![alt text][logo_ex5q2]

[logo_ex5q2]: ../w2_day5_ex5_q2.png "Learning curve "
