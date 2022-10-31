##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the number of unique values per feature outputted are:

```console
age             6
menopause       3
tumor-size     11
inv-nodes       6
node-caps       2
deg-malig       3
breast          2
breast-quad     5
irradiat        2
dtype: int64
```

##### The question 2 is validated if the transformed test set by the `OneHotEncoder` fitted on the train set is as below. Make sure the transformer takes as input a dataframe with the columns in the order defined `['node-caps' , 'breast', 'breast-quad', 'irradiat']` :

```console
#First 10 rows: 

array([[1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 1., 0., 0., 0., 0., 1., 0., 1., 0.],
       [1., 0., 0., 1., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0.],
       [1., 0., 0., 1., 0., 0., 1., 0., 0., 1., 0.],
       [1., 0., 0., 1., 0., 0., 1., 0., 0., 1., 0.],
       [1., 0., 0., 1., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 0., 1., 0., 0., 1., 0., 0., 1., 0.],
       [0., 1., 1., 0., 0., 0., 1., 0., 0., 0., 1.]])

```

##### The question 3 is validated if the transformed test set by the `OrdinalEncoder` fitted on the train set is as below with the columns ordered as `["menopause", "age", "tumor-size","inv-nodes", "deg-malig"]`:

```console
#First 10 rows: 

array([[1., 2., 5., 0., 1.],
   [1., 3., 4., 0., 1.],
   [1., 2., 4., 0., 1.],
   [1., 3., 2., 0., 1.],
   [1., 4., 3., 0., 1.],
   [1., 4., 5., 0., 0.],
   [2., 5., 4., 0., 1.],
   [2., 5., 8., 0., 1.],
   [0., 2., 3., 0., 2.],
   [1., 3., 6., 4., 2.]])

```

##### The question 4 is validated if the column transformer transformed that is fitted on the X_train, transformed the X_test as:

```console
# First 2 rows: 

array([[1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 2., 5., 0., 1.],
       [1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 3., 4., 0., 1.]])
```
