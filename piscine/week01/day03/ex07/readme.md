# Exercise 7 Plotly Box plots

The goal of this exercise is to learn to use Plotly to plot Box Plots. It is t is a method for graphically depicting groups of numerical data through their quartiles and values as min, max. It allows to compare quickly some variables.

Let us generate 3 random arrays from a normal distribution. And for each array add respectively 1, 2 to the normal distribution.

```python
y0 = np.random.randn(50)
y1 = np.random.randn(50) + 1 # shift mean
y2 = np.random.randn(50) + 2
```

1. Plot in the same Figure 2 box plots as shown in the image. In this exercise the style is not important.

![alt text][logo_ex7]

[logo_ex7]: ./w1day03_ex7_plot1.png "Box plot ex7"

The plot has to contain:

- the title
- the legend

https://plotly.com/python/box-plots/
