# Exercise 5 Regression 

The goal of this exercise is to learn to adapt the output layer to regression. 
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

1. Adapt the neuron class implemented in exercise 1. It now takes as a parameter `regression` which is boolean. When its value is `True`, `feedforward` should use the identity function as activation function instead of the sigmoid function. 


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