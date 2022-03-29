# Exercise 1 Regression - Optimize 

The goal of this exercise is to learn to set up the optimization for a regression neural network. There's no code to run in that exercise. In W2D2E3, we implemented a neural network designed for regression. We will be using this neural network: 

    ```
    model = keras.Sequential()
    model.add(Dense(8, input_shape=(5,), activation= 'sigmoid'))
    model.add(Dense(4, activation= 'sigmoid'))
    model.add(Dense(1, activation= 'linear'))

    ```
As a reminder, the main difference between a regression and classification neural network's architecture is the output layer activation function.

1. Fill this chunk of code to set up the optimization part of the regression neural network: 

```
model.compile(
  optimizer='adam',
  loss='',#TODO1
  metrics=[''] #TODO2
)
```
Hint: 
- Mean Squared Error (MSE) and Mean Absolute Error (MAE) are common loss functions used for regression problems. Mean Absolute Error is less sensitive to outliers. Different loss functions are used for classification problems. Similarly, evaluation metrics used for regression differ from classification. 

https://keras.io/api/metrics/regression_metrics/