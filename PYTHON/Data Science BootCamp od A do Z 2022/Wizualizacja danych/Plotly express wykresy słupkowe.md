[[0-Ploty Express wprowadzenie]]
[[plotly_wykr_powierz.png]]
[[Plotly express mapy]]

---

# Plotly wykresy słupkowe
#wykres_slupkowy
```py
import plotly
import plotly.express as px

from seaborn import load_dataset
df = load_dataset('flights')
df.head()
```



```py
px.bar(data_frame=df, x='year', y='passengers', color='year')
```

![[plotly_slup_1.png]]


```py
px.bar(data_frame=df, y='year', x='passengers', color='year', orientation='h')
```

![[plotly_slup_2.png]]

#histogram

HISTOGRAM
`px.histogram(df, x='passengers', nbins=50)`





