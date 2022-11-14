D O M  
[[11 - Event]]
ściągnil plugin DOM inspector  

>**node**  (węzeł)      jakikolwiek byt na stronie (document, head, html , ul ,...  

*document*       najwyższy element  
`document.getElementbyID( node_id)`

`setAttribute("class", "zmienKolor")`

`removeAttribue("class")`

`innerHTML`  cała zawartość HTML obiektu z tagami  

`textContent`      cała zawartość tekstowa  

firstChild
lastChild

----

**QUERYSELECTOR**            wybranie pierwszego napotkanego elementu spełniającego warunek  

**QUERYSELECTORALL()**      wybieranie wszystkicjh elementów spełniających warunek

```js
var kursyProgramowania = document.getElementById("kursyProgramowania").getElementsByTagname("li"); //zwraca tablicę  

alert(kursyprogramowania[0].innerHTML);  

// z query..  
var kursyProgramowaia = document.querySelector("#kursyProgramowania li"); //nie zwraca tablicy, ale pierwszy element  

alert(kursyprogramowania.innerHTML);  

var kursyProgramowaia = document.querySelectorAll("#kursyProgramowania li");  
alert(kursyprogramowania[0].innerHTML);  
   
document.querySelectorAll("li"); // wybiera wszystkie elementy 'li' na stronie  

document.querySelector("#kursyTworzenieStronWWW li");  

document.querySelector("#kursyTworzenieStronWWW li:nth-child(2)"); // tak jakby [2] przy All

```


*S T Y L E*  
```js
var kursyprog = document.querySelectorAll("#kursyProg li");                              kursyprog[0].**style.color** = "red";                                        

```


*T W O R Z E N I E   E L E M E N T Ó W*  
```js
var x = document.createElement("p");                  
x.style.color ="red";
x.className = "tess"; 
x.innerHTML ="new text";     

var body = document.querySelector("body");               
body.appendChild(x)   
```

*U S U W A N I E*  
```js
parent.removeChild("ee")  
```
Powinieneś uważać, gdy korzystasz z innerHTML, ponieważ właściwość ta zreparsuje wszystko, co było wewnątrz danego elementu -> co sprawi, że zmienne, które wskazywały na elementy tam się znajdujące, przestaną robić to poprawnie. Jeśli chcesz zachować referencje to powinieneś korzystać z createElement.

---
DHTML - dynamic html  
```html
<html>  
<head>  
     <title>Events</title>  
     <script src="script.js" async></script>  
<head>  

<body>  

 <!--<div onmouseover="wypiszTekst('asaf')"> To jest nowy tekst o niczym </div> -->  
<div id="test"> To jest nowy tekst o niczym </div>                                                                       
  function wypiszTest(tekst){  
         alert(tekst + " !!!!!!!!!!!!!");  
 }  

var test = document.getElementById("test");  
test.onclick = function(){  
	wypiszTest("to jest tekst z mojej funckj");                                         };  

</body>  

jeżeli miałbym wywołać funkcję, bez argumentów to wystarczy:  

test.onclick = nazwa_funkcji;  

gdybym jednak napisał  

test.onclick = nazwa_funkcji(); // to odrazu wywołabym tę funkcję
```






