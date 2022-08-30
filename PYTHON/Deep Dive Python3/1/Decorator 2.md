[[_ Deep Dive INTRO]]
[[Scopes, closures, Decorators]]

[[Decorators 1]]

---

# Decorator 2
#python/decorator 

built-in decorators that have args:
`@wraps(fn)     @lru_cache(maxsize=256)    ....`

Decorators without args:
```py
@mydeco
def my_func():
 ...

# or

my_func = mydeco(my_func)

```

If you want to pass some extra args to decorators, you can write:
```py
def my_deco(fn, extra_arg):
	...

my_func = my_deco(my_func, 20) # it's ok
```
but ==this syntax is incorrect==:
```py
@my_deco(20)
def my_func():
	...
```
__So, my_deco is a function__ that returns thet inner clouser that containes our original function (__my_func__)

So, `@time(10)` should returns a __decorator__ not a function.

so:
```py
dec = timed(10) # -> returns a decorator

@dec
def my_func():
   ...
```

```py
def outer(reps)
	def timed(fn): # this is our decorator
		...
		def inner(*args, **kwargs):
			...

		return inner
		
	return outer

######################

my_func = outer(10)(my_func) # ok
@outer(10)                   # ok
def my_func():
 ...

```
## Decorator Factories
The `outer` function is not itself a decorator
   instead it __returns__ a __decorator__ when __called__

and any arguments passed to outer can be referenced (as free variables) inside our decorator

> We  call this outer function ==a decorator factory== function 
> (
>    it is a function that creates a new decorator each time it is called
> ) 
> `@timed(10)` is a deco factory


```py
# dec factory
def def_fac():
  print("running de_fac")

  def dec(fn):
    print("running dec")

    def inner(*args, **kwargs):
      print("runing inner")

      return fn(*args, **kwargs)

    return inner

  return dec 
```

```py
@def_fac()
def mf():
  print("running mf")
```

```py
def dec_fac(a, b):
  print("running de_fac")

  def dec(fn):
    print("running dec")

    def inner(*args, **kwargs):
      print("runing inner")
      print(f'a={a} , b= {b}')
      return fn(*args, **kwargs)

    return inner

  return dec 

@dec_fac(10,20)
def my_fn():
  print("running my fn")
# -> 
# running de_fac
# running dec

my_fn()
# -> runing inner
# a=10 , b= 20
# running my fn
```















