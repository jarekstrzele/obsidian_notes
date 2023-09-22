

# Numpy wprowadzenie

#python/numpy
[numpy.com](numpy.com)

Colab ma tę bibliotekę
`pip install numpy`

[[NumPy typy danych]]
[[NumPy tablice]]
[[Numpy liczby pseudolosowe]]
[[NumPy funkcje]]
[[NumPy indeksowanie wycinanie]]
[[NumPy iteracja]]
[[NumPy wektory]]

---
`import numpy as np`
`np.__version__`

`dir(np)`
`help(np.array)`
*W numpy podstawową strukturą jest jednorodna i wielowymiarowa array*

wymiary=osie=axis

## 1D
tablica jednowymiarowa:
`x = np.array([1,3])`
`type(x)` -> `numpy.ndarray`
`x.ndim` -> zwraca wymiar tablicy `1`
`x.shape` -> `(2,)` rozmiar
`x.size` -> liczba elementów `2`
`x.dtype` -> `dtype('int64')`

## 2D
```py
x = np.array([ [1,2], [-3,1] ])`
x.ndim  #-> 2
x.shape #-> (2,2)
x.dtype
```


## 3D
```py
x = np.array([
	[[4,3,2],
	 [3,1,2]],

	 [[4,1,3],
	  [4,2,1]]
])
```



























