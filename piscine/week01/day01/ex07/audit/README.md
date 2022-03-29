##### The exercice is validated is all questions of the exercice are validated

##### This question is validated if, without having used a for loop or having filled the array manually, the output is:

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

There are two steps in this exercise:

- Create the vector that contains the grade of the first exam if available or the second. This can be done using `np.where`:

```python
    np.where(np.isnan(grades[:, 0]), grades[:, 1],     grades[:, 0])
```

- Add this vector as third column of the array. Here are two ways:

```python
    np.insert(arr = grades, values = new_vector, axis = 1, obj = 2)

    np.hstack((grades, new_vector[:, None]))
```
