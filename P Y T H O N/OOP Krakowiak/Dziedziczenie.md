#python/inheritance
[[0-OOP wprowadzenie OOP Krawkowiak]]
[[Podstawy OOP]]

DZIEDZICZENIE
>mechanizm wzpółdzieleniea funkcjonalności pomiędzy klasami

```py
class Parent1:
	pass

class Parent2:
	pass

class Child(Parent1, Parent2)
	pass

class  Child2(Parent1):
	pass

class Child3(Parent1):
	pass

class SuperChild(Child3):
	pass

```


`issubclass(Vehicle, object)` -> True
`issubclass(MyClass, (class1, class2, ...)`



## MRO Method Resolution Order
#mro
- metody brane według dziedziczenie od najniższej klasy do coraz bardziej ogólnej aż do klasy `object`
- `ClassName.mro()`


## Nadpisywanie metod
#python/method_overriding
w sumie zgodnie z *MRO*

```py
class Vehicle:

	def __init__(self, category=None):
		self.category = category if category else 'land'

	def __repr__(self):
		return f'{self.__class__.__name__}(category={self.category})'

class LandVehicle(Vehicle):
	pass



```


```py
class A:

  

 def work(self):

 print("Working")

  

 def session(self):

 print('Start session')

 self.work()

 print("End session")

  
  

class B(A):

 def work(self):

 print("Playing.. in B")

  

a = A()

a.session() # -> Working

b = B()

b.session() # -> Playing in B

```

**ALE napisania nie będzie w tym przypadku** 
```py
class A:

  

 def work(self):

 print("Working")

  

 def session(self):

 print('Start session')

 A.work(self)

 print("End session")

  
  

class B(A):

 def work(self):

 print("Playing.. in B")

  

a = A()

a.session() # -> Working

b = B()

b.session() # -> Working

```


## SUPER()
```py
class Vehicle:

	def __init__(self, brand, year):
		self.brand = brand
		self.year = year

	def show():
		print("I come from Vehicle")

class Car(Vehicle):

	def __init__*self, brand, year, horsepower):
		super().__init__(brand, year)
		self.horsepower = horsepower

	def show():
		super().show()
		print('and from Car')

```


# Klasa Abstrakcyjna
#python/abstract_class
- to swoisty interfejs dla klas dziedziczących
- musi dziedziczyć po klasie ABC `import abc`

```py

from abc import ABC, abstractmethod

class Figure(ABC):

 @abstractmethod
 def area(self):
	 pass

  
class Square(Figure):

 def __init__(self, a=1):
	 self.a=a
 
 def area(self):
	 return self.a*self.a

figures = [Square(), Square(5), Square(10)]
for fig in figures:
 print(f'Side length: {fig.a}')

 print(f'Area: {fig.area()}')
```

