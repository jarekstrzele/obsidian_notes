w folderze z plikem .js jest foder ` teksty` z plikami tekstowymi

# `exists`
wersja przestarzała
```js
const fs = require('fs') ; //file system

const path = require('path') ;

// path.sep --> '/' separator zależy od systemu
// path.join(sieżka, callback) połączy stringi odpowiednim separatorem
fs.exists(path.join(__dirname, 'teksty', 'lorem_12.txt' ),
                    function(exists) {
                        if (exists){
                        console.log("Plik istnieje") ;
                        }
                        else {
                        console.log("plik nie istnieje") ;
                            }})
console.log("To jest przed funkcja asynchroniczną")

```
bo jeżeli nie ma funkcji zwrotnej, `exists` zachowuje się niejednoznacznie
```js
const fs = require('fs') ; //file system
const path = require('path') ;

// path.sep --> '/' separator zależy od systemu
// path.join(sieżka, callback) połączy stringi odpowiednim separatorem

let fileExists = fs.existsSync(path.join(__dirname, 'teksty', 'lorem_2.txt' ) ) ;
if (fileExists){
    console.log("Plik istnieje") ;
}
else {
    console.log("plik nie istnieje") ;
}
```



# `stat` odczytywanie info o plikach i katalogach

*error-first callback* funkcja callback, która jako pierwszy argument przyjmuje `error`

```js
const fs = require('fs') ; //file system
const path = require('path') ;

// path.sep --> '/' separator zależy od systemu
// path.join(sieżka, callback) połączy stringi odpowiednim separatorem
fs.stat(path.join(__dirname, 'teksty', 'lorem_1.txt' ),
        function(err, stats) {
            if(err){
                console.log(err.message) ;
                throw err ;
            }

            console.log(`Data utworzenia: ${stats.birthtime}`); //birthtime jest obiektem Date
            console.log(`Data ostatnie modyfikacji: ${stats.mtime}`);
            console.log(`isFile: ${stats.isFile()}`); // czy lorem_1.txt jest plikiem?
            console.log(`isDirectory: ${stats.isDirectory()}`);
        })
console.log("To jest przed funkcja asynchroniczną")
```

---
# `readdit`  odczytywanie zawartości katalogu







