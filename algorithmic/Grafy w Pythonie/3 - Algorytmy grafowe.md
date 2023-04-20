[[_ 0 Grafy w Pythonie]]
'
# Graf skierowany z wagami - Dijkstra
(diejkstra)
#dijkstra
Graf musi być:
- skierowany
- mieć wagi dodatnie
- bez cykli


stacja kolejowa i koszty przejazdu z jednego węzła do drugiego 

1. utwórz tabelę z
	1. wszystkimi wierzchołkami  - pierwsza kolumna
	2. koszt dotarca do okrelślonego wierzchołka - druga kolumna `c`
	3. poprzednia stacja, na której musimy się znajdować, aby dostać się do danego wierzchoła 0 trzecia kolumna `p`


![[Dijkstra-graf.excalidraw | 600]]

algorytm wyznacza najtańsze połączenia do każdego wierzchołka
rozważamy połączenie od A do E

### Start
  _  | C | P
 --- | ---| ---
 A | 0 | - 
 B | inf | - 
 C | inf | - 
 D | inf | -
 E | inf | -

koszt dotarcia do A = 0, brak rodzica, dla reszty wierzchołków brak danych

### Pierwszy krok
Z A, dokąd mogę się dostać?
  _  | C | P
 --- | ---| ---
 A (przetworzony)| 0 | - 
 B | 2 | A 
 C | inf | - 
 D | 4 | A
 E | inf | -
z A do B koszt 2
z A do D koszt 2

wierzchołek A przetworzony
B i C jeszcze nie przetworzone, a wybieramy z nich ten, który jest najtańszy
, czyli B

### Drugi krok
Z B, dokąd mogę się dostać?
  _  | C | P
 --- | ---| ---
 A (przetworzony)| 0 | - 
 B (przetworzony) | 2 | A 
 C | 3 + 2 | B 
 D | 4 | A
 E | inf | -
do C dostanę się z B po koszcie 3 + 2
z B mogę dostać się też do D 2 + 3, ale to jest więcej niż dane  już wpisane do tabeli, więc nic nie zmieniam

### Trzeci krok
D ma najniższą cenę, a nie został jeszcze przetworzony, więc go wybieram
  _  | C | P
 --- | ---| ---
 A (przetworzony)| 0 | - 
 B (przetworzony) | 2 | A 
 C | 5 | B 
 D (przetworzony) | 4 | A
 E | 4 + 4 | D
koszt dodarcia do C z D to 4 + 3, a to więcej niż aktualna cena z tabeli, więc zostawiam
z D dotrzemy do E po koszcie 8 ( 4 z A do D plus 4 z D do e)

### Czwarty krok
wybieramy C, bo jest tańsze od E
  _  | C | P
 --- | ---| ---
 A (przetworzony)| 0 | - 
 B (przetworzony) | 2 | A 
 C (przetworzony) | 5 | B 
 D (przetworzony) | 4 | A
 E (przetworzony)| 7 | C
taniej jest dostać się do E z C a nie z D, więc aktualizujemy  tabelę

E jest z automotu przetworzony, bo nie ma już dalej

```python
graf = {
    'A': {'B':2, 'D': 4},
    'B': {'C':3, 'D': 3},
    'C': {'E':2},
    'D': {'C':3, 'E': 4},
    'E': {},
}

#

print("start")
def ustal_najtanszy_wezel(slownik_kosztow, lista_przetworzonych):
    print(f"W funckji ustal_najtanszy_wesel {slownik_kosztow = },  {lista_przetworzonych}")

    najtanszy_koszt = float('inf')
    najtanszy_klucz = None # najtanszy znaleziony wierzocholek

    print(f"{najtanszy_koszt = }, {najtanszy_klucz = }")

    for nazwa, koszt in slownik_kosztow.items():
        if nazwa not in lista_przetworzonych and koszt < najtanszy_koszt:
            najtanszy_koszt = koszt
            najtanszy_klucz = nazwa
            print(f"{najtanszy_klucz = }, {najtanszy_koszt = }")

    return najtanszy_klucz
  

# pythonowe przygotowanie struktur i danych
koszt = {}
rodzic = {}

for name in graf.keys():
    koszt[name] = float('inf')
print(f"{koszt =}")

wierzcholki_przetworzone = []
aktualny_wezel = 'A'
koszt[aktualny_wezel] = 0
rodzic[aktualny_wezel] = None
  

while aktualny_wezel:

    # koszt dotarcia do najbliżych sąsiadów aktualnego węzła
    for sasiad in graf[aktualny_wezel]:
        print(f"while, for {sasiad} in {graf[aktualny_wezel]}")
        # jeżeli udało się znaleźć tańszą drogę:
        if koszt[sasiad] > koszt[aktualny_wezel] + graf[aktualny_wezel][sasiad]:
            print(f"if {koszt[sasiad] = } > {koszt[aktualny_wezel] = } + {graf[aktualny_wezel][sasiad] = }")
            # aktualizacja kosztów
            koszt[sasiad] = koszt[aktualny_wezel] + graf[aktualny_wezel][sasiad]
            rodzic[sasiad] = aktualny_wezel    
            print(f"po aktualizacji {koszt[sasiad] = } ")
            print(f"po aktualizacji {rodzic[sasiad] = } ")
        print(f"wyjście z for {aktualny_wezel} ")

    wierzcholki_przetworzone.append(aktualny_wezel)  
    print(f"{wierzcholki_przetworzone = }")
    aktualny_wezel=ustal_najtanszy_wezel(koszt, wierzcholki_przetworzone)  


print("środek")
for d,c in koszt.items():
    print(f"The cost for {d} is {c}")

for d,c in koszt.items():
     print(f"The cost for {d} is {c}")

     curr_d = d
     while rodzic[curr_d]:
         print(curr_d)
         curr_d = rodzic[curr_d]
     else:
         print(curr_d)
print("Koniec")
```
