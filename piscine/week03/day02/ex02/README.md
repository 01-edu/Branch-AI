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