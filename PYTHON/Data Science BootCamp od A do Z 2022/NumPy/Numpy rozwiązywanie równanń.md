
[[0-NumPy wprowadzenie]]
[[Numpy macierze]]
[[NumPy wektory]]]

# Rozwiązywanie równań

$$a1x1 + a2xx2 = b1$$
a - współczynniki
x - niewiadome
b - wyrazy wolne

rozdzielamy te trzy elementy zapisując je jako 
- macierze współczynników, 
- macierze/wektor niewiadomych,
-  macierze/wektor wyrazów wolnych -> w skrócie
$$AX = B $$

Jeżeli macierz układu A jest macierzą kwadratową, tooznaczoność układu jest równoważna jej odwracalności:
$$AX = B $$
$$A^{-1}AX = A^{-1}B$$
$$X = A^{-1}B$$

przykład
$$
\begin{cases}
2x+4y = 10 \\
x-y = -1
\end{cases}
$$
```py
A = np.array([[2,4], [1,-1]])
B = np.array([[10],[-1]])
A_inv = np.linalg.inv(A)
X = np.dot(A_inv, B)

print(X)
#> [[1.] [2.]]
```










