# Exercise 4 Matplotlib 2

The goal of this plot is to learn to use Matplotlib to plot different lines in the same plot on different axis using `twinx`. This very useful to compare variables in different ranges.

Here is the data:

```python
left_data = [5, 7, 11, 13, 17]
right_data = [0.1, 0.2, 0.4, 0.8, -1.6]
x_axis = [0.0, 1.0, 2.0, 3.0, 4.0]
```

1. Reproduce this plot

![alt text][logo_ex4]

[logo_ex4]: ./w1day03_ex4_plot1.png "Twin axis plot ex4"

The plot has to contain:

- the title
- name on left y-axis and right y-axis
- **style**:
  - left data in black
  - right data in red