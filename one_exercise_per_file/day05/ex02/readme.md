# Exercise 2

The goal of this exercise is to learn to use Pandas on Time Series an on Financial data.

The data we will use is Apple stock.

1. Using `Plotly` plot a Candlestick

2. Aggregate the data to **last business day of each month**. The aggregation should consider the meaning of the variables. How many months are in the considered period ?

3. When comparing many stocks between them the metric which is frequently used is the return of the price. The price is not a convenient metric as the prices evolve in different ranges. The return at time t is defined as

- (Price(t) - Price(t-1))/ Price(t-1)

Using the open price compute the **daily return**. Propose two different ways **without for loop**.

