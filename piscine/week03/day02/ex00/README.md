# W3D02  Piscine AI - Data Science

## Keras 

The goal of this day is to learn to use Keras to build Neural Networks. As explained on Keras website, Keras is a deep learning API written in Python, running on top of the machine learning platform TensorFlow. It was developed with a focus on enabling fast experimentation. Being able to go from idea to result as fast as possible is key to doing good research.
And, TensorFlow was created by the Google Brain team, TensorFlow is an open source library for numerical computation and large-scale machine learning. TensorFlow bundles together a slew of machine learning and deep learning (aka neural networking) models and algorithms and makes them useful by way of a common metaphor. It uses Python to provide a convenient front-end API for building applications with the framework, while executing those applications in high-performance C++.

There are two ways to build Keras models: sequential and functional.The sequential API allows you to create models layer-by-layer for most problems. It is limited in that it does not allow you to create models that share layers or have multiple inputs or outputs. The exercises focuses on the usage of the sequential API. 

Note: 

The audit will provide the code and output because it is not straightforward to reproduce results using Keras. There are many source of randomness. Even if all the seeds are fixed to a constant they may be other source of randomness. https://machinelearningmastery.com/reproducible-results-neural-networks-keras/

## Exercises of the day

- Exercise 0 
- Exercise 1 Sequential
- Exercise 2 Dense
- Exercise 3 Architecture
- Exercise 4 Optimize

## Virtual Environment 
- Python 3.x
- NumPy
- Pandas
- Jupyter or JupyterLab
- Keras
- Scikit-learn

*Version of Keras I used to do the exercises: 2.4.3*. 
I suggest to use the most recent one.

## Ressources

- https://machinelearningmastery.com/tutorial-first-neural-network-python-keras/


# Exercise 0 Environment and libraries

The goal of this exercise is to set up the Python work environment with the required libraries.

**Note:** For each quest, your first exercice will be to set up the virtual environment with the required libraries. 

I recommend to use:

- the **last stable versions** of Python. 
- the virtual environment you're the most confortable with. `virtualenv` and `conda` are the most used in Data Science.
- one of the most recents versions of the libraries required

1. Create a virtual environment named with a version of Python >= `3.8`, with the following libraries: `pandas`, `numpy`, `jupyter`, `sklearn`, and `keras`.
