# W2D01  Piscine AI - Data Science

![Alt Text](w2_day01_linear_regression_video.gif)

## Linear regression with Scikit Learn

The goal of this day is to understand practical Linear regression and supervised learning.

The word "regression" was introduced by Sir Francis Galton (a cousin of C. Darwin) when he
studied the size of individuals within a progeny. He was trying to understand why
large individuals in a population appeared to have smaller children, more
close to the average population size; hence the introduction of the term "regression".

Today we will learn a basic algorithm used in **supervised learning** : **The Linear Regression**. We will be using **Scikit-learn** which is a machine learning library. It is designed to interoperate with the Python libraries NumPy and Pandas.

We will also learn progressively the Machine Learning methodology for supervised learning - today we will focus on evaluating a machine learning model by splitting the data set in a train set and a test set.

## Exercises of the day

- Exercise 0 Environment and libraries
- Exercise 1 Scikit-learn estimator
- Exercise 2 Linear regression in 1D
- Exercise 3 Train test split
- Exercise 4 Forecast diabetes progression
- Bonus: Exercise 5 Gradient Descent - **Optional**


## Virtual Environment 
- Python 3.x
- NumPy
- Pandas
- Matplotlib
- Scikit Learn
- Jupyter or JupyterLab

*Version of Scikit Learn I used to do the exercises: 0.22*. I suggest to use the most recent one. Scikit Learn 1.0 is finally available after ... 14 years. 

## Ressources

### To start with Scikit-learn

- https://scikit-learn.org/stable/tutorial/basic/tutorial.html

- https://jakevdp.github.io/PythonDataScienceHandbook/05.02-introducing-scikit-learn.html

- https://scikit-learn.org/stable/modules/linear_model.html

### Machine learning methodology and algorithms

- This course provides a broad introduction to machine learning, datamining, and statistical pattern recognition. Andrew Ng is a star in the Machine Learning community. I recommend to spend some time during the projects to focus on some algorithms. However, Python is not the language used for the course.  https://www.coursera.org/learn/machine-learning

- https://docs.microsoft.com/en-us/azure/machine-learning/algorithm-cheat-sheet

- https://scikit-learn.org/stable/tutorial/index.html

### Linear Regression

- https://towardsdatascience.com/laymans-introduction-to-linear-regression-8b334a3dab09

- https://towardsdatascience.com/linear-regression-the-actually-complete-introduction-67152323fcf2

### Train test split

- https://machinelearningmastery.com/train-test-split-for-evaluating-machine-learning-algorithms/

- https://developers.google.com/machine-learning/crash-course/training-and-test-sets/video-lecture?hl=en


# Exercise 0 Environment and libraries

The goal of this exercise is to set up the Python work environment with the required libraries.

**Note:** For each quest, your first exercice will be to set up the virtual environment with the required libraries. 

I recommend to use:

- the **last stable versions** of Python. 
- the virtual environment you're the most confortable with. `virtualenv` and `conda` are the most used in Data Science.
- one of the most recents versions of the libraries required

1. Create a virtual environment named `ex00`, with a version of Python >= `3.8`, with the following libraries: `pandas`, `numpy`, `jupyter`, `matplotlib` and `scikit-learn`.