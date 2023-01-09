
[[DOM and Events]]
[[11 - Event]]


---

# WPROWADZENIE

Arkadiusz Włodarczyk  

skróty:  
TAB                  wcięcie  
shift+TAB      cofnięcie wcięcia  
shift+end / home       zaznaczenie całej linni do końca/ początki  
shift+strzałka góra dół      zaznaczenie całej linii  
shift+shift+strzałka góra dół      skopiowanie  całej linii  
ctr+home /end            przeskoczenie do początku/ końca pliku  

---
# section 3: PODSTAWY  
**najbardzej optuymalne umieszczenie skryptu na stronie**  
```html
<script>  
      alert("test")  
</script>  
```
ten skrypt może być: w head, body, może być wczytywany z pliku (`<script src="js/script.js">`) albo z innego serwera  

**html**:  
-   przeglądarka pobiera `index.html`,  
-   parser (to, co przetwarza) przegląda tagi, spotyka `<script>` , więc musi go wykonać,  
-   jeżeli skrypt w head to jest odrazu wykonywany,      
-   jeżeli skrypt w body, to najpierw wczytywana jest strona, potem wykonywany skrypt      
-   jeżeli będzie problem z wczytaniem skryptu, to zwsze jakoś to się odbije na wyświetlanej stronie  
-   HTML 5 ma dodatkowy atrybyt ==asynchroniczności==:  
-   `<script src="js.script" async></script> ` 
    
problem:
	jeżeli jest kilka skryptów to drugi w kolejności może być wczytany przed pierwszym, dlatego ==bezpieczniej jest używać== 
    
    <script src="js.script" defer></script>  
    

## podstawy javascript

czytanie pliku od góry do dołu  
białe znaki nie są insterpretowane  
;       -       koniec instrukcji  
/*  
komentarz   * /  
// komentarz  

zmienna            
`var x;` deklaracja  
`x=2;`    inicjalizacja  

*typy*: number, string, true/false, tablice, null, undefined,   

`===`     identyczność wartości         `3 ==="3"   false  `
`==`       równość wartości                 `3 == "3" true  `

&&             koniunkcja  
||            alternatywa  

```js
if (warunke)  
     instrukcja;  
else if (warunek)  
    instrulacja;  
else
	instrukcja;  
```

```js
(wyrażenie) ? zwrócona_gdy_1 : zwrócona_gdy_0
var x = 6;  
var czyParzysta =  (x % 2 === 0) ? true : false;  
```

 ---
 
## funkcja
```js
function f_name(args) {  
            // body  
            return; // przerywa działanie funkcji  
}  

f_name()
```

---

## zasięg zmiennych 
*globalny*
- globalny (zawsze i z każdego miejsca) (np. mogę wywołać funkcję, która została zdefiniowana dalej w pliku)  
```js
var a=5;  
function test() { alert(a)  } // ok,  5  
function test() { a=2; alert(a)  }  // ok, 2  
```


*lokalny*
`function test(a){a=2;  alert(a)}  // ok,    2  `
 
*funkcje anonimowe*
```js
var x = function test() {} ; // to test jest funkcją o zasięgu lokalnym  

// x ma zasięg globalny  
var x = function() {} ;  

// funkcja STRZAŁKOWA
var y = (arg) => {

	let p = "100";
	arg = String(arg);
	console.log(arg + p)
}
```
    
---


## O B I E K T Y  
> **obiekt**      to pojemnik do przechowywania zmiennych i funkcji tematycznie ze sobą związanych do dalszego łatwiejszego ponownego użycia  

```js
{ key1: value, key2: value}  

var osoba = {  
      imie:"Jan" ,  
      toString: function () {                        //toString - stringowa reprezentacja obiektu  

            return this.imie  
      }  
} ;     
```
  

forma do tworzenia obiektów:  

> **klasa**      forma do wytwarzania obiektów. Ta forma służy do zebrania obiektów w jedną "klasę"  
> 
>   Daje możliwość stworzenie z tej formy wielu nowych różniących się minimalnie od siebie obiektów ale będących dalej do siebie podobnnymch cechami i metodami.  

  ```js
function osoba (imie, nazwisko){  
      this.imie = imie;  
      this.nazwisko = nazwisko;  
      this.toString = function () {                // toString - stringowa reprezentacja obiektu  

            return this.imie  
      }   
}  

var xx = new osoba("Arek", "Włodarczyk")  
```

**P R O T O T Y P**
#javascript/prototype

Mam obiekt obj. Chcę dodac mu nową właściwość:  

`obj.nowaWłaściwość = 12` -> to dodaje nową właściwość do tego konkretnego obiektu  

Wszystkie klasy wzorują się na `Object`.  

Gdy mamy już zdefiniowaną funkcję konstruującą _osoba_  możemy zmieniać właściwości wszystkich jej obiektów przez _prototype_  

`osoba.prototype.nowaWłaściwość = 12`
dodaje tę właściwość do wszystkich o obj stworzonych na  funkcji osoba  

---
---


# SECTION 8  A R R A Y
#javascript/array

`var produkty = [ "PHO", "Mysql", "JS"] ` 

tablica to obiekt  
`produkty.length`  
`produkty.push(elem)` elem dodany na koniec tablicy  

**ASSOCIATIVE ARRAYS**  
```js
var osoba = [];
osoba["imie"] = "Arek";
alert(osoba["imie"])  === alert(osoba.imie)  
var ul = document.getElementById("kursyTworzeniaStronWWW");  
var liArray = ul.getElementsByTagName("li");  
alert(liArray[2].innerHTML)// -> "JS"  
```

gdy chcę wypisać zawartość tablicy, wystarczy  napisać nazwę tablicy, a metoda _toString()_ sprawi, że będą wyświetlone wszystkie elementy tablicy.   

tablicy  `toString()`  i `valueOf()`    dają te same efekty  

`tab1.concat(tabl2)` -> zwraca NOWĄ tablicę będąco połączeniem tab1 i tab2  

`tab1.join("---x---")` ->      zwraca NOWĄ tablicę, której elementy są oddzielone "----x----"   

przy wyświetlaniu tablicy można `join("<br>")` i mamy elementy w nowych liniach  

`tab1.pop()` -> zwraca ostatni element tablicy i usuwa ten element z tablicy  
`tab1.shift()` -> zwraca pierwszy element tablicy i usuwa ten element z tablicy  

`tab1.push(elem)` -> popycha elem na **koniec** tablicy i zwraca długość tablicy  
`tab1.unshift(elem)` -> dodaje elem na początek listy i istniejące elementy przesuwa o 1  

`tab1.sort()`  roznąco zmienia oryginalną `[]`  nie sortuje liczb!!!  
`tab1.sort().reverse()` malejąco zmienia oryginalną `[]`
```js
tab1.sort(function(a, b) {return a-b} 
// rosnąco sortuje tablicę **liczb**  

tab1.sort(function(a, b) {return b-a}
//malejąco sortuje tablicę **liczb**  

tab1.slice(index1, index2)
// niezmienia oryginalnej tablicy index1 nie jest uwzględniony, index2 jest uwzględniony)  

tab1.splice(odKtórego, ileElementów, coDokleić)    //zmienia oryginalną tablicę odKtórego indeksu i ile elementów (, doklejać, lepić)  
```
  
---

## P Ę T L A  
#javascript/for_in   
`for in` szybko przechodzi przez obiekty (tablice też)  
```js
for (var property in person)  
{  
     alert(property)
//nazwy własności np.imie  

alert(person[property]
// wartości własności np. Arek  
}  
  ```

---


## O B I E K T   A R G U M E N T S  

Nie znamy ilości przesyłanych argumentów.  
Każda funkcja ma wbudowana własności: `arguments`  
```js 
function foo(){ 
      alert(arguments.length)
// arguments - jak lista -> arguments[i]
}
foo(1,2,3) -> 3
foo(1,2,3,1,2,3) -> 6  

typeof(arg) -> zwraca typ arg  

```
