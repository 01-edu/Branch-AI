# Exercise 1 Pandas plot 1

The goal of this exercise is to learn to create plots with use Pandas. Panda's `.plot()` is a wrapper for `matplotlib.pyplot.plot()`.

Here is the data we will be using:

```python
        df = pd.DataFrame({
        'name':['christopher','marion','maria','mia','clement','randy','remi'],
        'age':[70,30,22,19,45,33,20],
        'gender':['M','F','F','F','M','M','M'],
        'state':['california','dc','california','dc','california','new york','porto'],
        'num_children':[2,0,0,3,8,1,4],
        'num_pets':[5,1,0,5,2,2,3]
        })
```

1. Reproduce this plot. This plot is called a bar plot

![alt text][logo]

[logo]: ./w1day03_ex1_plot1.png "Bar plot ex1"

The plot has to contain:

- the title
- name on x-axis
- legend