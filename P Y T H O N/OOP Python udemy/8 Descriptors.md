[[_ 0 Python OOP]]

> W Pythonie deskryptory to specjalne klasy, które umożliwiają kontrolę dostępu do atrybutów klasy poprzez przesłanianie standardowych metod takich jak `__get__`, `__set__` i `__delete__`. Deskryptory są często wykorzystywane w programowaniu obiektowym do tworzenia bardziej zaawansowanych mechanizmów dostępu do atrybutów klasy, takich jak walidacja wartości czy automatyczne przeliczanie wartości.

control the semantics of attribute access in Python - you can
- intercept  the basic attribute and operation  (get, set, delete)
- customize the basic attribute and operation (get, set,delete)

# Attribute LookupChain Review
1. look in the instance(i.e. object) `__dict__` for a key with the attribute's name
2. look in hte instance;s type (i.e. class) `__dict__` for a key with the attribute'sname
3. look in the instance;s parent type (i..e. parent class) `__dict__` for a key with the attribute's name
4. if not found, repeat for each parent type in mro order
5. if not found, raise AttributeError

```python
class Pradziadek:
    name = "Hipolit"

class Dziadek(Pradziadek):
    # name = "Ignacy"
    pass

class Ojciec(Dziadek):
    # name = "Piotr"
    pass

class Syn(Ojciec):
    def __init__(self, name=None):
        if name:
            self.name=name

krzys=Syn("Krzyś")
krzys2=Syn()

print(krzys.__dict__)

print(krzys2.__dict__)
print(krzys2.name)
```

Descriptors can change this order

---
# Descriptor
>[!info] descriptor
>a descriptor is just an object that implements the descriptor protocol
>- **protocol** is a contract between an object an Python
>- **descriptor protocol**:
>	- `__get__()`
>	- `__set__()`
>	- `__delete__()`
>*any object that implements a combination of these methods is a descriptor*



```python
class Descriptor:
    def __get__(self, instance, owner):
        pass
    
    def __set__(self, instance, value):
        pass
    
    def __delete__(self, instance):
        pass
```








