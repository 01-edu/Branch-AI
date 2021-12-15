##### The solution of question 1 is accepted if the plot reproduces the plot in the image and respect those criteria. The code below shows a solution. 

###### Does it have a the title ? 
###### Does it have a legend ?

![alt text][logo_ex7]

[logo_ex7]: ../w1day03_ex7_plot1.png "Box plot ex7"

```python
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
