# W1D01  Piscine AI - Data Science

## NumPy 
The goal of this day is to understand practical usage of **NumPy**. **NumPy** is a commonly used Python data analysis package. By using **NumPy**, you can speed up your workflow, and interface with other packages in the Python ecosystem, like scikit-learn, that use **NumPy** under the hood. **NumPy** was originally developed in the mid 2000s, and arose from an even older package called Numeric. This longevity means that almost every data analysis or machine learning package for Python leverages **NumPy** in some way.

## Exercises of the day

- Exercise 0 Environment and libraries
- Exercise 1 Your first NumPy array
- Exercise 2 Zeros
- Exercise 3 Slicing
- Exercise 4 Random
- Exercise 5 Split, concatenate, reshape arrays
- Exercise 6 Broadcasting and Slicing
- Exercise 7 NaN
- Exercise 8 Wine
- Exercise 9 Football tournament

## Virtual Environment 
- Python 3.x
- NumPy
- Jupyter or JupyterLab

*Version of NumPy I used to do the exercises: 1.18.1*. 
I suggest to use the most recent one.

## Ressources

- https://medium.com/fintechexplained/why-should-we-use-NumPy-c14a4fb03ee9
- https://numpy.org/doc/
- https://jakevdp.github.io/PythonDataScienceHandbook/


# Exercise 0 Environment and libraries

The goal of this exercise is to set up the Python work environment with the required libraries and to learn to launch a `jupyter notebook`. Jupyter notebooks are very convenient as they allow to write and test code within seconds. However, it really easy to implement instable and not reproducible code using notebooks. Keep the notebook and the underlying code clean. An article below detail when the Notebook should be used. Notebook can be used for most of the exercices of the piscine as the goal is to experiment A LOT. But no worries, you'll be asked to build a more robust structure for all the projects. 

**Note:** For each quest, your first exercice will be to set up the virtual environment with the required libraries. 

I recommend to use:

- the **last stable versions** of Python. However, for educational purpose you will install a specific version of Python in this exercise. 
- the virtual environment you're the most confortable with. `virtualenv` and `conda` are the most used in Data Science.
- one of the most recents versions of the libraries required

1. Create a virtual environment named `ex00`, with Python `3.8`, with the following libraries: `numpy`, `jupyter`. Save the installed packages in `requirements.txt` in the current directory.

2. Launch a `jupyter notebook` on port `8891` and create a notebook named `Notebook_ex00`. `JupyterLab` can be used instead of Jupyter Notebook here. 

3. Put the text `H1 TITLE` as **heading level 1** and `H2 TITLE` as **heading level 2** in the first cell.

4. Run `print("Buy the dip ?")` in the second cell


## Ressources: 

- https://www.python.org/
- https://docs.conda.io/
- https://jupyter.org/
- https://numpy.org/
- https://towardsdatascience.com/jypyter-notebook-shortcuts-bf0101a98330
- https://odsc.medium.com/why-you-should-be-using-jupyter-notebooks-ea2e568c59f2
- https://stackoverflow.com/questions/50777849/from-conda-create-requirements-txt-for-pip3 
