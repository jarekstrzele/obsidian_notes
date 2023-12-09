[[_ 0 Python OOP]]

- an object namespace is a regular dictionary,
- it can be extends infinitally
- so two problems appear:
	- memory (to much memory is used)
	- execution speed

==Slots== are the way to solve that problem

>[!info] SLOTS
>They are class level attributes.
>`__slots__('attr1', 'attr2', ...)`

`myobject.__dict__` generates `AttributeError` 
slots replace an object `__dict__` into **fixed-size array**:
- in that way we use less memory (fixed-size)
- app run faster (array uses indexes (int))
	- dictionary is a hash map -> $O(n)$
	- fixed-array -> $O(1)$

but `slots` cause the loss of flexibility (we can't add any new attributes)
```python
class Humburger:
    __slots__ = ('name', 'price', 'weight')
    
    def __init__(self, name, price, weight):
        self.name=name
        self.price=price
        self.weight=weight
        
h = Humburger('Drwala', 33.5, '125g')
print(h.name)
h.name="Wieśmak"
print(h.name)
h.pro = "hum"
# print(h.__dict__) # AttributeError
# slots is in the class namespace

AttributeError: 'Humburger' object has no attribute 'pro'
```

`__slots__` creates a descriptor( an object that implement one of three methods: get(), set(), delete()) for each mapped attribute, thereby overriding the default `__getattribute__` behavior

`__slots__` attributes resides in the class' mappingproxy


## Memory usage
>[!info] Pympler
> Pympler is a tool for analyzing and monitoring memory usage by Python applications

`pip install pympler`

```python
class SlottedEmployee(object):
  __slots__ = ('name', 'surname', 'age', 'status', 'salary')

  def __init__(self, name, surname, age, status, salary):
    self.name = name
    self.surname = surname
    self.age = age
    self.status = status
    self.salary = salary

class RegularEmployee(object):
  
  def __init__(self, name, surname, age, status, salary):
    self.name = name
    self.surname = surname
    self.age = age
    self.status = status
    self.salary = salary

    
e1 = SlottedEmployee("Dobromir", "Dobrotliwy", 40, "FT", 4600)
e2 = RegularEmployee("Zosia", "Złośliwa", 30, "FT", 4600)

from pympler.asizeof import asizeof

e1_slotted_memory = asizeof(e1)
e2_regular_memory = asizeof(e2)
percent_reduction = (e1_slotted_memory - e2_regular_memory)/e2_regular_memory
print(f"slotted {e1_slotted_memory}")
print(f"Regular {e2_regular_memory}")
print(f"% reduction: {percent_reduction:.2%}")


```


---------
# Inheriting Slots

- slots in the parent class will be used for the child's attribute lookup (they are available)
- the child class by default also retains its instance `__dict__`
- if both the parent and child classes are slotted, the child loses its `__dict__`
- if the parent class is not slotted, but the child is is, the child retains its instance ``_dict__

```python
class Dom:
    __slots__=('wielkosc', 'cena', 'data_budowy')
    
    def __init__(self, wielkosc, cena, data_budowy):
        self.wielkosc=wielkosc
        self.cena=cena
        self.data_budowy=data_budowy
        

dom =Dom(150, 511222, '01-01-2000')
print(dom.wielkosc, dom.cena, dom.data_budowy)
print(dom.__dict__)
```

```
150 511222 01-01-2000
Traceback (most recent call last):
  File "<string>", line 12, in <module>
AttributeError: 'Dom' object has no attribute '__dict__'. Did you mean: '__dir__'?
```

```python
class DomekWiejski(Dom):
    pass

domek_wiejski = DomekWiejski(233, 333444, '01-01-1900')
print(domek_wiejski.__dict__)
domek_wiejski.lokalizacja = "Stary Olsztyn"
print(domek_wiejski.lokalizacja )
print(domek_wiejski.__dict__)
```

```
{}
Stary Olsztyn
{'lokalizacja': 'Stary Olsztyn'}
```

```python
class Dom:
    __slots__=('wielkosc', 'cena', 'data_budowy')
    
    def __init__(self, wielkosc, cena, data_budowy):
        self.wielkosc=wielkosc
        self.cena=cena
        self.data_budowy=data_budowy
        

class DomNaMarsie(Dom):
    __slots__=("material", "lokalizacja")
    def __init__(self, material, lokalizacja):
        self.material=material
        self.lokalizacja=lokalizacja
        
dom_na_marsie = DomNaMarsie("X54", "Alba Patera")
print(dom_na_marsie.material, dom_na_marsie.lokalizacja)
print(dom_na_marsie.__slots__)
print('-'*10)
dom_na_marsie.cena = 14567
print(dom_na_marsie.cena)
print('-'*10)
print(dom_na_marsie.__dict__)
```

```
X54 Alba Patera
('material', 'lokalizacja')
----------
14567
----------
Traceback (most recent call last):
File "<string>", line 23, in <module>
AttributeError: 'DomNaMarsie' object has no attribute '__dict__'. Did you mean: '__dir__'?
>  
```

You can write:
`__slots__=('atr1', 'atr2', ... , '__dict__')` -> now you can add attributes dynamically but you lost the optimizationi


# Should We Alway Use Slots?
- slots should be used for memory and performance optimization  when we have a specific need to optimize, typically indicated by profiling
- when using slots we should be mindful of the side effects, e.g. instance `__dict__` inheritance rules, etc.
- we should not use slots for the side effects


> **Dolnald Knuth**
> "premature optimization is the root of all evils"









