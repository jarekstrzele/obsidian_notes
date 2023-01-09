[[0-Wstęp Bazy danych (tech)]]

---


[[język HTML 5]]
[[FullStack/Python Django FullStack/CSS]]
[[Grafika na stronie internetowej]]
[[Grficzny projekt strony]]
[[]Animacja na stronie internetowej]]
[[Dźwięk i wideo]]
[[CMS]]
[[Testowanie i publikowanie strony]]




# WSTĘP
![Program przeglądarkowy jsbin](https://jsbin.com/)

**HTML**          - strukura strony
	- plik tekstowy
	- dynamiczne odnośniki
	- obiekty różnego typu
	- plik html jest interpretowany przez przeglądarkę (niezależnośc stron od systemu)
**CSS**             - wygląd strony
**JavaScript**  - zachowanie strony


## Pojęcia
**strona internetowa** 
dokument HTML (XHTML) zapisany w pliku i umieszczony na serwerze, odczytywany przez przeglądarkę na komputerze użytkownaika

**witryna internetowa**
zbiór stron internetowych powiązanych tematycznie i umieszczonych na jednym serwerze

**serwer internetowy**
- _komputer_ podłączony do internetu i świadczący różne usługi
- _oprogramowanie_ uruchamiane na tym komputerze (serwer FTP, DNS, HTTP)

**statyczna strona internetowa**
jej zawartość i wygląd nie zmieniają się, gdy plik jest wywoływany

**dynamiczna strona internetowa**
- generwowane na bieżąco przez serwer HTTP na podstawie zmiennyh i parameterów przekazanych przez przeglądarkę internetową
- jej zawartość i wygąd zmieniają się w zależności od interakcji z użytkownikiem
- zmiany:
	- client-side (JavaScript) zmiany po stronie użytkownika
	- server-side (PHP, Java, Python) strona jest kompilowana na serwarze


## Język HTML (HyperText Markup Language)
_wersja 5_
#html 
**znacznik**  
- polecenie w  `< >`  (`<body>`) informujące przeglądare  o strukurze strony i jej wyglądzie
- `<p>` znacznik otwierający,   `</p>` znacznik zamykający
- bez znaczników zamykających:
	- `<br>` łamanie wiersza `<br />`
	- `<hr>` linia poziomoa `<hr />`
	- `<img>` wstawianie obrazka `<img />`
- mają _atrybuty_ , które definiją działanie znacznika
	- `<znacznik atrybut="wartość"> treść </znacznik>`
	- `<img src="Obrazek.jpg"` (wielkość liter ma znaczenie)

`<!DOCTYPE html>` - deklaracja, że dokument jest HTML 5


## XML (Extensible Markup Language)
#xml
XML 1.0 określa testowy format do opisu danych (podobny składniowo dk HTML)

```xml
<nazwa_znacznika atrybut="wartość_atrybutu"> treść znacznika </nazwa_znacznika>

```

#XHTML (Extensible HyperText Markup Language)
dostosowuje zasady języka HTML 4 do XML
(np. nazwy znaczników i atrybutów pisane małymi literami, a wartości atrybutów ujęte w cudzysłowia)
(wychodzi z użycia)

# HTML5
#html5
 to rozwinięcie HTML4 i XHTML
 ważna nowości->  obsługa wideo i dźwieku
 **Deklaracja:**
 `<!DOCTYPE html>`
 
 **kodowanie znaków:**
 `<meta charset="UTF-8">`

**dołączanie arkusza stylów:**
`<link rel=stylesheet" href="file.css"`

**deklaracja JavaScript:**
`<script src="file.js"></script>`

rozdzielamy strukturę (HTML) od wyglądu (CSS)

**pliki.html**
_index.html_ domyślnie jest traktowany jako strona startowa dla danej witryny

Powrót do [[#WSTĘP]]






