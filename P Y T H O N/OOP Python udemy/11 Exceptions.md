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
```python
try:
    1/0
except ZeroDivisionError:
    print("You can't divide by zero.")
print("And now?")
# You can't divide by zero.
# And now?
```

```python
1/0

print("And now?")

Traceback (most recent call last):
File "<string>", line 1, in <module>
ZeroDivisionError: division by zero
```


### when you don't handle an exception:
```python
try:
    a + 10
except ZeroDivisionError:
    print("Somehting wrong")
print("And now?")

Traceback (most recent call last):
  File "<string>", line 2, in <module>
NameError: name 'a' is not defined
```

better (generic way - handle all exception):
```python
try:
    a + 10
except:
    print("Somehting wrong")
print("And now?")

# Somehting wrong
# And now?
```

better:
```python
try:
    a + 10
except NameError:
    print("Somehting wrong")
print("And now?")

# Somehting wrong
# And now?
```


----------
# Raising

```python
raise NameError
Traceback (most recent call last):
  File "<string>", line 1, in <module>
NameError


raise ValueError
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ValueError
```


```python
raise ValueError("This message is without meaning")
Traceback (most recent call last):
File "<string>", line 1, in <module>
ValueError: This message is without meaning


```

```python
try:
    raise NameError("THis is ....")
except NameError:
    print("Now, something wrong")
print("After....")

# Now, something wrong
# After....
```

```python
cats = [
    { "name": "Kicius", "age": 10},
    { "name": "Mruczek", "age": -1}
]


a= [ True for cat in cats if cat["age"] < 0]
print(a)

try:
    if any([True for cat in cats if cat["age"]< 0]):
        raise ValueError("Age must be >0")
    else:
        print("OK")
except ValueError as err:
    print(f"Something wrong!!\n{err}")
```


------------
# EAFP
# **E**asier to **A**sk for **F**orgiveness then **P**ermission - coding style

You want to open an file. A lot fo errors can be happened (e.g. the file doesn't exit, you can't read the file, you can't open that format ....)
Before you open the file you have to check all these possibilities this is other coding styl ==(*LBYL* - Look Before You Leep )==
or you can use EAFP

```python

try:
    my_file = open("hello_world.txt", "r")
    text = my_file.read()
    my_file.close()
    
    print(text)
except:
    print("File could not be read")

File could not be read
```


-----------
# `SyntaxError`

Syntax errors can't be catched!!!!!!
```python
try:
    ala ma kota
except SyntaxError:
    print("This is not a Python code")
print("And now?")

File "<string>", line 2
    ala ma kota
        ^^
SyntaxError: invalid syntax

```

but e.g. NameError handles:
```python
try:
    ala += 1
except NameError:
    print("This is not a Python code")

print("And now?")

# This is not a Python code
# And now?
```


The have the same inheritance:
```python
print(SyntaxError.__mro__)
print(NameError.__mro__)

(<class 'SyntaxError'>, <class 'Exception'>, <class 'BaseException'>, <class 'object'>)
(<class 'NameError'>, <class 'Exception'>, <class 'BaseException'>, <class 'object'>)
```

The difference comes from bytecode (your code --> byte code --> interpreter, but bytecode must be syntactically correct)
`SyntaxError` raises when python passes from written code to bytecode.

```python
try:
    eval("ala ma kota ")
except SyntaxError:
    print("This is not a Python code")

print("And now?")

# This is not a Python code
# And now?
```


> SyntaxError interrupts the compilation to bytecode, before any exception handling coed is interpreted

------------
# Exception Hierarchy

![[Python_Exception_Hierarchy.excalidraw | 700]]

Almost all exceptions inherit from `Exception` (e.g. Exception -> ArithmeticError-> ZeroDivisionError )
```python
print(ZeroDivisionError.__mro__)

(<class 'ZeroDivisionError'>, <class 'ArithmeticError'>, <class 'Exception'>, <class 'BaseException'>, <class 'object'>)
```

HANDLING THE PARENT CLASS WILL EFFECTIVELY HANDLE ALL INSTANCES OF THE RELATED SUBCLASSES
```python
try:
    1/0
except ZeroDivisionError:
    print("Catched error")

# Catched error

```

```python
try:
    1/0
except ArithmeticError:
    print("Catched error")

# Catched error
```

Severals `except` more specific first, more general later
```python
try:
    1/0
except ZeroDivisionError:
    print("Can't divide by zero ")
except ArithmeticError:
    print("Some Arithmetic error")

# Can't divide by zero 
```

```python
try:
    1/0
except ArithmeticError:
    print("Some Arithmetic error")
except ZeroDivisionError:
     print("Can't divide by zero ")

# Some Arithmetic error
```

-----------
# the `else` clause

- with `try-except` you can use `else` block
- `else` only executes when the code in the try does not lead to an exception

```python
# json.loads()
import json
  
cat1 = '{"name": "Mrucze"}'
decoded_data = json.loads(cat1) #json.loads(json_str) -> python object
print(decoded_data) # -> {'name': 'Mrucze'}

# cat2 = '{"name"}'
# decoded_data = json.loads(cat2) # -> json.decoder.JSONDecodeError
print(json.decoder.JSONDecodeError.__mro__) #-> (<class 'json.decoder.JSONDecodeError'>, <class 'ValueError'>, <class 'Exception'>, <class 'BaseException'>, <class 'object'>)
cat2 = '{"name"}'
try:
    decoded_data = json.loads(cat2)  
except json.decoder.JSONDecodeError:
    print("Invalid json string")
else:
    print("Json data decoded correctly")


try:
    decoded_data = json.loads(cat1)  
except json.decoder.JSONDecodeError:
    print("Invalid json string")
else:
    print("Json data decoded correctly")
```


-------

# Finally
The block that alway will be run.
Some times it is nessasery to execute a piece of code
- the finally  clause defines blocks of code that execute uder all circumstances
- this makes finally ideal for clean up operations that absolutely need to execute


```python
try:
    1/0
    # 1/10
except:
    print("You try to divide by zero")
finally:
    print("Always in terminal")

```


```python
import json

def json_decode(payload):
    decode=None
    
    try:
        decode = json.loads(payload)
    except json.JSONDecodeError:
        print("Invalide payload")
        return
    finally:
        print("Decoding attempt complete")
    
    return decode

j_correct = '{"name": "Joe"}'
j_incorrect = '{"name":}'

# json_decode(j_correct)
json_decode(j_incorrect)
  


```


-----------

# Nesting and Bundling

```python
run = True

while run:
    try:
        number = int(input("Podaj liczbę całkowitą: "))
    except ValueError:
        print("Nie wpisałeś liczby")
        try:
            answer = input("Czy chcesz wpisać liczbę (T / N): ").upper()
            
            if answer not in ('T', 'N'):
                raise ValueError
        except (ValueError, KeyboardInterrupt):
            print("AŁA")
            run = False
            
        else:
            if answer == 'N':
                run = False 
    else:
        print(f"wpisałeś liczbę {number}, która w systemie dwójowym jest {number: b}")
    
```


----------
# Rolling our own





























