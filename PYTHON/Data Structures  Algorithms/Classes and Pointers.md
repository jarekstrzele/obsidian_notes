[[_Data Structures & Algorithms]]


----
# Classes and Pointers
## Class
class is like a cookie cutter (is a data type)

## Pointer
### immutable data
```pyton
num1 = 11
num2 = num1
```

`id(num1)` -> shows a memory address
`id(num1) == id(num2)` TRUE
but if you change `num2`, you DON"T change `num1`

### mutable data
```pythn
dict1 = {'value': 1}
dict2 = dict1
```

`id(dict1) == id(dict2)` TRUE
but if you change `dict2`, you change `dict1`

