[[_ 0 Python OOP]]
#python/dataclass

INTRO:
*problem* : you want to have a structure to save some data without behaviors

- often in programming we need instances whose sole purpose is to encapsulate data
- built-in data structures (list, tuple, dict) are not usefull in large projects
- defining a new class for that purpose is overhead

**dataclass** solves this problems

-----
# Another alternative
# Namedtuple

- use to encapsulate data with named attributes 
- creates tuple-like objects, with 
	- convenient defaults,
	- nice representations
	- easy access by
		- index
		- attribute name

```python
from collections import namedtuple

# namedtuple is a factory function
# namedtuple(new_type_name, list_of_attributes)
RE = namedtuple("RowerElektryczny", ["marka", "zasięg", "cena"])
row1 = RE("bmx", 40, 10000)
print(row1)

####
> RowerElektryczny(marka='bmx', zasięg=40, cena=10000)

```

```python
from collections import namedtuple

Kr = namedtuple("Krasnoludek", ["ksywa", "wzrost", "wiek"], defaults=("",10, 100))
koszalek = Kr()
print(koszalek.wzrost)
###
10
```

### from namedtuple to normal dict
```python
from collections import namedtuple


Kr = namedtuple("Krasnoludek", ["ksywa", "wzrost", "wiek"], defaults=("",10, 100))
koszalek = Kr()
print(koszalek.wzrost)

slownikowy_koszalek = koszalek._asdict()
print(koszalek)
print(slownikiwoy_koszalek)
```

a new syntax for attrs (single string with white space between attributes):
```python
from collections import namedtuple

Herbata = namedtuple("Hebratka", "nazwa rodzaj cena")
zielona_herbata = Herbata("Słodka zielen", "zielona", 9.54)
print(zielona_herbata)
```

### immutability
```python
from collections import namedtuple

Herbata = namedtuple("Hebratka", "nazwa rodzaj cena")
zielona_herbata = Herbata("Słodka zielen", "zielona", 9.54)
print(zielona_herbata)
zielona_herbata.nowyAtrybut = "coś nowego"
##
-> AttributeError: 'Hebratka' object has no attribute 'nowyAtrybut'
```

