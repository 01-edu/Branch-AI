To validate this exercise all answers should return the expected numerical value given in the correction AND uses Pandas. For example using NumPy to compute the mean doesn't respect the philosophy of the exercise which is to use Pandas.

1. How many rows and columns are there?**10000 entries** and **14 columns**

    There many solutions based on: shape, info, describe

2. What is the average Purchase Price? **50.34730200000025**

    Even if `np.mean` gives the solution, `df['Purchase Price'].mean()` is preferred

3. What were the highest and lowest purchase prices?

    min: 0

    max: 99.989999999999995

4. How many people have English `'en'` as their Language of choice on the website? **1098**

5. How many people have the job title of `"Lawyer"` ? **30**

6. How many people made the purchase during the `AM` and how many people made the purchase during `PM` ?

    PM:    5068

    AM:    4932

    There many ways to the solution but the goal of this question was to make you use `value_counts`

7. What are the 5 most common Job Titles?

    Interior and spatial designer    31

    Lawyer                           30

    Social researcher                28

    Purchasing manager               27

    Designer, jewellery              27

    There many ways to the solution but the goal of this question was to make you use `value_counts`

8. Someone made a purchase that came from Lot: `"90 WT"` , what was the Purchase Price for this transaction? **75.1**
9. What is the email of the person with the following Credit Card Number: `4926535242672853`. **bondellen@williams-garza.com**
10. How many people have American Express as their Credit Card Provider and made a purchase above `$95` ? **39**

    The prefered solution is based on this:

    `df[(df['A'] == X) & (df['B'] > Y)]`
11. How many people have a credit card that expires in `2025`? **1033**

    The preferred solution is based on the usage of `apply` on a `lambda` function that slices the string that contains the expiration date.

12. What are the top 5 most popular email providers/hosts (e.g. gmail.com, yahoo.com, etc...)

    - hotmail.com     1638
    - yahoo.com       1616
    - gmail.com       1605
    - smith.com         42
    - williams.com      37

    The preferred solution is based on the usage of `apply` on a `lambda` function that slices the string that contains the email. The `lambda` function uses `split` to split the string on `@`. Finally, `value_counts` is used to count the occurrences.