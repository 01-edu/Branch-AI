# Exercise 4 Forward propagation
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
