
## Section 19 metody specjalne
#python/__new__  #python/__init__ 

```py
class Company:

	def __init__(self, name):
		self.name = name

company = Company('Micri')

company2  = Company.__new__(Company)
company2.__init__('Micri')

```

#python/__repr__
zwraca formalą reprezentację obiektu
`help(object.__repr__)`

```py
class Phone:
 ...

 def __repr__(self):
	 return f'Phone {self.brand}'
```


#python/__str__
nieformalna reprezentacja obiektu
gdy jest zaimplementowana *_ _repr_ _* oraz *_ _str_ _* ,to:
- używając funkcji *print* będzie wywołane *_ _ str _ _*,
- używając funkcji *str* będzie wywołane *_ _ str _ _*,
- wywołując samą nazwę obiektu będzie wywołane *_ _ repr _ _*,

#python/__len__
w klasie `object` nie jest zaimplementowana

#python/__bool__
zwraca False lub True
gdy brak jej implementacji, działa funkcja `len` 
gdy klasa nie implementuje `len` wszystko jest True
np
```py
class Point:
...
	def __bool__(self):
		return sum(self._coord_) != 0

```


`object._ _add_ _ _(self, other) `

`object._ _iadd_ _ _(self, other) `  self += other

implementując eq  not ne jest przez Python samodzielnie opracowywana

`return NotImplemented`


 ##### metoda _ _ hash _ _
 - zwraca liczbę całkowitą
- obiekty, które są równe mają tę samą wartość hash

```py
class Doc:
 pass

d1 = Doc()
d2 = Doc()

hash(d1), hash(d2)

---
(8739368757593, 8739368757665)

```

>W klasie
implementując metodę `__hash__` powinniśmy również zaimplementować metodę `__eq__`.
Jeżeli zdefiniujemy '`__eq__` ', ale nie `__hash__` to nasze obiekty nie będą mogły bć elementami zbiorów lub słowników (ogólnie w kolekcjach hashowalnych)


##### metoda _ _ call _ _
pozwala na naszej instancji wykonać wywołania `moj_obiekt()`
```py

class ....

	def __call__(self):
		print(f'Wywołanie..{self}'')
```

```py
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
		components = tuple(x + y for x, y in zip(self.components, other.components))
		return Vector(*components)

v1 = Vector(4, 2)
v2 = Vector(-1, 3)
print(v1 + v2)
```