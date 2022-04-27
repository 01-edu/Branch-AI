##### The exercice is validated is all questions of the exercice are validated

##### To validate this exercise all answers should return the expected numerical value given in the correction AND uses Pandas. For example using NumPy to compute the mean doesn't respect the philosophy of the exercise which is to use Pandas.

##### The solution of question 1 is accepted if it contains **10000 entries** and **14 columns**. There many solutions based on: shape, info, describe.

##### The solution of question 2 is accepted if the answer is **50.34730200000025**.

    Even if `np.mean` gives the solution, `df['Purchase Price'].mean()` is preferred

##### The solution of question 3 is accepted if the min is `0`and the max is `99.989999999999995`


##### The solution of question 4 is accepted if the answer is **1098**

##### The solution of question 5 is accepted if the answer is  **30**

##### The solution of question 6 is accepted if the are `4932` people that made the purchase during the `AM` and `5068` people that made the purchase during `PM`. There many ways to the solution but the goal of this question was to make you use `value_counts`

##### The solution of question 7 is accepted if the answer is as below. There many ways to the solution but the goal of this question was to use `value_counts`

    Interior and spatial designer    31

    Lawyer                           30

    Social researcher                28

    Purchasing manager               27

    Designer, jewellery              27

    
##### The solution of question 8 is accepted if the purchase price is **75.1**


##### The solution of question 9 is accepted if the email adress is **bondellen@williams-garza.com**

##### The solution of question 10 is accepted if the answer is **39**. The prefered solution is based on this: `df[(df['A'] == X) & (df['B'] > Y)]`


##### The solution of question 11 is accepted if the answer is **1033**. The preferred solution is based on the usage of `apply` on a `lambda` function that slices the string that contains the expiration date.

##### The solution of question 12 is accepted if the answer is as below. The preferred solution is based on the usage of `apply` on a `lambda` function that slices the string that contains the email. The `lambda` function uses `split` to split the string on `@`. Finally, `value_counts` is used to count the occurrences.

    - hotmail.com     1638
    - yahoo.com       1616
    - gmail.com       1605
    - smith.com         42
    - williams.com      37
