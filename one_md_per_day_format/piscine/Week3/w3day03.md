# D02  Piscine AI - Data Science 


# Table of Contents:


# Introduction
Keras backend TF
The goal of this day is to learn to use Keras to build Neural Networks and train them on small data sets. 

classification & regression 

'2.4.3'

## Historical



## Rules

The correction will provide the code and output because it is not straightforward to reproduce results using Keras. There are many source of randomness. Even if all the seeds are fixed to a constant they may be other source of randomness. https://machinelearningmastery.com/reproducible-results-neural-networks-keras/
A developper
## Ressources 
https://machinelearningmastery.com/tutorial-first-neural-network-python-keras/


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

## Correction: 

1. This question is validated if the chunk of code is: 

```
model.compile(
  optimizer='adam',
  loss='mse',
  metrics=['mse'] 
)
```
All regression metrics or losses used are correct. As explained before, the loss functions are chosen thanks to nice mathematical properties. That is why most of the time the loss function used for regression is the MSE or MAE. 

https://keras.io/api/losses/regression_losses/
https://keras.io/api/metrics/regression_metrics/


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



## Correction 

1. This question is validated if the input DataFrames are: 

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

2. This question is validated if the mean absolute error on the test set is smaller than 10. Here is an architecture that works: 

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

# Exercise 3 Multi classification - Softmax

The goal of this exercise is to learn to a neural network architecture for multi-class data. This is an important type of problem on which to practice with neural networks because the three class values require specialized handling. A multi-classification neural network uses as output layer a **softmax** layer. The **softmax** activation function is an extension of the sigmoid as it is designed to output the probabilities to belong to each class in a multi-class problem. This output layer has to contain as much neurons as classes in the multi-classification problem. This article explains in detail how it works. https://developers.google.com/machine-learning/crash-course/multi-class-neural-networks/softmax

Let us assume we want to classify images and we know they contain either apples, bears, candies, eggs or dogs (extension of the example in the link above). 

1. Create the architecture for a multi-class neural network with the following architecture and return `print(model.summary())`: 

    - 5 inputs variables
    - hidden layer 1: 16 neurons and sigmoid as activation function
    - hidden layer 2: 8 neurons and sigmoid as activation function
    - output layer: The number of neurons and the activation function should be adapted to this multi-classification problem. 


## Correction 

1. This question is validated if the code that creates the neural network is: 

    ```
    model = keras.Sequential()
    model.add(Dense(16, input_shape=(5,), activation= 'sigmoid'))
    model.add(Dense(8, activation= 'sigmoid'))
    model.add(Dense(5, activation= 'softmax'))

    ```
# Exercise 4 Multi classification - Optimize 

The goal of this exercise is to learn to optimize a multi-classification neural network. As learnt previously, the loss function used in binary classification is the log loss - also called in Keras `binary_crossentropy`. This function is defined for binary classification and can be extended to multi-classfication. In Keras, the extended loss that supports multi-classification is `binary_crossentropy`. There's no code to run in that exercise.

1. Fill the chunk of code below in order to optimize the neural network defined in the previous exercise. Choose the adapted loss, adam as optimizer and the accuracy as metric.

```
model.compile(loss='',#TODO1
              optimizer='', #TODO2
              metrics=['']) #TODO3
```
## Correction 

1. This question is validated if the chunk of code is:

```
model.compile(loss='categorical_crossentropy',
              optimizer='adam',
              metrics=['accuracy'])
```

# Exercise 5 Multi classification example

The goal of this exercise is to learn to use a neural network to classify a multiclass data set. The data set used is the Iris data set which allows to classify flower given basic features as flower's measurement. 

Preliminary: 
    - Split train test. Keep 20% for the test set. Use `random_state=1`. 
    - Scale the data using Standard Scaler


1. Use the `LabelBinarizer` from Sckit-learn to create a one hot encoding of the target. As you know, the output layer of a multi-classification neural network shape is equal to the number of classes. The output layer expects to have a target with the same shape as its output layer.  

2. Train a neural network on the train set and predict on the test set. The neural network should have 1 hidden layers. The expected **accuracy** on the test set is minimum 90%.
*Hint*: inscrease the number of epochs 
**Warning**: Do no forget to evaluate the neural network on the **SCALED** test set. 


## Correction 

1. This question is validated if the output of the first ten values of the train labels are: 

```
array([[0, 1, 0],
       [0, 0, 1],
       [0, 1, 0],
       [0, 0, 1],
       [0, 0, 1],
       [1, 0, 0],
       [0, 1, 0],
       [1, 0, 0],
       [0, 1, 0],
       [0, 0, 1]])
```

2. This question is validated if the accuracy on the test set is bigger than 90%. To evaluate the accuracy on the test set you can use: `model.evaluate(X_test_sc, y_test_multi_class)`.

Here is an implementation that gives 96% accuracy on the test set. 

```
model = Sequential()
model.add(Dense(10, input_dim=4, activation='sigmoid'))
model.add(Dense(3, activation='softmax'))
# Compile model
model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
model.fit(X_train_sc, y_train_multi_class, epochs = 1000, batch_size=20)
```

