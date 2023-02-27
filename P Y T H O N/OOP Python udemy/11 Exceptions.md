#python/exception


---
**Co to jest wyjątek?**
*wyjątek*/*exception* wydarza się, gdy program napotyka błąd lub nieoczekiwany problem (przykładowe powody: błędne dane wejściowe, błąd syntaktyczny, ...)

**Co robi Python, gdy napotka wyjątek?**
Python przerywa działanie programu i wyświetla komunikat o wyjątku, który wystąpił.

**Co zrobić z wyjątkiem**
użyj konstrukcji `try-eccept`
*try* - pilnuje kodu, w którym może wystąć wyjątek
*except* zawiera informacje o tym, co trzeba zrobić, gdy wyjątek wystąpi
*finally* wykonuje kod niezależnie od wystąpienia wyjątku

--------------------

# The Exception Object

>[!info] exception
>It is an object that stop and redirect control flow.
>exception != error (an exception can indicate an error but doesn't have)


example
```python
a + 4

Traceback (most recent call last):
File "<string>", line 1, in <module>
NameError: name 'a' is not defined

#####################
'a' + 4

Traceback (most recent call last):
  File "<string>", line 1, in <module>
TypeError: can only concatenate str (not "int") to str
```

All exceptions are subclasses of `BaseException()`
```bash
>>> issubclass(TypeError, BaseException)
True
>>> issubclass(NameError, BaseException)
True

>>> TypeError.__mro__
(<class 'TypeError'>, <class 'Exception'>, <class 'BaseException'>, <class 'object'>)
```


An example of ==an exception that is not an error==:
```python
>>> my_iter = iter(list(range(5)))     
>>> for i in range(10):                
...  print(next(my_iter))
... 
0
1
2
3
4
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
StopIteration
```



### `SyntaxErrors are pure errors`

--------------
# Handling

















