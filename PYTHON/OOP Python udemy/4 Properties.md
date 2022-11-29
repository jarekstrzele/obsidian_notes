[[_ 0 Python OOP]]

```python
class Customer:
  def __init__(self, loyalty):
    self.loyalty = loyalty


c1 = Customer("bronze")
c2 = Customer("gold")
c3 = Customer("platinum")

def get_discount(customer):
  discounts = {
    "bronze": .1,
    "gold": .2,
    "platinum":.3
  }

  discount = discounts.get(customer.loyalty, None)
  if not discount:
    raise ValueError("Could not determine the customer's discount!")

  return discount 

for customer in [c1,c2,c3]:
  print(f"Your discount is {get_discount(customer):.0%}")


```


In Python:
- accessor methods (getters, setters) for attributes are best added when needed
- it's considered best practice to start with plain, public attributes and evolve to controlled access only as needed


We need to restrict the set of init values  for customers (only bronze, gold, platinum)
```python
class Customer:
  loyalty_levels = {"bronze", "gold", "platinum"}
  
  def __init__(self, loyalty):
    self.set_loyalty(loyalty)


  def get_loyalty(self):
    return self.loyalty

  def set_loyalty(self, level):
    if level not in self.__class__.loyalty_levels:
      raise ValueError(f"Invalid loyalty {level} specified")

    self.loyalty = level

c1 = Customer("Niedopuszczalna wartość atrybuty")
print("Done")

####
#->  ValueError: Invalid loyalty Niedopuszczalna wartość atrybuty specified
```

A problem:
`c2=Customer("bronze")`
`c2.loyalty = "Niedopuszczalna wartość atrybutu"` -> ok

Solution `self.loyalty` -> `self._loyalty`

```python
class Customer:
  loyalty_levels = {"bronze", "gold", "platinum"}
  
  def __init__(self, loyalty):
    self.set_loyalty(loyalty)


  def get_loyalty(self):
    return self._loyalty

  def set_loyalty(self, level):
    if level not in self.__class__.loyalty_levels:
      raise ValueError(f"Invalid loyalty {level} specified")

    self._loyalty = level

c1 = Customer("bronze")
c1.loyalty = "Błędny atrybut, ale nowy"
print(c1.__dict__)
print(c1._loyalty)
print("Done")
```


# Private and Mangled Attributes

the code above and changed by to dunderscore :
```python
   self.__loyalty = level

c1 = Customer("bronze")

print(c1.__dict__)
print(c1.__loyalty)
print(c1.__dict__) #{'_Customer__loyalty': 'bronze'}
print("Done")
```

# Property
You can write `c1.loyalty` or `c1.__loyalty`. You have to write `c1.get_loyalty()`

To get the functionality from function and notation from the dot notation => use property

```python
class Customer:
  loyalty_levels = {"bronze", "gold", "platinum"}
  
  def __init__(self, loyalty):
    self.loyalty = loyalty #self.set_loyalty(loyalty)

  def get_loyalty(self):
    return self._loyalty

  def set_loyalty(self, level):
    if level not in self.__class__.loyalty_levels:
      raise ValueError(f"Invalid loyalty {level} specified")

    self._loyalty = level
    
  loyalty =property(fget=get_loyalty, fset=set_loyalty)

c1 = Customer("bronze")

print(c1.__dict__)
print(c1.loyalty)
c1.loyalty ="gold"
print(c1.loyalty)

print("Done")
```


add a new attr membership
```python

class Customer:
  loyalty_levels = {"bronze", "gold", "platinum"}
  
  def __init__(self, loyalty, membership):
    self.loyalty = loyalty #self.set_loyalty(loyalty)
    self.membership = membership

  

  def get_membership(self):
    return self._membership

  def set_membership(self, years):
    if years < 0 or years > 30:
      raise ValueError("Invalid years, allowed values: <0,30>")
    self._membership = years


  def get_loyalty(self):
    return self._loyalty

  def set_loyalty(self, level):
    if level not in self.__class__.loyalty_levels:
      raise ValueError(f"Invalid loyalty {level} specified")

    self._loyalty = level
    
  loyalty = property(fget=get_loyalty, fset=set_loyalty)
  membership = property(fget= get_membership, fset=set_membership) 

c1 = Customer("bronze", 12)

print(c1.__dict__)
print(c1.loyalty)
c1.membership=12
print(c1.membership)
# c1.membership +=33 # ValueError
print("Done")
```

### You find these properties in the class dict:
```python
for k,v in Customer.__dict__.items():
    print(f'key ({k}): value({v}' )
```
-  all the properties we define live in the class' mappingproxy, not the instance dictionary
- properties take precedence over instance attributes of the same name


## Decorator 

### syntax
```python

class Customer:
  loyalty_levels = {"bronze", "gold", "platinum"}
  
  def __init__(self, loyalty, membership):
    self.loyalty = loyalty #self.set_loyalty(loyalty)
    self.membership = membership

  
  @property    
  def membership(self):
    return self._membership
  
  @membership.setter
  def membership(self, years):
    if years < 0 or years > 30:
      raise ValueError("Invalid years, allowed values: <0,30>")
    self._membership = years

  @property
  def loyalty(self):
    return self._loyalty

  @loyalty.setter
  def loyalty(self, level):
    if level not in self.__class__.loyalty_levels:
      raise ValueError(f"Invalid loyalty {level} specified")

    self._loyalty = level
   
c1 = Customer("bronze", 12)

print(c1.__dict__)
print(c1.loyalty)
c1.membership=12
print(c1.membership)
 
print("Done")
```

>[[!info]] decorator
>It is a function that:
>	- takes another function as an argument
>	- adds some functionality
>	- returns it
>	- no change in the function passed as a argument

### some explanation

#### functions
```python
def ten_times(x):
    return x*10

print(ten_times(12))
new_old_func=ten_times
print(new_old_func(12))


def pass_two_to(func):
    two = 2
    
    return func(two)
    
print(pass_two_to(ten_times))
```

defining function within a another function
	and return a result of this inner function
```python
def outer():
    def inner():
        return "inner function"
    
    result=inner()
    
    return result
    
print(outer())

```

and return a reference to this inner function
```python
def outer():
    def inner():
        return "inner function is comming"
    
    return inner
    
print(outer())
xxx = outer()
print(xxx())
```

#### closures
#python/closure 

>[! important] closure
>It is a nested function that has access to a variable in its outer enclosing scope

```python
def greet(who):
    how = " Hello my friend! You are "
    def make_complex_greeting():
        print(f"{how} {who}! And I come from inner function")
    
    return make_complex_greeting
    
greeting = greet("Hans Solo")
greeting()
```

`make_complex_greeting` remembers the variable `how` and this function and variable `how` are closure

### decorators
```python
from random import randint

def lotto():
    return randint(1,49)
    
for i in range(6):
    print(lotto())
```

with some decorator:
```python
from random import randint

def lotto():
    return randint(1,49)
    
for i in range(6):
    print(lotto())
    
def even_or_odd(func):
    def inner():
        num=func()
        print(f"The numer {num} is {'even' if num % 2 == 0 else 'odd'}" )
    
    return inner

lotto = even_or_odd(lotto)
for i in range(6):
    print(lotto())
```

the same with `@`
```python
from random import randint
    
def even_or_odd(func):
    def inner():
        num=func()
        print(f"The numer {num} is {'even' if num % 2 == 0 else 'odd'}" )
    
    return inner

@even_or_odd
def lotto():
    return randint(1,49)

for i in range(6):
    print(lotto())
```


## Read or Write Onlyt Properties

==read only== set only getter property
```python
class Pirate:
    def __init__(self, name):
        self._name=name
        
    @property 
    def name(self):
        return self._name

p = Pirate("Sparrow")
print(p.name)
p.name="Matti Cash"
```












