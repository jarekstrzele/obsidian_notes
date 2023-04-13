script1.js
```js
var msg = "moduł script1 ";
console.log(msg) ;

function add(x,y){
        return x + y
};
```

main.js
```js
const add = require("./script1") ;

console.log(add) ;
```

```bash
jarek@pop-os:~/Desktop/Prog$ node main.js
moduł script1 
{}
```
`{}`, bo każdy moduł (a każdy plik to moduł ) mamy `module.exports = {}` domyślnie dopisywany

teraz
sript1.js
```js
var msg = "moduł script1 ";
console.log(msg) ;

function add(x,y){
        return x + y
};

module.exports = add; // przekazujemy referencję do funkcji
```

```bash
$ node main.js
moduł script1 
[Function: add]
```
zawartość pliku script1.js jest prywatna oprócz funkcji add

funkcja `require()` wykonała cały plik `script1`, a to co zwrócił ten plik została zapisane w zmiennej add w pliku `main`


-------
# Importowanie katalogów

w fodlerze `calc` jest m.in.
index.js
```js
const add = require("./add") ;
const divide = require("./divide")

module.exports ={
	add: add,
	divide: divide
}
```
main.js
```js
const calc = require("./calc") ; // calc to folder, w którym jest index.js i JS będzie szukać index.js

console.log("main moduł")

console.log(calc.add(5,6)) ;
```

```bash
$ node main.js
moduł add 
moduł divide 
main moduł
11
```



----
# package.json
można też do folderu `calc` dodać `package.json`
zmieńmy nazwę `index.js` na `my_calc.js`
```json
{
"main": "my_calc.js"
}
```
`node main` -> będzie szukał pliku `index` w folderze `calc`,
	nie znajdzie go, więc
	zacznie szukać `package.json`, znalazł, więc
	sprawdzi wartość atrybutu `main` i wykona plik, który jest wartością tego atrybutu, czyli `my_calc.js`
	



--------------------
# Parsowanie .json
Możem importować:
- katalogi,
- pliki js
- oraz również pliki z rozszerzeniem `json`

automatyczne parsowanie json
 w folderze `calc` obok `package.json` utworzę plik `config.json`
```js
{
	"name":"calculator",
	"version": "1.0.0"
}
```

w pliku `my_calc` dopisuję
```js
const add = require("./add") ;
const divide = require("./divide")

module.exports ={
	add: add,
	divide: divide ,
	config: require("./config") // JS będzie szukał katalogu, pliku .js, jak nie uda się, to poszuka pliku json i go sparsuje do zwykłego obiektu JS
}
```

jako obiekt będzie config dostępne w main np. `calc.config.name`

-----------

# Node pakuje zawartość pliku do specjalnej funkcji

np. 
script1.js
```js
var msg = "moduł script1 ";
console.log(msg) ;

function add(x,y){
        return x + y
};
```

zamieni na
```js
(function (exports, require, module, __filename, __dirname){
	var msg = "moduł script1 ";
	console.log(msg) ;
	
	function add(x,y){
	        return x + y
	};
})();

```


-----------
### `__filename` ścieżka do pliku
### `__dirname` ścieżka do folderu

```js
const calc = require("./calc/my_calc") ; // calc to folder, w którym jest index.js

console.log("main moduł")
console.log(__filename, __dirname)

console.log("Czy to główny moduł? " + (require.main === module ? "Tak": "Nie."))
```

```bash
$ node main.js
moduł add 
moduł divide 
main moduł
/home/jarek/Desktop/Prog/node/main.js /home/jarek/Desktop/Prog/node
Czy to główny moduł? Tak
```

> [!important] 
> Node zapisuje w pamięci podręcznej moduły, które importujesz!!!



------
# Wbudowane moduły Node.js
https://nodejs.org/docs/latest-v16.x/api/

# PATH and UTIL
````js
const path = require('path') ;
const utils = require('util') ;

let log = utils.format("Nazwa pliku to %s", path.basename(__filename)) ;

console.log(log) ;
console.log(__filename) ;
````

```bash
$ node main.js 
Nazwa pliku to main.js
/home/jarek/Desktop/Prog/node/main.js
```





