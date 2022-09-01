# Exercise 5 Multi classification example

The goal of this exercise is to learn to use a neural network to classify a multiclass data set. The data set used is the Iris data set which allows to classify flower given basic features as flower's measurement. 

Preliminary: 
    - [Load the dataset from `sklearn`.](https://scikit-learn.org/stable/auto_examples/datasets/plot_iris_dataset.html)
    - Split train test. Keep 20% for the test set. Use `random_state=1`. 
    - Scale the data using Standard Scaler


1. Use the `LabelBinarizer` from Sckit-learn to create a one hot encoding of the target. As you know, the output layer of a multi-classification neural network shape is equal to the number of classes. The output layer expects to have a target with the same shape as its output layer.  

2. Train a neural network on the train set and predict on the test set. The neural network should have 1 hidden layers. The expected **accuracy** on the test set is minimum 90%.
*Hint*: inscrease the number of epochs 
**Warning**: Do no forget to evaluate the neural network on the **SCALED** test set. 
