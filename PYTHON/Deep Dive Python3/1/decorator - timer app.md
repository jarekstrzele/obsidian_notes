[[_ Deep Dive INTRO]]
[[Scopes, closures, Decorators]]

[[Decorators 1]]


---
# Timer

```py
def timed(fn):
  from time import perf_counter
  from functools import wraps

  @wraps(fn)
  def inner(*args, **kwargs):
    start = perf_counter()
    result = fn(*args, **kwargs)
    end = perf_counter()
    elapsed = end - start

    args_ = [str(a) for a in args]
    kwargs_ = ['{0}={1}'.format(k,v) for (k, v) in kwargs.items()]
    all_args = args_ + kwargs_
    args_str = ','.join(all_args)

    print('{0}({1}) took {2:.6f}s to run. '.format(fn.__name__, args_str, elapsed))

    return result 
```

## recursive
```py
@timed
def calc_recursive(n):
  if n <=2:
    return 1
  else:
    return calc_recursive(n-1) + calc_recursive(n-2)


fib_rec(10) took 0.000030s to run. 
55
```


## loop
```py
@timed
def fib_loop(n):
  fib1 = 1
  fib2 = 1
  for i in range(3, n+1):
    fib1, fib2 = fib2, fib1 + fib2

  return fib2


fib_loop(10) took 0.000004s to run. 
55
```

## reduce
#python/reduce
```
n = 1
(1, 0) --> (1, 1) result t[0] = 1

n = 2
(1, 0) --> (1, 1) --> (2, 1) result t[0]=2

n=3
(1,0) --> (1, 1) --> (2, 1) --> (3,2) result t[0] =3

n=4
(1,0) --> (1, 1) --> (2, 1) --> (3, 2) --> (5, 3) result t[0]=5

general form:
previous value = (a, b)
new value = (a+b, a)

```

```py
from functools import reduce
@timed
def fib_reduce(n):
  initial = (1,0)
  dummy = range(n)
  fib_n = reduce(lambda prev, n: (prev[0] + prev[1], prev[0])
                 ,dummy
                 ,initial)
  return fib_n[0]



fib_reduce(10)
fib_reduce(10) took 0.000010s to run. 
89
```










