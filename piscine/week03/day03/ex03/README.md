# Exercise 3 Multi classification - Softmax

The goal of this exercise is to learn to a neural network architecture for multi-class data. This is an important type of problem on which to practice with neural networks because the three class values require specialized handling. A multi-classification neural network uses as output layer a **softmax** layer. The **softmax** activation function is an extension of the sigmoid as it is designed to output the probabilities to belong to each class in a multi-class problem. This output layer has to contain as much neurons as classes in the multi-classification problem. This article explains in detail how it works. https://developers.google.com/machine-learning/crash-course/multi-class-neural-networks/softmax

Let us assume we want to classify images and we know they contain either apples, bears, candies, eggs or dogs (extension of the example in the link above). 

1. Create the architecture for a multi-class neural network with the following architecture and return `print(model.summary())`: 

    - 5 inputs variables
    - hidden layer 1: 16 neurons and sigmoid as activation function
    - hidden layer 2: 8 neurons and sigmoid as activation function
    - output layer: The number of neurons and the activation function should be adapted to this multi-classification problem. 