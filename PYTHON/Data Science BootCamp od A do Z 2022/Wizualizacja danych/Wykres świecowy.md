[[0-Plotly]]
#python/plotly 

---

# Wykres świecowy

```py
def fetch_financial_data(company="AMZN"):
  import pandas_datareader.data as web
  return web.DataReader(name=company, 
            data_source="stooq")


df = fetch_financial_data()
df = df.reset_index()
df = df[df.Date >'2019-01-01']
df.head(3)
	
```

```py
fig = go.Figure(data=go.Candlestick(x=df.Date, open=df.Open, high=df.High, low=df.Low, close=df.Close))
fig.show()
```

![[wykres_świecowy.png]]










