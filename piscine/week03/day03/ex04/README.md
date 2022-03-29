# Exercise 4 Multi classification - Optimize 

The goal of this exercise is to learn to optimize a multi-classification neural network. As learnt previously, the loss function used in binary classification is the log loss - also called in Keras `binary_crossentropy`. This function is defined for binary classification and can be extended to multi-classfication. In Keras, the extended loss that supports multi-classification is `binary_crossentropy`. There's no code to run in that exercise.

1. Fill the chunk of code below in order to optimize the neural network defined in the previous exercise. Choose the adapted loss, adam as optimizer and the accuracy as metric.

```
model.compile(loss='',#TODO1
              optimizer='', #TODO2
              metrics=['']) #TODO3
```