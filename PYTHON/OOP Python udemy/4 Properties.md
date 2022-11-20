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

















