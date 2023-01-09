
[[0-NumPy wprowadzenie]]
[[NumPy typy danych]]


# Numpy tablice
#python/numpy_array

`np.zeros(shape=(4,10))`

```py
z = np.zeros(shape=(4,10))
print(z)

[[0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]]

```

`z = np.ones(shape=(5,5))`
```py
np.full(shape=(3,3), fill_value=4, dtype='int')
array([[4, 4, 4], 
	   [4, 4, 4],
	   [4, 4, 4]])
```

`np.arrange(10)
`array([0,1,2,3,4,5,6,7,8,9])
`np.arange([start=100, stop=10, setp=-10])`

`np.linspace(start=0, stop=1, num=11])` num - ile elementów równo rozłożonych w tablicy

*zmiana kształt*
```py
A = np.array(15)
A.reshape((3,5)) # 3 podtablice po 5 elementów

```

gdy chcemy, aby Python sam dopasował rozmiar:
```py
A = np.array(15)
A.reshape((3, -1)) # chcę trzy wiersze
A.reshape((-1, 3)) # chcę trzy kolumny

```


# Operacje na tablicach

```py
# muszą mieć ten sam rozmiar
A = np.array([3,1,4,2])
B = np.array([3,-1,3,2])

A+B # -> array([6,0,7,4])
A-B
A*B
A/B
A+3 # -> array([6,4,7,5])
A*2
A+3*B
```

specjalne metody
#python/numpy_matrix_multiplication
```py
np.add(A,B)
np.subtract(A,B)
np.myltiply(A,B)
np.divide(A,B)

# mnożenie po elemencie j.w.

#mnożenie MACIERZOWE
# mnożenie wiersz razy kolumn
# nie jest przemienne
X = np.array([ [1,3], [-2,0]])
Y = np.array([ [6,0], [-1,2]])

np.dot(X,Y)
# X.dot(Y)
# X @ Y
>array([[ 3, 6], [-12, 0]])

```
