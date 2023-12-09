#node #express 
[[_ React, TypeScript, Node]]




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

nowy styl
```js
const fs = require("fs/promises") ;
// nowsza wersja import fs from "fs";
// w package.json "type:"module"

(async function(){
	await fs.writeFile("test-promise.txt", "Witaj , obietnico");
	const readText = await fs.readFile("test-promise.txt", "utf-8");
	console.log(readText) ;
})
```

# Prosty serwer Node

`npm init` ---> project name 
make  a new file `server.mjs` 
```js
import http from "http" ;

const server = http.createServer((req,res) => {
	console.log(req) ;
	res.end("Witaj świecie") ;
})

//nakaanie obiektowi serwer nasłuchiwania
const port = 8000;
server.listen(port, () => {
	console.log(`server na porcie ${port}`) ;
})
```

`node server.mjs`

# Żądania i odpowiedzi
Gdy żądanie jest przesłane przez przeglądarkę do serwera, framework serwera tworzy DWA OBIEKTY:
- `Request` - dane związane z żądaniem przesłanym przez przeglądarkę
- `Response` - odpowiedź, która zostanie odesłana

można je podglądnąć w przeglądarce *Network* (żądanie z punktu widzenia przeglądarki)

## adres URL żądania
reprezentuje on kompletną ścieżkę URL przesłaną na serwer:
- `Request URL: http://localhost:8000/`
- gdyby wysłano `http://localhost:8000/home?userid=1` - chodzi o stronę lub dane API umieszczone w podkatalogu home, od znaku zapytania zaczyna się sekcja **parametrów,** które mogą być oddzielone `&`

## metoda żądania
reprezentuje tak zwany "czasownik HTTP" - to opis informujący serwer o czynności, o które wykonanie prosi klient
GET (wszelkie parametry muszą być przekazywane w adresie URL)
POST - utworzyć lub wstawić coś, (wszystkie parametry zapisywane w treści żądania)
PUT - aktualizacja
DELETE - usunięcie 

## kod statusu
200 - ok
400 - złe żądanie
401 - dostęp nieautoryzowany
500 - wewnętrzny błąd serwera

# nagłówki
opisy, metadane

### nagłówki żądania
`Content-Type` określa typy mediów stanowiących zawartość odpowiedzi (dla POST, PUT, `application/json` - żądanie zawiera dane zapisane w formacie JSON)

`Cookie` mały plik tekstowy zawierający informacje o użytkoniku oraz jego sesji
 ....

### nagłówki odpowiedzi
`Allow` określa dozwolone czasowniki HTTP

`Access-Control-Allo-Origin` stosowane w technice CORS, by zezwolić stronom z różnych witryn (o różnych adresach URL)  na generowanie żądań. `* ` dowolny adres URL

------
## Trasowanie `routing`
To w pewnym sensie przekazywanie parametrów do serwera.
Kiedy serwer zauważy podaną trasę (*route*) będzie wiedział, że musi odpowiedzieć na żądanie w określony sposób
mechanizm  *route* -  pozwala nam określać, w jaki sposób serwer powinien reagować na poszczególne żądania

```js
const server = http.createServer((req, res) => {
	if (req.url === "/") {
		res.end("Witaj, świecie!");
	} else if (req.url === "/a") {
		res.end("Witaj na trasie A");
	} else if (req.url === "/b") {
		res.end("Witaj na trasie B");
	} else if (req.url ==="/c" && req.method === "POST"){
		let body = [] ;
		req.on("data", (chunk) => {
			body.push(chunk);
		})
	} else {
		res.end("Do zobaczenia");
	}
});
```

















