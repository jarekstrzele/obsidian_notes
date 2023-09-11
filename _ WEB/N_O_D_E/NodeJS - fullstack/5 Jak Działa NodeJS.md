[[_ 0 NodeJS - zostań fullstack]]


# Jednowątkowa pętla zdarzeń

## Proces
>[!info] Proces
>To instancja uruchomionego programu, której system operacyjny przydzielił zasoby takie jak czas procesora, pamięć operacyją, dostęp do urządzeń I/O, pliki

**Każdy nowo uruchomiony proces posiada własną niezależną przestrzeń adresową**

np. uruchamiasz Photoshopa, to taki uruchomiony proces jest procesem Photoshopa
np. `cmd` > `tasklist`


# Wątek
#node/thread

>[!info] Wątek (*thread*)
>część programu wykonywana współbieżnie, uruchomiona przez procesor. Proces może uruchamiać wiele wątków. Wątek tym różni się od procesu, że współdzieli z innymi wątkami zasoby przydzielone dla procesu

- Wątki wymagają mniej zasobów do działania, a także są szybciej tworzone. 
- Mogą przekazywać pomiędzy sobą dowolną ilość danych bez ich kopiowania, jedynie przekazując sobie wskaźniki w pamięci operacyjnej.
- aby otrzymać wrażenie współbieżności, procesor przełącza się pomiędzy wątkamiw którkich odstępach czasu


## Wielowątkowy Node.js i jednowątkowa pętla zdarzeń

>  Node to:
>>  - silnik V8 (interpreter języka JS)
>> 	 - jest jednowątkowy
>>  - C++ (dodatkowe biblioteki C++) (NodeJS APIs)


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





# Bloki budulcowe Node.js






