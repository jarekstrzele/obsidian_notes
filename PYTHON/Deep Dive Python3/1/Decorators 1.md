[[_ Deep Dive INTRO]]
[[Closures]]
[[Variable Scopes]]
[[Scopes, closures, Decorators]]


---

# Decorators  1
#python/decorator
[[decorator - timer app]]
[[Decorator (logger, Stacked Decorators)]]
[[decorator app memoization]]






a simple  closure counter
```py
def counter(fn):
	count=0
	def inner(*args, **kwargs):
		nonlocal count
		count += 1
		print(f'Function {fn.__name__} was called {count}')

		return fn(*args, **kwargs)

	return inner
```

```py
def add(a, b=0):
	return a+b

add = counter(add)

result = add(1,2) # -> function add called 1 time
				  # result = 3
```

We essentially modified our `add` function by wrapping it inside another function that added some functionality to it.
We also say that we decorated our function `add` with the function `counter`.
And we call `counter` a ==DECORATOR== function!!!

---

## DEFINITION
==DECORATORS==

In general a decorator function:
- takes a function as an argument
- return a closure
- the closure usually accepts any combination of parameters
- runs some code in the inner function (closure)
- the closure function calls the original function using the arguments passed to the closure
- returns whatever is returned by that function call

![[decorator_1.excalidraw|700]]

---

## Symbol `@`

In general, if `func` is a decorator function, we ==decorate== another function `my_func` using

				my_func = func(my_func)

This is so common that Python provides a convenient way fo writing that:

				@func
				def my_func(...):
					...

is the same as writing:

				def my_fun(...):
					...

				my_func = func(my_func)

---

## Introspecting Decorated Functions
```py
@counter
def mult(a, b, c=1):
	"""
		return the product of three values
	"""
	return a * b * c
```

	mult.__name__ -> inner    not mult

		help(mult) -> Help on function inner in module __main__: inner(*args, **kwargs)

We have also "lost" our docstring, and even the original function signature

==To solve these problems== 
`from functools import wraps`

`wrap` function it itself a decorator 

```py
def counter(fn):
	count=0
	@wraps(fn)
	def inner(*args, **kwargs):
		nonlocal count
		count += 1
		print(f'Function {fn.__name__} was called {count}')

		return fn(*args, **kwargs)

	return inner
```

>You don't have to use `@wraps`, but it will make debugging easier








