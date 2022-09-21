[[0-Ploty Express wprowadzenie]]
[[Plotly express Iris]]

Wykresy w plotly są dynamiczne.


```py
import ploty
import plotly.express as px
df = px.data.tips()
```


---

```py
px.scatter(data_frame=df, x='total_bill', y = 'tip', facet_col='day', category_orders={'day': [ 'Thur', 'Fri', 'Sat', 'Sun']}, trendline='ols', color='smoker')
```

![[images/plotly_tips_1.png]]



```py
px.scatter(data_frame=df, x='total_bill', y = 'tip', facet_row='time', trendline='ols', color='smoker')
```


![[images/plotly_tips_2.png]]


Do Danych KATEGORYCZNYCH

```py
px.parallel_categories(data_frame=df, color='size')
```

![[images/plotly_tips_cat.png]]





