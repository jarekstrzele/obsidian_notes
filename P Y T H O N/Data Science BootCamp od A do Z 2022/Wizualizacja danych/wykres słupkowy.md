[[0-Plotly]]

## Wykres słupkowy
#wykres_slupkowy 
```py
fig = go.Figure(
    data=go.Bar(y=[2,3,1,4]),
    layout=go.Layout(title={'text': 'Wykres słupkowy'}) )
fig.show()

# paramet title można zamienić na title_text='Wykres słupkowy'
```

![[images/plotly_plotly_slupkowy.png]]

Można taki wykres zapisać jako html, i taki wykres pozostanie interaktywny
`fig.write_html('nazwa.html')`

---
