[[_ CSS]]

![[drzewo elementów HTML.excalidraw_0 | 700]]

---
# Selektory
==selektor== to dowolny element HTML, dla którego definiujemy parametry formatowania

Ze względu na to, w jaki sposób odwołujemy się w definicji do reguł formatowania, wyróżniamy:
- selektor elementów,
- selektor atrybutów,
- selektor  speccjalny,
- selektor  pseudoklasy,
- selektor pseudoelemetu

## Selektory elementu
Wybranie elementu na podstawie jego nazwy.

składnia `selektor {właściwość: wartość;}`

### selektor typu elementu
`p {color: blue; font-size: 15px;}`
`h2 {background-color: green;}`

### selektor uniwersalny
ogólny
`* {właściwość: wartość;}`
`*{font-family: courier new; color:green}`


### selektor potomka
Formatowanie elementów, które są wewnątrz innego znacznika
`selektor selektor {właściwość: wartość;}`

`div span {font-size: 13pt; color:red;}` ,czyli sformatuje znacznik `span` zawarty w znaczniku `div`
ten CSS zadziała nawet, gdy `span` znajduje się w innym znaczniku, który znajduje się w innym znaczniku, który znajduje się w `div`

### selektor dziecka
działa jak selektor potomka, tyle że element formatowany musi znajdować się bezpośrednio w znaczniku nadrzędnym

`rodzic > dziecko {właściowść: wartość;}`

`div > p {background-color: blue;}` znacznik `p` musi wystąpić bezpośrednio w `div`
```html
<div>
  ...
  <p> coś tam co CSS będzie formatował </p>
  ...
</div>
```


### selektor sąsiadującego brata 
dla elementów  znajdujących się  w tym samym rzędzie herarchii można zdefiniować  selektor  sąsiadującego brata

`brat1 + brat2 {właściwość: wartość;}`

`div + p {font-size: 23px; color: red;}`
```html
<div>
  coś tam
  <p> ten paragraf nie będzie sformatowany </p>
<div>

<p> ten paragraf będzie sformatowany </p>
```

### selektor braci
Elementy znajdują się w tym samym rzędzie hierarchii definiujemy selektor braci, czyli drugi element i pozostałe będzą sformatowane zgodnie z definicją 
`brat1 ~ brat2 {property: value;}`
```css
div ~ p{ font-`size: 33px; color:lightblue;}`
```

```html
<div>
	<p> ten w divie, więc formatowany </p>
	coś tam
	<p> ten w divie też, więc jest formatowany </p> 

</div>

<p> ten nie powinien bć formatowany
```


## Selektory atrybutów
Formatujemy znacznik na podstawie atrybutów, które ma.
`selektor[atrybut="wartość"] {właściwość: wartości;}`

`p[id="xx"] {font-size:14pt;}` paragraf o atrybucie `id`, który ma wartość `xx` będzie miał sformatowane czcionki o wielkości `14pt`


## Selektory specjalne

### selektor klasy
`selektor.nazwa_klasy {właściwość: wartość;}`

`p.tekst1{color:green;}` każdy paragraf, którego atrybut `class` ma wartość `tekst1`
(np. `<p class="tekst1"> ...  </p>`)

### uniwersalny selektor klasy
`.nazwa_klasy{właściowść: wartość;}`
Każdy element, którego klasa ma wartość `nazwa_klasy` zostanie odpowiednio zformatowany

```css
.wielki{font-size: 30pt;}
```

```html
<p class="wielki"> To są duże litery </p>
<p> To jest zwykły tekst </p>
<br>
Ten tekst <span class="wielki"> będzie pisany dużymi literami </span> a ten już nie


```

### selektor identyfikatora
`#identyfikator {właściwość: wartość;}`

```css
#wzmianka{background-color: black; color:white;}
```

```html
<div id="wzmianka"> Jakaś tam wzmianka </div>
```


## pseudoklasy
W języku CSS style są dodawane do elementów lub grup elementów na podstawie ich nazw, atrybutów lub zawartości.

Inny sposób:
> element nabywa styl lub go traci w związku z działaniem użytkownika lub w zależności od umiejscowienia

np. _linki_ zmieniają swój wygląd po najechaniu na nie kursorem

==pseudoklasy== (umożliwiają dynamiczną zmianę stylu):
- `:link` link nieaktywny, nie został przez użytkownika odwiedzony;
- `:visited` link odwiedzony, strona była otwierana;
- `:hover` link gotowy do kliknięcia, kursor myszy ustawiony nad linkiem (może być użyta do innych elementów niż odsyłacze);
- `:active` link odwiedzany, strona jest obecnie wczytana

`a:link {właściwość: wartość;}` formatowanie wszystkich nieodwiedzonych linkó
`a:link {color: green; background: yellow;}`


`a.moja_klasa:link { właściwość: wartość; }` formatowanie niedowiedzonych linków, które należą do klazy `moja_klasa`
`a:moja_klasa:link {color: orange;}`


Analogicznie z pozostałymi pseudoklasami:
`a:visted {color:red;}`
`a.pewna_klasa:hover {color: yellow;}`
`a:active {color: blue;}`

POPRAWNA KOLEJNOŚĆ DEFINIOWANIA pseudoklas:
1. `:link`
2. `:visted`
3. `:hover`
4. `:active`

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  
  <title></title>
  <style>
    #moj_hover:hover{
      color:green;
    }
    
    #moj_link:link{
      color:purple;
    }
    
    #moj_active:active{
      color:Chartreuse;
    }
  
  </style>
</head>
<body>
  <a href="http://donika.pl">To jest link donikąd </a> <br>
  <a id="moj_hover" href="http://donika.pl">To jest link hover green </a> <br>
  <a id="moj_link" href="http://donika.pl">To jest link hover green </a> <br>
  <a id="moj_active" href="http://donika.pl">To jest link hover green </a> <br>

  
</body>
</html>
```











