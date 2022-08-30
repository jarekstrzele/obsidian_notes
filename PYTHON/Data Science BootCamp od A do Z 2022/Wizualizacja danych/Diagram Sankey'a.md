[[0-Plotly]]
[[Wykres świecowy]]

---
# Diagram Snakey


```py
data = [go.Sankey(node=dict(label=['Nonchurn_2018', 'Churn_2018', 'Nonchurn_2019', 'Churn_2019']),
                  link=dict(source=[0,0,1,1], # indeks odpowiadający etykiecie (labels)
                        target=[2,3,2,3],
                        value=[65,12,18,5]
                   ))]
fig = go.Figure(data=data, layout=go.Layout(width=800, height=400))
fig.show()
```

![[Snakey.png]]








