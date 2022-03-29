# Exercise 1: K-Fold

The goal of this exercise is to learn to use `KFold` to split the data set in a k-fold cross validation. Most of the time you won't use this function to split your data because this function is used by others as `cross_val_score` or `cross_validate` or `GridSearchCV` ... . But, this allows to understand the splitting and to create a custom one if needed.  

```python
X = np.array(np.arange(1,21).reshape(10,-1))
y = np.array(np.arange(1,11))
```

1. Using `KFold`, perform a 5-fold cross validation. For each fold, print the train index and test index. The expected output is:

    ```console
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