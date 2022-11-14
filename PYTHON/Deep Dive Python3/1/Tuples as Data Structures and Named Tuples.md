
[[_ Deep Dive INTRO]]


---

# Tuples as Data Structures and Named Tuples
[[Tuples - Named Tuples]]



> tuples are read-only lists
> but
> this way of thinking misses out on some interesting ideas


TUPLES:
==position of value has meaning== so tuples are as a data records or strucures

## Tuples as Data Structures
__container__ an object that contains other objects

tuples | lists | strings
------- | ------| -------
containers | containers | containers
order matters | order matters | order matters
==heterogeneous==/<br>homogeneous |heterogeneous/<br>==homogeneous== | homogenenous
indexable | indexable | indexable
iterable | iterable | iterable
immutable: <br> - fixed length <br> - fxed order: <br> - can't do in-place sorts <br> - can't do in-place reversals| mutable: <br> - length can change <br> - order of elems can change: can do in-place sorts <br> can do in-place reversals | immutable: <br> - fixed length <br> - fxed order: <br> can't do in-place sorts <br> can't do in-place reversals

---

Think of a tuple as a data record where the position of data has meaning

		london = ('London', 'UK', 8_780_000)
		new_york= ('New_york', 'New York', 8_500_000)

`city=london[0] `

>indexing,   slicing,     interating ,     upacking

__unpacking__
```py
city, country, population = ('London', 'UK', 8_780_000)

city, country, population = 'London', 'UK', 8_780_000

city, _, population = ('New_york', 'New York', 8_500_000)
```

```py
record = ('DJIA', 2018, 1, 19, 25987.35, 26071.72, 25942.83,26071.72)

symbol, year, month, day, *_, close = record
symbol, year, month, day, *ignored, close = record

```


__LISTs__ are typically __homogenous__
__TUPLEs__ are typically __heterogenious__
```py
london = 'London', 'UK', 8_780_00
new_york  = 'New York', 'USA', 8_500_00
beijing = 'Beijing', 'China', 21_000_000

cities = [london, new_york, beijing]
total = sum([city[2] for city in cities])

print(total) # -> print(total)

for city, country, population in cities:
	print(city, country, population)


for index, city in enumarate(cities):
	print(index, city)

```







