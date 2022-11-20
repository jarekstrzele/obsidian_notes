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













