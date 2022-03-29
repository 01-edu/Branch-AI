## Exercise 2: Pandas plot 2

The goal of this exercise is to learn to create plots with use Pandas. Panda's `.plot()` is a wrapper for `matplotlib.pyplot.plot()`.

```python
        df = pd.DataFrame({
        'name':['christopher','marion','maria','mia','clement','randy','remi'],
        'age':[70,30,22,19,45,33,20],
        'gender':['M','F','F','F','M','M','M'],
        'state':['california','dc','california','dc','california','new york','porto'],
        'num_children':[4,2,1,0,3,1,0],
        'num_pets':[5,1,0,2,2,2,3]
        })
```

1. Reproduce this plot. This plot is called a scatter plot. Do you observe a relationship between the age and the number of children ?

![alt text][logo_ex2]

[logo_ex2]: ./w1day03_ex2_plot1.png "Scatter plot ex2"

The plot has to contain:

- the title
- name on x-axis
- name on y-axis