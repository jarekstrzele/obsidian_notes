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







