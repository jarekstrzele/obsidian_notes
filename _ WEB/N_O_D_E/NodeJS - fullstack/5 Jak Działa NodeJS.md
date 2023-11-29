[[_ 0 NodeJS - zostań fullstack]]


# Jednowątkowa pętla zdarzeń

## Proces
>[!info] Proces
>To instancja uruchomionego programu, której system operacyjny przydzielił zasoby takie jak czas procesora, pamięć operacyją, dostęp do urządzeń I/O, pliki

**Każdy nowo uruchomiony proces posiada własną niezależną przestrzeń adresową**

np. uruchamiasz Photoshopa, to taki uruchomiony proces jest procesem Photoshopa
np. `cmd` > `tasklist`
lub program *Monitor zasobów* / *Resource Monitor*

# Wątek
#node/thread

>[!info] Wątek (*thread*)
>część programu wykonywana współbieżnie, uruchomiona przez procesor. 
>Proces może uruchamiać wiele wątków. 
>Wątek tym różni się od procesu, że współdzieli z innymi wątkami zasoby przydzielone dla procesu

- Wątki wymagają mniej zasobów do działania, a także są szybciej tworzone. 
- Mogą przekazywać pomiędzy sobą dowolną ilość danych bez ich kopiowania, jedynie przekazując sobie wskaźniki w pamięci operacyjnej.
- aby otrzymać wrażenie współbieżności, procesor przełącza się pomiędzy wątkami w krótkich odstępach czasu


## Wielowątkowy Node.js i jednowątkowa pętla zdarzeń

>  Node to:
>>  - silnik V8 (interpreter języka JS)
>> 	 - jest jednowątkowy
>>  - C++ (dodatkowe biblioteki C++) (NodeJS APIs)

PROGRAM DO ŚLEDZENIA WYKONANIA PROGRAMU http://latentflip.com/loupe


PRZYKŁAD
Mamy kod:
```js
1.   console.log("Hello") ;
2.   setTimeout(function cb() {
3. 	   console.log("3 sekundy później") ;
4.   }, 3000) ;
5.
6.   console.log("world!");
```

silnik V8 podejmuje się interpretacji tego kodu.
1. czyta pierwszy wiersz (`console.log` wrzuca na stos `stack`) i wykona ją
```bash
>> Hello
```
zrzuca ze stosu zakończoną funkcję `console.log`

2. Przejdzie do `setTimeout` (tej funkcj w JS nie ma,w  przeglądarkach jest wykonywana przez specjalne API,a w NodeJS przez APIs NodeJS(C++) )
	1. silnik V8 
		1. "wie", że nie potrafi wykonać tej funkcji,
		2. i że musi ją oddelegować do APIs(C++), a po wykonaniu przez C++ tego kodu, silnik V8 będzie mógł wykonać funkcję `cb()` (callback)
		3. i że może przejść do dalszej interpretacji kodu JS
	2. silnik V8 wrzuca `setTimeout` na stos, ze stosu do NodeJS API, no i `setTimeout` ściąga ze stosu (więc główny wątek JavaScriptowy nie jest zainteresowany tym, co dzieje się w NodeJS APIs)
	3. silnik V8 wrzuca na stos `console.log("world!")` wykonuje je
```bash
>> Hello
>> world!!
```
3. Po trzech sekundach NodeJS API kończy wykonywanie funkcji `setTimeout`, ale wyniku nie może wrzucić na stos, bo na stosie mogłby się dziać różne inne rzeczy 
4. więc NodeJS APIs wrzuca naszą funkcję `cb` do KOLEJKI obsługiwanej przez PĘTLę ZDARZEŃ (`event loop`) 
	1. jeżeli na stosie nie ma żadnego kodu aktualnie wykonywanego, to PĘTLA ZDARZEŃ sprawdzi kolejkę (a jest tam `cb`, i tę funkcję wrzuci na stos, aby silnik mógł ją wykonać
```bash
>> Hello
>> world!!
>> 3 sekundy później
```

https://www.youtube.com/watch?v=8aGhZQkoFbQ&t=808s

```js
function sleep(ms){
    let now = Date.now();
    while(Date.now() - now < ms){}
}
 

console.log("Hello") ;
console.time("setTimoutaa")
setTimeout( () => {
    console.log("3 sekundy później")
    console.timeEnd("setTimoutaa") ;    
}, 3000) ;

sleep(6000) ;

console.log("world!");
```


### z serwerem 
> QueryString (ciąg zapytań) to część adresu URL (Uniform Resource Locator), która zawiera dane przekazywane do serwera. Zazwyczaj występuje po znaku zapytania (`?`) i składa się z pary klucz-wartość, gdzie klucz i wartość są oddzielone znakiem równości (` = `), a poszczególne pary są oddzielone znakiem ampersand (`&`).








# Bloki budulcowe Node.js

JEDEN WĄTEK OBSŁUGUJE WSZYSTKIE POŁĄCZENIA,
więc trzeba dbać, aby pracę wykonywać asynchronicznie.

projekt Node na GitHUbie
https://github.com/nodejs/node
Node składa się z TRZECH głównych BLOKÓW:
1. ZALEŻNOŚCI (folder `deps`), - np:
	1.  `V8` - interpreter JavaScript
	2. `openssl` szyfrowanie
	3. `npm` 
	4. `http_parser`
	5. w folderze `uv` jest `libuv` (JEDNA Z NAJWAŻNIEJSZYCH):
		1. napisana C++
		2. pozwala wykonywać asynchroniczne operacje input/output (np. odczytywanie plików)
	6. `src` API
		1. `node/src/node_file.cc` to plik C++
		2. tam jest wiele funkcji np.     `FS_TYPE_TO_NAME(MKDIR, "mkdir")` , czyli gdy w JS napiszesz `mkdir` to wykonaj `MKDIR` cplusowy
	7. `lib` API Node Standard Library - np. moduły
		1. `fs` np
			1. jest tam `const binding = process.binding('fs')` to jest połączenie JS z C++
			2. w czystym JS nie ma możliwości odczytywania plików, ale w C++ już tak
		2. `events`
		3. `http`
		4. ....




