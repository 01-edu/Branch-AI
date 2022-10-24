# Exercise 2  **Electric power consumption**

The goal of this exercise is to learn to manipulate real data with Pandas.

The data set used is [**Individual household electric power consumption**](https://assets.01-edu.org/ai-branch/piscine-ai/household_power_consumption.txt)


1. Delete the columns `Time`, `Sub_metering_2` and `Sub_metering_3`
2. Set `Date` as index
3. Create a function that takes as input the DataFrame with the data set and returns a DataFrame with updated types:

    ```python
        def update_types(df):
            #TODO
            return df
    ```

4. Use `describe` to have an overview on the data set
5. Delete the rows with missing values
6. Modify `Sub_metering_1` by adding 1 to it and multiplying the total by 0.06. If x is a row the output is: (x+1)*0.06
7. Select all the rows for which the Date is greater or equal than 2008-12-27 and `Voltage` is greater or equal than 242
8. Print the 88888th row.
9. What is the date for which the `Global_active_power` is maximal ?
10. Sort the first three columns by descending order of `Global_active_power` and ascending order of `Voltage`.
11. Compute the daily average of `Global_active_power`.