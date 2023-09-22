[[0-Ploty Express wprowadzenie]]
[[Plotly express wykresy słupkowe]]

---

# Plotly mapy
```py
import plotly
import plotly_express as px


import pandas as pd
df = pd.read_csv("https://ml-repository-krakers.s3-eu-west-1.amazonaws.com/plotly-course/us-cities-top-1k.csv")

```

```py
fig=px.scatter_mapbox(df, lat='lat', lon='lon', hover_name='City', hover_data=['State', 'Population'], zoom=3)
fig.update_layout(mapbox_style='carto-positron', margin={'r':10, 't':10, 'l':10, 'b':10})
fig.show()
```

![[images/plotly_map_1.png]]




