# Exerice 2 Neural network

The goal of this exercise is to understand how to combine three neurons to form a neural network. A neural newtwork is nothing else than neurons connected together. As shown in the figure the neural network is composed of **layers**:

  - Input layer: it only represents input data. **It doesn't contain neurons**.
  - Output layer: it represents the last layer. It contains a neuron (in some cases more than 1).
  - Hidden layer: any layer between the input (first) layer and output (last) layer. Many hidden layers can be stacked. When there are many hidden layers, the neural networks is deep.

Notice that the neuron **o1** in the output layer takes as input the output of the neurons **h1** and **h2** in the hidden layer. 

In exercise 1, you implemented this neuron.
![alt text][neuron]

[neuron]: ./w3_day1_neuron.png "Plot"

Now, we add two more neurons: 

- h2, the second neuron of the hidden layer
- o1, the neuron of the output layer


![alt text][nn]

[nn]: ./w3_day1_neural_network.png "Plot"

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