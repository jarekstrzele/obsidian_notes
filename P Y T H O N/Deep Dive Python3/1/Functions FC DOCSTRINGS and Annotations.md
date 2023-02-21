[[- Functions First-Class]]

---
# DOCstrings and Annotation

`help(x)` returns some documentation for `x`

```python
def foo(a):
	""" docstrings
		or " "
		are stored in the 
		property foo.__doc__
	"""
```

`__doc__` stores a docstring

```python
# def my_fnc(a: <expression>) - <expression>

def my_fnc (a:str = 'xyz',
			args: 'additional params',
			b: int = 1,
			**kwargs: 'additional keyword') -> str:
			pass

print(my_fnc.__annotations)
# {'a':str, n:int ...}

```


>[!important]
>docstrings and annotations are used by external tools and modules: 
>e.i. Sphinx - generate documentation

```python
def foo():
  """ this is my docstrings """
  return "ok"

foo.__doc__
#  this is my docstrings 
foo.__annotations__
{}





```