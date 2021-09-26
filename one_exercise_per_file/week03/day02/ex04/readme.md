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