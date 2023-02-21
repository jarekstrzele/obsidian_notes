# 150 ćw. OOP Python
[[0-OOP wprowadzenie OOP Krawkowiak]]
[[2 OOP Krakowiak]]

`sys.version.split()[0]` -> wersja pythona
`sys.version.split()`
output: `['3.7.13', '(default,', 'Apr', '24', '2022,', '01:04:09)', '[GCC', '7.5.0]']`


---
### przestrzeń nazw moduły datetime
#python/datetime

```python
import datetime

for n in sorted(datetime.__dict__):
  print(n)
```

---
### [[builtins]]
```python
import builtins
 
help(builtins.sum)
print(builtins.sum([-4, 3, 2]))
 
```

----
## Atrybuty klasy
wyświetl wszystkie klucze atrybutu słownikowego `__dict__` klasy Container
```python
class Container:
    """This is a Container class."""
 
 
print(Container.__dict__.keys())
```


wyświetlenie wartości atrybutu `__module__`
```python 
class Container:
  """This is a Container class"""

print(Container.__module__)
```
output: `__main__`

`print(an_object.__class__)` == `print(type(an_oject))

#python/isinstance
`print(isinstance(object1, Class1))`
`print(isinstance(object1, (Class1, Class2)))`

wyświetlenie wartości atrybutów klasy
#python/getattr
```python
class Phone:
    brand = 'Apple'
    model = 'iPhone X'
    
print(getattr(Phone, 'brand')
print(getattr(Phone, 'model'))
```

#python/setattr
```python
class Laptop:
    brand = 'Lenovo'
    model = 'ThinkPad'

setattr(Laptop, 'brand', 'Acer')
setattr(Laptop, 'model', 'Predator')

print(f'brand: {Laptop.brand}')
print(f'model: {Laptop.model}')
```

#python/del #python/delattr
```python
class OnlineShop:
    sector = 'electronics'
    sector_code = 'ELE'
    is_public_company = False
 
# del OnlineShop.sector_code
delattr(OnlineShop, 'sector_code')

```

atrybuty klasy
#python/class_attributes
```python
class HouseProject():
    number_of_floors = 3
    area = 100
    
    def describe_project(cls):
        print(f"Floor number: {cls.number_of_floors}")
        print(f"Area: {cls.area}")
        
HouseProject().describe_project()
```


# Atrybuty instancji
#python/object_attributes
```python
class Book:
    language = 'ENG'
    is_ebook = True


book_1 = Book()
book_2 = Book()

book_1.author = 'Dan Brown'
book_1.title = 'Inferno'

book_2.author = 'Dan Brown'
book_2.title = 'The Da Vinci Code'
book_2.year_of_publishment = 2003

books = [book_1, book_2]
for book in books:
  for attr in book.__dict__:
    print(f"{attr} -> {getattr(book, attr)}")

  print("-"*30)

```

## tworzenie atrybutów instancji
`object_1.nowy_atrybut=wartosc_nowego_atrynutu`

przy użyciu metody `setattr(obiekt, atrybut, wartość)`
```python
class Book:
    language = 'ENG'
    is_ebook = True
 
 
books_data = [
    {    
        'author': 'Dan Brown', 
        'title': 'Inferno'
    },
    {
        'author': 'Dan Brown',
        'title': 'The Da Vinci Code',
        'year_of_publishment': 2003,
    },
]
 
books = []
for book_data in books_data:
    book = Book()
    for attr, value in book_data.items():
        setattr(book, attr, value)
    books.append(book)
 
for book in books:
    print(book.__dict__)
```
output:
```shell
{'author': 'Dan Brown', 'title': 'Inferno'}
{'author': 'Dan Brown', 'title': 'The Da Vinci Code', 'year_of_publishment': 2003}

```

```python
class Book:
    language = 'ENG'
    is_ebook = True
 
    def set_title(self, value):
        if not isinstance(value, str):
            raise TypeError(
                'The value of the title attribute must be of str ' )
        self.title = value
  
book = Book()
book.set_title('Inferno')
print(book.title)
```

```python
class Book:
    language = 'ENG'
    is_ebook = True
 
    def set_title(self, value):
        if not isinstance(value, str):
            raise TypeError(
                'The value of the title attribute must be of str ')
        self.title = value
  
book = Book()
 
try:
    book.set_title(False)
except TypeError as error:
    print(error)
```

---
# 11 `__init__`

tworzenie obiektu z dowolną ilością argumentow nazwanych
```python
class Bucket:
    
    def __init__(self, **kwargs):
        for attr, val in kwargs.items():
          setattr(self, attr, val)

bucket = Bucket(apple=3.5, milk=2.5, juice=4.9, water=2.5)
print(bucket.__dict__)
```

z walidacją jednego atrybutu
```python
class Laptop:
    def __init__(self, brand, model, price):
        self.brand = brand
        self.model = model
        if isinstance(price, (int, float)) and price > 0:
            self.price = price
        else:
            raise TypeError(
                'The price attribute must be a positive int or float.'
            )
 
 
laptop = Laptop('Acer', 'Predator', 5490)
print(laptop.__dict__)
```


z przechwytywaniem błędu
```python
class Laptop:

    def __init__(self, brand, model, price):
        self.brand = brand
        self.model = model
        if isinstance(price, (int, float)) and price > 0:
            self.price = price
        else:
            raise TypeError('The price attribute must be a positive int or float.')

try:
  laptop = Laptop('Acer', 'Predator', '5900')
except TypeError as err:
  print(err)
```

---
# 12 Widoczność zmiennych

```python
 
    def __init__(self, brand, model, price):
        self.brand = brand   # zwykły, goły
        self._model = model  # chroniony
        self.__price = price # prywatny
```


```python
class Laptop:
 
    def __init__(self, brand, model, price):
        self.brand = brand
        self._model = model
        self.__price = price
 
 
laptop = Laptop('Acer', 'Predator', 5490)
print(f'brand -> {laptop.brand}')
print(f'model -> {laptop._model}')
print(f'price -> {laptop._Laptop__price}')
```

wyświetlania prywanych atrybutów
```python
  def display_private_attrs(self):
        for attr in self.__dict__:
            if attr.startswith(f'_{self.__class__.__name__}__'):
                print(attr)  
```


---
# 13 Hermetyzacja

```python
class Laptop:
 
    def __init__(self, price):
        self._price = price
 
    def get_price(self):
        return self._price
 
    def set_price(self, value):
 
        if isinstance(value, (int, float)):
            if value > 0:
                self._price = value
            else:
                raise ValueError(
                    'The price attribute must be a positive int '
                    'or float value.'
                )
        else:
            raise TypeError(
                'The price attribute must be an int or float type.'
            )
 
 
laptop = Laptop(3499)
try:
    laptop.set_price('-3000')
except TypeError as error:
    print(error)
```

#python/property
```python
class Person:
 
    def __init__(self, first_name):
        self._first_name = first_name
 
    def get_first_name(self):
        return self._first_name
 
    first_name = property(fget=get_first_name)
        
 
person = Person('John')
print(person.first_name)
```

```python
class Person:
  def __init__(self, first_name, last_name):
    self._first_name = first_name
    self._last_name = last_name 

  def get_first_name(self):
    return self._first_name

  def get_last_name(self):
    return self._last_name
  
  first_name = property(fget=get_first_name)
  last_name = property(fget=get_last_name)

p = Person('John', 'Dow')
print(p.first_name)    
print(p.last_name)
```

```python
class Person:
  def __init__(self, first_name):
    self._first_name = first_name
   
  def get_first_name(self):
    return self._first_name

  def set_first_name(self, v):
    self._first_name = v
  
  first_name = property(fget=get_first_name, fset=set_first_name)
 
p = Person('John')
p.first_name = 'Mike'
print(p.first_name) 
```

#python/del 
```python
class Person:

    def __init__(self, first_name):
        self._first_name = first_name

    def get_first_name(self):
        return self._first_name

    def set_first_name(self, value):
        self._first_name = value

    def del_first_name(self):
      del self._first_name

    first_name = property(fget=get_first_name, fset=set_first_name, fdel=del_first_name)

p = Person('Tom')
p.del_first_name()
print(p.__dict__)
```

#python/property 
```python
class Pet:
  def __init__(self, name):
    self._name = name

  @property
  def name(self):
    return self._name

pet = Pet('Max')
print(pet.__dict__)
```

```python
class Pet:
  def __init__(self, name, age):
    self._name = name
    self._age = age

  @property
  def name(self):
    return self._name

  @property
  def age(self):
    return self._age


pet = Pet('Max', 5)
print(pet.__dict__)

```

setter
#python/setter
```python
class Pet:
  def __init__(self, name):
    self._name = name

  @property
  def name(self):
    return self._name

  @name.setter
  def name(self, value):
    self._name = value

  
pet = Pet('Max')
pet.name = 'Oscar'
print(pet.__dict__)
```


```python
class Pet:
  def __init__(self, name, age):
    self._name = name
    self.age = age

  @property
  def name(self):
    return self._name

  @name.setter
  def name(self, value):
    self._name = value

  @property
  def age(self):
    return self._age 

  @age.setter
  def age(self, v):
    if not isinstance(v, int):
      raise TypeError('The value of age must be of type int')
    if v <= 0:
      raise ValueError('The value of age must be positive integer')
    self._age = v

try:
  pet = Pet('Max', 'seven')
except TypeError as err:
  print(err)
```

#python/deleter
```python
class TechStack:
 
    def __init__(self, tech_names):
        self._tech_names = tech_names
 
    @property
    def tech_names(self):
        return self._tech_names
 
    @tech_names.setter
    def tech_names(self, value):
        self._tech_names = value
 
    @tech_names.deleter
    def tech_names(self):
        del self._tech_names
 
        
tech_stack = TechStack('python,java,sql')
print(tech_stack.tech_names)
 
tech_stack.tech_names = 'python,sql'
print(tech_stack.tech_names)
 
del tech_stack.tech_names
print(tech_stack.__dict__)
```

```python
class Game:
  def __init__(self, level=0) -> None:
      self.level = level 
  @property
  def level(self):
    return self._level

  @level.setter
  def level(self, v):
    if not isinstance(v, int):
      raise TypeError('The value of leve must be of type int.')
    if v < 0:
      self._level = 0
    elif v > 100:
      self._level = 100
    else:
      self._level = v
      
games = [ Game(), Game(10), Game(-10), Game(120)]
for game in games:
  print(game.level)
  
```

----
# 14 Obliczanie atrybutów
#python/property 
```python
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
```

---
# 15 Metoda klasy
#python/classmethod 

```python
class Person:
 
    def show_details(cls):
        print(f'Running from {cls.__name__} class.')
        
    show_details = classmethod(show_details)
 
 
Person.show_details()
```

```python
class Container:
    @classmethod
    def show_details(cls):
        print(f"Running from {cls.__name__} class.")
        

Container.show_details()
container = Container()
container.show_details() # ok
```

```python
class Person:
  instances = []

  def __init__(self):
    Person.instances.append(self)

  @classmethod
  def count_instances(cls):
    return len(Person.instances)

a = Person()
b = Person()
c = Person()

print(Person.count_instances())
```


---
# Metoda statyczna
#python/staticmethod

```python
import time
 
 
class Container:

    def get_current_time():
        return time.strftime('%H:%M:%S', time.localtime())
 
    get_current_time = staticmethod(get_current_time)
```

```python
import uuid


class Book:

    def __init__(self, title, author):
        self.book_id = Book.get_id()
        self.title = title
        self.author = author
        
        
    @staticmethod
    def get_id():
    """zwraca 6-ci elementowy string"""
        return str(uuid.uuid4().fields[-1])[:6]
        
book1=Book('Inferno', 'Dan Brown')
print(book1.__dict__.keys())

```


---
# Metody specjalne
```python
class Vector:

    def __init__(self, *components):
        self.components = components

    def __repr__(self):
        return f'Vector{self.components}'

    def __str__(self):
        return f'{self.components}'

    def __len__(self):
        return len(self.components)
        
    def __bool__(self):
       return False if not self.components or self.components[0]==0 else True
        
v1 = Vector()
v2 = Vector(3,2)
v3 = Vector(0, -3, 2)
v4 = Vector(5, 0, -1)

print(bool(v1))
print(bool(v2))
print(bool(v3))
print(bool(v4))
```


```python
class Vector:

    def __init__(self, *args):
        self.components = args

    def __repr__(self):
        return f"Vector{self.components}"

    def __str__(self):
        return f'{self.components}'

    def __len__(self):
        return len(self.components)
        
v1 = Vector(4,2)
v2 = Vector(-1,3)

try:
  v1+v2
except TypeError as err:
  print(err)
```

```python
class Vector:
 
    def __init__(self, *components):
        self.components = components
 
    def __repr__(self):
        return f'Vector{self.components}'
 
    def __str__(self):
        return f'{self.components}'
 
    def __len__(self):
        return len(self.components)
 
    def __add__(self, other):
        components = tuple(
            x + y
            for x, y in zip(self.components, other.components)
        )
        return Vector(*components)
 
 
v1 = Vector(4, 2)
v2 = Vector(-1, 3)
print(v1 + v2)
```


