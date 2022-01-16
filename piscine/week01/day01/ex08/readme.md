
# Exercise 8: Wine

The goal of this exercise is to learn to perform a basic data analysis on real data using NumPy.

The data set that will be used for this exercise is the red wine data set.

https://archive.ics.uci.edu/ml/datasets/wine+quality

How to tell if a given 2D array has null columns?

1. Using `genfromtxt` load the data and reduce the size of the numpy array by optimizing the types. The sum of absolute differences between the original data set and the "memory" optimized one has to be smaller than 1.10**-3. I suggest to use `np.float32`. Check that the numpy array weights **76800 bytes**.

2. Print 2nd, 7th and 12th rows as a two dimensional array

3. Is there any wine with a percentage of alcohol greater than 20% ? Return True or False

4. What is the average % of alcohol on all wines in the data set ? If needed, drop `np.nan` values

5. Compute the minimum, the maximum, the 25th percentile, the 50th percentile, the 75th percentile, the median (50th percentile) of the pH

6. Compute the average quality of the wines having the 20% least sulphates

7. Compute the mean of all variables for wines having the best quality. Same question for the wines having the worst quality
