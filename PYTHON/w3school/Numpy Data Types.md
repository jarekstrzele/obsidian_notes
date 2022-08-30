[[_Numpy w3school]]


---
# Numpy data type
## python data types
- strings
- integer
- float
- boolean
- complex

## numpy data types
- `i` integer
- `b` boolean
- `u` unsigned integer
- `f` float
- `c` complex float
- `m` timedelata
- `M` datetime
- `O` object
- `S` string
- `U` unicode string
- `V` fixed chunk of memory for orher type

## checking data type
```python 
arr = np.array([1,2,3,4])
print(arr.dtype) # -> int64

arr= np.array(['appl', 'banana', 'cherry'])
print(arr.dtype) # -> <U6
```

## array() function
```python
import numpy as np
arr = np.array([1,2,3,4], dtype='S')

```

## converting
to change the data type of an exisiting array
=> MAKE A COPY of the array with the `astype()` method
`astype()` creates a copy of the array, and allows you to specify the data type as a parameter

```python
import numpy as np

arr = np.array([1.1, 2.1, 3.1])
newarr = arr.astype('i')
print(newarr)
print(newarr.dtype)

arr2 = np.array([1, 0, 3])
newarr2 = arr2.astype(bool)
print(newarr2)
print(newarr2.dtype)

```
