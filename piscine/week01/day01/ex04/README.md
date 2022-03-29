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