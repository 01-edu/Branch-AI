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