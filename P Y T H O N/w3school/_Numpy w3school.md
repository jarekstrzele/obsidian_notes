[[NumPy Array Slicing]]

# Numpy w3school

- numpy is a Python library written in C, C++ and Python
- numpy is used for working with arrays
- numpy is short for Numerical Python

- numpy has functions for working in domain of linear algebra, fourier transform, and  matrices
- numpy was created in 2005 by Travis Oliphant

`ndarray` is an Numpy array object (very fast, because is stored at one continuous place in memory)

>==Data Science== is a branch of computer science where we study how to store, use and analyze data for deriving information from it


`pip install numpy`

```py
import numpy as np

arr = np.array([1,2,3,4])
print(arr)
print(np.__version__)
```


## Dimensions in Arrays
__a dimension__ in arrays is one level of array depth (nested arrays)

### 0-D Arrays, Scalars
each value in an array is a 0-D array
`np.array(42)`

### 1-D Arrays, uni-dimensional
its elements are 0-D arrays
`np.array([1,2,3,4])`

__access__: `narray_name[index]` 
`np.array([1,2,3])[1]` -> 2


### 2-D Arrays
its elements are 1-D arrays
(It represents a matrix -> `numpy.mat` is a sub module to operate on matrix)
`np.array([[1,2,3], [4,5,6]])`

__access__: `narray_name[row_index, column_index]`
`arr[1,0]`

### 3-D Arrays
its elements are 2-D arrays
Tjese are often used to represent a 3rd order tensor.!!
`np.array([[[1,2,3], [4,5,6]], [[1,2,3],[4,5,6]]])`

__access__: `narray_name[index, index, index]`
`arr[0,1,1]`

`ndim` is an attribute that returns an integer that tells us how many dimensions the array have

```py
import numpy as np

a = np.array(44) # -> 0
b = np.array([1,2,3]) # -> 1
c = np.array([[1,2,3], [11,22,33]]) # -> 2
```


```py
import numpy as np

arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])

print('Last element from 2nd dim: ', arr[1, -1])
# Last element from 2nd dim:  10
```



### Predefine the highest dimension
```py
import numpy as np

arr = np.array([1,2,3,4], ndmin=5)
print(arr)
print(f"number of dimensions: {arr.ndim}")
```

output
`[[[[[1 2 3 4]]]]]`
`number of dimensions: 5`













