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

module.exports = add;
```

```bash
$ node main.js
moduł script1 
[Function: add]
```
zawartość pliku script1.js jest prywatna oprócz funkcji add



-------
## Importowanie katalogów










