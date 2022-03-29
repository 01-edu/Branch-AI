##### The exercice is validated is all questions of the exercice are validated


##### The question 1 is validated if the solution doesn't involve a for loop or writing all integers from 1 to 100 and if the array is: `np.array([1,...,100])`. The list from 1 to 100 can be generated with an iterator: `range`.

##### The question 2 is validated if the solution is: `integers[::2]`

##### The question 3 is validated if the solution is: `integers[::-2]`

##### The question 4 is validated if the array is: `np.array([0, 1,0,3,4,0,...,0,99,100])`. There are at least two ways to get this results without for loop. The first one uses `integers[1::3] = 0` and the second involves creating a boolean array that indexes the array:

```python
mask = (integers+1)%3 == 0
integers[mask] = 0
```
