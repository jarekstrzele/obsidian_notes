# SECTION 13  Metoda  `__init__`  
#python/__init__ 
  
```py
class Phone:   
	pass
	p = Phone.__new__(Phone) # -> creates and returns an objectp.__init__() # -> init the object  

def __init__(self, *args, **kwargs):  

   ...  

   

def __init__(self, **kwargs):      
	for attr_name, attr_value in kwargs.item():  
         setattr(self, attr_name, attr_value)  

  ```


WALIDACJA  

def __init__(self, brand, model, price):      if isinstance(price, (int, float)):  

            sel.price = price  

      else:  

            raise TypeError("this arg must be int or float")  

  ---
  
# SECTION 9  HERMETYZACJA

property   - językowo metoda,  użytkowo własność  
```py
class Phone:  

 def __init__(self, price):  
  self._price = price    

 def get_price(self):  
  return self._price  

 def set_price(self, value):  
  if isinstance(value, (int, float)):
    if value > 0:  
     self._price = value
	else:
     raise ValueError('The price attribute must be positive.')   
  else:
      raise TypeError('The price attribute must be an int or float value')
  ```

W powyższym kodzie brakuje walidacji na etapie tworzenia obiektu -> zmienić __init__  
```py
def __init__(self, price):  

      self.set_price(price)  
```
  

----------------------  

**P R O P E R T Y**  

```py
class Phone:  

  

 def __init__(self, price):  

 self._price = price  

  

 def price(self):  

 return self._price  

     

 def set_price(self, value):  

 self._price = value  

  

 # property 'price' jest tylko do odczytu, nawet nie można jej skasować
  price = property(**fget**=price) 
  # aby można było ją modyfikować
  # price = property(**fget**=price, **fset**=set_price)
  

p = Phone(1000)  

p.price -> 1000  

``` 


jak usuwać atrybuty?  

dodajemy  

def del_price(self):
   print('deleting...')  

   del self._price

price = property(**fget**=price, **fset**=set_price, **fdel**=del_price)

del ob.price
# można przywrócić 'price'
# ob.price = 100  

  

**DEKORATORY**  

> to funkcja, która przyjumje za parametr funkcję, którą chcemy udekorować i następnie  
> 
> tworzy wewnętrzną funkcję, która nadpisuje funkcję przesłaną i zwraca wewnętrzną funkcję  

def pp(func):  

 def wrapper():  

 print('='*30)  

 func()  

 print('='*30)  

 return wrapper  

  

pp(hello)()  

hello = pp(hello)  

hello()  

  

z dekoratorem  

@pp  

def hello():  

  print('Python')  

  

hell0() -> udekorowany napis 'Python'
  

  

**DEKORATOR   P R O P E R T Y**  

class Phone:  

  

 def __init__(self, price):  

 self._price = price  

  @property  # property do odczytu  

 def price(self):  

 return self._price  

     

 def set_price(self, value):  

 self._price = value  

  

 # aby ustawić:  

 # price = price.setter(set_price)   

lepsze rozwiązanie  

@price.setter
def price(self, value):  self._price = value  

aby usunąć  

@price.deleter
def price(self):  

   del self._price     

aby walidacja była dostępna na poziomio tworzenie obiektu  

def __init__(self, price):  

    self.price = price  # 'price' jest już property  

inny przykład  

class Worker:  

     

    def __init__(self, first_name, last_name):  

        self._first_name = first_name  

        self._last_name = last_name  

         

    def get_first_name(self):  

        return self._first_name  

         

    def get_last_name(self):  

        return self._last_name  

         

    first_name = property(fget=get_first_name)  

    last_name = property(fget=get_last_name)  

     

worker = Worker('John', 'Dow')  

print(worker.first_name)  

print(worker.last_name)  

  

---

  

 # SECTION 16  OBLICZANIE ATRYBUTÓW

  
```py
class Model:
	
	def __init__(self, y_true, y_pred):  

		 if not isinstance(y_true, (list, tuple):  

			 raise TypeError('The y_true object must be of type list or tuple'  

				 f'Not {type(y_true.__name__}')  

  
 self._y_true = y_true
 self._y_pred = y_pred
 self._accuracy = None  

  

 @property  

 def y_true(self):  

 return self._y_true  

  

 @y_true.setter  

 def y_true(self, value):  

 self._y_true = value  

 self._accuracy = None  

  

 @property  

 def y_pred(self):  

 return self._y_pred  

  

 @y_pred.setter  

 def y_true(self, value):  

 self._y_pred = value  

 self._accuracy = None  

  

 @property  

 def accuracy(self):  

 if not self._accuracy:  

 print('Calculating...')  

 self._accuracy = sum([ i == j   

 for i,j in zip(self.y_true, self.y_pred)]) / len(self.y_true)  

 print(f'Model accuracy: {self._accuracy:.4f}')  

  

model = Model([0,0,1,0,0,1,0], [0,0,1,0,0,0,0])  

model.__dict__  


```

import math   

  

class Circle:  

  

    def __init__(self, radius):  

        self.radius = radius  

        self._area = None  

         

    

    @property  

    def radius(self):  

        return self._radius  

  

    @radius.setter  

    def radius(self, value):  

        self._radius = value  

        self._area = None  

         

    @property  

    def area(self):  

        if self._area is None:  

            self._area = math.pi * self._radius * self._radius  

        return self._area  

  

circle = Circle(3)  

print(f'{circle.area:.4f}')