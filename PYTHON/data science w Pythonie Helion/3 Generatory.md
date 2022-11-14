[[3 - Zaawansowane koncepcje]]


---
# Generatory

### generator ( ... for .. in ...)

```python
generator = (f'data-{x}' for x in range(4))
print(generator)
# <generator object <genexpr> at 0x7fb5263e04d0>

print(next(generator))
print(next(generator))
print(next(generator))
print(next(generator))
print(next(generator))

data-0
data-1
data-2
data-3
--------------------------
StopIteration                             Traceback (most recent call last)
<ipython-input-7-78c2ea1818d1> in <module>()
      3 print(next(generator))
      4 print(next(generator))
----> 5 print(next(generator))

StopIteration: 
```
**`StopIteration`** to nie błąd, ale informacja, że wyczerpaliśmy zasoby z generatora
czyli generator to jakby lista, która usuwa swoje elementy po ich odczytaniu

### generator `iter` na iteratorze
```python
gen = iter(range(3))
gen = iter(range(3))
print(next(gen))
print(next(gen))
print(next(gen))
print(next(gen))

0
1
2
------------------------------------
StopIteration                             Traceback (most recent call last)
<ipython-input-20-0c958d4f889d> in <module>()
      3 print(next(gen))
      4 print(next(gen))
----> 5 print(next(gen))

StopIteration: 
```



### generator funkcja z `yield`



na przykład mamy bardzo duży plik, zaczytanie wszystkich danych na raz mogłoby zapełnić pamięć RAM, więc potrzebujemy czegoś co będzie częsciami zaczytywać dane

```python
# funkcja zwraca generator
def lazy_load(path):
	f = open(path, 'r')
	for line in f:
        # yield - obietnica zwrócenia 1 linii
		yield line

gen = lazy_load('emails.txt')
next(gen) # -> zwraca jedną linię z pliku

```

NIESKOŃCZONY GENERATOR CIĄGU FIBBONACCIEGO
```python
# funkcja zwraca generator
def fib(a=0, b=1):
	while True:
		yield a
		a, b = b, a+b

f = fib() # f jest generatorem
# lista 20 pierwszych liczb fibbonacciego
print([next(f) for i in range(20)])

# [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597, 2584, 4181]

```




