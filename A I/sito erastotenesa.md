

Sito Eratostenesa to klasyczny algorytm do znajdowania wszystkich liczb pierwszych mniejszych niż pewna dana liczba **n**. Jest to jeden z najefektywniejszych sposobów na obliczanie liczb pierwszych w przedziale od 2 do n.


Algorytm Sito Eratostenesa działa na zasadzie **wykreślania** wielokrotności liczb, które są złożone, pozostawiając liczby pierwsze.


### Przykład działania dla n = 30:

1. Zaczynamy od listy liczb: 2, 3, 4, 5, 6, 7, 8, ..., 30.
2. Zaznaczamy 2 jako liczbę pierwszą, a następnie skreślamy wszystkie jej wielokrotności (4, 6, 8, 10, ..., 30).
3. Przechodzimy do 3, zaznaczamy ją jako liczbę pierwszą, i skreślamy wszystkie jej wielokrotności (6, 9, 12, ..., 30).
4. Przechodzimy do 5, zaznaczamy ją jako liczbę pierwszą, i skreślamy wszystkie jej wielokrotności (10, 15, 20, ..., 30).
5. Kontynuujemy do √30 ≈ 5.5. Liczby, które nie zostały skreślone to liczby pierwsze: **2, 3, 5, 7, 11, 13, 17, 19, 23, 29**.



## Sito implementacja w Pythonie
wstęp
```python
for i in range(0,10):
    print(i, end="") # 0123456789

for i in range(0,10,2):
    print(i, end="") # 02468
```

W **Sicie Eratostenesa** każda liczba jest reprezentowana przez **indeks** w liście , przy czym wartość `True`, będzie wskazywać na liczbę pierwszą, a wartość `False` na liczbę złożoną.

- na początku wszystkie elementy listy są ustawione na `True`, czyli potencjalnie są liczbami pierwszymi
- indeksy odpowiadające liczbom złożonym (czyli wielokrotnościom liczb pierwszych) są zmieniane na `False`, a te, które pozostają `True`, są liczbami pierwszymi.

**przykład** dla `n=10`
`[False, False, True, True, True, True, True, True, True, True, True]`
- `False` dla indeksów `0` i `1`, ponieważ 0 i 1 nie są liczbami pierwszymi.

po działaniu algorytmu
`[False, False, True, True, False, True, False, True, False, False, False]`
- `True` pozostaje na indeksach 2, 3, 5, 7, ponieważ są to liczby pierwsze.
- `False` oznacza liczby złożone (np. 4, 6, 8, 9, 10).

==implementacja==
`liczby = [True] * (n+1)` wypełniamy listę wartościami True, dajemy n+1, aby indeksy odpowiadały liczbą, czyli jeżeli n=10, to tablica musi mieć 11 elementów (ostatni element ma indeks 10).

```python
n=10
liczby = [True] *(n+1)
print(liczby) # [True, True, True, True, True, True, True, True, True, True, True]

liczby[0]=liczby[1]= False # indeksy 0 i 1 ustawiamy na False, bo nie są liczbami pierwszymi

# iterujemy od indeksu 2, czyli od pierwszej liczby pierwszej
# ustawiamy zakres od 2 do pierwiastek z 10 + 1 (range tworzy zakres otwarty)
for i in range(2, int(n**0.5)+1):
	if liczby[i]:
		# wielokrotności i zamieniamy True na False
		for j in range(i*i, n+1, i):
			liczby[j] = False
```
pierwsza iteracja:
- `i = 2`
- `liczby[2]==True` , więc warunek się wykona
	- `j= 4`, bo `i*i=2*2=4`, będziemy iterować do `n`, w kroku `2`
		- `liczby[4]=False`
	- `j=6`, bo `4+2`
		- `liczby[6]=False`
	- `j=8`, bo `6+8`
		- `liczby[8]=False`
	- `j=10`, bo `8+2`
		- `liczby[10]=False`
- `i=3`
	- `liczb[3]==True`, więc warunek się wykonuje
		- `j=6`, bo `i*i=9` 
			- `liczby[9]=False`
		- `j=12` poza zakresem


`[x for x in range(2, n + 1) if liczby[x]]`
tworzy listę, liczb pierwszych, bo zwraca liczby indeksów, dla których wartości są `True`



