# Macierze
[[NumPy wektory]]
[[0-NumPy wprowadzenie]]
[[Numpy rozwiązywanie równanń]]



#python/matrix
#python/linear_algebra
## Mnożenie macierzy

warunki do spełnienia, aby można było mnożyć macierz
*liczba kolumn w lewej macierzy musi zgadzać się z liczbą wierszy prawej macierzy*

_mnożenie macierzy nie jest przemienne!_
$$
AB \neq BA
$$

mnożymy wiersz razy kolumnę

$$
\begin{bmatrix}  
 5 & 3  \\
 3 & 9  
\end{bmatrix}  * 

\begin{bmatrix}  
  1 \\
 -1  
\end{bmatrix}=

\begin{bmatrix}  
 5  \\
 -6  
\end{bmatrix}  * 
$$


`5*1 + 3*(-1) = 5-3 = 2`
`3*1 + 9*(-1) = 3-9 = -6`

```py
X = np.array([[5,3], [3,9]])
Y = np.array([[1],[-1]])

print(X)
print(Y)
# > [[5 3] [3 9]] 
# > [[ 1] [-1]]

Z = np.dot(X,Y)
print(Z)
# > [[ 2] [-6]]

```

macierz wynikowa będzie rozmiaru:
- ilość wierszy pierwszej macierzy
- razy ilość kolumn drugiej 
- `m x n`  oraz   `n x k` to rozmiar `m x k`
- 


 ## Wyznacznik macierzy
mamy macierz kwadratową `n x n`
symbol wyznacznika `|A|` lub `det A`
$$
det A =
\begin{bmatrix}
a11 & a12 \\
a21 & d22 


\end{bmatrix} = a11a22-a12a21
$$
przy `3x3`
najpierw mnożymy poprzekątnych i dodajemy a potem odejmujemy


```py
A = np.array([[2,4], [-1,3]])
round(np.linalg.det(A))
# > 10
```

## Ślad macierzy
macierz kwadratowa
ślad to suma elementów na przkątnej
symbol `tr(A)`

$$
tr(A)=
\sum_{i=1}^n a_{ii} = a_{11} + a_{22} + ... + a_{nn}
$$

```py
A = np.array([[2,4], [-1, 3]])
np.trace(A)
```

 ## Macierz jednostkowa
macierz jednostkowa to macierz kwadratowa, której współczynniki podane są wzorem:
$$
a_{ij} =\begin{cases}  
 1 &\text{if } i=j \\  
 0 &\text{if } i\neq j
\end{cases}
$$


$$
I_1=\begin{bmatrix}
1
\end{bmatrix}
$$

$$
I_1=\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$
```py
np.eye(5, dtype='int')
```


## Macierz odwrotna
A - macierz kwadratowa n stopnia. Macierz A ma macierz odwrotną, gdy istnieje macierz B, taka że
$$
AB = BA = I
$$

```py
A = np.array([[2,4], [-1,3]])
B = np.linalg.inv(A)
print(B)
# >[[ 0.3 -0.4] [ 0.1 0.2]]
```


## Macierz transponowana
zamiana wierszy na kolumny i kolumn na wiersze

$$A=
\begin{bmatrix}
2 & 4 \\
-1 & 3
\end{bmatrix}
, A^T=
\begin{bmatrix}
2 & -1 \\
4 & 3
\end{bmatrix}
$$
```py
A = np.array([[2,4], [-1,3]])
# print(np.transpose(A))
print(A.T)

# >[[ 2 -1] [ 4 3]]
```






















