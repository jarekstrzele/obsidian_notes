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


