# W3D01  Piscine AI - Data Science

## Neural Networks 

Last week you learnt about some Machine Learning algorithms as Random Forest or Gradient Boosting. Neural Networks are another type of Machine Learning algorithms that are intensively used because of their efficiency. Neural networks are a set of algorithms, modeled loosely after the human brain, that are designed to recognize patterns. They interpret sensory data through a kind of machine perception, labeling or clustering raw input. The patterns they recognize are numerical, contained in vectors, into which all real-world data, be it images, sound, text or time series, must be translated. Different types of neural networks exist and are specific to some use-cases. For example CNN for images, RNN or LSTMs for time-series or text, etc ...

Today we will focus on Artificial Neural Networks. The goal is to understand how do the neural networks work, train them on data and understand the challenges of training a neural network. The ressources below expalin very well the mecanisms behind neural networks, step by step. 

However the exercices won't cover architectures as RNN, LSTM - used on sequences as time series or text, CNN - used a lot on images processing. One of the projects will require to know how to use the special architectures. To do so, I suggest that you go through this lesson: https://fr.coursera.org/specializations/deep-learning.

## Exercises of the day

- Exercise 1 The neuron 
- Exercise 2 Neural network
- Exercise 3 Log loss
- Exercise 4 Forward propagation
- Exercise 5 Regression

## Virtual Environment 
- Python 3.x
- NumPy
- Jupyter or JupyterLab

*Version of NumPy I used to do the exercises: 1.18.1*. 
I suggest to use the most recent one.

## Ressources

- https://victorzhou.com/blog/intro-to-neural-networks/


- https://srnghn.medium.com/deep-learning-overview-of-neurons-and-activation-functions-1d98286cf1e4

- https://towardsdatascience.com/machine-learning-for-beginners-an-introduction-to-neural-networks-d49f22d238f9


# Exercise 0 Environment and libraries

The goal of this exercise is to set up the Python work environment with the required libraries.

**Note:** For each quest, your first exercice will be to set up the virtual environment with the required libraries. 

I recommend to use:

- the **last stable versions** of Python. 
- the virtual environment you're the most confortable with. `virtualenv` and `conda` are the most used in Data Science.
- one of the most recents versions of the libraries required

1. Create a virtual environment with a version of Python >= `3.8`, with the following libraries:  `numpy` and `jupyter`.
