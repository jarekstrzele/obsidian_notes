[[_ 0 Python OOP]]

**dunders** double underscore methods

# Object reprezentation
## `__repr__`
```python
class Book:
    def __init__(self, title, author, book_type, pages):
        self.title=title
        self.author = author
        self.book_type = book_type
        self.pages = pages
        

b1 = Book("Koziołek Matołek", "Kornel Makuszyńsrki","komiks", "34")
print(b1) # <__main__.Book object at 0x7f733c189f10>

```

add a new method to  the `Book` class:
```python
   def __repr__(self):
	   return f"title: {self.title}, author: {self.author}"

print(b1) # title: Koziołek Matołek, author: Kornel Makuszyńsko
```


### `__repr__` vs `__str__`

`__str__` is a string representation of an object
add to the `Book` class a new method:
```python
  def __str__(self):
        return f'<string representation> Title: {self.title}, book type: {self.book_type}, pages: {self.pages}'
```

```python
print(repr(b1))
print(str(b1))
```

- The `str()` function returns a ==user-friendly== description of an object.
- The `repr()` method returns a ==developer-friendly== string representation of an object.

**How this functions work**?
- When you call `str()` on an object, it calls the special method `__str__` of the object.
-  And when you call `repr()` on an object, it calls the special method `__repr__` of the object.
- Also, when you call `print()` on an object, it calls `__str__` method of the object. If `__str__` is not implemented, the `__repr__` is called as a fallback.

---

# Object formating
## `__format__`
This dunder allow us to control and customize how our own objects will be format.

formating numbers
```python
a = 100

print(f'{a}' )
print(f'{a:.3f}' )
print(format(a, '.3f'))
print('{:.3f}'.format(a))
```


```python
class Book:
    def __init__(self, title, author, book_type, pages):
        self.title=title
        self.author = author
        self.book_type = book_type
        self.pages = pages
    
    
    def __repr__(self):
        return f"title: {self.title}, author: {self.author}, book type:{self.book_type}, pages: {self.pages}"
        
    def __format__(self, format_spec):
        if format_spec == 'short':
            return f"title: {self.title}, author:{self.author}"
        

b1 = Book("Koziołek Matołek", "Kornel Makuszyńsko", "komiks", "34")
print(b1) 
print("---- short ----")
print(f"{b1:short}")
print(format(b1, 'short'))
print("{:short}".format(b1))

```


# Object Equality
## `__eq__`

```python
class Sparrow:
    def __init__(self, length, mass):
        self.length=length
        self.mass = mass

s1 = Sparrow(16, 39)
s2 = Sparrow(16, 39)
print(s1==s2)
print(id(s1), id(s2))
```

our implementation for  `__eq__`:
```python
class Sparrow:
    def __init__(self, length, mass):
        self.length=length
        self.mass = mass
        
    def __eq__(self, other):
        if not isinstance(other, Sparrow):
            return False
        return True if self.length==other.length and \
			           self.mass==other.mass \
 		            else False

s1 = Sparrow(16, 39)
s2 = Sparrow(16, 39)
print(s1==s2)
s3 = Sparrow(16, 30)
print(s1==s3)
print(s1=="23")

```



# Hashing and Mutability

```python
my_list = ["ala", "ma", 12]
my_dict = { my_list: "new list"}
# TypeError: unhashable type: 'list'
```

```python
my_list = ["ala", "ma", 12]
hash(my_list)
# TypeError: unhashable type: 'list'

```


==immutable objects== are hashable
```python
my_tuple = ("ala", "ma", 12)
print(hash(my_tuple))
# ok
```

other:
- int
- string
- bool
- float ...

>[!important] hashable object
>- it could be compared to other objects
>- if it compares equal, shares the same hash with the other object
>- it has a has value that never changes over its life
>

```python
a = "dom"
print(hash(a))
b = a
print(hash(b))
c = "dom"
print(hash(c))
a = "domy"
print(f"teraz a: {a}" )
print(hash(a))
print(hash(b))
print(hash(c))

# 5047170301842377569
# 5047170301842377569
# 5047170301842377569
# teraz a: domy
# 6332118699000456437
# 5047170301842377569
# 5047170301842377569 
```


>[!info] hash
>a hash is just a fixed-length integer that identifies an object

>[!important] hashable
>an object is hashable if it:
>	- has a hash value that never changes over its life
>	- is comparable to other objects, and
>	- shares the same hash  value   to as equal with objects it compares
>
>Immutable data types in python (imt, str, ...) are hashable.
>Hashes are extremely useful in facilitating fast looups in:
>	- dict
>	- membership checks in sets (=> keys and set members need to be hashable)
>
```python
a = ["jeden", [222]]
my_set = {a, 123}
print(my_set) # TypeError: unhashable type: 'list'
```

## Hashable classes

>[!info]
>- by default , user-defined classes are hashable
>- when we define dunder `__eq__`, python makes that class unhashable
>- we make a class hashable again by defining dunder hash which should always return an integer
>- as it is closely related to equality, it's a good idea for dunder hash to consider the same attributes that `__eq__` uses in determinining equality

```python
class Monster:
    def __init__(self, name, anger_level):
        self.name = name
        self.anger_level = anger_level
        
cookie_monster = Monster("Janusz", 22)
print(hash(cookie_monster)) # 8760676633164
```

```python
class Monster:
    def __init__(self, name, anger_level):
        self.name = name
        self.anger_level = anger_level
    
    def __eq__(self, other):
        if not isinstance(other, Monster):
            return False
        
        return True if self.name == other.name
cookie_monster = Monster("Janusz", 22)
cm = Monster("Janusz", 1)
print(hash(cookie_monster)) # TypeError: unhashable type: 'Monster'
```
If you add a new definition `__hash__(self)` objects will be hashable:
```python
# all objects of the Monster class will have 1 as their hash
# this is not correct
   def __hash__(self):
        return 1
```

To repair that, use attributes from the `__eq__` methdo:
```python
class Monster:
    def __init__(self, name, anger_level):
        self.name = name
        self.anger_level = anger_level
    
    def __eq__(self, other):
        if not isinstance(other, Monster):
            return False
        
        return True if self.name == other.name and \
                       self.anger_level == other.anger_level else False
        
    def __hash__(self):
        return hash((self.name, self.anger_level)) # tuble are hashable by default
        
cookie_monster = Monster("Janusz", 22)
cm1 = Monster("Janusz", 3)
cm2 = Monster("Janusz", 3)
print(cm1==cm2)
print(cm1==cookie_monster)
```



## `__gt__`

```python
class Book:
    def __init__(self, title, author, book_type, pages):
        self.title = title
        self.author = author
        self.book_type = book_type
        self.pages = pages
        
    def __eq__(self, other):
        if not isinstance(other, Book):
            return False
            
        return self.title == other.title and self.author == other.author
        
    def __gt__(self, other):
        if not isinstance(other, Book):
            return NotImplemented
            
        return self.pages > other.pages

    def __ge__(self, other):
        if not isinstance(other, Book):
            return NotImplemented
            
        return self.pages >= other.pages
        
    def __le__(self, other):
        return NotImplemented
        
book1 = Book("Potom", "Sienkiewicz", "horror", 151900)
book2 = Book("Hobbit", "Tolkien", "romansidło", 121)


print(book1  > book2)
print(book1  < book2)
print(book1  >= book2)
print(book1  <= book2)
print(book1  > "nowa książka")
```

### Better way
#### `functools` Higher order functions and operations on callable objects

> `total_ordering`

```python
from functools import total_ordering

@total_ordering
class Book:
    def __init__(self, title, author, book_type, pages):
        self.title = title
        self.author = author
        self.book_type = book_type
        self.pages = pages
        
    def __eq__(self, other):
        if not isinstance(other, Book):
            return False
            
        return self.title == other.title and self.author == other.author
        
    def __gt__(self, other):
        if not isinstance(other, Book):
            return NotImplemented
            
        return self.pages > other.pages

# you need only __eq__ and one of {__gt__, lt, ge, le}
# wrap you class by the total_ordering function
# Book = total_ordering(Book)
# or use decorator @total_ordering

book1 = Book("Potom", "Sienkiewicz", "horror", 151900)
book2 = Book("Hobbit", "Tolkien", "romansidło", 121)


print(book1  > book2)
print(book1  < book2)
print(book1 >= book2)
print(book1 <= book2)
print(book1 == book2)
print(book1 != book2)

```



# Truthiness `__bool__`
- objects, including instances of user-defined classes. by default, are thruthy
- to cusomize this behavior, we define special logic within dunder bool

add to Book class
```python
	def __bool__(self):
		return bool(self.pages) and not(self.pages < 1)
```


## `__len__`
`len(book1)` => TypeError: object of type 'Book' has no len()

add to class Book
```python
def __len__(self):
	return self.pages if self.pages > 0 else 0
```


If you don't define `__bool__`, Python search for `__len__`, so
when you define `__len__`, you don't have to define `__bool__`


# Container Class 
``
```python
class Dragon:
    def __init__(self, name, power):
        self.name=name
        self.power=power
        
# container class
class Cave:
    def __init__(self, capacity):
        self.dungeons=[]
        self.capacity= capacity
    
    def add_dragon_to_dungeon(self, dragon):
        if not isinstance(dragon, Dragon):
            raise TypeError("Only dragons can be imprisoned in these types of dungeon ")
        
        if not self.capacity > len(self.dungeons):
            raise OverflowError("Dungeons are full!")
        
        self.dungeons.append(dragon)
        print(f" {dragon.name} added")

misiek = Dragon("Misiek", 10)
puchatek = Dragon("Puchatek", 100)
zadziora = Dragon("Zadziora", 123)

jaskinia = Cave(2)
jaskinia.add_dragon_to_dungeon(misiek)
jaskinia.add_dragon_to_dungeon(puchatek)
jaskinia.add_dragon_to_dungeon(123)
#jaskinia.add_dragon_to_dungeon(zadziora)
```


## `__add__` dungeon + dragon

- our custom class can support the plus operato -> we  have to implemente `__add__`
- to guarantee commutativity ->implement  `__radd__`
`obj1.__add__(obj2)` -> if it doesn't work -> `obj2.__radd__(obj1)`

- other operators could be similarly overloaded to support user-defined classes
`__sub__` and `__rsub__`
`__mul__` and `__rmul__`
`__div__` and `__rdiv__`


```python
# ...
misiek = Dragon("Misiek", 10)
puchatek = Dragon("Puchatek", 100)
zadziora = Dragon("Zadziora", 123)

jaskinia = Cave(2)
jaskinia + misiek #TypeError: unsupported operand type(s) for +: 'Cave' and 'Dragon'
```

add to Cave class:
```python
	def __add__(self, dragon: 'Drago') -> 'new dungeons':
```

```python
class Dragon:
    def __init__(self, name, power):
        self.name=name
        self.power=power
    
    def __repr__(self):
        return f"I'am {self.name}" 
        
# container class
class Cave:
    def __init__(self, capacity):
        self.dungeons=[]
        self.capacity= capacity
    
    def add_dragon_to_dungeon(self, dragon):
        if not isinstance(dragon, Dragon):
            raise TypeError("Only dragons can be imprisoned in these types of dungeon ")
        
        if not self.capacity > len(self.dungeons):
            raise OverflowError("Dungeons are full!")
        
        self.dungeons.append(dragon)
        print(f" {dragon.name} added")
    
    def __repr__(self):
        return str(self.dungeons)
        
    def __add__(self, dragon: 'Dragon') -> 'new dungeons':
        if not isinstance(dragon, Dragon):
            raise TypeError("Only dragons can be imprisoned in these types of dungeon ")
        
        new_dungeons = Cave(self.capacity)
        
        for d in self.dungeons:
            new_dungeons.add_dragon_to_dungeon(d)
        
        new_dungeons.add_dragon_to_dungeon(dragon)
        
        return new_dungeons

    def __radd__(self, dragon):
         if not isinstance(dragon, Dragon):
            raise TypeError("Only dragons can be imprisoned in these types of dungeon ")
        
         return self + dragon
        

misiek = Dragon("Misiek", 10)
puchatek = Dragon("Puchatek", 100)
zadziora = Dragon("Zadziora", 123)

jaskinia = Cave(2)
jaskinia.add_dragon_to_dungeon(misiek)
# print('nowe lochy ', jaskinia + puchatek)
# print(jaskinia)

print('nowe lochy ', puchatek + jaskinia)



```


## `__getitem__`
How to get dragon from the dungeon?
You can define a new function `get_dragon()`, but also you can do this in more pythonic way redefining `__getitem__` method

> implementing `__getitem__` also makes our class iterable


First way:
```python
# ...
	    
    def __getitem__(self, item):
        return self.dungeons[item]


misiek = Dragon("Misiek", 10)
puchatek = Dragon("Puchatek", 100)
zadziora = Dragon("Zadziora", 123)

jaskinia = Cave(10)
jaskinia.add_dragon_to_dungeon(misiek)
jaskinia.add_dragon_to_dungeon(puchatek)
jaskinia.add_dragon_to_dungeon(zadziora)
print(jaskinia[2])
```

==more sophisticated way==
```python
	   def __getitem__(self, item):
        if isinstance(item, str):
            return [dragon for dragon in self.dungeons if item in dragon.name]
        
        return self.dungeons[item]


jaskinia = Cave(10)
jaskinia.add_dragon_to_dungeon(misiek)
jaskinia.add_dragon_to_dungeon(puchatek)
jaskinia.add_dragon_to_dungeon(zadziora)
print(jaskinia["Za"]) # -> [I'am Zadziora]
print(jaskinia["ek"]) #->[I'am Misiek, I'am Puchatek]
print(jaskinia[1:2])
print(("-------"))
for dragon in jaskinia:
    print(dragon)
```









