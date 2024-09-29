

Sito Eratostenesa to klasyczny algorytm do znajdowania wszystkich liczb pierwszych mniejszych niż pewna dana liczba **n**. Jest to jeden z najefektywniejszych sposobów na obliczanie liczb pierwszych w przedziale od 2 do n.


Algorytm Sito Eratostenesa działa na zasadzie **wykreślania** wielokrotności liczb, które są złożone, pozostawiając liczby pierwsze.


### Przykład działania dla n = 30:

1. Zaczynamy od listy liczb: 2, 3, 4, 5, 6, 7, 8, ..., 30.
2. Zaznaczamy 2 jako liczbę pierwszą, a następnie skreślamy wszystkie jej wielokrotności (4, 6, 8, 10, ..., 30).
3. Przechodzimy do 3, zaznaczamy ją jako liczbę pierwszą, i skreślamy wszystkie jej wielokrotności (6, 9, 12, ..., 30).
4. Przechodzimy do 5, zaznaczamy ją jako liczbę pierwszą, i skreślamy wszystkie jej wielokrotności (10, 15, 20, ..., 30).
5. Kontynuujemy do √30 ≈ 5.5. Liczby, które nie zostały skreślone to liczby pierwsze: **2, 3, 5, 7, 11, 13, 17, 19, 23, 29**.







