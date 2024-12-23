[[_ 0 Python OOP]]
#python/inheritance 

```python
class Virus: # Super/Base/Parent class
	pass

class RNAVirus(Virus): # Derived/Child/Subclass class
	pass

class CoronaVirus(RNAVirus):
	pass

class SARSCov2(CoronaVirus):
	pass


```


```python
class Virus: 
	def __init__(self, name, reproduction_rate, virus_number):
	    self.name=name
	    self.reproduction_rate=reproduction_rate
	    self.virus_number=virus_number
	    self.host=None
	    
	def infect(self, host):
	    self.host=host
	     
	def reproduce(self):
	    if self.host is not None:
	        self.virus_number *= (1+self.reproduction_rate)
	        
	        return True, f"Virus reproduce in {self.host}. Number of virus {self.virus_number}" 
	     
	    raise AttributeError("Virus needs to infect a host")
	     
wirus_zombi = Virus("zombi", 2.93, 1)
# wirus_zombi.infect("human")
print(wirus_zombi.reproduce())
```


> Inheritance is a example of **is-a** relationship
```python
class Virus: 
	def __init__(self, name, reproduction_rate, virus_number):
	    self.name=name
	    self.reproduction_rate=reproduction_rate
	    self.virus_number=virus_number
	    self.host=None
	    
	def infect(self, host):
	    self.host=host
	     
	def reproduce(self):
	    if self.host is not None:
	        self.virus_number *= (1+self.reproduction_rate)
	        
	        return True, f"Virus reproduce in {self.host}. Number of virus {self.virus_number}" 
	     
	    raise AttributeError("Virus needs to infect a host")
	     
class DraculaVirus(Virus):
    genome="super blood dna"
    
    def reproduce(self):
        success, status = Virus.reproduce(self)
        
        if success:
            print(f"{self.name} just replicated in the cytoplasm of {self.host} cell")
            
class BimbrownicusVirus(Virus):
  genome="vodka superpower"
    
  def reproduce(self):
   success, status = Virus.reproduce(self)
        
   if success:
       print(f"{self.name} just replicated in the nucleus of {self.host} cell")      


virus_dv = DraculaVirus("DV", 1.2, 3.11)
# print(virus_dv.reproduce())
virus_dv.infect("Hrabia Drakula")
print(virus_dv.reproduce())

sb = BimbrownicusVirus("SB", 4.2, 2.7)
# print(virus_dv.reproduce())
sb.infect("Hrabia Drakula")
print(sb.reproduce())
```

inheritance:
- add or modify functionality from an existing class without modifying that class
- this contributes to code reuse and organization as well as object hirerchies that are easy to reason about

--------
# All classes inherit from object

```python
o1 = object()
o2 = object()
print(id(o1), id(o2))
print('class: ', o1.__class__)
print('repr: ', o1.__repr__)
```


## `__call__`

>   
>   object is callable - its type implement  `__call__`
>   

`ClassName()` - you call the class

---

# Method resolution Order

1. first Python checks `__dict_` of an object
2. second checks `__dict__` of a class
3. third checks `__dict__` of a parent class until `object`
4.  if it doesn't find,  raise  `AttributeError`

```python
class Roslina:
    jakas_roslina="jakaś roślina"

class Mniszek(Roslina):
    rodzaj_class = "klasowy rodzaj"
    
    def __init__(self, rodzaj):
        self.rodzaj = rodzaj

m = Mniszek("Miniszkowaty")
print(m.rodzaj)
print(m.__dict__)
print(m.rodzaj_class)
print(m.jakas_roslina)
print(Mniszek.__base__)
print(Roslina.__base__)
print(Mniszek.__mro__)
print(Roslina.__mro__)
print(object.__base__)

```

---

# Parent Delegation

- the pythonic way to reference the parent class from a subclass is to use the `super()`  built-in
- `super()` returns an instance of the parent class, enabling us to directly reference its methods and attributes
- `super()` could be called within any subclass method as well at any step, i.e. not necessarily thi first thing we do

```python
class Pies:
    kolor = 'czerwony'
    
    def __init__(self, imie, rasa):
        self.imie=imie
        self.rasa=rasa
        
    def atakuj(self, wrog):
        print(f'{self.imie} atakuje {wrog}' )

class Doberman(Pies):
    
    def pokaz_kolor(self):
        print(super().kolor)
        
class Bernenczyk(Pies):
    
    
    def atakuj(self, wrog):
        super().atakuj(wrog)
        print("Berneńczyk tylko żartuje, że atakuje")

d=Doberman('zabójca', 'doberman')
d.pokaz_kolor()
d.atakuj('złodziej')
b=Bernenczyk('Figa', 'bernanski pies pasterski')
b.atakuj('złodziej')
```


#### `__init__`
```python
class Parent:
    def __init__(self, age):
        self.age=age
        print(f'{self} is {self.age} old')
        
class Child(Parent):
    pass

# man = Child()
# TypeError: __init__() missing 1 required positional argument: 'age'
man=Child(22)
```


---
## Subclassing Properties

- properties defined in the parent coud be extended/modified in the subclass
- properties live in the namespace of the class in which they-re defined, reffering to them from subclasses you have to use fullname `className.propertyName`

```jsx
class Parent:
    def __init__(self, gold):
        self.gold=gold
        
    @property
    def gold(self):
        print("I am getter from Parent")
        return self._gold
    
    @gold.setter
    def gold(self, v):
        print("I am setter from Parent")
        if v < 1:
            raise ValueError("Value must be greater than 1")
        self._gold=v

p = Parent(100)
print(p.gold)
p.gold=1
print(p.gold)

class Child(Parent):
    pass

ch = Child(10)
print(ch.gold)
ch.gold=-21
```

you can change `Child` class
```jsx
class Child(Parent):
    @Parent.gold.setter
    def gold(self, v):
        print('I am setter from Child')
        self._gold = v

ch = Child(10)
print(ch.gold)
ch.gold=-21
print(ch.gold)
```


## Extending Built-ins
- in python, you could extend the behavior of built-in data structures just like we do with regualr user-defined ones
- to do that:
	- define a subclass that inherits from the respective built-in
	- modify/enhance only the behaviour you care about


```python
uczniowie = {
    "jan": [1,2,2,6],
    "zuzia": [3,1,5],
    "marek": [6,6,6]
}
print(uczniowie['jan'])
print(uczniowie['JAN'])

[1, 2, 2, 6]
Traceback (most recent call last):
  File "<string>", line 7, in <module>
KeyError: 'JAN'
```

```python
class ManagerUczniow(dict):
    def __getitem__(self, item):
        if item not in self:
            return "Sorki, ale takiego ucznia"
        
        return super().__getitem__(item)

uczniowie = ManagerUczniow({
    "jan": [1,2,2,6],
    "zuzia": [3,1,5],
    "marek": [6,6,6]
})
print(uczniowie['jan'])
print(uczniowie['JAN'])

[1, 2, 2, 6]
Sorki, ale takiego ucznia
```

other example
```python
my_list = [1,2,3,4,5,10]
print(sum(my_list)/len(my_list))

class ModernList(list):
    @property
    def avg(self):
        return sum(self)/len(self)
        

ml = ModernList([1,2,3,4,5,10])
print(ml.avg)
```

or
```python
my_list = [1,2,3,4,5,10]
print(sum(my_list)/len(my_list))

class ModernList(list):
    
    def __init__(self,*args):
        if args and type(args[0]) != list:
            super().__init__(args)
        else:
            super().__init__(args[0])
            
    @property
    def avg(self):
        return sum(self)/len(self)
        

ml = ModernList(1,2,3,4,5,10)
print(ml.avg)
ml = ModernList([1,2,3,4,5,10])
print(ml.avg)
```

First, instead of overriding built-in type, look at https://docs.python.org/3/library/collections.html

----
# Composition
Maybe instead of using inheritance use COMPOSITON:
> one object is made to contain others and produce more complex constructs


> [!info] inheritance
> use inheritance for objects 
> that naturally align in "is-a" relationships

>[!info] composition
>use composition for those objects 
>that conceptually fit "has-a" relationships














