[[0-Pandas wprowadzenie]]
[[1. Case Study]]
[[Zapis odczyt danych CSV, XLSX]]

### London bike
```py
import pandas as pd
import numpy as np

df = pd.read_csv('london_bike.csv')

```

ustalamy indeks:
`df = df.set_index('timestamp')`

# Łączenie danych
```py
def fetch_finacial_data(company="AMZN"):

 import pandas_datareader.data as web

 return web.DataReader(name=company, data_source='stooq')


apple=fetch_finacial_data("AAPL")
amazon=fetch_finacial_data("AMZN")
google=fetch_finacial_data("GOOGL")
uber=fetch_finacial_data("UBER")

```

dodajemy prefix do nazw column
```py
apple.columns = ['app_' + col.lower() for col in apple.columns]
amazon.columns = ['amazon_' + col.lower() for col in apple.columns]
google.columns = ['google_' + col.lower() for col in apple.columns]
uber.columns = ['ubber_' + col.lower() for col in apple.columns]

```

**concat**
```py
df = pd.concat(objs=[apple, amazon, google, uber], axis=1)`

# ustawiamy sposób formatowania
pd.set_option('display.float_format', lambda x: f'{x:.2f}')

df.describe().T

# korelacja poszczególnych zmiennych
df.corr()
```
**korelacja danych z kolumny Close**
```py
closes = [col for  col in df.columns if col.endswith('close')]
# ['app_close', 'amazon_app_close', 'google_app_close', 'ubber_app_close']

df[closes].corr()
```

## Metoda APPEND
pozwala dołączać elementy do obiekty dataframe

```py
uber.head()
Date
2022-03-04 31.50 31.73 29.27 29.83 52160494
2022-03-03 34.22 34.29 31.41 31.72 38337646
2022-03-02 34.00 34.22 32.97 34.042 6112459
...
```

wytniemy czerwcowe dane i lipcowe'
i połączymy je, o ile kolumny są te same
```py
uber_6 = uber[uber.index.month == 6]
uber_7 = uber[uber.index.month == 7]

uber_6_7 = uber_6.append(uber_7)
```

