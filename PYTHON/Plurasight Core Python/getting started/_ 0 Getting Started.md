#python #plurasight #smallshire_robert #bingham_austin


# Getting Started
[[#Modularity]]
[[#Objects and Types]]
[[#Buil-in Collections]]
[[#Exceptions]]



#### REPL
Python will
**Read** read whatever input we type in, 
**Evaluate** evaluate it
**Print** print the result
**Loop** loop back to the beginning

```shell
$ python
Python 3.9.7 (default, Sep 16 2021, 13:09:58) 
[GCC 7.5.0] :: Anaconda, Inc. on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 2+3
5
>>> _ *20
100
>>> 
```

---

`int()   float()

`None` often represents the absence of a value
`a is None`

`Bool([])` - > `False`

---
`str()`
Sequence of Unicode code points
Immutable
raw string -> what you see what you get
`r"C:\data"`
`help(str)`

`bytes`
Data type for sequances of bytes
Raw binary data
Fixed-width single-byte encodings
`b'data'`

```python
>>> a = b'some bytes'
>>> a[1]
111
>>> a.split() # -> list of byte objects
[b'some', b'bytes']
>>> 
```

**converting strings <-> bytes**
bytes --- decode ---> string
string --- encode ---> bytes
```python
>>> pl = "Ściemnia się żesz"
>>> data = pl.encode('utf8')
>>> data
b'\xc5\x9aciemnia si\xc4\x99 \xc5\xbcesz'
>>> pol = data.decode('utf8')
>>> pol
'Ściemnia się żesz'
```

`list`
Sequances of objects
```python
>>> list("jarek")
['j', 'a', 'r', 'e', 'k']
```

`dict`
Map keys to values (maps, associative arrays)

`for ... in ...:`


> HTTP data is provided as bytes
> Use `bytes.decode()` to get strings


---
# Modularity
functions
	DUNDER `__feature__`

> [!__name__]
> specially named variable allowing us to detect whether a module is run as a script or imported into another module

```python
if __name__ = '__main__':
	# do something
```
if dunder name is not equal to `'__main__'` the module knows it's being imported into another module, not executed


`def` is a statement
Top-level functions are defined when a module is imported or run


Python
modul | script | program
--- | --- | ---
convenient import with API | Convenient execution from the command line | Perhaps composed of many modules

#### Command line args:
```python
import sys

a = sys.argv[1] # take the first arg when execute file in command line

# $ python file first_arg
```


#### Docstrings
```python
def foo():
""" docstring """"
```

or at the beginning of the fule

#### Shebang
`#!/usr/bin/env python` - which interpreter will be used

---------
# Objects and Types

## Assigning to a variable
`x = 1000` -> Python creates a `int object 1000` and `an object reference x` and arranges for `x` tp refer to the `int object 1000`

>[!`id()`]
>Returns a unique integer identifier for an object that is constant for the life of the object

>[!remember]
>- the assignment operator only binds objects to names. It never copies an object to a value.
>- Python has named references to objects not boxes holding a value
```python
>> p = [1,2,3]
>> q = [1,2,3]
>> p == q
True
>> p is q
False
```

### Argument passing Semantics
`func(arg)` If you pass a list, you pass reference to the list (->side-effect) 

> Function args are transferred using pass-by-object-reference.
> References to objects are copied, not the objects themselves.


### Func args
> Args with default values must come after those without default values.
> 

### Default value Evaluation
>[!rememeber]
> - `def` is a statement executed ar runtime
> - default args are evaluated when `def` is executed
> - immutable default values don't cause problems
> - mutable default values can cause confusing effects

### SCOPES - LEGB rule
==Local== inside the current function
==Enclosing== inside enclising functions
==Global== at the top level of the module
==Built-in== in the special `builtins` module
>[!remember]
>Scopes in Python do not corresnpond to source code blocks
>

`global   `

### Everything is an object
`type(objectName)` to see type of an object
`dir(objectName)` to see attributes of an object (-> list of attributes including the ones we defined)
`__name__` the name of a function or module
`__doc__` docstings

---------
# Buil-in Collections
## tuple
immutable sequences of arbitrary objects
`t = ("ddd", 3, 23.2, True)`
`t = ("ewew",)`
`t=()`
### tuple unpacking
destructuring operation that unpacks data structures into named references
`lower, upper = minmax([21,4,1,24,5,6])` minmax returns two values

## string
### use `str.join()` to join strings
it inserts a separator berween a collection of string
```python
colors = ';'.join(['#23454', '#67456', '#214412'])
# -> '#23454';'#67456';#214412'

colors.splt(';')
#-> ['#23454', '#67456', '#214412']
```

### `partition()`
```python
>> "unforgetable".partition('forget')
('un', 'forget', 'able')
>>> dep, sep, arr = "London:Edinburgh".partition(':')
>>> dep
'London'
>>> sep
':'
>>> arr
'Edinburgh'

```

## Range
Sequence representing anarithmetic progression od integers
```python
>>> range(5)
range(0, 5)
>>> list(range(0,5))
[0, 1, 2, 3, 4]

```

## List
### slicing
Extended form of indexing for referring to a portion of a list or other sequence
`somelist[start:stop]`

copy list: 
- `newcopylist = oldlist[:]`
- `newcopylist = oldlist.copy()`

### `list.index()`
find the location on an object in a list
returns the index oof the first list element which is equal to the argument
....
## Dict   Set

## Protocols
#python/protocol
A set of operation that a type must support ot implement the prorocol.
Do not need to be defined as interfaces or base classes.
Type only need to provide functioning implementations.

Protocol | Implementation collections | example
---|---|---
Container | str,list,dict,range, tuple, set, bytes | in, not in
Size | str,list,dict,range, tuple, set, bytes | len()
iterable | str,list,dict,range, tuple, set, bytes | can be use in `for`
Sequence | str,list,dict,range, tuple | `ob[index], count(), index(), reversed()`
...

-----
# Exceptions
[[8  Exceptions]]



---

# Iteration and Iterables




----
# Classes
#python/class 



----
# File IO and Resource Managements


