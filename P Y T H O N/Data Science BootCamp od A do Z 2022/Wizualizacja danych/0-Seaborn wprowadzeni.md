
[[0-Matplotlib wprowadzenie]]

---

# Seaborn
#python/seaborn
biblioteka do wizualizacji danych
to wysoko poziomowy interfejs dla biblioteki matplotlib

```py
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

sns.set()

df.columns ## ->
# Index(['total_bill', 'tip', 'sex', 'smoker', 'day', 'time', 'size'], dtype='object')


```

```py
# ładujemy wbudowany zbiór danych o napiwkach
df = sns.load_dataset('tips')
df.head(10)

df.describe() # -> statystyki numeryczne
df.describe(include=['category']) # -> statystyki typu 'category'


```

---
# Dane o napiwkach


## Wykresy liniowe
wykres rozrzutu zmiennej `tip` i `total_bill`
`sns.relplot(data=df, x='total_bill', y='tip')`

![[images/seaborn_relplot_tip_total_bill.png]]

zmiana wielkości _font_
#python/seaborn_font
`sns.set(font_scale=1.2)`


dodanie nowego parametru `size` wielkość kropki, którą uzależnimy od wielkości grupy oraz parametrem `hue` zmienimy kolor
`sns.relplot(data=df, x='total_bill', y='tip', size='size', hue='size')`

![[images/seaborn_relplot_tip_total_bill_2.png]]
rozbijemy nasz wykres na dwa ze względu na czas `time`
`sns.relplot(data=df, x='total_bill', y='tip', size='size', hue='size', col='time')`

![[images/seaborn_relplot_tip_total_bill_3.png]]
Możemy rozbić również na wiersze; np. dotatkowo ze względu na palenie
`sns.relplot(data=df, x='total_bill', y='tip', size='size', hue='size', col='time')`

![[images/seaborn_relplot_tip_total_bill_4.png]]

---

## Wykresy typowe dla zmiennych kategorycznych

`_ = sns.catplot(data=df, x='day', y='total_bill')`

![[images/seaborn_catplot_1.png]]
dodatkowy parametr `kind` zmienia wygląd wykresy (np. `kind='box' ; kind='swarm' ; kind='violin'  ; kind='bar'`)

Wizualizacja częstości dnia
`_ = sns.catplot(data=df, x='day', y='total_bill')`

![[images/seaborn_catplot_2.png]]
W piątek (Fri) jest najmniej klientów

---
# Dane z katastrofy Tytanica
```py
df.sns.load_dataset('titinic')
df.head()

```

częstotliwość występowanie pokładu, z nową paletą kolorów
`sns.catplot(data=df, x='deck', kind='count'`

![[images/seaborn_catplot_titanic_1.png]]

## Iris
wykres pairplot z kolorowanie ze wględu na gatunek
`sns.pairplot(data=df, hue='species')`

![[images/seaborn_catplot_iris_1.png]]









