# Podstawowe informacje z Pythona
 

`import math` importuje moduł umożliwiający rozszerzone działania matematyczne

`print(f"2 + 2 = {2+2}")` **f-string** pozwala na umieszczanie wyrażeń
wewnątrz string (wyrażenie - to, co zwraca pewną wartość)
`print(f"Pierwiastek liczby pi to {math.sqrt(math.pi):.4f}")`
`23//12` dzielenie typu `int`, `23/12` dzielenie `typu float`

`input("Pewna treść")` funkcja wczytująca dane od użytkownika

## Zadanie 1
napisz program, króry wczytuje od użytkownika dane (imie użytkownika, promień koła),
a zwraca informacje o polu i obwodzie koła z dokładnością do piątgego miejsca po przecinku
  
-----------------------
# Liczby pseudolosowe

`import random` importowanie moduły random
`random.randint(1,100)` losowy wybór liczby całkowitej z przedziały od 1 do 100
`random.random()` losowa liczba z przedziału 0 1
`random.choice(<iterator>)` losowy wybór jednego elementu z iteratora (np. z listy)

##  Zadanie 2
Napisz program, który będzie symulował losowanie dużego lotka.
Pierwsza wersja: losowy wybór 6 cyfr z 49 i wyświetlenie ich na monitorze.
Druga wersja: użytkownik podaje 6 liczb, komputer losuje 6 z 49 i informuje użytkownika o tym, jakie liczby zostały wylosowane i jaki wynik uzyskał użytkownik


-------------

# Instrukcje warunkowe

```python
if warunek:
kod
elif warunek:
kod
else:
kod
```


#### ternary operator
`<wartość_zwracana_gdy_prawda> if warunek else <wartość_zwracana_gdy_fałsz>'


```python
a = True
"wszystko ok" if a else "jest źle"
```

## ZADANIE 3
Napisz program, który oblicza pierwiastki równania kwadratowego $ax^2+bx+c=0$.
Użytkownik wprowadza wartości dla $a$, $b$, $c$.


------------------------------------------

##  Zadanie 4

Napisz program, który za pomocą instrukcji `for`:
- znajduje największą i najmniejszą liczbę ze zbioru $n$ wylosowanych liczb całkowitych,
generowanych losowo, w przedziale od 0 do 100 (niech $n = 5$) oraz
- oblicza wartość średnią ze wszystkich wylosowanych liczb.


------------------

# Metoda Monte Carlo
Używamy jej, gdy próbujemy modelować bardzo złożone procesy.
Ogólna idea:
- losowo generujemy wielkości charakteryzyjące pewne zjawisko (w uproszczeniu: im więcej takich wielkości, tym dokłdniejszyw wynik, choć ogranicznikiem jest silnik losujący liczby losowe)
- losowanie jest przeprowadzana zgodnie ze znamy dla danego procesu rozkładem

## ZADANIE 5

Obliczanie Pi:
1. Wpisz koło o promieniu $r$ w kwadrat o boku $2r$.
2. Losowo wygeneruj punkty i umieść je w kwadracie.
3. Wyznacz liczbę punktów, które znajdują się jednocześnie w kwadracie i w kole.
(spełniają nierówność $x^2+y^2<=r$)
4. Niech promień $r$ będzie wyznaczony przez stosunek liczby punktów znajdujących się
w kole do liczby punktów znajdujących się w kwadracie.
5. $?$ ~ $4.0r$.
)

-------------------------

Znajdź liczby pierwsze z przedziału od 2 do 200.
Funcja `all()` zwraca wartość `True`, gdy wysztkie elementy iterowalne są prawdziwe. W przeciwnym wypadku `False`.

``` python

a = [1, 2, 'tak', True]
all(a) # -> True

b = [1, 2, 'tak', '']
all(a) # -> False


```

## ZADANIE 6
Znajdź liczby pierwsze z przedziału od 2 do 200.

--------------------

# Funkcje
```python
def nazwafunkcji(args):
	pass
```

## ZADANIE 7

Napisz funkcję signum i wywołaj ją.
Funkcja signum:
- dla liczb rzeczywistych mniejszych od zera zwraca -1
- dla zera zwraca 0
- dla liczb rzeczywistych większych od zera zwraca 1


# Rekurencja

1. Funkcja, która wywołuje samą siebie.
2. Jeżeli chcesz zrozumieć funkcje rekurencyjne, przeczytaj punkt 2.

## ZADANIE 8

Napisz funkcję rekurencyjną, która wydrukuje $n$ razy napis "Jestem funkcją rekurencyhną". Wartość $n$ jest przekazywana do funkcji jako argument.

## ZADANIE 9
Napisz funkcję rekurencyjną obliczającą silnię liczby $n$.
$3! = 1*2*3$, $5! = 1*2*3*4*5$ 
$0!=1$ 
$1!=1$
# Funkcja anonimowa
`lambda ar1, ar2, ... : wartość zwracana`

Funkcje lambda można przypisać do zmiennej:
`a=lambda x: x*100`
`a(10)` wywołanie funkcji

funkcje lambda można bezpośrednio wywoływać
`(lambda y, z : y + z)(22, 11)`
  

## ZADANIE 10

- utwórz trzy dowolne funkcje lambda i przypisz je do różnych zmiennych
- wywołaj funkcje lambda używając przypisanych im zmiennych