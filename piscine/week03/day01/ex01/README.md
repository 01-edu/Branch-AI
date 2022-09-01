# Exercise 1 The neuron 

The goal of this exercise is to understand the role of a neuron and to implement a neuron. 

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

    def feedforward(cls, x1, x2):
        #TODO
        return y


    ```

Note: if you are confortable with matrix multiplication, feel free to vectorize the operations as done in the article. 

https://victorzhou.com/blog/intro-to-neural-networks/
