[[0-Ploty Express wprowadzenie]]
[[Plotly express tworzenie animacji]]


---

# Plotly wykresy powierzchniowe
```py
import plotly
import plotly.express as px
```

```py
def fetch_financial_data(company='AMZN'):
  import pandas_datareader.data as web
  return web.DataReader(name=company, data_source='stooq')

df = fetch_financial_data()
df = df.reset_index()
df.head()
```

---


```py
# skala liniowa
# px.area(data_frame=df, x='Date', y='Close')

# skala logarytmiczna
px.area(data_frame=df, x='Date', y='Close', log_y=True, title='WYkres spółki Amazon')
```

![[images/plotly_wykr_powierz.png]]



















