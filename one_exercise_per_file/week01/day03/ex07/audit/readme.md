1. This question is validated if the plot is in the image is reproduced given those criteria:

The plot has to contain:

- the title
- the legend

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
