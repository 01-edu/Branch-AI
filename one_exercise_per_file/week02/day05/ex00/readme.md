# W2D05  Piscine AI - Data Science

## Model selection methodology

If you finished yesterday's exercises you should be able to train several Machine Learning algorithms and to choose one returned by GridSearchCV.
GridSearchCV returns the model that gives the best score on the test set. Yesterday, as I told you, I changed the **cv** parameter to compute the GridSearch with a train set and a test set.

It means that the selected model is based on one single measure. What if, by luck, we predict correctly on that section ? What if the best model is bad ? What if I could have selected a better model ?

We will answer these questions today ! The topics we will cover are the one of the most important in Machine Learning.

## Exercises of the day

- Exercise 0 Environment and libraries
- Exercise 1 K-Fold
- Exercise 2 Cross validation (k-fold)
- Exercise 3 GridsearchCV
- Exercise 4 Validation curve and Learning curve

## Virtual Environment 
- Python 3.x
- NumPy
- Pandas
- Jupyter or JupyterLab
- Scikit-learn
- Matplotlib

*Version of Pandas I used to do the exercises: 1.0.1*. 
I suggest to use the most recent one.

## Resources

**Must read before to start the exercises**

### Biais-Variance trade off, aka Underfitting/Overfitting:
  - https://machinelearningmastery.com/gentle-introduction-to-the-bias-variance-trade-off-in-machine-learning/

  - https://jakevdp.github.io/PythonDataScienceHandbook/05.03-hyperparameters-and-model-validation.html

### Cross-validation
  - https://algotrading101.com/learn/train-test-split/


# Exercise 0 Environment and libraries

The goal of this exercise is to set up the Python work environment with the required libraries.

**Note:** For each quest, your first exercice will be to set up the virtual environment with the required libraries. 

I recommend to use:

- the **last stable versions** of Python. 
- the virtual environment you're the most confortable with. `virtualenv` and `conda` are the most used in Data Science.
- one of the most recents versions of the libraries required

1. Create a virtual environment named `ex00`, with a version of Python >= `3.8`, with the following libraries: `pandas`, `numpy`, `jupyter`, `matplotlib` and `scikit-learn`.
