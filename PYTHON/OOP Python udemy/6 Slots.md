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

- slots in the parent class will be used for the child's attribute lookup ()

























