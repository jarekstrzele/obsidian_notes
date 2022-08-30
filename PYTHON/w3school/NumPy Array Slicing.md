
[[_Numpy w3school]]

----
# NumPy Array Slicing
>[!slicing definition ]
>slicing in python means taking elements from one given index to another given index
`[start: end: step]`
'end' is excluded

## negative slicing
`arr[-3:-1]`
`arr[-4:]`


## slicing 2-D arrays
From the second element, slice elements from index 1 to index 4 (not included)
```python
import numpy as np
arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])
print(arr[1, 1:4])
```

`arr[index, start:end]`

from both elements, slice index 1 to index 4 (not included), this return a 2-D array:
```python
import numpy as np
arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])

print(arr[0:2, 1:4])
```

from both elements, return index 2
```python numpy as np
arr = np.array([[1,2,3,4,5], [6,7,8,9,10]])
print(arr[0:2, 2])
```


