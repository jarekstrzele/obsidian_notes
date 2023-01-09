[[_ Wstęp Pandas Data Science]]


---
# Series struktury danych
#python/series 
pyder
> Tools -> Preferences -> Editor -> Run code -> zaznaczyć pole Copy full cell contents to the console when running code cells

`Series` najbardziej podobne do kolumny w excelu

praca w *Spyder*

```python
import pandas as pd
import numpy  as np 

# Example 1
s = pd.Series(4)

# Example 2
s_def = pd.Series(data=[21,34,54], index=['adam', 'tomek', 'pawel'], 
                  name='age')
```
index | age
--- | ---
adam | 21
tomek | 34
pawel | 54

```python

# %% Example 3 shift + enter uruchamia tę część
A = np.random.randn(10) # rozkład normalny 
s = pd.Series(A)


# %% Example 4
stocks = {'Apple':'USA', 'CD Project': 'Poland', 'Amazon':'USA'}
series = pd.Series(stocks, name='country')
```
index|country
--- | ---
Apple | USA
CD Project | Poland
Amazon | USA


```python
# %% Example 5
stocks_price = {'Apple':196, 'CD Projekt': 215, 'Amazon': 1877}
stocks_price_series = pd.Series(stocks_price, name='price')

stocks_price_array = stocks_price_series.values # return ndarray

apple_price = stocks_price_series['Apple']

'Apple' in stocks_price_series


```

```python
# %% Example 6
np.random.seed(0)

A = np.random.randn(20)
s = pd.Series(A)


s[0]
s[5:10]
```

---
# Podstawowe operacje na obiektach Series

```python
#!/usr/bin/env python3

import pandas as pd
import numpy as np


# generation some data
np.random.seed(0)

A = np.random.randint(0,10, 10)
series = pd.Series(A, name="los") # name="los" nazwa dla 


print(series.dtype) # jakie typy są elementami
print(series.iloc[3]) # wycinanie element z indeksem 3
print(series.iloc[-1])
print(series.index) #  RangeIndex(start=0, stop=10, step=1)
print(series.name) # los

# konwersja z pandas na numpy array
array_A = series.values

# %% dwie tablica z rozkładu normalnego
N = np.random.randn(10) # numpy.ndarray
M = np. random.randn(10)


series_N = pd.Series(N)
series_M = pd.Series(M)


# %% basic methods
series_N.abs()
series_N.add(series_M) # dodawanie elementów do siebie
series_N.divide(series_M)
series_N.subtract(series_M)

# wyrzucanie duplikatów
series.drop_duplicates()

# element na czwartym indeksie będzie miał brak wartości
series[4] = np.nan
series.dropna() # series bez zmian, ale wyświetla bez wartości nan

# wyciągnij indeks wartości największej
series.idxmax()
series.idxmin() # indeks najmniejszej wartości

series.count() # zlicza ilość wartości, nie uwzględnia nan


series_N.cumsum() # sumowanie kumulatywne
series_N.cummin()
series_N.cummax()

# zlicza częstość występowania wartości
# i sortuje w kolejność od najczęściej występującej
series.value_counts() 

series.sum()
series.std() # odchylenie standardowe
series.describe() # zestaw statystyk


```


---
### histogram

```python
# %% histogram
import matplotlib 
hist_data = pd.Series(np.random.randn(10000))
hist_data.hist(bins=100, color='red') # bins ilość pionowych słupków

```

----
```python

# %% top n
top_3 = series_N.nlargest(3) # najlepsze wartości
bottom_4 = series_N.nsmallest(4) # 4 najgorsze wartości

q_1 = series_N.quantile(0.25)
q_2 = series_N.quantile(0.5)

series_N.round(3)

# przesuwanie wartość o n rzędów do dołu
shift_1 = series.shift(3)
# przesuń o dwa, a NaN zastąp zerem
shift_2_replace_0 = series.shift(2).fillna(0) 

# %% sort
# sortowanie rosnące
sorted_series = series.sort_values()
# sortowanie malejące
sorted_series = series.sort_values(ascending=False)





```

----
## agregacje
```python
import pandas as pd
import numpy as np

# %%

np.random.seed(0)
s = pd.Series(np.random.randn(20))

# %% aggragate

minimum = s.aggregate(min)
maximum = s.aggregate(max)
sum = s.aggregate(sum) 

mean = s.aggregate(np.mean)
std  = s.aggregate(np.std)

# w obiekcie Series 'stats' zapisane będą statystyki
stats = s.aggregate(['min', 'max', 'sum', 'mean']) 

# statystki przez odwołanie się do funkcji w numpy
stats_np = s.aggregate([np.mean,np.std, np.median])
```

---
## metoda `apply()`
```pyhton

import pandas as pd
import numpy as np

# %%

np.random.seed(0)
# sigma = 10, mean = 5
s = pd.Series(10 * np.random.randn(20) + 5)

# %%
s.apply(abs)
s.apply(float.is_integer)
s.apply(int) # konwersja danych na int

s.apply(lambda x: 100 *x) # pomnożenie każdego elementu s przez 100
s_norm = s.apply(lambda x: x - np.mean(x - np.mean(s)) / np.std(s))


sigmoid = s_norm.apply(lambda x: 1 / (1 + np.exp(x)))


def more_complex(x):
    import math
    return math.sqrt(np.exp(x))

s.apply(more_complex)

```

---
## Import/export danych
ze strony https://stooq.pl/q/d/?s=rcrcdpro0623.pl pobieramy dane historyczne jako plik csv





