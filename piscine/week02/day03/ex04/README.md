# Exercise 4 Ordinal Encoder

The goal of this exercise is to learn how to deal with Categorical variables using the Ordinal Encoder.

In that case, we want the model to consider that: **good > neutral > bad**

```python
X_train = [['good'], ['bad'], ['neutral']]
```

1. Fit the `OrdinalEncoder` by specifying the categories in the following order: `categories=[['bad', 'neutral', 'good']]`. Transform the train set. Print the `categories_`

2. Transform the X_test using the fitted Ordinal Encoder on train set.

```python
X_test = [['good'], ['good'], ['bad']]
```

*Note: In the version 0.22 of Scikit-learn, the Ordinal Encoder doesn't handle new values in the test set. But it will be possible in the version 0.24 !*