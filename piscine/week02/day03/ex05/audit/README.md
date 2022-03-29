##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the number of unique values per feature outputted are:

```console
age             3
menopause      11
tumor-size      7
inv-nodes       2
node-caps       3
deg-malig       2
breast          5
breast-quad     2
irradiat        2
dtype: int64
```

##### The question 2 is validated if the transformed test set by the `OneHotEncoder` fitted on the train set is:

    ```console
    First 10 rows: 

    array([[1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0.],
        [1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0.],
        [0., 1., 1., 0., 0., 1., 0., 0., 0., 0., 1., 0., 1.],
        [0., 1., 1., 0., 0., 1., 0., 0., 0., 0., 1., 1., 0.],
        [1., 0., 1., 0., 0., 0., 1., 0., 0., 1., 0., 0., 1.],
        [1., 0., 1., 0., 0., 0., 0., 1., 0., 1., 0., 1., 0.],
        [1., 0., 0., 1., 0., 0., 0., 0., 1., 1., 0., 1., 0.],
        [1., 0., 0., 1., 0., 1., 0., 0., 0., 1., 0., 1., 0.],
        [1., 0., 1., 0., 0., 0., 0., 1., 0., 0., 1., 0., 1.],
        [1., 0., 0., 1., 0., 1., 0., 0., 0., 1., 0., 0., 1.]])
    ```

##### The question 3 is validated if the transformed test set by the `OrdinalEncoder` fitted on the train set is:

    ```console
    First 10 rows: 

    array([[2., 2., 0., 1.],
        [2., 2., 0., 0.],
        [2., 4., 5., 2.],
        [1., 5., 1., 1.],
        [2., 5., 0., 2.],
        [1., 1., 0., 1.],
        [1., 8., 0., 1.],
        [2., 2., 0., 0.],
        [2., 5., 0., 2.],
        [1., 3., 0., 0.]])
    ```

##### The question 3 is validated if the column transformer transformed that is fitted on the X_train, transformed the X_test as:

```console
# First 2 rows: 

array([[1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0., 2., 2., 0.,
        1.],
       [1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0., 2., 2., 0.,
        0.]])
```