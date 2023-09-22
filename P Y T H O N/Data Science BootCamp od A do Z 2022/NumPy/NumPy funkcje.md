[[0-NumPy wprowadzenie]]

`np.exp(1)`
`np.sqrt(9)`

*czy wszystkie elementy są prawdziwe?*
`np.all([1,3,2])` -> True
`np.all([1,3,0])` -> False

*Czy przynajmniej jeden elem jest prawdzuwy?*
`np.any([1,0,0,])` -> True
`np.any([0,0,0])` -> False


```py
A = np.random.rand(5)

# argmax -> index najwyższej wartości
np.argmax(A)
A[np.argmax(A)] # -> najwyższa wartość

np.argmin(A)
np.argsort(A) # -> zwraca tabl z indeksami od najmniejszej wartości do największej

np.max(A)
np.min(A)
np.mean(A)
np.median(A)
np.std(A) # odchylenie standardowe

```









