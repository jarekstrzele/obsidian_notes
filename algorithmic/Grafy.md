#grafy


# Grafy

>[!info] Graf (*graph*)
>struktura danych składająca się z 
>	- niepustego zbioru wierzchołków
>	- zbioru połączeń między nimi (krawędzie)

==sąsiadujące wierzchołki grafu== to wierzchołki połączone krawędzią


> [!quotes] 
> ==Graf prosty==  $G = (V, E)$ defniujemy jako:
> uporządkowaną parę skªładającą się z :
> 	- niepustego skończonego zbioru wierzchoªków $V$ , oraz ze 
> 	- skończonego zbioru krawędzi $E$ (par wierzchołków) łączących te wierzchołki. Na rysunkach wierzchołki, inaczej nazywane węzłami, oznaczamy jako kółka z zapisaną w środku unikalną etykietą identyfikuącą wierzchołek, natomiast krawędzie jako proste odcinki pomiędzy nimi.


>[!note] graf prosty
>graf, w którym dwa wierzchołki mogą łączyć conajwyżej jedna krawędź oraz z żadnego wierzchołka nie prowadzi krawędź do niego samego

==waga== wartość przypisana krawędzi grafu

>[!note] graf ważony
>graf, którego krawędzie mają wagi

>[!note] graf nieskierowany
>graf, w którym przejście wzdłuż krawędzi jest możliwe w obu kierunkach
>> [!quote] 
>> Graf nieskierowany (ang. *undirected graph*) to graf prosty, w którym zbiór krawędzi $E$ jest zbiorem nieuporządkowanych par wierzchołków. Oznacza to, że krawędź łączy dwa  różne  wierzchołki , a zbiory ${u, v}$ oraz ${v, u}$ gdzie $u, v∈V$ i $u != v$ oznaczają te same krawędzie.







>[!note] graf skierowany
>graf, w którym po krawędzi można przejść w określonym kierunku

>[!note] graf spójny
>graf, w którym istnieje droga z każdego wierzchołka do każdego

## Reprezentacja grafu

### macierz sąsiedztwa
złożoność pamięciowa i złożoność czasowa to $O(n^2)$
Do przechowywania informacji o grafie można wykorzystać tablicę dwuwymiarową $n x n$ ($n$ to liczba wierzchołków grafu).

`(i,j)` - ten element tablicy informuje, czy istnieje krawędź od wierzhołka  `i` do wierzchołka `j`

dla grafow nieważonych informacja o istnieniu krawędzi to `boolean`: `1, 0`, `true, false`

Grafy nieskierowane: `(i,j)` = `(j,i)`
Wartość w tablicy może reprezentuje wagę w grafach ważonych

### listy sąsiedztwa
Dla każdego wierzchołka pamięta się listę sąsiadujących z nim wierzchołków (połączonych krawędzią z tym wierzchołkiem).

Jeżeli graf **nie jest ważony**, elementami danej listy będą numery sąsiednich wierzchołków:
- 0 -> 1 2 3
- 1 -> 0 2 
- 2 -> 0
- 

Jeżeli graf jest ważony, dla każdego wierzchołka należy pamiętać dwie wartości:
	- numer sąsiedniego wierzchołka
	- waga krawędzi, która do niego prowadzi
- 0 -> (1,3) (3,3) (zerowy łączy się z jedynką wagą 3)
- 1 -> (2,4) (jedynka łączy się z dwójką wagą 4)
- ...
Implementacja:
- każdy element listy jest wierzchołkiem grafu nieskierowanego
- każdy element to lista wierzchołków, z którymi ten wierzchołek/element jest połączony













