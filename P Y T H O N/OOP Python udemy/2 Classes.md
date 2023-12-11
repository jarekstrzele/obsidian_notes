[[_ 0 Python OOP]]

#python/class 
#PEP8

## PEP8 
==P==ython ==E==nhancement ==P==roposal (jakby czysty kod dla Pythona)
Style Guide for Python Code
https://peps.python.org/pep-0008/

## Class
```python
# CamelCase - name
class Fiat126:
	pass

Fiat126 # -> <class '__main__.Fiat126'>
Fiat126.__base__ # -> a tuple of base classes
Fiat126.__name__ # -> a name of this class
Fiat126() # we call a class -> we get a new instance
fiat1 = Fiat126()
fiat2 = Fiat126()
fiat1 == fiat2 # -> false
```

```python
# __dict__ dundar dictionary
# attributes are in the class namespace
class Fiat126:
	doors = 2 # this class state is shared across all instances
	wheels = 4 # # this class state is shared across all instances

Fiat126.__dict__ # -> {'__module__': '__main__', 'doors': 2, 'wheels': 4, '__dict__': <attribute '__dict__' of 'Fiat126' objects>, '__weakref__': <attribute '__weakref__' of 'Fiat126' objects>, '__doc__': None}

# dynamically extended or changed
Fiat126.doors=4
Fiat126.engin = 'turbo'

# objects
f1 = Fiat126()
f2 = Fiat126()

f1.doors
f2.doors

f2.engin
f1.engin

```



## Methods and Behaviour
```python
class Fiat126:
	doors = 2
	wheels = 4

	def drive(self):
		return self

m1 = Fiat126()
print(m1 == m1.drive()) # True
print(m1 == Fiat126) # False
print(m1 is m1.drive()) # True

m2 = Fiat126()
print(m2.drive()) # -> <__main__.Fiat126 object at 0x7efdeb442d90>
print(m1.drive()) # -> <__main__.Fiat126 object at 0x7efdeb5374c0>

print(Fiat126.drive) # <function Fiat126.drive at 0x7fa4e618ae50>
print(type(Fiat126.drive)) # <class 'function'>

print(m1.drive) # <bound method Fiat126.drive of <__main__.Fiat126 object at 0x7f1adfff44c0>>
print(m2.drive) # <bound method Fiat126.drive of <__main__.Fiat126 object at 0x7f1adfeffd90>>

print(m1.drive == m2.drive) # False
print(m1.drive is m2.drive) # False
```


## Instance Attributes

```python
class Fiat126:
	doors = 2
	wheels = 4
	
	def __init__(self, color="black"):
	    self.color = color
	
	def drive(self):
	    return self

# m1 = Fiat126() -> TypeError: __init__() missing 1 required positional argument: 'color'

m1 =  Fiat126('red')
print(m1.color)
# print(Fiat126.color) -> AttributeError: type object 'Fiat126' has no attribute 'color'
```

### `getattr()`, `setattr()`
```python
m1 =  Fiat126('red')
print(getattr(m1, 'color')) "red"
m1.color = 'green'
print(getattr(m1, 'color')) # green
setattr(m1, 'color', 'black')
print(getattr(m1, 'color')) #  black
```

### You use this syntax to change attributes programatically:
```python
class Fiat126:
	doors = 2
	wheels = 4
	
	def __init__(self, color="black"):
	    self.color = color
	
	def drive(self):
	    return self


cars = [Fiat126('red'), Fiat126('green')]
attrs = ["doors", "wheels"]
values = [2, 4]
for car in cars:
    for attr, val in zip(attrs, values):
        setattr(car, attr, val)

print(cars[0].doors, cars[0].wheels, cars[0].color)
print(cars[1].doors, cars[1].wheels, cars[1].color)
```


### You can make your code simpler
```python
print(m1.newAttrNoExists) # AttributeError: 'Fiat126' object has no attribute 'newAttrNoExists'

try:
    print(m1.newAttrNoExists)
except AttributeError as e:
    print(e) # 'Fiat126' object has no attribute 'newAttrNoExists'

# simpler way
print(getattr(m1, "newAttrNoExists", "no attr found")) # no attr found


```



## `self`
`self` this name is a convention

```python
class Fiat126:
	doors = 2
	wheels = 4
	
	def __init__(self, color="black"):
	    self.color = color
	
	def drive(self):
	    return self
	
	# def auto_drive():
	#    print("Auto-driving ....")
	def auto_drive(aa):
		print("AA Auto-driving ...")

c1 = Fiat126()
c1.drive()
# c1.auto_drive() # auto_drive() takes 0 positional arguments but 1 was given
c1.auto_drive()
```

## class and static method, class method
>[!info] static vs class
>to decide whether to use `@staticmethod` or `@classmethod` you have to look inside your method. **If your method accesses other variables/methods in your class then use @classmethod**. On the other hand, if your method does not touches any other parts of the class then use @staticmethod.



#### static method
- a static method is like a regular function but hidden inside the class name

#### class method
- a class method:
	- one predefined parameter `cls`
	- use it to modify a class
```python
class Fiat126:
	doors = 2
	wheels = 4
	
	def __init__(self, color="black"):
	    self.color = color
	
	def drive(self):
	    return self
	
	@staticmethod
	def auto_drive():
		print("AA Auto-driving ...")


Fiat126.auto_drive()
c1 = Fiat126()
c1.auto_drive()
```

```python
class Fiat126:
    doors = 2
    wheels = 4
	
    def __init__(self, color="black"):
        self.color = color
	
    def drive(self):
        return self
	
    @staticmethod
    def auto_drive():
        print("AA Auto-driving ...")
	# other syntax
	# auto_drive = staticmethod(auto_drive)
	
    @classmethod
    def my_class_method(cls):
        return f'Hello I am cls: {cls} '
    # other syntax
	# my_class_method = staticmethod(my_class_method)
        
Fiat126.auto_drive()
c1 = Fiat126()
c1.auto_drive()
print(Fiat126.my_class_method())
print(c1.my_class_method())
```


## Dunder Dict - namespace
All instance attributes are stored in a mapping object that could be accessed using dunder dict
```python
class Fiat126:
    doors = 2
    wheels = 4
	
    def __init__(self, color="black"):
        self.color = color
	
c1 = Fiat126("white")
c2 = Fiat126("purple")
print(c1.color)
print(c1.__dict__)
print(c2.color)
print(c2.__dict__)
```
these two named spaces are completely separated
==The namespace of each instance is separated==
```python

c1.horse_power = 200
print(c1.__dict__)
print(c2.__dict__)

```

```python
c2.__dict__["horse_power"] = 499
print(c2.__dict__)
```


==Where is stored `__dict__` attribute?==
It is stored in the class  namespace!

1. all instance attributes are stored in an instance-specific mapping object ()
2. for instances, that mapping object is a plain python dictionary
3. it is accessed using `instance.__dict__` syntax

---
## Class vs Instance `__dict__`
Classes have their own namespaces.
```python
class Fiat126:
    doors = 2
    wheels = 4
	
    def __init__(self, color="black"):
        self.color = color
	
c1 = Fiat126("white")
print(c1.__dict__)
print(Fiat126.__dict__)
# {'__module__': '__main__', 'doors': 2, 'wheels': 4, '__init__': <function Fiat126.__init__ at 0x7f87076f2dc0>, '__dict__': <attribute '__dict__' of 'Fiat126' objects>, '__weakref__': <attribute '__weakref__' of 'Fiat126' objects>, '__doc__': None}
print(type(Fiat126.__dict__))
#<class 'mappingproxy'> # -> dictionary but keys are always string <- optimaliztion

```


First Python check the instance namespace (`object_name.__dict__`), 
if it can't find the attribute, it starts to check the class namespace (`class_name.__dict__`)


## Mutable, immutable class attributes

### immutable class attributes
immutable: `int   float   string   boolean tuple`
```python
class Fiat126:
    doors = 2
    wheels = 4
	
    def __init__(self, color="black"):
        self.color = color
	
c1 = Fiat126("white")
c2 = Fiat126()
print(c1.__dict__)
print(c2.__dict__)
print(Fiat126.__dict__)
print(c1.doors)
print(c2.doors)
c1.doors=5
print(c1.__dict__)
print(Fiat126.__dict__)
```


### mutable
mutable: `object`, `list ....`
```python
class Tire:
    def __init__(self, distance_covered):
        self.distance_covered = distance_covered

class Fiat126:
    doors = 2
    wheels = 4
    tires = [ Tire(200) for i in range(4)]
	
    def __init__(self, color="black"):
        self.color = color
	
c1 = Fiat126("white")
c2 = Fiat126()
print(c1.__dict__)
print(c2.__dict__)
print(c1.tires)
print(c2.tires)
c1.tires.append(Tire(300))
print(c1.tires)
print(c2.tires)
```
all cars share the same `Tire` objects (memory address)


## Docstrings
>[!info] Python Docstrings
>They are strings written as the first statement of a class, function  or module

`help` without docstrings
```python
class Tire:
    def __init__(self, distance_covered):
        self.distance_covered = distance_covered

class Fiat126:
    doors = 2
    wheels = 4
    tires = [ Tire(200) for i in range(4)]
	
    def __init__(self, color="black"):
        self.color = color

help(getattr)
help(Tire)
```

`help` that can uses docstrings
```python
class Tire:
    """Defines an automobile tire object.
    :param distance_covered: the distance in km the tire has covered
    """
    def __init__(self, distance_covered):
        self.distance_covered = distance_covered

class Fiat126:
    doors = 2
    wheels = 4
    tires = [ Tire(200) for i in range(4)]
	
    def __init__(self, color="black"):
        self.color = color

help(Tire)
```

This docstring is stored in `__doc__` built-in attribute (see `Tire.__dict__`)
`print(Tire.__dict__)`
`print(Tire.__dict__['__doc__'])`


