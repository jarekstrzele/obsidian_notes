[[0-Plotly]]



---

## Wykres kołowy i pierścieniowy
#wykres_kolowy
#wykres_pierscieniowy
/
```
from seaborn import load_dataset
df = load_dataset('diamonds')
```

`df.cut.value_counts()`
->
```
Ideal        21551
Premium      13791
Very Good    12082
Good          4906
Fair          1610
```

`df = df.reset_index()`
->
```
    index   	cut
0	Ideal	    21551
1	Premium	    13791
2	Very Good	12082
3	Good	    4906
```

zmieniamy nazwy kolumn
`dff.columns = ['type','count']`

```py
fig = go.Figure(
    data = go.Pie(labels=dff['type'], values=dff['count']),
    layout=go.Layout(title_text="Rozkłąd zmiennej cut", width=800)
)
fig.show()
```

![[plotly_kolowy.png]]

__WYKRES PIERŚCIENIOWY__
dodajemy parametr hole w klasie Pie
```py
fig = go.Figure(
    data = go.Pie(labels=dff['type'], values=dff['count'], hole=0.4),
    layout=go.Layout(title_text="Rozkłąd zmiennej cut", width=800)
)
fig.show()
```

![[plotply_pierscien.png]]
