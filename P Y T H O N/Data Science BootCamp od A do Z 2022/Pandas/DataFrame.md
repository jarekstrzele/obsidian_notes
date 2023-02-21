# DataFrame
[[Series]]

**datafrane** to połączone ze sobą obiekty series.

```py
import pandas as pd
df = pd.DataFrame(data=[12,12,32])
# pd.DataFrame(data=[[1,2,3], [22,33,44]])
df

  0
0 12
1 12
2 32
```

```py
df = pd.DataFrame(data=[12,12,32], index=['first','second', 'third'], columns=['col_1'])
df
  
       col_1
first  12
second 12
third  32
```

## DataFrame ze słownika
```py
df = pd.DataFrame(data={'WIG20': ['PKN ORLEN', 'PKO BP'], 'mWIG40': ['Amica', 'Playway']})

df

    WIG20         mWIG40

0   PKN ORLEN    Amica
1   PKO BP       Playway
```


## funkcje dla DataFrame
```py
df = pd.DataFrame(data=[[10,12,32], [23,12,10]], index=['first','second'], columns=['col_1', 'col_2', 'col_3'])

df.index # -> Index(['first', 'second'], dtype='object')
df.values # 0> array([[10, 12, 32], [23, 12, 10]])
df.info()
df.describe()
df.describe().T
```

## wycinanie kolumny

```py
df=pd.DataFrame(data=[[10,12,32], [23,12,10]],
index=['first','second'], columns=['col_1', 'col_2', 'col_3'])

df['col_1'] # -> zwraca obiekt typu pandas.core.series.Series
df.col_1 # -> --||--; problem z nazwą ze spacją 'col 1'
first 10 
second 23 
Name: col_1, dtype: int64

df[['col_1']] # -> zwraca obiekt typu pandas.core.frame.DataFrame
```


## zmiana nazwy kolumn
#python/pandas_loc
#python/pandas/iloc
```py
df.columns # -> Index([nazwy ... kolumn])
df.columns = [ 'a', 'b', 'c']

# dodajemy nową kolumnę
df['d'] = df.a + df.c

# wycinanie po **nazwach**
df.loc['first']
col_1 10 
col_2 12 
col_3 32 
Name: first, dtype: int64

# wycinanie po **indeksie**
df.iloc[0]

# wycinanie loc[nazwa_wiersza, nazwa_kolumny]
df.loc['first', 'col_2']
df.iloc[0,1]
# wycięcie całej kolumny
df.loc[:, 'col_2']
```


[[1. Case Study]]








