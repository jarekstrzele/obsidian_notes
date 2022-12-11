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
> 
> Inheritance is a example of *is a* relationship
> 
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











