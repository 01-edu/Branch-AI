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
