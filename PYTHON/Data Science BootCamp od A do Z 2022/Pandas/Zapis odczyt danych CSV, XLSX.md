[[0-Pandas wprowadzenie]]
[[Łączenie danych]]

# Zapis, odczyt danych CSV, XLSX

## CSV
#python/pandas_csv
```py
import pandas as pd
import numpy as np

def fetch_finacial_data(company="UBER"):
""""pobieranie danych doyczących notowań spółek na giełdzie według symboli na serwisie stooq.pl"""
 import pandas_datareader.data as web

 return web.DataReader(name=company, data_source='stooq')

df = fetch_finacial_data("FB")
df.head()

```


```py
df.to_csv("name.csv")

df_nov = df[(df.index.month==11) & (df.index.year==2019)]
df_nov.to_csv('fb_nov.csv')
```

```py

new_df = pd.read_csv('nazwa.csv')

# można określić, która kolumna będzie indeksem
new_df = pd.read_csv('nazwa.csv', index_col=0)


```

## Excel

#### to excel
`df.nov.to_excel('nazwa.xlsx)'`

#### from excel
`new_df = pd.read_excel('nazwa.xlsx')` # -> nie ma określonego indeksu

`new_def=pd.read_excel('nazwa.xlsx', index_col=0)` # -> pierwsza kolumna będzie indeksem


