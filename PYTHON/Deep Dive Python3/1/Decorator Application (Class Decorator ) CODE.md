[[_ Deep Dive INTRO]]
[[Scopes, closures, Decorators]]


[[Decorator Application (Class Decorator )]]

----------
# Monkey patching
> - dynamiczna modyfikacja klasy lub modułu w czasie uruchamiania
> - fragment kodu, który rozszerza lub modyfikuje inny kod podczas wykonywania programu
> - możliwy tylko w językach dynamicznych

```python
from fractions import Fraction

Fraction.is_integral = lambda self: self.denominator == 1

```

other way
```python
from fractions import Fraction

def fn_mp(cls):
  cls.is_integral = lambda self: self.__class__._denominator == 1
f= Fraction(64,8)
f.is_integral()

# -> True
```

We can write a class decorator, if our decorator is quite general
```python
from math import sqrt
from functools import total_ordering

@total_ordering
class Point:
  def __init__(self,x,y):
    self.x=x
    self.y=y

  def __abs__(self):
    return sqrt(self.x**2 + self.y **2)

  def __repr__(self):
    return ('Point({0}, {1})'.format(self.x, self.y))

  def __eq__(self, other):
    if isinstance(other, Point):
      return self.x == other.x and self.y == other.y
    else:
      return False

  def __lt__(self, other):
     if isinstance(other, Point):
      return abs(self) < abs(other)
     else:
      return NotImplemented

```








