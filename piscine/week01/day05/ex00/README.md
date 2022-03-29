# W1D05  Piscine AI - Data Science

## Time Series with Pandas

Time series data are data that are indexed by a sequence of dates or times. Today, you'll learn how to use methods built into Pandas to work with this index. You'll also learn for instance:
- to resample time series to change the frequency
- to calculate rolling and cumulative values for times series
-  to build a backtest

Time series a used A LOT in finance. You'll learn to evaluate financial strategies using Pandas. It is important to keep in mind that Python is vectorized. That's why some questions constraint you to not use a for loop ;-).

## Exercises of the day

- Exercise 1 Series
- Exercise 2 Financial data
- Exercise 3 Multi asset returns
- Exercise 4 Backtest


## Virtual Environment 
- Python 3.x
- NumPy
- Pandas
- Jupyter or JupyterLab

*Version of Pandas I used to do the exercises: 1.0.1*. 
I suggest to use the most recent one.

## Resources

- https://jakevdp.github.io/PythonDataScienceHandbook/

- https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf

- https://www.learndatasci.com/tutorials/python-pandas-tutorial-complete-introduction-for-beginners/

- https://towardsdatascience.com/different-ways-to-iterate-over-rows-in-a-pandas-dataframe-performance-comparison-dc0d5dcef8fe


# Exercise 0 Environment and libraries

The goal of this exercise is to set up the Python work environment with the required libraries.

**Note:** For each quest, your first exercice will be to set up the virtual environment with the required libraries. 

I recommend to use:

- the **last stable versions** of Python. 
- the virtual environment you're the most confortable with. `virtualenv` and `conda` are the most used in Data Science.
- one of the most recents versions of the libraries required

1. Create a virtual environment named `ex00`, with a version of Python >= `3.8`, with the following libraries: `pandas`, `numpy` and `jupyter`.