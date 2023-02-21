[[Decorator 2]]

[[_ Deep Dive INTRO]]
[[Scopes, closures, Decorators]]
[[Decorators 1]]

[[decorator - timer app]]
[[Decorator (logger, Stacked Decorators)]]



---

# Decorator app memoization

```py
def fib(n):
  print(f'Calculating fing{n}')
  return 1 if n < 3 else fib(n-1) +fib(n-2)
```

In this function there are to many calculation repetitions.

__a class solution__:
```py
class Fib:
  def __init__(self):
    self.cache = {1:1, 2: 1}

  def fib(self, n):
    if n not in self.cache:
      print(f'Calc fib({n})')
      self.cache[n] = self.fib(n-1) + self.fib(n-2)

    return self.cache[n]

f=Fib()
f.fib(10)
```

__a closure solution__ (it will have the same behaviour as the class solution):
```py
def fib():
  cache = {1:1, 2:1}

  def calc_fib(n):
    if n not in cache:
      cache[n] = calc_fib(n-1) + calc_fib(n-2)

    return cache[n]

  return calc_fib

f=fib()
f(10)
```


__a decorator solution__:
```py
def memoize_fib(fib):
  cache={1:1, 2:1}

  def inner(n):
    if n not in cache:
      cache[n]= fib(n)

    return cache[n]

  return inner

@memoize_fib
def fib(n):
  print(f'Calculating fin({n})')
  return 1 if n < 3 else fib(n-1) +fib(n-2)
  
```


__a more general decorator__
```py
def memoize(fn):
  cache=dict()

  def inner(n):
    if n not in cache:
      cache[n]= f(n)

    return cache[n]

  return inner
```


__a built-in decorator solution__:
```py
from functools import lru_cache

@lru_cache()
def fib(n):
  print(f'Calculating fib({n})')
  return 1 if n < 3 else fib(n-1) +fib(n-2)
```


