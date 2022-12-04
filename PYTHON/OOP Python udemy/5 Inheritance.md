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
- this contrubutes to code reuse and organization as well as object hirerchies that are easy to 








