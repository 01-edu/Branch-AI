##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the input DataFrames are: 

X_train_scaled shape is (313, 5) and the first 5 rows are:

|    |   cylinders |   displacement |   horsepower |   weight |   acceleration |
|---:|------------:|---------------:|-------------:|---------:|---------------:|
|  0 |     1.28377 |       0.884666 |     0.48697  | 0.455708 |       -1.19481 |
|  1 |     1.28377 |       1.28127  |     1.36238  | 0.670459 |       -1.37737 |
|  2 |     1.28377 |       0.986124 |     0.987205 | 0.378443 |       -1.55992 |
|  3 |     1.28377 |       0.856996 |     0.987205 | 0.375034 |       -1.19481 |
|  4 |     1.28377 |       0.838549 |     0.737087 | 0.393214 |       -1.74247 |

The train target is: 

|    |   mpg |
|---:|------:|
|  0 |    18 |
|  1 |    15 |
|  2 |    18 |
|  3 |    16 |
|  4 |    17 |


X_test_scaled shape is (79, 5) and the first 5 rows are:

|     |   cylinders |   displacement |   horsepower |    weight |   acceleration |
|----:|------------:|---------------:|-------------:|----------:|---------------:|
| 315 |   -1.00255  |      -0.554185 |    -0.5135   | -0.113552 |      1.76253   |
| 316 |    0.140612 |       0.128347 |    -0.5135   |  0.31595  |      1.25139   |
| 317 |   -1.00255  |      -1.05225  |    -0.813641 | -1.03959  |      0.192584  |
| 318 |   -1.00255  |      -0.710983 |    -0.5135   | -0.445337 |      0.0830525 |
| 319 |   -1.00255  |      -0.840111 |    -0.888676 | -0.637363 |      0.813262  |

The test target is: 

|     |   mpg |
|----:|------:|
| 315 |  24.3 |
| 316 |  19.1 |
| 317 |  34.3 |
| 318 |  29.8 |
| 319 |  31.3 |

##### The question 2 is validated if the mean absolute error on the test set is smaller than 10. Here is an architecture that works: 

```
# create model
model = Sequential()
model.add(Dense(30, input_dim=5, activation='sigmoid'))
model.add(Dense(30, activation='sigmoid'))
model.add(Dense(1))
# Compile model
model.compile(loss='mean_squared_error',
                optimizer='adam', metrics='mean_absolute_error')
```

The output neuron has to be `Dense(1)` - by defaut the activation funtion is linear. The loss has to be **mean_squared_error** and the **input_dim** has to be **5**. All variations on the others parameters are accepted. 

*Hint*: To get the score on the test set, `evaluate` could have been used: `model.evaluate(X_test_scaled, y_test)`. 