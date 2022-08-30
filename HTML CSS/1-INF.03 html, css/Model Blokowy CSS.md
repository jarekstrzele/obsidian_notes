		[[_ CSS]]
[[Elementy składowe strony WWW]]

---
# Model blokowy
Każdy element w języku HTML może być uznany za "prostokątne pudełko":
- ma margines
- ma obramowanie,
- ma wtypełnienie
- ma zawartość


![[Model blokowy css.excalidraw|700]]

- __margin__ marginses wokół ramki (margines zew.)
- __border__ obramowanie wokół zawartości elementu
- __padding__ odstęp między obramowanie i zawartością (margines wew.)
- __content__ zawarość elementu


## BORDER

### szerokość obramowania
`selector{border-width: wartość;}`
- _1 wartość_ - jednakowa szerokość dla wszystkich krawędzi
- _2 wartości_ - taka sama szerokość dla krawdędzi poziomych i taka sama szerokość dla krawędzi pionowych
- _3 wartości_ - krawędź górna, dwie krawędzie  pionowe, krawędź dolna
- _4 wartości_ - krawędź (górna, prawa, dona, lewa)

__wartość__:
- _thin_ cienkie obramowanie
- _medium_ średnie obramowanie
- _thick_ grube obramowanie

lub dowolne jednostki

__definiowanie pojedynczej krawędzi__:
`selector {border-top-width: szerość}`
`selector {border-bottom-width: szerość}`
`selector {border-left-width: szerość}`
`selector {border-right-width: szerość}`

```css
h1 {border-width: 2px;}
p {border-bottom-width: 11px;}
nav{border-width: medium;}
```

### styl obramowania
`selector {border-style: wartość;}`

- _1 wartość_ - jednakowy styl dla wszystkich krawędzi
- _2 wartości_ - taki sam styl dla krawdędzi poziomych i taka sama szerokość dla krawędzi pionowych
- _3 wartości_ - krawędź górna, dwie krawędzie  pionowe, krawędź dolna
- _4 wartości_ - krawędź (górna, prawa, dona, lewa)

definiowanie pojedynczej krawędzi:
`selector {border-top-style: styl;}`
`selector {border-bottom-style: styl;}`
`selector {border-left-style: styl;}`
`selector {border-right-style: styl;}`

__wartość stylu__
- `none` brak obramowania
- `hidden` ukryte
- `dotted` linia kropkowana
- `dashed` linia kreskowana
- `solid` linia ciągła
- `double` linia ciągła podwójna
- `groove` rowek
- `ridge` grzbiet
- `inset` ramka, okienko
- `outset` przycisk 


>Obowiązkowo podawaj wartość dla stylu i szerokości


### kolor obramowania
`selector{border-color: kolor;}`

[[Color html]]

__wartość kolor__
- nazwa (orange)
- heksadecymalnie (#ff00ff)
- rgb(r,g,b)

oddzielne kolorowanie krawędzi
`border-top-color`
`border-bottom-color`
`border-left-color`
`border-right-color`


### jednoczesne definiowanie atrybutów
`selector{border: width style color;}`

```css
p {border: double 1px red;}
h2 {border: 20px  outset blue;}

```

---
## Marginesy zew.
oddzielanie elementu od innych elementów
`selektor { margin-top: rozmiar; }`
`selektor { margin-bottom: rozmiar; }`
`selektor { margin-left: rozmiar; }`
`selektor { margin-right: rozmiar; }`
_rozmiar_ liczba w _px_, _cm_, ...
np. `p {margin-bottom: 1cm;}`

### ustawianie marginesów dla wszytkich boków
`selektor {margin: wartość}` jednakowe 4 boki
`selektor {margin: w1, w2}` górny/dolny oraz lewy/prawy
`w1,w2,w3}` górny, lewy/prawy, dolny
`w1,w2,w3,w4}` górny, prawy, dolny, lewy

np. `h3 {margin: 1cm, 2cm, 5px;}`





