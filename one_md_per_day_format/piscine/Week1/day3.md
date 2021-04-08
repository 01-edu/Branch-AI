# D03  Piscine AI - Data Science 


Author: 



# Introduction

While working on a dataset it is important to check the distribution of the data. Obviously, for most of humans it is difficult to visualize the data in more than 3 dimensions

Viz is important to understand the data and to show results. We have already seen there are some basinc viz functionalities in Pandas. 
Now we'll discover two of the most know viz libraries in Python: 
- Pandas viz
- Matplotlib
- Plotly
  

Pandas viz is pratique: rapid plot, relies on Matplotlib. (check matplotlib doc sometimes not all params are detailed in pandas doc)
For more elaborate plots Matplotlib is necessary 

And finaly Plotly is a interactive plot library. 

## Rules
Always a title, legend, ... 

## Ressources 
https://matplotlib.org/3.3.3/tutorials/index.html
https://towardsdatascience.com/matplotlib-tutorial-learn-basics-of-pythons-powerful-plotting-library-b5d1b8f67596

https://github.com/rougier/matplotlib-tutorial
https://jakevdp.github.io/PythonDataScienceHandbook/05.13-kernel-density-estimation.html



# Exercise 1 Pandas plot 1

The goal of this exercise is to learn to create plots with use Pandas. Panda's `.plot()` is a wrapper for `matplotlib.pyplot.plot()`. 

Here is the data we will be using: 

```
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

[logo]: images/day03/w1day03_ex1_plot1.png "Bar plot ex1"
The plot has to contain: 

- the title
- name on x-axis 
- legend

## Correction

1. This question is validated if the plot reproduces the plot in the image. It has to contain a title, an x-axis name and a legend. 
![alt text][logo]

[logo]: images/day03/w1day03_ex1_plot1.png "Bar plot ex1"


## Exercise 2: Pandas plot 2

The goal of this exercise is to learn to create plots with use Pandas. Panda's `.plot()` is a wrapper for `matplotlib.pyplot.plot()`. 


```
        df = pd.DataFrame({
        'name':['christopher','marion','maria','mia','clement','randy','remi'],
        'age':[70,30,22,19,45,33,20],
        'gender':['M','F','F','F','M','M','M'],
        'state':['california','dc','california','dc','california','new york','porto'],
        'num_children':[2,0,0,3,8,1,4],
        'num_pets':[5,1,0,5,2,2,3]
        })
```

1. Reproduce this plot. This plot is called a scatter plot. Do you observe a relationship between the age and the number of children ? 

![alt text][logo_ex2]

[logo_ex2]: images/day03/w1day03_ex2_plot1.png "Scatter plot ex2"
The plot has to contain: 

- the title
- name on x-axis 
- name on y-axis 

## Correction

1. This question is validated if the plot reproduces the plot in the image. It has to contain a title, an x-axis name and an y-axis name. 
You should also observe that  the older people are the bigger the number of children is. 

![alt text][logo_ex2]

[logo_ex2]: images/day03/w1day03_ex2_plot1.png "Scatter plot ex2"




## Exercise 3 Matplotlib 1

The goal of this plot is to learn to use Matplotlib to plot data. As you know, Matplotlib is the underlying library used by Pandas. It provides more options to plot custom visualizations. Howerver, most of the plots we will create with Matplotlib can be reproduced with Pandas' `.plot()`. 


1. Reproduce this plot. We assume the datapoints have integers coordinates. 

![alt text][logo_ex3]

[logo_ex3]: images/day03/w1day03_ex3_plot1.png "Scatter plot ex3"

The plot has to contain: 

- the title
- name on x-axis and y-axis
- x-axis and y-axis are limited to [1,8]
- **style**: 
        
        - red dashdot line with a width of 3
        - blue circles with a size of 12

## Correction 

1. This question is validated if the plot reproduces the plot in the image and respect those criterias

        - the title
        - name on x-axis and y-axis
        - x-axis and y-axis are limited to [1,8]
        - **style**: 
        
                        - red dashdot line with a width of 3
                        - blue circles with a size of 12

![alt text][logo_ex3]

[logo_ex3]: images/day03/w1day03_ex3_plot1.png "Scatter plot ex3"

# Exercise 4 Matplotlib 2
The goal of this plot is to learn to use Matplotlib to plot different lines in the same plot on different axis using `twinx`. This very useful to compare variables in different ranges. 

Here is the data: 

```
left_data = [5, 7, 11, 13, 17]
right_data = [0.1, 0.2, 0.4, 0.8, -1.6]
x_axis = [0.0, 1.0, 2.0, 3.0, 4.0]
```
1. Reproduce this plot
![alt text][logo_ex4]

[logo_ex4]: images/day03/w1day03_ex4_plot1.png "Twin axis plot ex4"
The plot has to contain: 

- the title
- name on left y-axis and right y-axis
- **style**: 
        
        - left data in black
        - right data in red

## Correction 

1. This question is validated if the plot reproduces the plot in the image and respect those criterias

        The plot has to contain: 

        - the title
        - name on left y-axis and right y-axis
        - **style**: 
                
                - left data in black
                - right data in red

![alt text][logo_ex4]

[logo_ex4]: images/day03/w1day03_ex4_plot1.png "Twin axis ex4"

https://matplotlib.org/gallery/api/two_scales.html

# Exercise 5 Matplotlib subplots
The goal of this exerice is to learn to use Matplotlib to create subplots. 

1. Reproduce this plot using a **for loop**: 

![alt text][logo_ex5]

[logo_ex5]: images/day03/w1day03_ex5_plot1.png "Subplots ex5"

The plot has to contain: 

- 6 subplots: 2 rows, 3 columns
- Keep space between plots: `hspace=0.5` and `wspace=0.5`
- Each plot contains

  - Text (2,3,i) centered at 0.5, 0.5. *Hint*: check the parameter `ha` of `text`
  - a title: Title i 

## Correction

1. The question is validated if the plot reproduces the image and the given criterias:

The plot has to contain: 

- 6 subplots: 2 rows, 3 columns
- Keep space between plots: `hspace=0.5` and `wspace=0.5`
- Each plot contains

  - Text (2,3,i) centered at 0.5, 0.5. *Hint*: check the parameter `ha` of `text`
  - a title: Title i 

![alt text][logo_ex5]

[logo_ex5]: images/day03/w1day03_ex5_plot1.png "Subplots ex5"

Check that the plot has been created with a for loop. 

# Exercise 6 Plotly 1
Plotly has evolved a lot in the previous years. It is important to **always check the documentation**. 

Plotly comes with a high level interface: Plotly Express. It helps building some complex plots easily. The lesson won't detail the complex examples. Plotly express is quite interesting while using Pandas Dataframes because there are some built-in functions that leverage Pandas Dataframes. 

The plot outputed by Plotly is interactive and can also be dynamic. 

The goal of the exercise is to plot the price of a company. Its price is generated below. 

```
returns = np.random.randn(50)
price = 100 + np.cumsum(returns)

dates = pd.date_range(start='2020-09-01', periods=50, freq='B')
df = pd.DataFrame(zip(dates, price),
                  columns=['Date','Company_A'])
```

1. Using Plotly express, reproduce the plot in the image. As the data is generated randomly I do not expect you to reproduce the same line. 

![alt text][logo_ex6]

[logo_ex6]: images/day03/w1day03_ex6_plot1.png "Time series ex6"

The plot has to contain: 

- title 
- x-axis name
- yaxis name

2. Same question but now using `plotly.graph_objects`. You may need to use `init_notebook_mode` from `plotly.offline`. 

https://plotly.com/python/time-series/e


## Correction

1. This question is validated if the plot is in the image is reproduced using Plotly express given those criterias:

The plot has to contain: 

- a title 
- x-axis name
- yaxis name
![alt text][logo_ex6]

[logo_ex6]: images/day03/w1day03_ex6_plot1.png "Time series ex6"

2. This question is validated if the plot is in the image is reproduced using `plotly.graph_objects` given those criterias:

The plot has to contain: 

- a title 
- x-axis name
- yaxis name

![alt text][logo_ex6]

[logo_ex6]: images/day03/w1day03_ex6_plot1.png "Time series ex6"

# Exercise 7 Plotly Box plots

The goal of this exercise is to learn to use Plotly to plot Box Plots. It is t is a method for graphically depicting groups of numerical data through their quartiles and values as min, max. It allows to compare quickly some variables. 

Let us generate 3 random arrays from a normal distribution. And for each array add respectively 1, 2 to the normal distribution. 

```
y0 = np.random.randn(50)
y1 = np.random.randn(50) + 1 # shift mean
y2 = np.random.randn(50) + 2
```
1. Plot in the same Figure 2 box plots as shown in the image. In this exercise the style is not important. 

![alt text][logo_ex7]

[logo_ex7]: images/day03/w1day03_ex7_plot1.png "Box plot ex7"

The plot has to contain: 

- the title
- the legend
https://plotly.com/python/box-plots/

## Correction 

1. This question is validated if the plot is in the image is reproduced given those criterias:

The plot has to contain: 

- the title
- the legend

![alt text][logo_ex7]

[logo_ex7]: images/day03/w1day03_ex7_plot1.png "Box plot ex7"


        ```
        import plotly.graph_objects as go
        import numpy as np

        y0 = np.random.randn(50)
        y1 = np.random.randn(50) + 1 # shift mean
        y2 = np.random.randn(50) + 2

        fig = go.Figure()
        fig.add_trace(go.Box(y=y0, name='Sample A',
                        marker_color = 'indianred'))
        fig.add_trace(go.Box(y=y1, name = 'Sample B',
                        marker_color = 'lightseagreen'))

        fig.show()
        ```
