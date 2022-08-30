[[_ Deep Dive INTRO]]
[[Decorator (logger, Stacked Decorators)]]

[[Scopes, closures, Decorators]]

---

# Decorator Application (Class Decorator )

How  we can use classes to decorate functions

## a Function as a decorator
__a function (factory) that decorat (make a decorator) another function__
```python
def my_dec(a, b):
	def dec(fn):
		def inner(*args, **kwargs):
			print("decorated fun called: a={0}, b={1}".format(a,b))
			return fn(*args. **kwargs)
		return inner

	return dec

@my_dec(10,20)
def my_func(s):
	print("Hello {0}".format(s))

my_func("World")
# -> decorated fun called: a=10, b=20
# -> Hello Wolrd
```

## an Instance of class as a decorator
__class instances__ can be callable!!
`def __call__(self, ...): ...`

```python
class MyClass:
	def __init__(self, a, b):
		self.a=a
		self.b=b

	def __call__(self,c):
		print("called a={0}  b={1} c={2}".format(self.a, self.b, c))


obj=Class(10,20)
obj.__call__("World")
obj("World")
```

We can define `__call__` method as a real decorator:
```python
class MyClass:
	def __init__(self, a, b):
		self.a=a
		self.b=b

	def __call__(self,c):
		#the body comes from the function decorator
		# __call__ is a dec
		def inner(*args, **kwargs):
			print("decorated fun called: a={0}, b={1}".format(self.a, self.b))
			return fn(*args. **kwargs)
		return inner

# we get the same result
@MyClass(10,20)
def my_func(s):
	print("Hello {0}".format(s))

my_func("World")
# -> decorated fun called: a=10, b=20
# -> Hello Wolrd
```



