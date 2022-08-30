https://developer.mozilla.org/pl/docs/Learn/CSS/CSS_layout/Flexbox

---
[[Flexbox Model Blokowy]]



---

# Intro
#css/layout    #flexbox

==FLEXBOX== to jednowymiarowa metoda rozmieszczania elementów w wierszach lub kolumnach, elementy rozciągają się, aby wypełnić dodatkową przestrzeń lub kurczą się, aby dopasowaś się do mniejszych przestrzeni


1. Chcemy zmienić położenie elementu, więc na rodzicu tego elementu ustawiamy `display: flex;`
```html
<section>
	<article> ...
	<article> ...
	<article> ...
</section>
```
więc w CSS tworzymy `section` jako elastyczny kontener, w którym będą trzy `article`
```css
section {
	display:flex;
}
```
(jeżeli chciałbym, aby liniowe elementy były jakby blockowe to `display: inline-flex` [[display css]])

Trzy `article` będą w trzech jednakowych kolumnach.



## Zwijanie elementów potomnych
Jeżeli z jakiś powodów elementy potomne "wylewają się" poza rodzica, to możemy to naprawić dodając do rodzica regułę CSS:
	`flex-wrap: wrap;`

## Połączenie `flex-diretion` z `flex-wrap`

`flex-flow: <flex-direction value> <flex-wrap value>`
`flex-flow: row wrap`

---

## Ustawianie wymiarów elementów `flex`
```css
article{
	flex: 1;
}
```
czyli każdy `article` będzie wzdłuż osi głownej (`main axis`) zajmował procentową wartość 1, czyli każdy tyle samo
ale dodanie tego kodu
```css
article:nth-of-type(3) {
  flex: 2;
}
/*
:nth-of-type(indeks) pseudoklasa 
pozwala wybrać element z listy
w/w wybierze trzeci z kolei article
*/
```
sprawi, że trzeci element `article` zajmuje dwa razy więcej niż pozostałe (mamy trzy `article` więc pierwsze dwa zajmują po jednej czwartej (razem 1/2) a trzeci zajmuje pozostałą częśc, czyli 1/2)

można dodać drugą wartość do `flex`
```css
article{
  flex:1 200px;
}

article:nth-of-type(3) {
  flex: 2 200px;
}
```
każdy element `article` ma 200px dostępnej przestrzeni, a następnie przeglądarka dzieli przestrzeń według wartości procentowej (trzeci `article` ma dwa razy więcej przestrzeni niż pozostałe `article`)

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  <header>
    <h1> FLEXBOX</h1>
  </header>
  
  <section>
   
    <article>
          <h2> First article </h2>
          <p> lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed libera lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed liberas
            </p>
    </article>
    
    <article>
    <h2> Second article </h2>
 <p>lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed libera lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed liberas
            </p>
    </article>
    
    
    <article>
    <h2> Third article </h2>
 <p> lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed libera lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed liberas   </p>
    </article>
  <!--
    <article>
    <h2> n article </h2>
 <p> lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed libera lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed liberas
            </p>
    </article>
    <article>
    <h2> n article </h2>
 <p> llorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed libera lorem ipsum et ides quit ali sed liberas lorem ipsum et ides quit ali sed liberas    </p>
    </article>
  
    -->
    
    </section>
</body>
</html>
```


```css
header {
   background: purple;
   height: 100px;
}
article {
  padding: 10px;
  margin: 10px;
  background: aqua;
}

h1 {
/*text-align wyrównywanie tekstu w poziomie
wartości: 
  left
  right
  center
  justify każda linia ma jednakową szerokość
*/
  
/*line-height odstęp między wierszami
wartości:
  - normal
  - length px, pt, cm
  - % procentowa wielkość odstępu (względem aktualnej wielkości czcionki)
  */
        text-align: center;
        color: white;
        line-height: 100px;
        margin: 0;
      }

section{
  display: flex;
  /*
  flex-direction: row;
  flex-wrap: wrap;
  */
  flex-flow: row wrap;
  
}

article{
  flex:1 200px;
}

article:nth-of-type(3) {
  flex: 2 200px;
}
```

---
## Horyznontalne i wertykalne wyrównywanie

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  <body>
    <div>
      <button>Smile</button>
      <button>Laugh</button>
      <button>Wink</button>
      <button>Shrug</button>
      <button>Blush</button>
    </div>
  </body>
</html>
</html>
```

```css
html {
 font-family: sans-serif;
}

body {
/*
width definuje szerokość elementu
      wartość w %, czyli jaki procent
      całości zajmuje dany element

max-width definuje maksymalną szerokość elementu
  
*/
   width: 70%;
   max-width: 960px;
   margin: 20px auto;
}

button {
  font-size: 18px;
  line-height: 1.5;
  width: 15%;
}

div {
/*
wysokość każdego elementu div
zostaje określona na 100 pikseli
a granica tego elemenu ma mieć grubość jednego piksela
  być koloru czarnego 
  być linią

*/
height: 100px;
border: 1px solid black;
}



/* div jako flex container */
div {
  display: flex;
  align-items: center;
  justify-content: space-around;
  
/*
align-items odpowiada za ułożenie flex items względem cross axis
            stretch domyślna wartości (elestyczny)(wypełnij flex container w kierunku cross axis)
            center elementy będa maksymalnie w środku cross axis  
            flex-start "przyczepia" do góry
            flex-end   "przyczepia" do dołu
*/

/*
justify-content  odpowiada za ułożenie flex items względem main axis
jego wartości:
  flex-start to wartość domyślna, element ustawiane do main start (lewo)
  flex-end ustaw elementy do main end (prawo)
  center centruj elementy
  space-around rozmiesza elementy równo wzdłuż main axis z wolnym miejscem po obu jej końcach
  space-between jak space-around tylko nie zostawia wolnego miejsca
  
*/
}


/* 
button:nth-of-type(2) {
nadpisujemy własność align-items przez użycie align-self
  zmieniamy położenie tego oto elementu względem cross axis (góra dół)
  wartości: stretch, center, start, end
 
 można użyć innych pseudo klas:
  :last-child wybiera ostatni element
  :nth-of-type(index) wybiera element z danej grupy o określonym indeksie
                      bp. :nth-of-type(2) wybierze drugi element
 
  align-self: start;
}
   
  */
```

## Uporządkowanie flex items
Możemy zmieniać kolejność flex items
```css
 button:first-child{
	 order:1
 }
```
spowoduje, że nasz przycisk "Smile" będzie ostatni, a nie pierwszy, czyli zostanie przemieszczony wzdłuż main axis.
- `0` to wartość domyślna
- `im większa liczba` elementu tym ów element pojawia się później (jest przesunięty w prawo)
- `te same liczby` mają elementy, to pojawią się w porządku wynikającym z pierwotnego kodu
`order: -1` element z tak ustawioną własnością pojawi się wcześniej niż element z ustawioną wartości `0`


## zagnieżdżone flex boxes
*flex item* może być *flex container*

Przykładowa struktura html
```
section - article
          article
          article - div - button
                    div   button
                    div   button
                          button
                          button
```

CSS:
```css
section{
	display: flex;
}
```
czyli `section` staje się *flex container*

```css
article:nth-of-type(3) {
  flex: 3 200px;
  display: flex;
  flex-flow: column;
}
```
trzeci `article` staje się *flex container*

```css
article:nth-of-type(3) div:first-child {
  flex: 1 100px;
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  justify-content: space-around;
}
```
wybieramy pierwszego `div`, który jest *flex item* trzeciego elementu `article`







