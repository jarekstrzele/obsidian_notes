[[0-Ploty Express wprowadzenie]]
[[Plotly express tips]]

---

# Plotly - tworzenie animacji

```py
px.scatter(df.query('year== 2007'), x='gdpPercap', y='lifeExp', size='pop', color='continent', log_x=True, hover_name='country', size_max=60)
```

![[images/plotly_anim_1.png]]

```py
px.scatter(df, x='gdpPercap', y='lifeExp', size='pop', color='continent', log_x=True, hover_name='country', size_max=60, animation_frame='year', range_y=[25,90])
```

![[images/plotly_anim_2.png]]

```py
px.scatter(df, x='gdpPercap', y='lifeExp', size='pop', color='continent', log_x=True, hover_name='country', size_max=60, animation_frame='year',
           range_y=[25,90], facet_col='continent', animation_group='country')
```

![[images/plotly_anim_3.png]]


```py
px.line(data_frame=df.query("continent=='Europe'"), x='year', y='pop', color='country')
```

![[images/plotly_lin.png]]















