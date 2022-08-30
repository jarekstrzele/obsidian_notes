[[_ Deep Dive INTRO]]

[[Tuples as Data Structures and Named Tuples]]

-----------------
[[Tuples -  Generating Named Tuples]]
[[Tuples - Accessing Named Tuples]]

# NAMED Tuples
The ==position of the object contained in== the tuple gave it meaning.
`pt = (10, 20)` as a 2D coordinate
-> `x, y = pt`   or `x = pt[0]` and  `y=pt[1]`
but indexes are not meaningfull for people.

---
## `namedtuple`
- create tuples and give meaningful names to the positions
- `namedtuple` is a function which generates a new class (so `namedtuple` is a ==class factory==)
	- that new class inherits from tuple
	- provides named properies to access elements of the tuble
	- an INSTANCE of that class IS STILL a TUPLE

`from collections import namedtuple`
_collections_ is a standard library module

---
## `rename` as a keyword-only argument 
(by default is `False`)

_broken code_:
`Person = namedtuple('Person', 'name age _ssn')`
but
`Person = namedtuple('Person', 'name age _ssn', rename=True)`
will be ok (`_ssn` will be rename by `_2`) (index is 2)

---
## Introspection

### `_fields`
`Person = namedtuple)'Person', 'name age _ssn', rename=True)`
`Person._fields` -> `('name', 'age', '_2_')`

### `_source`
`Person._source` shows the code for class `Person`

---
## Extracting Named Tuple Values to a Dictionary
`_asdict()` creates a dictionary of all the named values in the tuple

```oy
Point2D = namedtuble('Point2D', 'x y')
pt1 = Point2D(10,20)

pt1._asdict() # -> {'x':10, 'y': 20}

```






























