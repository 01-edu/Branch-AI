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