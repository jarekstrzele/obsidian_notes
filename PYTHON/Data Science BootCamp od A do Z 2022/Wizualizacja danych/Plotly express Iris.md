[[0-Ploty Express wprowadzenie]]
[[Plotly express tips]]

---

wczytujemy dane 'Iris'
```py
df = px.data.iris()
df.head()
```

`px.scatter(pandasObject, x, y)`

```py
px.scatter(df,
		x='sepal_length', 
		y='sepal_width', 
		width=500, 
		height=400)
		
```

![[plotly_1.png]]


`px.scatter(df, x='sepal_length', y='sepal_width', width=700, height=400, color='species')`

![[plotly_2.png]]

`px.scatter(df, x='sepal_length', y='sepal_width', width=700, height=400, color='species', marginal_x='violin')`

![[plotly_3.png]]


`px.scatter(df, x='sepal_length', y='sepal_width', width=700, height=400, color='species', marginal_x='violin', marginal_y="box", title="Iris", trendline='ols')`

![[plotly_4.png]]



`px.scatter_matrix(data_frame=df, dimensions=['sepal_length', 'sepal_width', 'petal_length', 'petal_width'], color='species', title='Scatter matrix')`
![[plotly_5.png]]


wykres współrzędnych rówoległych
` px.parallel_coordinates(data_frame=df, color="species_id")`

![[plotly_6.png]]

---






