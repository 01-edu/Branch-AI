# Exercise 2 Regression example

The goal of this exercise is to learn to train a neural network to perform a regression on a data set.
The data set is Auto MPG Dataset and the go is to build a model to predict the fuel efficiency of late-1970s and early 1980s automobiles. To do this, provide the model with a description of many automobiles from that time period. This description includes attributes like: cylinders, displacement, horsepower, and weight.

https://www.tensorflow.org/tutorials/keras/regression


1. Preprocess the data set as follow:
    - Drop the columns: **model year**, **origin**, **car name**
    - Split train test without shuffling the data. Keep 20% for the test set.
    - Scale the data using Standard Scaler


2. Train a neural network on the train set and predict on the test set. The neural network should have 2 hidden layers and the loss should be **mean_squared_error**. The expected **mean absolute error** on the test set is maximum 10.
*Hint*: inscrease the number of epochs 
**Warning**: Do no forget to evaluate the neural network on the **SCALED** test set. 