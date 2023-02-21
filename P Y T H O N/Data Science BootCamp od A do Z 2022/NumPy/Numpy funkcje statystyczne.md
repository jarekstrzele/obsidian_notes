[[0-NumPy wprowadzenie]]
#python/statistics


```py

price = np.array([ [12.40, 12.80, 11.90, 12.60, 1000],

 [12.50, 13.00, 11.70, 12.20, 2000],

 [12.20, 13.40, 12.20, 13.20, 1500]])

# suma wszystkich elementów
price.sum()

#suma po kolumnach
price.sum(axis=0)

#suma po wierszach
price.sum(axis=1)

```

```py
# min z całości
np.min(price)

# min z kolumn
np.min(price, axis=0)

# tak samo z max

```

```py

# mediana
np.median(price)

# średnia po kolumnach
np.mean(price, axis=0)

# odchylenie standardowe
np.std(price, axis=0)

# wariancja
np.var(price, axis=0)

```