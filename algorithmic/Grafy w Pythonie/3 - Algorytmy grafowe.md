[[_ 0 Grafy w Pythonie]]
'
# Graf skierowany z wagami - Dijkstra
(diejkstra)
#dijkstra

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










