[[0-NumPy wprowadzenie]]
[[NumPy tablice]]

---
# Liczby pseudolosowe

*ziarno losowań*
`np.random.seed(0)

*losowa wartość z  rozkładu normalnego*
`np.random.randn()`

tablica 10 elementowa rozkładu normalnego
`np.random.randn(10)`

matryca
`np.random.randn(10,4)`


*rozkład jednostajny na przedziale*
`np.random.rand() ` # wartość losowa z <0,1]
`np.random.rand(10,2)` # (wiersze, kolumny)

*randint*
`np.random.randint(10)` zwraca <0,10]
`np.random.randint(low=10, high=101)`
`np.random.randint(low=10, high=101, size=10)` -> lista 10 elementowa


*choice*
wybiera losowo element z obiektu iterowalnego
`np.random.choice([4,2,1,6])`
`np.random.choice(['java', 'python', 'sql'])`

*shuffle przetasowanie*
zmienia zawartość obiektu!!
`data = np.arange(10)`
`np.random.shuffle(data)




