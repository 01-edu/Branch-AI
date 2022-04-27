##### The exercice is validated is all questions of the exercice are validated

##### This question is validated if the text file has successfully been loaded in a NumPy array with
 `genfromtxt('winequality-red.csv', delimiter=',')` and the reduced arrays weights **76800 bytes**

##### This question is validated if the output is

 ```python
 array([[ 7.4   ,  0.7   ,  0.    ,  1.9   ,  0.076 , 11.    , 34.    ,
         0.9978,  3.51  ,  0.56  ,  9.4   ,  5.    ],
       [ 7.4   ,  0.66  ,  0.    ,  1.8   ,  0.075 , 13.    , 40.    ,
         0.9978,  3.51  ,  0.56  ,  9.4   ,  5.    ],
       [ 6.7   ,  0.58  ,  0.08  ,  1.8   ,  0.097 , 15.    , 65.    ,
         0.9959,  3.28  ,  0.54  ,  9.2   ,  5.    ]])
 ```

This slicing gives the answer `my_data[[1,6,11],:]`.

##### This question is validated if the answer if False. There many ways to get the answer: find the maximum or check values greater than 20.

##### This question is validated if the answer is 10.422983114446529.

##### This question is validated if the answers is:

    ```console
    pH stats
    25 percentile:  3.21
    50 percentile:  3.31
    75 percentile:  3.4
    mean:  3.3111131957473416
    min:  2.74
    max:  4.01
    ```

    > *Note: Using `percentile` or `median` may give different results depending on the duplicate values in the column. If you do not have my results please use `percentile`.*

##### This question is validated if the answer is ~`5.2`. The first step is to get the percentile 20% of the column `sulphates`, then create a boolean array that contains `True` of the value is smaller than the percentile 20%, then select this rows with the column quality and compute the `mean`.

##### This question is validated if the output for the best wines is:

```python
array([ 8.56666667,  0.42333333,  0.39111111,  2.57777778,  0.06844444,
    13.27777778, 33.44444444,  0.99521222,  3.26722222,  0.76777778,
    12.09444444,  8.        ])
```

##### This question is validated if the output for the bad wines is:

```python
array([ 8.36    ,  0.8845  ,  0.171   ,  2.635   ,  0.1225  , 11.      ,
    24.9     ,  0.997464,  3.398   ,  0.57    ,  9.955   ,  3.      ])
```

This can be done in three steps: Get the max, create a boolean mask that indicates rows with max quality, use this mask to subset the rows with the best quality and compute the mean on the axis 0.
