# Exercise 3 One hot Encoder

The goal of this exercise is to learn how to deal with Categorical variables using the OneHot Encoder.

```python
X_train = [['Python'], ['Java'], ['Java'], ['C++']]
```

1. Using `OneHotEncoder` with `handle_unknown='ignore'`, fit the One Hot Encoder and transform X_train. The expected output is:

    |    |   ('C++',) |   ('Java',) |   ('Python',) |
    |---:|-----------:|------------:|--------------:|
    |  0 |          0 |           0 |             1 |
    |  1 |          0 |           1 |             0 |
    |  2 |          0 |           1 |             0 |
    |  3 |          1 |           0 |             0 |

    To get this output create a DataFrame from the transformed X_train and the attribute `categories_`.

2. Transform X_test using the fitted One Hot Encoder on the train set.

```python
X_test = [['Python'], ['Java'], ['C'], ['C++']]
```

The expected output is:

    |    |   ('C++',) |   ('Java',) |   ('Python',) |
    |---:|-----------:|------------:|--------------:|
    |  0 |          0 |           0 |             1 |
    |  1 |          0 |           1 |             0 |
    |  2 |          0 |           0 |             0 |
    |  3 |          1 |           0 |             0 |

- https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html
