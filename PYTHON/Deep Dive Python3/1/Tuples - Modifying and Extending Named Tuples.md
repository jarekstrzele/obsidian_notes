[[_ Deep Dive INTRO]]
[[Tuples - Named Tuples]]

[[Tuples - Accessing Named Tuples]]

---

# Modifying and Extending Named Tuples

## Modifying
__To modify tuples__:
we have to create a NEW tuple, with the modied values

 example:
```python
Point2D = namedtuple('Point2D', 'x y')
pt = Point2D(0,0)

# we want to change the x coordinate
# Simple approach:
pt = Point2D(100, pt.y)
```

To cope with long tuples better way is to use a built-in method `_replace`:
- it will copy the named tuple into a new one, replacing any vaues from keyword arguments
- the keyword arguments are simple the field names in the tuple and the new value
- the keyword name must match an existing field name

```python
Stock = namedtuple('Stock', 'symbol year month day open high low close')

djia = Stock('DIJA', 2018, 1 25, 26_313,26_458, 26_360, 36_394)

djia = djia._replace(day=26, high=26_459, close=26_394)

```

You can use `_make` class method, but you need to create aniterable that contains all values first:
`djia = Stock._make(new_values)`
`new_values` must be an iterable (tuple, list, ...)

---
## Extending 
Somtimes we want to create named tuple that extends another named tuple, appending one or more fields

example
```python
Stock = namedtuple('Stock', 'symbol year month day open high low close')

Stock._fields # -> ('Stock', 'symbol year month day open high low close')

new_fields = Stock_fields + ('previous_close',)
StockExt = namedtuple('StockExt', new_fields)


```

If you want to extend values from one tuple to a new one:
```python
Stock = namedtuple('Stock', 'symbol year month day open high low close')

StockExt = namedtuple('StockExt', Stock_fields + ('previous_close',))

djia = Stock('DIJA', 2018, 1 25, 26_313,26_458, 26_360, 36_394)
dija_ext = StockExt(*djia, 26_00)
# or
djia_ext = StockExt._make(djia + (26_000,))


```
