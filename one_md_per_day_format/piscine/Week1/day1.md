# D01  Piscine AI - Data Science

The goal of this day is to understand practical usage of **NumPy**. **NumPy** is a commonly used Python data analysis package. By using **NumPy**, you can speed up your workflow, and interface with other packages in the Python ecosystem, like scikit-learn, that use **NumPy** under the hood. **NumPy** was originally developed in the mid 2000s, and arose from an even older package called Numeric. This longevity means that almost every data analysis or machine learning package for Python leverages **NumPy** in some way.

Version of NumPy I used to do the exercises: 1.18.1

I suggest to use the most recent one.

Author:

<div style="page-break-after: always"></div>

# Outline: (optional)

A. Introduction

B. Rules

C. Exercises

## Rules

... Notebook Colabs or Jupyter Notebook
Save one notebook per day or one per exercise. Use markdown to divide your notebook in different exercises.

## Ressources

- https://medium.com/fintechexplained/why-should-we-use-NumPy-c14a4fb03ee9
- https://numpy.org/doc/
- https://jakevdp.github.io/PythonDataScienceHandbook/

# Exercise 1 Your first NumPy array

The goal of this exercise is to use many Python data types in **NumPy** arrays. **NumPy** arrays are intensively used in **NumPy** and **Pandas**. They are flexible and allow to use optimized **NumPy** underlying functions.

1. Create a NumPy array that contains: an integer, a float, a string, a dictionary, a list, a tuple, a set and a boolean.

The expected output is:

```python
for i in your_np_array:
    print(type(i))

<class 'int'>
<class 'float'>
<class 'str'>
<class 'dict'>
<class 'list'>
<class 'tuple'>
<class 'set'>
<class 'bool'>
```

## Correction

1. This question is validated if the your_numpy_array is a NumPy array. It can be checked with `type(your_numpy_array)` that should be equal to `numpy.ndarray`. And if the type of is element are as follow.

```python
for i in your_np_array:
    print(type(i))

<class 'int'>
<class 'float'>
<class 'str'>
<class 'dict'>
<class 'list'>
<class 'tuple'>
<class 'set'>
<class 'bool'>
```

---

# Exercise 2 Zeros

The goal of this exercise is to learn to create a NumPy array with 0s.

1. Create a NumPy array of dimension **300** with zeros without filling it manually
2. Reshape it to **(3,100)**

## Correction

1. The question is validated is the solution uses `np.zeros` and if the shape of the array is `(300,)`

2. The question is validated if the solution uses `reshape` and the shape of the array is `(3, 100)`

---

# Exercise 3 Slicing

The goal of this exercise is to learn NumPy indexing/slicing. It allows to access values of the NumPy array efficiently and without a for loop.

1. Create a NumPy array of dimension 1 that contains all integers from 1 to 100 ordered.
2. Without using  a for loop and using the array created in Q1, create an array that contain all odd integers. The expected output is: `np.array([1,3,...,99])`. *Hint*: it takes one line
3. Without using  a for loop and using the array created in Q1, create an array that contain all even integers reversed.  The expected output is: `np.array([100,98,...,2])`. *Hint*: it takes one line

4. Using array of Q1, set the value of every 3 elements of the list (starting with the second) to 0. The expected output is: `np.array([[1,0,3,4,0,...,0,99,100]])`

## Correction

1. This question is validated if the solution doesn't involve a for loop or writing all integers from 1 to 100 and if the array is: `np.array([1,...,100])`. The list from 1 to 100 can be generated with an iterator: `range`.

2. This question is validated if the solution is: `integers[::2]`

3. This question is validated if the solution is: `integers[::-2]`

4. This question is validated if the array is: `np.array([0, 1,0,3,4,0,...,0,99,100])`. There are at least two ways to get this results without for loop. The first one uses `integers[1::3] = 0` and the second involves creating a boolean array that indexes the array:

```python
mask = (integers+1)%3 == 0
integers[mask] = 0
```

---

# Exercise 4 Random

The goal of this exercise is to learn to generate random data.
In Data Science it is extremely useful to generate random data for many reasons:
Lack of real data, create a random benchmark, use varied data sets.
NumPy proposes a lot of options to generate random data. In statistics, assumptions are made on the distribution the data is from. All data distribution that can be generated randomly are described in the documentation. In this exercise we will focus on two distributions:

- Uniform: For example, if your goal is to generate a random number from 1 to 100 and that the probability that all the numbers is equal you'll need the uniform distribution. NumPy provides `randint` and `uniform` to generate uniform distribution

- Normal: The normal distribution is the most important probability distribution in statistics because it fits many natural phenomena.For example, if you need to generate a data sample that represents **Heights of 14 Year Old Girls** it can be done using the normal distribution. In that case, we need two parameters: the mean (1m51) and the standard deviation (0.0741m). NumPy provides `randn` to generate normal distribution (among other)

https://numpy.org/doc/stable/reference/random/generator.html

1. Set the seed to 888
2. Generate a **one-dimensional**  array of size 100 with a normal distribution
3. Generate a **two-dimensional** array of size 8,8 with random integers from 1 to 10 - both included (same probability for each integer)
4. Generate a **three-dimensional** of size 4,2,5 array with random integers from 1 to 17 - both included (same probability for each integer)

## Correction

For this exercise, as the results may change depending on the version of the package or the OS, I give the code to correct the exercise. If the code is correct and the output is not the same as mine, it is accepted.

1. The solution is accepted if the solution is: `np.random.seed(888)`

2. The solution is accepted if the solution is `np.random.randn(100)`. The value of the first element is `0.17620087373662233`.

3. The solution is accepted if the solution is `np.random.randint(1,11,(8,8))`.

    ```console
    Given the NumPy version and the seed, you should have this output:

    array([[ 7,  4,  8, 10,  2,  1,  1, 10],
        [ 4,  1,  7,  4,  3,  5,  2,  8],
        [ 3,  9,  7,  4,  9,  6, 10,  5],
        [ 7, 10,  3, 10,  2,  1,  3,  7],
        [ 3,  2,  3,  2, 10,  9,  5,  4],
        [ 4,  1,  9,  7,  1,  4,  3,  5],
        [ 3,  2, 10,  8,  6,  3,  9,  4],
        [ 4,  4,  9,  2,  8,  5,  9,  5]])
    ```

4. The solution is accepted if the solution is `np.random.randint(1,18,(4,2,5))`.

    ```console
    Given the NumPy version and the seed, you should have this output:

    array([[[14, 16,  8, 15, 14],
            [17, 13,  1,  4, 17]],

        [[ 7, 15,  2,  8,  3],
            [ 9,  4, 13,  9, 15]],

        [[ 5, 11, 11, 14, 10],
            [ 2,  1, 15,  3,  3]],

        [[ 3, 10,  5, 16, 13],
            [17, 12,  9,  7, 16]]])
    ```

---

# Exercise 5: Split, concatenate, reshape arrays

The goal of this exercise is to learn to concatenate and reshape arrays.

1. Generate an array with integers from 1 to 50:  `array([1,...,50])`

2. Generate an array with integers from 51 to 100:  `array([51,...,100])`

3. Using `np.concatenate`, concatenate the two arrays into:  `array([1,...,100])`

4. Reshape the previous array into:

    ```console
    array([[  1,  ... ,  10],
                ...
        [ 91,  ... , 100]])
    ```

## Correction

1. This question is validated if the generated array is based on an iterator as `range` or `np.arange`. Check that 50 is part of the array.

2. This question is validated if the generated array is based on an iterator as `range` or `np.arange`. Check that 100 is part of the array.

3. This question is validated if you concatenated this way `np.concatenate(array1,array2)`.

4. This question is validated if the result is:

    ```console
    array([[  1,  ... ,  10],
                ...
        [ 91,  ... , 100]])
    ```

The easiest way is to use `array.reshape(10,10)`.

https://jakevdp.github.io/PythonDataScienceHandbook/ (section: The Basics of NumPy Arrays)

---

# Exercise 6: Broadcasting and Slicing

The goal of this exercise is to learn to access values of n-dimensional arrays efficiently.

1. Create an 2-dimensional array size 9,9 of 1s. Each value has to be an `int8`.
2. Using **slicing**, output this array:

    ```python
    array([[1, 1, 1, 1, 1, 1, 1, 1, 1],
        [1, 0, 0, 0, 0, 0, 0, 0, 1],
        [1, 0, 1, 1, 1, 1, 1, 0, 1],
        [1, 0, 1, 0, 0, 0, 1, 0, 1],
        [1, 0, 1, 0, 1, 0, 1, 0, 1],
        [1, 0, 1, 0, 0, 0, 1, 0, 1],
        [1, 0, 1, 1, 1, 1, 1, 0, 1],
        [1, 0, 0, 0, 0, 0, 0, 0, 1],
        [1, 1, 1, 1, 1, 1, 1, 1, 1]], dtype=int8)
    ```

https://jakevdp.github.io/PythonDataScienceHandbook/ (section: Computation on Arrays: Broadcasting)

## Correction

1. The question is validated if the output is the same as:
`np.ones([9,9], dtype=np.int8)`

2. The question is validated if the output is

    ```console
    array([[1, 1, 1, 1, 1, 1, 1, 1, 1],
        [1, 0, 0, 0, 0, 0, 0, 0, 1],
        [1, 0, 1, 1, 1, 1, 1, 0, 1],
        [1, 0, 1, 0, 0, 0, 1, 0, 1],
        [1, 0, 1, 0, 1, 0, 1, 0, 1],
        [1, 0, 1, 0, 0, 0, 1, 0, 1],
        [1, 0, 1, 1, 1, 1, 1, 0, 1],
        [1, 0, 0, 0, 0, 0, 0, 0, 1],
        [1, 1, 1, 1, 1, 1, 1, 1, 1]], dtype=int8)
    ```

    The solution is not accepted if the values of the array have been changed one by one manually. The usage of the for loop is not allowed neither.
    Here is an example of a possible solution:

    ```console
        x[1:8,1:8] = 0 
        x[2:7,2:7] = 1 
        x[3:6,3:6] = 0 
        x[4,4] = 1 
    ```

---

# Exercise 7: NaN

The goal of this exercise is to learn to deal with missing data in NumPy and to manipulate NumPy arrays.

Let us consider a 2-dimensional array that contains the grades at the past two exams. Some of the students missed the first exam. As the grade is missing it has been replaced with a `NaN`.

1. Using `np.where` create a third column that is equal to the grade of the first exam if it exists and the second else. Add the column as the third column of the array.

**Using a for loop or if/else statement is not allowed in this exercise.**

```python
import numpy as np

generator = np.random.default_rng(123)
grades = np.round(generator.uniform(low = 0.0, high = 10.0, size = (10, 2)))
grades[[1,2,5,7], [0,0,0,0]] = np.nan
print(grades)
```

## Correction

1. There are two steps in this exercise:

- Create the vector that contains the grade of the first exam if available or the second. This can be done using `np.where`:

```python
    np.where(np.isnan(grades[:, 0]), grades[:, 1],     grades[:, 0])
```

- Add this vector as third column of the array. Here are two ways:

```python
    np.insert(arr = grades, values = new_vector, axis = 1, obj = 2)

    np.hstack((grades, new_vector[:, None]))
```

This question is validated if, without having used a for loop or having filled the array manually, the output is:
    This question is validated if, without having used a for loop or having filled the array manually, the output is: 
This question is validated if, without having used a for loop or having filled the array manually, the output is:

```console
[[ 7.  1.  7.]
[nan  2.  2.]
[nan  8.  8.]
[ 9.  3.  9.]
[ 8.  9.  8.]
[nan  2.  2.]
[ 8.  2.  8.]
[nan  6.  6.]
[ 9.  2.  9.]
[ 8.  5.  8.]]
```


---

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

## Correction

1. This question is validated if the text file has successfully been loaded in a NumPy array with
 `genfromtxt('winequality-red.csv', delimiter=',')` and the reduced arrays weights **76800 bytes**

2. This question is validated if the output is

 ```python
 array([[ 7.4   ,  0.7   ,  0.    ,  1.9   ,  0.076 , 11.    , 34.    ,
         0.9978,  3.51  ,  0.56  ,  9.4   ,  5.    ],
       [ 7.4   ,  0.66  ,  0.    ,  1.8   ,  0.075 , 13.    , 40.    ,
         0.9978,  3.51  ,  0.56  ,  9.4   ,  5.    ],
       [ 6.7   ,  0.58  ,  0.08  ,  1.8   ,  0.097 , 15.    , 65.    ,
         0.9959,  3.28  ,  0.54  ,  9.2   ,  5.    ]])
 ```

This slicing gives the answer `my_data[[1,6,11],:]`.

3. This question is validated if the answer if False. There many ways to get the answer: find the maximum or check values greater than 20.

4. This question is validated if the answer is 10.422983114446529.

5. This question is validated if the answers is:

    ```console
    pH stats
    25 percentile:  3.21
    50 percentile:  3.31
    75 percentile:  3.4
    mean:  3.3111131957473416
    min:  2.74
    max:  4.01
    ```

    > *Note: Using `percentile` or `median` may give different results depending on the duplicate values in the column. If you do not have my results please use `percentile`.*

6. This question is validated if the answer is ~`5.2`. The first step is to get the percentile 20% of the column `sulphates`, then create a boolean array that contains `True` of the value is smaller than the percentile 20%, then select this rows with the column quality and compute the `mean`.

7. This question is validated if the output for the best wines is:

```python
array([ 8.56666667,  0.42333333,  0.39111111,  2.57777778,  0.06844444,
    13.27777778, 33.44444444,  0.99521222,  3.26722222,  0.76777778,
    12.09444444,  8.        ])
```

And the output for the bad wines is:

```python
array([ 8.36    ,  0.8845  ,  0.171   ,  2.635   ,  0.1225  , 11.      ,
    24.9     ,  0.997464,  3.398   ,  0.57    ,  9.955   ,  3.      ])
```

This can be done in three steps: Get the max, create a boolean mask that indicates rows with max quality, use this mask to subset the rows with the best quality and compute the mean on the axis 0.

---

# Exercise 9 Football tournament

The goal of this exercise is to learn to use permutations, complex

A Football tournament is organized in your city. There are 10 teams and the director of the tournaments wants you to create a first round as exciting as possible. To do so, you are allowed to choose the pairs. As a former data scientist, you implemented a model based on teams' current season performance. This models predicts the score difference between two teams. You used this algorithm to predict the score difference for every possible pair.
The matrix returned is a 2-dimensional array that contains in (i,j) the score difference between team i and j. The matrix is in  `model_forecasts.txt`.

Using this output, what are the pairs that will give the most interesting matches ?

If a team wins 7-1 the match is obviously less exciting than a match where the winner wins 2-1.
The criteria that corresponds to **the pairs that will give the most interesting matches** is **the pairs that minimize the sum of squared differences**

The expected output is:

```console
 [[m1_t1 m2_t1 m3_t1 m4_t1 m5_t1]
  [m1_t2 m2_t2 m3_t2 m4_t2 m5_t2]]

```

- m1_t1 stands for match1_team1
- m1_t1 plays against m1_t2 ...

**Usage of for loop is not allowed, you may need to use the library** `itertools` **to create permutations**

https://docs.python.org/3.9/library/itertools.html

## Correction

This exercise is validated if the output is:

```console
 [[0 3 1 2 4]
  [7 6 8 9 5]]
```
