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

AttributeError: 'Humburger' object has no attribute 'pro'
```








