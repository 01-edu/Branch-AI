# W1D1  Piscine AI - Data Science 


# Table of Contents:

Reproduire cet article sans back prop 
https://towardsdatascience.com/machine-learning-for-beginners-an-introduction-to-neural-networks-d49f22d238f9

# Introduction

Deep learning is a huge domain. We will focus on Artificial Neural Networks. The goal is to understand how do the neural networks train and train them on data. Understand the challenges of training a neural network
Architectures as RNN, LSTM (learn sequences, used in TS and NLP),CNN used a lot in image processing are well know algorithms in deep learning but won't be covered by the AI branch. Once you have a good understanding of ANN feel free to extend your knowledge to new architectures. 


## Rules

## Ressources 
https://victorzhou.com/blog/intro-to-neural-networks/


https://srnghn.medium.com/deep-learning-overview-of-neurons-and-activation-functions-1d98286cf1e4#:~:text=What%20is%20a%20neuron%3F,to%20become%20the%20neuron's%20output.

Reproduire cet article sans back prop 
https://towardsdatascience.com/machine-learning-for-beginners-an-introduction-to-neural-networks-d49f22d238f9

# Exercice 1 The neuron 

The goal of this exercice is to understand the role of a neuron and to implement a neuron. 

An artificial neuron, the basic unit of the neural network, (also referred to as a perceptron) is a mathematical function. It takes one or more inputs that are multiplied by values called “weights” and added together. This value is then passed to a non-linear function, known as an activation function, to become the neuron’s output.

As desbribed in the article, **a neuron takes inputs, does some math with them, and produces one output**.

Let us assume there are 2 inputs. Here are the three steps involved in the neuron: 

1. Each input is multiplied by a weight
    - x1 -> x1 * w1
    - x2 -> x2 * w2
2. The weighted inputs are added together with a biais b
    - (x1 * w1) + (x2 * w2) + b
3. The sum is passed through an activation function
    - y = f((x1 * w1) + (x2 * w2) + b)

    - The activation function is a function you know from W2DAY2 (Logistic Regression): **the sigmoid**

Example: 

x1 = 2 , x2 = 3 , w1 = 0, w2= 1, b = 4

1. Step 1: Multiply by a weight
    - x1 -> 2 * 0 = 0 
    - x2 -> 3 * 1 = 3 
2. Step 2: Add weigthed inputs and bias
    - 0 + 3 + 4 = 7 
3. Step 3: Activation function
    - y = f(7) = 0.999
---
1. Implement a the function feedforward of the class `Neuron` that takes as input the inputs (x1, x2) and that uses the attributes: the weights and the biais to return y: 


    ```
    class Neuron:
    def __init__(self, weight1, weight2, bias):
        self.weights_1 = weight1
        self.weights_2 = weight2
        self.bias = bias

    def feedforward(self, x1, x2):
        #TODO
        return y


    ```

Note: if you are confortable with matrix multiplication, feel free to vectorize the operations as done in the article. 

https://victorzhou.com/blog/intro-to-neural-networks/


## Correction: 

1. This question is validated if this code:

    ```
    neuron = Neuron(0,1,4)
    neuron.feedforward(2,3)
    ```

 returns **0.9990889488055994**.


# Exerice 2 Neural network

The goal of this exercice is to understand how to combine three neurons to form a neural network. A neural newtwork is nothing else than neurons connected together. As shown in the figure the neural network is composed of **layers**:

  - Input layer: it only represents input data. **It doesn't contain neurons**.
  - Output layer: it represents the last layer. It contains a neuron (in some cases more than 1).
  - Hidden layer: any layer between the input (first) layer and output (last) layer. Many hidden layers can be stacked. When there are many hidden layers, the neural networks is deep.

Notice that the neuron **o1** in the output layer takes as input the output of the neurons **h1** and **h2** in the hidden layer. 

In exercice 1, you implemented this neuron.
![alt text][neuron]

[neuron]: images/day1/ex2/w3_day1_neuron.png "Plot"

Now, we add two more neurons: 

- h2, the second neuron of the hidden layer
- o1, the neuron of the output layer


![alt text][nn]

[nn]: images/day1/ex2/w3_day1_neural_network.png "Plot"

1. Implement the function `feedforward` of the class `OurNeuralNetwork` that takes as input the input data and returns the output y. Return the output for these neurons:

    ```
    neuron_h1 = Neuron(1,2,-1)
    neuron_h2 = Neuron(0.5,1,0)
    neuron_o1 = Neuron(2,0,1)
    ```

    ```
    class OurNeuralNetwork:
        
        def __init__(self, neuron_h1, neuron_h2, neuron_o1):
            self.h1 = neuron_h1
            self.h2 = neuron_h2
            self.o1 = neuron_o1

        def feedforward(self, x1, x2):
        # The inputs for o1 are the outputs from h1 and h2
        # TODO
            return y

    ```



## Correction 

1. This question is validated the output is: **0.9524917424084265**

# Exercice 3 Log loss

The goal of this exercice is to implement the Log loss function. As mentioned last week, this function is used in classification as a **loss function**. It means that the better the classifier is, the smaller the loss function is. W2D1, you implemented the gradient descent on the MSE loss to update the weights of the linear regression. Similarly, the minimization of the Log loss leads to finding optimal weights. 

Log loss: - 1/n * Sum[(y_true*log(y_pred) + (1-y_true)*log(1-y_pred))]

1. Create a function `log_loss_custom` and compute the loss for the data below: 

    ```
    y_true = np.array([0,1,1,0,1])
    y_pred = np.array([0.1,0.8,0.6, 0.5, 0.3])
    ```
    Check that `log_loss` from `sklearn.metrics` returns the same result
https://scikit-learn.org/stable/modules/generated/sklearn.metrics.log_loss.html

## Correction 

1. This question is validated if the output is: **0.5472899351247816**.


# Exercice 4 Forward propagation
The goal of this exerice is to compute the log loss on the output of the forward propagation. The data used is the tiny data set below. 


| name   |   math |   chemistry |   exam_success |
|:-------|-------:|------------:|---------------:|
| Bob    |     12 |          15 |              1 |
| Eli    |     10 |           9 |              0 |
| Tom    |     18 |          18 |              1 |
| Ryan   |     13 |          14 |              1 |


The goal if the network is to predict the success at the exam given math and chemistry grades. The inputs are `math` and `chemistry` and the target is `exam_sucess`.

1. Compute and return the output of the neural network for each of the students. Here are the weights and biases of the neural network: 

    ```
    neuron_h1 = Neuron(0.05, 0.001, 0)
    neuron_h2 = Neuron(0.02, 0.003, 0)
    neuron_o1 = Neuron(2,0,0)
    ```
2. Compute the logloss for the data given the output of the neural network with the 4 students. 

## Correction 

1. This question is validated if the output is: 
    ```
    Bob: 0.7855253278357536
    Eli: 0.7771516558846259
    Tom: 0.8067873659804015
    Ryan: 0.7892343955586032
    ```
2. This question is validated if the logloss for the 4 students is **0.5485133607757963**.


# Exercice 5 Regression 

The goal of this exercice is to learn to adapt the output layer to regression. 
As a reminder, one of reasons for which the sigmoid is used in classification is because it contracts the output between 0 and 1 which is the expected output range for a probability (W2D2: Logistic regression). However, the output of the regression is not a probability. 

In order to perform a regression using a neural network, the activation function of the neuron on the output layer has to be modified to **identity function**. In mathematics, the identity function is: **f(x) = x**. In other words it means that it returns the input as so. The three steps become: 


1. Each input is multiplied by a weight
    - x1 -> x1 * w1
    - x2 -> x2 * w2
2. The weighted inputs are added together with a biais b
    - (x1 * w1) + (x2 * w2) + b
3. The sum is passed through an activation function
    - y = f((x1 * w1) + (x2 * w2) + b)
    - The activation function is **the identity**
    - y = (x1 * w1) + (x2 * w2) + b

All other neurons' activation function **doesn't change**.

1. Adapt the neuron class implemented in exercice 1. It now takes as a parameter `regression` which is boolean. When its value is `True`, `feedforward` should use the identity function as activation function instead of the sigmoid function. 


    ```
    class Neuron:
    def __init__(self, weight1, weight2, bias, regression):
        self.weights_1 = weight1
        self.weights_2 = weight2
        self.bias = bias
        #TODO

    def feedforward(self, x1, x2):
        #TODO
        return y

    ```

    - Compute the output for:

        ```
        neuron = Neuron(0,1,4, True)
        neuron.feedforward(2,3)
        ```


2. Now, the goal of the network is to predict the physics' grade at the exam given math and chemistry grades. The inputs are `math` and `chemistry` and the target is `physics`.

| name   |   math |   chemistry |   physics |
|:-------|-------:|------------:|---------------:|
| Bob    |     12 |          15 |              16 |
| Eli    |     10 |           9 |              10 |
| Tom    |     18 |          18 |              19 |
| Ryan   |     13 |          14 |              16 |


Compute and return the output of the neural network for each of the students. Here are the weights and biases of the neural network: 

    ```
    #replace regression by the right value
    neuron_h1 = Neuron(0.05, 0.001, 0, regression)
    neuron_h2 = Neuron(0.002, 0.003, 0, regression)
    neuron_o1 = Neuron(2,7,10, regression)
    ```
3. Compute the MSE for the 4 students. 

## Correction 

1. This question is validated if the output is **7**.

2. This question is validated if the outputs are:

    ```
    Bob: 14.918863163724454
    Eli: 14.83137890625537
    Tom: 15.086662606964074
    Ryan: 14.939270885974128
    ```

3. This question is validated if the MSE is **10.237608699909138**

