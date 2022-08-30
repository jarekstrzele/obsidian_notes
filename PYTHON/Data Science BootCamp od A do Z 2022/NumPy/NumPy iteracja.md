[[0-NumPy wprowadzenie]]

```py
A = np.arange(20)
A = A.reshape(4,5)

# działanie odwrotne do reshape
# ravel()
# A.ravel()

for row in A:
	print(row)

for row in A:
	print(row[0])

for item in A.flat:

	print(item) # jeden ciąg wszystkich elementów

# transponowanie macierzy
# zamiana kolumn na wiersze
A.T


```


**maski logiczne**
#python/maska_logiczna
```py
A = np.arange(start=-10,stop=10,step=0.5)
A = A.reshape(10,-1) # mamy 10 rows

# chcemy wiedzieć,gdzie są wartości większe od 0
A > 0 # dostajemy array z False, True, to jest maska
A[A>0] # -> array z elementami > 0
```

jeżeli chcielibyśmy więcej warunków:
```py
A[np.bitwise_and(A > -5, A < 5)]
A[np.bitwise_or(A > -5, A < 5)]

```
