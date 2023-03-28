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

`self` - represents an instance of that class
`owner` - refers to the class from where the descriptor is invoked (and set to a class variable)
				in the example below PersonTable class owns the descriptor
```python
class PersonTable:
    first_name = TextField(20)
    last_name = TextField(40)

print(PersonTable.__dict__)
{'__module__': '__main__', 
 
 'first_name': <__main__.TextField object at 0x7ff3e4d81210>, 
 'last_name': <__main__.TextField object at 0x7ff3e4d813d0>, 
 
 '__dict__': <attribute '__dict__' of 'PersonTable' objects>, 
 '__weakref__': <attribute '__weakref__' of 'PersonTable' objects>, '__doc__': None}
```

`PersonTable` is owner of these specific instances of the descriptor class named `TextField`

-
`instance` refers to the instance of the owing class



# Data descriptor

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



-----------

##  Descriptor storage

> use `instance.__dict__` for storing descriptor field values

#### some changes
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

#### **a problem**
```python
p2=PersonTable("Janosik")
p2.first_name="Hanka"

print(p.first_name) # -> Hanka not Jerry, because descriptor is a class attribute

```

#### SOLUTION
```python
class TextField:
	def __init__(self, length):
		self.length=length

	def __get__(self, instance, owner):
		# return self.value
		return instance.__dict__.get("text_field_value", None)

	def __set__(self, instance, value):
		if not type(value) == str:
			raise TypeError("Value should be a string")
		if len(value) > self.length:
			raise ValueError(f"Value cannot exceed {self.length} characters")

		instance.__dict__["text_field_value"] = value


	def __delete__(self, instance):
		pass

class PersonTable:
	first_name = TextField(20)

p1 = PersonTable()
p2 = PersonTable()
p1.first_name="Tom"
p2.first_name="Jerry"
print(f"{p1.first_name =}" ) # Tom
print(f"{p2.first_name =}" ) # Jerry 
print(f"{p1.__dict__ =}" ) # p1.__dict__ ={'text_field_value': 'Tom'}

print(f"{p2.__dict__ =}" ) # p2.__dict__ ={'text_field_value': 'Jerry'}


		
```


---
#### a new problem
```python

class TextField:
	def __init__(self, length):
		self.length=length

	def __get__(self, instance, owner):
		# return self.value
		return instance.__dict__.get("text_field_value", None)

	def __set__(self, instance, value):
		if not type(value) == str:
			raise TypeError("Value should be a string")
		if len(value) > self.length:
			raise ValueError(f"Value cannot exceed {self.length} characters")

		instance.__dict__["text_field_value"] = value


	def __delete__(self, instance):
		pass

class PersonTable:
	first_name = TextField(20)
	last_name = TextField(30)

p = PersonTable()
p.first_name = "Hans"
p.last_name = "Kloss" 
print(p.first_name, p.last_name) # Kloss, Kloss
print(p.__dict__) # {'text_field_value': 'Kloss'}


```


#### SOLUTION
`self.field_name = field_name`
`f"TextField_{self.field_name}`
```python
class TextField:
	def __init__(self, length, field_name):
		self.length=length
		self.field_name = field_name

	def __get__(self, instance, owner):
		# return self.value
		return instance.__dict__.get(f"TextField_{self.field_name}", None)

	def __set__(self, instance, value):
		if not type(value) == str:
			raise TypeError("Value should be a string")
		if len(value) > self.length:
			raise ValueError(f"Value cannot exceed {self.length} characters")

		instance.__dict__[f"TextField_{self.field_name}" ] = value


	def __delete__(self, instance):
		pass

class PersonTable:
	first_name = TextField(20, "first_name")
	last_name = TextField(30, "last_name")

p = PersonTable()
p.first_name = "Hans"
p.last_name = "Kloss" 
print(p.first_name, p.last_name) # Kloss, Kloss
print(p.__dict__) # {'text_field_value': 'Kloss'}
```

---------------------

## Using `__set_name__`
> - `__set_name__` is defined in the descriptor class and called each time the descriptor is instantiated
> - the second parameter(`name`) of that method captures the name of the class attribute the instance of the descriptor is assigned to

```python
class TextField:
	def __init__(self, length):
		self.length=length
		
	def __set_name__(self, owner, name):
	    self.name = name

	def __get__(self, instance, owner):
		# return self.value
		return instance.__dict__.get(f"TextField_{self.name}", None)

	def __set__(self, instance, value):
		if not type(value) == str:
			raise TypeError("Value should be a string")
		if len(value) > self.length:
			raise ValueError(f"Value cannot exceed {self.length} characters")

		instance.__dict__[f"TextField_{self.name}" ] = value


	def __delete__(self, instance):
		pass


class PersonTable:
	first_name = TextField(20)
	last_name = TextField(30)

p = PersonTable()
p.first_name = "Hans"
p.last_name = "Kloss" 
print(p.first_name, p.last_name) # Kloss, Kloss
print(p.__dict__) # {'text_field_value': 'Kloss'}
```

-----------
## define deleter
```python
class TextField:
# ...
	def __delete__(self,  instance):
		del instance.__dict__[f"Text_field_{self.name}"]
	
```


-----------
## `self, owner, instance`

```python
class Descriptor:
    def __get__(self, instance, owner):
        pass
    
    def __set__(self, instance, value):
        pass
    
    def __delete__(self, instance):
        pass
```

`self` - represents an instance of that class
`owner` - refers to the class from where the descriptor is invoked (and set to a class variable)
				in the example below PersonTable class owns the descriptor
```python
print(PersonTable.__dict__)
{'__module__': '__main__', 
 
 'first_name': <__main__.TextField object at 0x7ff3e4d81210>, 
 'last_name': <__main__.TextField object at 0x7ff3e4d813d0>, 
 
 '__dict__': <attribute '__dict__' of 'PersonTable' objects>, 
 '__weakref__': <attribute '__weakref__' of 'PersonTable' objects>, '__doc__': None}
```

	`PersonTable` is owner of these specific instances of the descriptor class named `TextField`

- `instance` refers to the instance of the owing class

	WHEN THE DESCRIPTOR ATTRIBUTE IS ACCESSED FROM THE CLASS DIRECTLY, THE INSTANCE ARGUMENT IS SET TO `None`
```python
class TextField:
# ...

	def __get__(self, instance, owner):
		# return self.value
		print(instance)
		print(owner)
 	if instance is None:
 	    return self
		return instance.__dict__.get(f"TextField_{self.name}", None)

# ...

class PersonTable:
	first_name = TextField(20)
	last_name = TextField(30)

p = PersonTable()
p.first_name = "Hans"
p.last_name = "Kloss" 
print(PersonTable.first_name)
# None
# <class '__main__.PersonTable'>
# <__main__.TextField object at 0x7fd48aa81110>
```

-------------

# Non-Data Descriptor

> [!important]  Non-Data Descriptor
> Descriptor that implements only `__get__`

- DATA descriptor has the highest precedence (**before** the `instance.__dict__`)
- NON-DATA descriptor doesn't have the highest precdence (**after** the `instance_dict__`)

add to `PersonTabel` and `TextField` a new non-data descriptor:
```python
from random import randint

class LuckyNumber:
	def __get__(self, instance, owner):
		return randint(1,100)


class PersonTable:
	first_name = TextField(20)
	last_name = TextField(30)
	person_num = LuckyNumber()

p = PersonTable()
print(p.person_num)
p = PersonTable()
p.first_name = "Jan"
p.last_name = "Kowalski"
# p.person_num = 10
print(p.person_num)
print(p.__dict__)
print(PersonTable.person_num)
# 61
# {'TextField_first_name': 'Jan', 'TextField_last_name': 'Kowalski'}
# 27
```

----------
# Properties vs Descriptors

- properties provide syntactic sugar over the descriptor protocol
- descriptors are significantly more reusable
- in small project properties are good but in large projects descriptors are better



## properties provide syntactic sugar over the descriptor protocol
```python
class PersonTableWithProps:
    
    def __init__(self, first_name_length):
        self._TextField_first_name = None
        self.first_name_length = first_name_length
        
    @property
    def first_name(self):
        return self._TextField_first_name
        
    @first_name.setter
    def first_name(self, value):
        if not type(value) == str:
            raise TypeError(f"Value should be a string")
        
        if len(value) > self.first_name_length:
            raise ValueError(f"Value cannot exceed {self.first_name_length} characters")
            
        self._TextField_first_name = value
        
    @first_name.deleter
    def first_name(self):
        del self._TextField_first_name
        

p = PersonTableWithProps(10)
p.first_name = "Jerry"
print(p.first_name) # Jerry

# p.first_name = "abc"*11
# Traceback (most recent call last):
#   File "<string>", line 27, in <module>
#   File "<string>", line 17, in first_name
# ValueError: Value cannot exceed 10 characters


# p.first_name = 123*11111
# Traceback (most recent call last):
#  File "<string>", line 27, in <module>
#  File "<string>", line 14, in first_name
# TypeError: Value should be a string
```

but this syntax above is just a syntactic suger for that one:
```python
class PersonTableWithProps:
    
    def __init__(self, first_name_length):
        self._TextField_first_name = None
        self.first_name_length = first_name_length
        
    
    def get_first_name(self):
        return self._TextField_first_name
        
    
    def set_first_name(self, value):
        if not type(value) == str:
            raise TypeError(f"Value should be a string")
        
        if len(value) > self.first_name_length:
            raise ValueError(f"Value cannot exceed {self.first_name_length} characters")
            
        self._TextField_first_name = value
        
    
    def del_first_name(self):
        del self._TextField_first_name
        
    first_name = property(fget=get_first_name, fset=set_first_name, fdel=del_first_name)


p = PersonTableWithProps(10)
p.first_name = "Tom"
print(p.__dict__)
# {'_TextField_first_name': 'Tom', 'first_name_length': 10}
```


`first_name = property(fget=get_first_name, fset=set_first_name, fdel=del_first_name)` - this is descriptor protocol


## descriptors are significantly more reusable
if  you want to add some new attributes, your call will be horrible
```python
class PersonTableWithProps:
    
    def __init__(self, first_name_length, last_name_length, occupation_length):
        self._TextField_first_name = None
        self._TextField_last_name = None
        self._TextField_occupation = None
        
        self.last_name_length = last_name_length
        self.occupation_length = occupation_length
        self.first_name_length = first_name_length
        
    @property
    def first_name(self):
        return self._TextField_first_name
        
    @first_name.setter
    def first_name(self, value):
        if not type(value) == str:
            raise TypeError(f"Value should be a string")
        
        if len(value) > self.first_name_length:
            raise ValueError(f"Value cannot exceed {self.first_name_length} characters")
            
        self._TextField_first_name = value
        
    @first_name.deleter
    def first_name(self):
        del self._TextField_first_name

#################        
    @property
    def last_name(self):
        return self._TextField_last_name
        
    @last_name.setter
    def last_name(self, value):
        if not type(value) == str:
            raise TypeError(f"Value should be a string")
        
        if len(value) > self.last_name_length:
            raise ValueError(f"Value cannot exceed {self.last_name_length} characters")
            
        self._TextField_flast_name = value
        
    @last_name.deleter
    def first_name(self):
        del self._TextField_last_name
        
################################3
    @property
    def occupation(self):
        return self._TextField_occupation
        
    @occupation.setter
    def occupation(self, value):
        if not type(value) == str:
            raise TypeError(f"Value should be a string")
        
        if len(value) > self.occupation_length:
            raise ValueError(f"Value cannot exceed {self.occupation_length} characters")
            
        self._TextField_occupation = value
        
    @occupation.deleter
    def first_name(self):
        del self._TextField_occupation
        

p = PersonTableWithProps(10, 5, 7)
p.first_name = "Jerry"
print(p.first_name)
```


if you use descriptor:
```python
class PersonTableWithDescriptor
	first_name=TextField(10)
	last_name=TextField(5)
	occupation=TextField(7)
```






