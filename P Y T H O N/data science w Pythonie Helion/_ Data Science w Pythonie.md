#data_science  #python  #żero_oleg #helion 

----
# Wstęp data science
[[3 - Zaawansowane koncepcje]]


---
Zawartość tej notatki:
[[#funkcja]]
[[#anonimowe lambda]]
[[#klasy]]
[[#list comprehension]]
[[#MODUŁY]]
		[[#math]]
		[[#random]]
		[[#statistics]]
				
[[#STRING]]
[[#Datetime]]


-----
## funkcja
najbardziej generyczna:
```python
def exampl(arg1, arg2, *args, kw="xx", kw2="yy", **kwargs):
	pass
```

wywołanie w terminalu samej nazwy funkcji -> SYGNATURA funkcji

### anonimowe, lambda
#python/reduce  #python/map  #python/filter #python/lambda
```python
X = list(range(10))

# PRZEKSZTAŁCANIE
# comprehension
[x**2 + 1 for x in X]
# to samo z lambda
list(map(lambda x: x**2 +1, X))

# WYBIERANIE
# comprehension
[x for x in X if x % 2]
# to samo z lambda
list(filter(lambda x: x%2, X))

# AGREGACJA
# reduce wykonuja atomiczne obliczenie
# przez które akumulują się wszystkie
# wartości
import functools import reduce

reduce(lambda x, y: x + y, X)
reduce(lambda x, y: x * y, X)



```

## klasy
`nazwa_obiektu.__dict__` -> wszystkie własności obiektu
`nazwa_klasa__base__` -> co jest bazową klasą tej klasy

`@property`, `@classmethod`  , `@staticmethod`, 
dziedziczenie, kompozycja

## list comprehension
`[ [i for j in range(2)] for i in rang(3) ]` -> `[[0,0], [1,1], [2,2]]`

```python
cities = ['London', 'Oslo', 'Tokyo']
calls = [2,4,10]

{x:y for x, y in zip(cities, calls)}
```


## MODUŁY
### math
`import math`

#### type float
`math.nan` not a number, jak null, ale bardziej szczegółowy przypadek 

`math.inf` nieskończoność
`math.inf - 10**100` -> inf

`math.`+tab -> jakie są metody

`math.floor`
`math.ceil`
`math.factorial`


### random
#python/random

`import random`

`random.gauss(0,1)`
`random.uniform(0,1)`

```python
import random

a = list(range(100))

# losowe wybieranie elementów z próbki
random.sample(a, 2) # wybierz dwie próbki z a

# losowe przetasowanie
random.shuffle(a) # zmienia listę a

# losowe wybranie int z przedziału
random.randint(0,10)

# lista liczb losowych
[random.random() for x in range(10)]

# ZIARNO SEED, jeżeli je zdefiniujemy
# sekwencja liczb będzie taka sama
random.seed(43)
[random.random() for x in range(5)]
[random.random() for x in range(5)] # będzie taki sam wynik, jak w porzedniej

```

### statistics
`import statistics`

`statistics.mean([1,2,3])`
`statistics.variance([1,2,3])`
`statistics.median([1,2,3])`
...

-----
## STRING
`t.split()` z `string` do `list`
	odwrotna do split jest join
	`''.join(lista)` z `list` do `string`
`t.strip()` likiwidacja spacji na początku i na końcy
`t.count(v)` ile razy `v` w `t`

### `import string`
`string.ascii_letter`
...

`print("{:02d}".format(1))` -> 01
`print("{:04d}".format(1))` -> 0001

`ord('T')`  zwraca liczbę ascii danej litery
	odwrotną jest `char(84)` -> 'T'

`s = "This is some stuff 123-haha"`
`s.translate({ord('T'):'1', ord('s'): '2'})`
`1hi2 i2 2ome ...`

### `import re`
```python
# string zaczyna się od e lub E 
# potem trzy dowolne znaki 
# końcowy znak to l
pattern ='^[eE]...l$'

s1 = 'email'
s2 = 'elvis'
re.match(pattern, s1)
re.match(pattern, s2)

# znajdowanie
pattern = '\d' # pojedyczna liczba
re.findall(pattern , s)
# '\d+' co najmniej jedna liczba


# podmiana
pattern = '\d+'
# trzy liczby zamień na '???'
re.sub(pattern, '???', s)


```


----
## Datetime
### time
`import time`

Ten moduł ma funkcję `sleep` (zatrzymanie programu na kilka sektun)

### datetime
obsługuje: datę, godzinę, strefy czasowe
`from datetime import datetime`

```python
from datetime import datetime
teraz = datetime.now() # -> 2022-06-28 06:30:29.034359
print(teraz)

# zmiana daty na unikalną sygnaturę czasową
print(datetime.timestamp(teraz) )# -> 1656397829.034359

# składowe daty
print(datetime.date(teraz)) #->2022-06-28
print(teraz.year)

# tworzenie obiektów czasowe 
b = datetime(year=2020, month=1, day=1, hour=1, minute=10, second=1)
print(b)
# ze string do date
bday='19 Feb 1986 10:40:12'
print(datetime.strptime(bday, '%d %b %Y %H:%M:%S' ))

# z date do string
print(b.strftime('Born: %h:%m on %d-%m-%y'))
```


#### operacje
a, b to obiekty czasowe
`a - b`
`dt = a - b`
`c  = a + (dt /2)`
....

#### tworzenie w locie obietów czasowych
```python
from datetime import timedelta

[(b + timedelata(day=x)).strftime('%a') for x in range(10)]



```


#### strefy czasowe `pytz`
#python/pytz

```python
import pytz
here = datetime.now(pytz.timezone('Europ/Warsaw'))

there = datetime.now(pytz.timezone('America/NewYork'))
```

```python
(here - there).second //3600
```



