# Exercise 3: Train test split

The goal of this exercise is to learn to split a data set. It is important to understand why we split the data in two sets. To put it in a nutshell: the Machine Learning model learns on the training data and evaluates on the data the model hasn't seen before: the testing data.

This video gives a basic and nice explanation: https://www.youtube.com/watch?v=_vdMKioCXqQ

This article explains the conditions to split the data and how to split it: https://machinelearningmastery.com/train-test-split-for-evaluating-machine-learning-algorithms/

```python
X = np.arange(1,21).reshape(10,-1)
y = np.arange(1,11)
```

1. Split the data using `train_test_split` with `shuffle=False`. The test set represents 20% of the total size of the data set. Print X_train, y_train, X_test, y_test.

https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html