[[Scopes, closures, Decorators]]
[[Decorators 1]]

[[decorator - timer app]]
[[decorator app memoization]]

---

# Logger, Stacked Decorators
```py
def logged(fn):
  from functools import wraps
  from datetime import datetime, timezone

  @wraps(fn)
  def inner(*args, **kwargs):
    run_dt = datetime.now(timezone.utc)
    result = fn(*args, **kwargs)
    print('{0}: called {1}'.format(run_dt, fn.__name__))
    
    return result

  return inner

# funct_1 = logged(funct_1)
@logged
def funct_1():
  pass

funct_1()
2022-04-14 19:32:39.921899+00:00: called funct_1
```

```py
def fact(n):
	from operator import mul
	from functools import reduce

	return reduce(mu, range(1, n+1))
```

You can decorate `fact`:
```py
fact = logged(timed(fact))

# or

@logged                # is first
@timed                 # is second
def fact(n)...         # 

```









