[[0-Pandas wprowadzenie]]

---

# SERIES
#python/series
```py
s = pd.Series(data=[3,2,4,6])
s

#  0 3
#  1 2
#  2 4
#  3 6
#  dtype: int64
```

## zmiana indeksów i nadanie nazwy obiektowi
```py
s = pd.Series(data=[3,2,4,6], index=['a','b','c','d'], name='sample')
s
#  a 3
#  b 2
#  c 4
#  d 6
#  Name: sample, 
# dtype: int64

```

## Wstawianie braków danych
#python/nan
NaN - nie jest wstawiane do wyliczeń
```py
import numpy as np

s=pd.Series(data=[3, np.nan,4,6], index=['a','b','c','d'], name='sample')

print(s)

```

series typu Bool
#python/bool
```py
s = pd.Series(data=[True,False, False])

```

## Obiekt series, którego indeksami są daty
```py
# np array 10-19
s = pd.Series(data=np.arange(10,20),
index=pd.date_range(start='20200101', periods=10))
print(s)

# 
# 2020-01-01 10 2020-01-02 11 # # 2020-01-03 12 2020-01-04 13 # # 2020-01-05 14 2020-01-06 15 # # 2020-01-07 16 2020-01-08 17 # # 2020-01-09 18 2020-01-10 19 # Freq: D, dtype: int64

s.index
# DatetimeIndex(['2020-01-01', '2020-01-02', '2020-01-03', '2020-01-04', '2020-01-05', '2020-01-06', '2020-01-07', '2020-01-08', '2020-01-09', '2020-01-10'], dtype='datetime64[ns]', freq='D')
```

```py
import pandas as pd

s = pd.Series(data=['python', 'java', 'sql'], name = 'languages')

s

# 0 python 
# 1 java 
# 2 sql 
# Name: languages, dtype: object
```

## Atrybuty
### index
```py
s = pd.Series(data=['python', 'java', 'sql'], name = 'languages')

s.index # RangeIndex(start=0, stop=3, step=1)


```

### values
```py
s.values
# array(['python', 'java', 'sql'], dtype=object)

```

### dtypes
```py
s.dtypes
# dtype('O')

```

### shape
`s.shape`

---
## wycinanie
```py
price = pd.Series(data={'Apple': 200, 'CD Project': 60, 'Amazon':1900})
price

# Apple 200 
# CD Project 60 
# Amazon 1900 
# dtype: int64
```

```py
price['CD Procject'] # -> 60
price[1] # -> 60
```

## zliczanie
`np.nan` występowanie wartości `NaN` nie będzie uwzglęnianie w statystykach.
w funkcji `values_counts(dropna=False)` spowoduje również zliczanie wystąpień `NaN`
#python/nan 
[[Numpy funkcje statystyczne]]

```py
price.count() # -> 3

# zliczanie ile razy wystąpił dany element
price.value_counts()
# 200 1 
# 60 1 
# 1900 1 
# dtype: int64


price.sum()
price.min()
price.max()
price.std() # odchylenie standardowe

price.describe() # opisuje zestaw statystyk


# zliczanie największych lub najmniejszych
# parametr określa ile ma być zwrócone
price.nlargest(1)
# Amazon 1900
# dtype: int64

price.nsmallest(2)
# CD Project 60 
# Apple 200 
# dtype: int64
``` 


```py
import pandas as pd
import numpy as np
price = pd.Series(data={'Apple': 200, 'CD Project': 60, 'Amazon':1900, 'KGHM':np.nan})

price.rank()
Apple 2.0 
CD Project 1.0 
Amazon 3.0 
KGHM NaN dtype: float64

#python/pandas_sort
price.sort_values()
CD Project 60.0
Apple 200.0 
Amazon 1900.0 
KGHM NaN 
dtype: float64

price.sort_values(ascending=False)
Amazon 1900.0 
Apple 200.0 
CD Project 60.0 
KGHM NaN 
dtype: float64



```

## apply 
#python/pandas_apply
nie zmienia stanu obiektu pierwotnego
```py
# np. konwersja ceny z dolarów na złotówki przy kursie 3.8
price.apply(lambda x: x*3.8)
Apple 760.0 
CD Project 228.0 
Amazon 7220.0 
KGHM NaN 
dtype: float64
```
[[DataFrame]]