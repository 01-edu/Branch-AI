##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the output of `y_train.values[:10]` and `y_test.values[:10]`are:

    ```console
    y_train.values[:10]: 
    [[202.]
    [ 55.]
    [202.]
    [ 42.]
    [214.]
    [173.]
    [118.]
    [ 90.]
    [129.]
    [151.]]

    y_test.values[:10]: 
    [[ 71.]
    [ 72.]
    [235.]
    [277.]
    [109.]
    [ 61.]
    [109.]
    [ 78.]
    [ 66.]
    [192.]]
    ```

##### The question 2 is validated if the coefficients and the intercept are:

    ```console
    [('age', -60.40163046086952),
    ('sex', -226.08740652083418),
    ('bmi', 529.383623302316),
    ('bp', 259.96307686274605),
    ('s1', -859.121931974365),
    ('s2', 504.70960058378813),
    ('s3', 157.42034928335502),
    ('s4', 226.29533600601638),
    ('s5', 840.7938070846119),
    ('s6', 34.712225788519554),
    ('intercept', 152.05314895029233)]
    ```

##### The question 3 is validated if the output of `predictions_on_test[:10]` is:

    ```console
    array([[111.74351759],
        [ 98.41335251],
        [168.36373195],
        [255.05882934],
        [168.43764643],
        [117.60982186],
        [198.86966323],
        [126.28961941],
        [117.73121787],
        [224.83346984]])
    ```

##### The question 4 is validated if the mse on the **train set** is `2888.326888` and the mse on the **test set** is `2858.255153`.
