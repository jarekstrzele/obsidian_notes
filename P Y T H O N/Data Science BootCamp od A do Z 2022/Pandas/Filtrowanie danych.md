[[0-Pandas wprowadzenie]]
[[1. Case Study]]

---
# Filtrowanie danych



```py
def fetch_finacial_data(company="UBER"):
"""pobieranie danych doyczących notowań spółek na giełdzie według symboli
 na serwisie stooq.pl"""
 
 import pandas_datareader.data as web

 return web.DataReader(name=company, data_source='stooq')

df=fetch_finacial_data()
df.info()


df['Close_shift'] = df.Close.shift(1)
df['Daily_Change']=df.Close/df.Close_shift -1
df.head()


```

maska logiczna
#python/maska_logiczna 
```py
# wybierz z tej kolumny wartości nieujemne
df_positive = df.Daily_Change > 0
df_positive

"""Date 
2022-03-03 False 
2022-03-02 True
...
"""

# średnia dodatnia
df_positive.Daily_Change.mean()

# rekordy, w których wartość zamknięcia == wartości najwyższej
df[df.Close == df.High]

"""Date 
2022-03-03 False 
2022-03-02 True
...
"""
```

---

```py
df.index

"""DatetimeIndex(['2022-03-03', '2022-03-02', '2022-03-01', '2022-02-28',..."""

#python/maska_logiczna

df.index > '2019-11-01' #-> maska logiczna
df[df.index>'2019-11-01'] # -> wszystkie sesje po 11.01.2019

#python/koniunkcja &
#python/alternatywa |
df[(df.index >= '2019-11-01') & (df.index < '2019-11-15')]


```

```
# df.index.month
#python/maska_logiczna 
# tylko maj ze wszystkich lat
df[df.index.month == 5]

# tylko rok 2019
df[df.index.year == 2019]
```
