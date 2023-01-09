[[0-NumPy wprowadzenie]]

# Indeksowanie, wycinanie

```py
# A[idx], A[start:stop] , A[start:],  A[:stop]

data = np.arange(20)
data = data.reshape(4,5)

[[ 0 1 2 3 4] 
 [ 5 6 7 8 9] 
 [10 11 12 13 14] 
 [15 16 17 18 19]]

# wycinanie wierszy
data[0]
data[1]
# ...

# wycinanie kolumn
data[:,0]
> array([ 0, 5, 10, 15])

data[:,1]
> array([ 1, 6, 11, 16])

data[:,-1]
> array([ 4, 9, 14, 19])

# wycinanie konkretnego elementu
# data[wiersz, kolumna]
data[1,1] # -> 6
data[1:3, 1:2]
> array([[ 6, 7], [11, 12]])


```
