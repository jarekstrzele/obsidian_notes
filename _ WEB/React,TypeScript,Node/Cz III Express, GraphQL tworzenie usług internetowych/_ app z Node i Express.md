#node #express 

**Node** to środowisko uruchomieniowe ogólnego przeznaczenia, a  nie jedynie serwer WWW(s.226)

**przeglądarki i JS**:
- przeglądarki mają wbudowany silnik JS
	- odczytywanie kodu JS
	- maszyna wirtualna wykonująca kod
- *sandbox* w przeglądarce pamięć do bezpiecznego wykonywania kodu JS
- *web API* internetowy interfejs programowania  (dodatkowe możliwości JS)
	- dostęp do DOM,
	- obsługa żądań sieciowych
	- ....

**Node i JS**
- ma silnik dla JS
- kontener uruchomieniowy, w którym może być wykonywany nasz kod
- sercem Node jest ==libuv== - usługa dla Node napisana w C, która stanowi interfejs pośredniczący z jądrem systemu i udostępnia ==asynchroniczne mechanizmy obsługi wejścia-wyjścia==;
- **libuv** używana jest ==pętla zdarzeń== (*event loop*) - daje błyskawiczny dostęp do jej uslug


# Pętla zdarzeń
sercem Node jest *libuv* oraz *pętla zdarzeń*

>[!info] event loop
>Otóż jest to działający w ramach usługi *libuv* mechanizm wykonywania wątków, który przypomina nieco pętlę obsługi zdarzeń przeglądarki Chrome 
>i zapewnia możliwość iteracyjnego wykonywania asynchronicznych wywołań zwrotnych.

1. start: wykonywanie zdania asynchronicznie (uruchamia je pętla zdarzeń)
2. proces w pętli zdarzeń ma fazy, które się powtarzają
	1. najpierw wykonywane są **liczniki czasu** (*timers*), 
		1. a jeśli jakieś funkcje zwrotne tych liczników są już umieszczone w kolejce, to zostają wywołane jedne po  drugiej
		2. jeśli nie ma do wykonania żadnych funkcji zwrotnych liczników czasu, i jeśli jakieś liczniki właśnie zostały zakończone, to pętla zapisze w kolejce funkcje zwrotne, które należy wykonać
		3. i tak w kółko


# Node 

`const fs = require("fs")` - to sposób importu *Common-JS*

tworzenie pliku i odczytywanie go (stary styl)
```js
fs.writeFile("Text.txt", "Witaj świecie!", ()=>{
	fs.readFile("test.txt", "utf8", (err, msg) => {
		console.log(msg)
	});
});
```







