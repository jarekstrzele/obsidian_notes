

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

W **Sicie Eratostenesa**, każda liczba jest reprezentowana przez **indeks** w liście , przy czym wartość `True`, będzie wskazywać na liczbę pierwszą, a wartość `False` na liczbę złożóną.

- Na początku wszystkie elementy listy są ustawione na `True`, czyli potencjalnie są liczbami pierwszymi
- indeksy odpowiadające liczbom złożonym (czyli wielokrotnościom liczb pierwszych) są zmieniane na `False`, a te, które pozostają `True`, są liczbami pierwszymi.

**przykład** dla `n=10`
``












