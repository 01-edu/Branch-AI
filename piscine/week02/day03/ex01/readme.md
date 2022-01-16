# Exercise 1 Imputer 1

The goal of this exercise is to learn how to use an Imputer to fill missing values on basic example.

```python
train_data = [[7, 6, 5], 
              [4, np.nan, 5], 
              [1, 20, 8]]
```

1. Fit the `SimpleImputer` on the data. Print the `statistics_`. Check that the statistics match `np.nanmean(train_data, axis=0)`.

2. Fill the missing values in `train_data` using the fitted imputer and `transform`.

3. Fill the missing values in `test_data` using the fitted imputer and `transform`.

```python
test_data = [[np.nan, 1, 2], 
             [7, np.nan, 9], 
             [np.nan, 2, 4]]
```