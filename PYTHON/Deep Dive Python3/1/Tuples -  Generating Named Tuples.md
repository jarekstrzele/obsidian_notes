[[_ Deep Dive INTRO]]
[[Tuples as Data Structures and Named Tuples]]


[[Tuples - Named Tuples]]

---
## Generating Named Tuple Classes
`namedtuple` needs a few things to generate this class:
- the ==class name== we want to use
- a sequence of ==field names (strings)== we want to assign, in the order of the elements in the tuple (==names cannot start with an underscore==)
- the ==return== value of the call to namedtuple will be a ==class==
```py
Point2D = namedtuple('Point2D', ['x', 'y'])
pt = Point2D(10,20)

# or
XXX = namedtuple('Point2D', ['x', 'y'])
pt = XXX(10,20)
```

![[namedtuple.excalidraw|700]]

Any sequence can be used to provide the list of field names to the `namedtuple` function!!
- a list of stings
- a tuple of stings
- a single string with the field names separated by whitespace or commas

`namedtuple('Point2D', ['x', 'y'])`
`namedtuple('Point2D', ('x', 'y'))`
`namedtuple('Point2D', 'x, y')`
`namedtuple('Point2D', 'x y'])`


---
## Instantiating Named Tuples
```py

Point2D = namedtuple('Point2D', 'x y')`
pt1 = Point(10, 20)
pt2 = Point(x=10, y=20)
```

```py
isinstance(pt1, tuple) #-> True
```

> `pt1` and `pt2` are IMMUTABLE

