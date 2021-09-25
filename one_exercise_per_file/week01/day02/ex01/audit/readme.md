1. The solution is accepted if the DataFrame created is the same as the "model" DataFrame. Check that the index is not 1,2,3,4,5.

2. The solution is accepted if the types you get for the columns are

    ```console
    <class 'pandas.core.series.Series'>
    <class 'pandas.core.series.Series'>
    <class 'pandas.core.series.Series'>
    ```

and if the types of the first value of the columns are

```console
    <class 'str'>
    <class 'list'>
    <class 'float'>
```
