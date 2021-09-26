# W3D2  Piscine AI - Data Science 


# Table of Contents:


# Introduction
Keras backend TF
The goal of this day is to learn to use Keras to build Neural Networks. 

There are two ways to build Keras models: sequential and functional.

The sequential API allows you to create models layer-by-layer for most problems. It is limited in that it does not allow you to create models that share layers or have multiple inputs or outputs. The exercises focuses on the usage of the sequential API. 

'2.4.3'

## Historical



## Rules

The correction will provide the code and output because it is not straightforward to reproduce results using Keras. There are many source of randomness. Even if all the seeds are fixed to a constant they may be other source of randomness. https://machinelearningmastery.com/reproducible-results-neural-networks-keras/
A developper
## Ressources 
https://machinelearningmastery.com/tutorial-first-neural-network-python-keras/

# Exercise 1 Sequential

The goal of this exercise is to learn to call the object `Sequential`. 

1. Put the object Sequential in a variable named `model` and print the variable `model`.

## Correction 

1. This question is validated if the output is: `<tensorflow.python.keras.engine.sequential.Sequential object at  xxx`





# Exercise 2 Dense

The goal of this exercise is to learn to create layers of neurons. Keras proposes options to create custom layers. The neural networks build in these exercises do not require custom layers. `Dense` layers do the job. A dense layer is simply a layer where each unit or neuron is connected to each neuron in the next layer. As seen yesterday, there are three main types of layers: input, hidden and output. The **input layer** that specifies the number of inputs (features) is not represented as a layer in Keras. However, `Dense` has a parameter `input_dim` that gives the number of inputs in the previous layer. The output layer as any hidden layer can be created using `Dense`, the only difference is that the output layer contains one single neuron. 

1. Create a `Dense` layer with these parameters and return the output of `get_config`: 

    - First hidden layer connected to 5 input variables. 
    - 8 neurons 
    - sigmoid as activation function 


2. Create a `Dense` layer with these parameters and return the output of `get_config`: 

    - Hidden layer (not the first one)
    - 4 neurons 
    - sigmoid as activation function 

3. Create a `Dense` layer with these parameters and return the output of `get_config`: 

    - Output layer
    - 1 neuron 
    - sigmoid as activation function 

## Correction 

1. This question is validated if the fields`batch_input_shape`,`units` and `activation` match this output: 

    ```
    {'name': 'dense_7',
    'trainable': True,
    'batch_input_shape': (None, 5),
    'dtype': 'float32',
    'units': 8,
    'activation': 'sigmoid',
    'use_bias': True,
    'kernel_initializer': {'class_name': 'GlorotUniform',
    'config': {'seed': None}},
    'bias_initializer': {'class_name': 'Zeros', 'config': {}},
    'kernel_regularizer': None,
    'bias_regularizer': None,
    'activity_regularizer': None,
    'kernel_constraint': None,
    'bias_constraint': None}
    ```

2. This question is validated if the fields`units` and `activation` match this output: 

    ```
    {'name': 'dense_8',
    'trainable': True,
    'dtype': 'float32',
    'units': 4,
    'activation': 'sigmoid',
    'use_bias': True,
    'kernel_initializer': {'class_name': 'GlorotUniform',
    'config': {'seed': None}},
    'bias_initializer': {'class_name': 'Zeros', 'config': {}},
    'kernel_regularizer': None,
    'bias_regularizer': None,
    'activity_regularizer': None,
    'kernel_constraint': None,
    'bias_constraint': None}
    ```
3. This question is validated if the fields`units` and `activation` match this output: 

    ```
    {'name': 'dense_9',
    'trainable': True,
    'dtype': 'float32',
    'units': 1,
    'activation': 'sigmoid',
    'use_bias': True,
    'kernel_initializer': {'class_name': 'GlorotUniform',
    'config': {'seed': None}},
    'bias_initializer': {'class_name': 'Zeros', 'config': {}},
    'kernel_regularizer': None,
    'bias_regularizer': None,
    'activity_regularizer': None,
    'kernel_constraint': None,
    'bias_constraint': None}
    ```

# Exercise 3 Architecture

The goal of this exercise is to combine the layers and to create a neural network. 

1. Create a neural network for regression with the following architecture and return `print(model.summary())`: 

    - 5 inputs variables
    - hidden layer 1: 8 neurons and sigmoid as activation function
    - hidden layer 2: 4 neurons and sigmoid as activation function
    - output layer: 1 neuron. Find the adapted activation function

## Correction 

1. This question is validated if the code that creates the neural network is: 

    ```
    model = keras.Sequential()
    model.add(Dense(8, input_shape=(5,), activation= 'sigmoid'))
    model.add(Dense(4, activation= 'sigmoid'))
    model.add(Dense(1, activation= 'linear'))

    ```

The first two layers could use another activation function that sigmoid (eg: relu)
# Exercise 4 Optimize

The goal of this exercise is to learn to train the neural network. Once the architecture of the neural network is set there are two steps to train the neural network: 

- `compile`:  The compilation step aims to set the loss function, to choose the algoithm to minimize the chosen loss function and to choose the metric the model outputs.

  - The **optimizer**. We’ll stick with a pretty good default: the Adam gradient-based optimizer. Keras has many other optimizers you can look into as well.
  - The **loss function**. Depending on the problem to solve: classification or regression Keras proposes different loss functions. In classification Keras distinguishes between `binary_crossentropy` (2 classes) and `categorical_crossentropy` (>2 classes), so we’ll use the latter. 
  - The **metric(s)**. A list of metrics. Depending on the problem to solve: classification or regression Keras proposes different loss functions. For example for classification the metric can be the accuracy. 


- `fit`: Training a model in Keras literally consists only of calling fit() and specifying some parameters. There are a lot of possible parameters, but we’ll only manually supply a few:
  - The **training data**, commonly known as X and Y, respectively.
  - The **number of epochs** (iterations over the entire dataset) to train for.   
  - The **batch size** (number of samples per gradient update) to use when training.

  This article gives more details about **epoch** and **batch size**: https://machinelearningmastery.com/difference-between-a-batch-and-an-epoch/

1. Create the following neural network (classification): 
    - Set the right number of inputs variables
    - hidden layer 1: 10 neurons and sigmoid as activation function.
    - hidden layer 2: 5 neurons and sigmoid as activation function.
    - output layer: 1 neuron and sigmoid as activation function.
    - Choose the accuracy metric, the adam optimizer, the adapted loss and epoch smaller than 50. 

    Import the breast cancer data set from `sklearn.datasets` using `load_breast_cancer` and train the neural network on the data set.  

2. Scale the data using `StandardScaler` from `sklearn.preprocessing`. Train the neural network again. 

## Correction

1. This question is validated if the output of `model.get_config()['layers']` matches the fields `batch_input_shape`, `units` and `activation`.

```
[{'class_name': 'InputLayer',
  'config': {'batch_input_shape': (None, 30),
   'dtype': 'float32',
   'sparse': False,
   'ragged': False,
   'name': 'dense_134_input'}},
 {'class_name': 'Dense',
  'config': {'name': 'dense_134',
   'trainable': True,
   'batch_input_shape': (None, 30),
   'dtype': 'float32',
   'units': 10,
   'activation': 'sigmoid',
   'use_bias': True,
   'kernel_initializer': {'class_name': 'GlorotUniform',
    'config': {'seed': None}},
   'bias_initializer': {'class_name': 'Zeros', 'config': {}},
   'kernel_regularizer': None,
   'bias_regularizer': None,
   'activity_regularizer': None,
   'kernel_constraint': None,
   'bias_constraint': None}},
 {'class_name': 'Dense',
  'config': {'name': 'dense_135',
   'trainable': True,
   'dtype': 'float32',
   'units': 5,
   'activation': 'sigmoid',
   'use_bias': True,
   'kernel_initializer': {'class_name': 'GlorotUniform',
    'config': {'seed': None}},
   'bias_initializer': {'class_name': 'Zeros', 'config': {}},
   'kernel_regularizer': None,
   'bias_regularizer': None,
   'activity_regularizer': None,
   'kernel_constraint': None,
   'bias_constraint': None}},
 {'class_name': 'Dense',
  'config': {'name': 'dense_136',
   'trainable': True,
   'dtype': 'float32',
   'units': 1,
   'activation': 'sigmoid',
   'use_bias': True,
   'kernel_initializer': {'class_name': 'GlorotUniform',
    'config': {'seed': None}},
   'bias_initializer': {'class_name': 'Zeros', 'config': {}},
   'kernel_regularizer': None,
   'bias_regularizer': None,
   'activity_regularizer': None,
   'kernel_constraint': None,
   'bias_constraint': None}}]
```
You should notice that the neural network is struggling to learn. By luck the initialization of the weights might have led to an accuracy close of 90%. But when I trained the neural network, with `batch_size=300` on the data here is the ouptput of the last epoch (50):

`Epoch 50/50
2/2 [==============================] - 0s 1ms/step - loss: 0.6559 - accuracy: 0.6274`

2. This solution is validated if the the accuracy at epoch 50 is higher than 95%.