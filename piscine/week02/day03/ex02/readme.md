
# Exercise 2 Scaler

The goal of this exercise is to learn to scale a data set. There are various scaling techniques, we will focus on `StandardScaler` from scikit learn.

We will use a tiny data set for this exercise that we will generate by ourselves:

```python
X_train = np.array([[ 1., -1.,  2.],
                     [ 2.,  0.,  0.],
                     [ 0.,  1., -1.]])
```

1. Fit the `StandardScaler` on the data and scale X_train using `fit_transform`. Compute the `mean` and `std` on `axis 0`.

2. Scale the test set using the `StandardScaler` fitted on the train set.

```python
X_test = np.array([[ 2., -1.,  1.],
                     [ 3.,  3.,  -1.],
                     [ 1.,  1., 1.]])
```

**WARNING:
If the data is split in train and test set, it is extremely important to apply the same scaling the test data. As the model is trained on scaled data, if it takes as input unscaled data, it returns incorrect values.**

Resources:

- https://medium.com/technofunnel/what-when-why-feature-scaling-for-machine-learning-standard-minmax-scaler-49e64c510422

- https://scikit-learn.org/stable/modules/preprocessing.html