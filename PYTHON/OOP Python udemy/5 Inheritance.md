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
wirus_zombi.reproduce()
```
> 
> Inheritance is a example of *is a* relationship
> 











