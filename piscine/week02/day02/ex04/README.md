
# Exercise 4: Train test split

The goal of this exercise is to learn to split a classification data set. The idea is the same as splitting a regression data set but there's one important detail specific to the classification: the proportion of each class in the train set and test set.  

```python
   X = np.arange(1,21).reshape(10,-1)
   y = np.zeros(10)
   y[7:] = 1
```

1. Split the data using `train_test_split` with `shuffle=False`. The test set represents 20% of the total size of the data set. Print X_train, y_train, X_test, y_test. Compute the proportion of class `1` on the train set and test set.

2. Having a train set with different properties than the test set is not recommended. The analogy of the exam (https://www.youtube.com/watch?v=_vdMKioCXqQ) helps to understand this point: if the questions you have at the exam are completely different from what you prepared for you are not evaluated on what you learn. The training set has to be representative of the data set. Now, split the data in a train set and test set, but keep the proportion of class `1` nearly constant. The parameter `shuffle` in theory works as it relies on a random sampling. The parameter `stratify` will always split the data and keep the same proportion of class `1` in the train set and test set. Using the parameter `stratify` split the data below and print the proportion of class `1` in the train set and train set.

```python
X = np.arange(1,201).reshape(100,-1)
y = np.zeros(100)
y[70:] = 1
```