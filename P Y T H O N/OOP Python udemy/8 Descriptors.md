[[_ 0 Python OOP]]

> W Pythonie deskryptory to specjalne klasy, które umożliwiają kontrolę dostępu do atrybutów klasy poprzez przesłanianie standardowych metod takich jak `__get__`, `__set__` i `__delete__`. Deskryptory są często wykorzystywane w programowaniu obiektowym do tworzenia bardziej zaawansowanych mechanizmów dostępu do atrybutów klasy, takich jak walidacja wartości czy automatyczne przeliczanie wartości.

control the semantics of attribute access in Python - you can
- intercept  the basic attribute and operation  (get, set, delete)
- customize the basic attribute and operation (get, set,delete)

# Attribute LookupChain Review
1. look in the instance(i.e. object) `__dict__` for a key with the attribute's name
2. look in the instances type (i.e. class) `__dict__` for a key with the attribute's name
3. look in the instances parent type (i..e. parent class) `__dict__` for a key with the attribute's name
4. if not found, repeat for each parent type in *mro* order
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

print(krzys.__dict__) # {'name': 'Krzyś'}

print(krzys2.__dict__) # {}
print(krzys2.name) # Hipolit
print(krzys2.gotowka) # AttributeError: 'Syn' object has no attribute 'gotowka'
```

Descriptors can change this order

---
# Descriptor

## definition
>[!info] descriptor
>a descriptor is just an object that implements the descriptor protocol
>- **protocol** is a contract between an object and Python
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

---
## using a descriptor
> problem:
> *we want to be able to define a PersonTable class that has a first_name attribute that is text of maximum length 200*



```python
# our descriptor
# by convention use `instance` and `owner`
class TextField:
    def __init__(self, length):
        self.length=length
    
    def __get__(self, instance, owner):
	    print(f"{instance =}" )
        print(f"{owner =} ")
        return self.value
    
    def __set__(self, instance, value):
        if not type(value) == str:
            raise TypeError("Value should be a string")
        
        if len(value) > self.length:
            raise ValueError(f"Value cannot exceed {self.length} charachers")
    
        self.value=value
    def __delete__(self, instance):
        pass


class PersonTable:
    first_name = TextField(20)

p = PersonTable()
p.first_name = "a"*10
print(p.first_name)
# instance =<__main__.PersonTable object at 0x7ff8aa755a10>
# owner =<class '__main__.PersonTable'> 
# aaaaaaaaaa

```


> 
> **`__get__`  of descriptor has absolute precedence**
> first the getter next the `__dict__` of instance


-----------
## some changes
```python
class PersonTable:
    first_name=TextField(20)
    
    def __init__(self, first_name):
        self.__dict__["first_name"]=first_name

p = PersonTable("Tom")
p.first_name = "Jerry"
print(p.__dict__) # {'first_name': 'Tom'}
print(p.first_name) #Jerry
```

**a problem**
```python
p2=PersonTable("Janosik")
p2.first_name="Hanka"

print(p.first_name) # -> Hanka not Jerry

```





























