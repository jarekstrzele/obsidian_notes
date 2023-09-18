[[_ 0 NodeJS - zostań fullstack]]
#express 

info o wszystkich metodach https://expressjs.com/en/4x/api.html


# INSTALACJA
- zrób folder
- wewnątrz `npm init` (package json)
>1. `npm install express --save`: Ta komenda instaluje pakiet [Express](https://www.google.com/search?q=Express) i zapisuje go jako zależność w pliku `package.json` w sekcji `dependencies`. Dzięki temu, gdy inni programiści będą chcieli uruchomić twoją aplikację, będą mogli zainstalować wszystkie zależności zdefiniowane w pliku `package.json`, w tym [Express](https://www.google.com/search?q=Express).
    2. `npm install express`: Ta komenda instaluje pakiet [Express](https://www.google.com/search?q=Express), ale nie zapisuje go w pliku `package.json`. Oznacza to, że [Express](https://www.google.com/search?q=Express) nie jest traktowany jako zależność projektu i inni programiści będą musieli jawnie zainstalować [Express](https://www.google.com/search?q=Express), jeśli chcą uruchomić twoją aplikację.
    >
> W praktyce zaleca się używanie `--save` lub `-S` (skrót) przy instalowaniu pakietów, aby zapisywać zależności w pliku `package.json`.


- `npm install express --save`

```js

const express = require("express") // zwraca funkcję
const app = express() // tworzy obiekt

```


# pierwszy przykład
```js
const express = require("express")
const app = express()


app.disable("X-Powered-By") //wyłączy nagłówek

app.get('/', (req,res)=>{
    res.send("Witaj świecie")
})

app.listen(9090, ()=>console.log("localhost:9090"))
```
sprawdź na adresie `/` (*sieć*) oraz na fałszywym adresie (`/noctam`)

# Serwowanie statycznych plików
```js
const express = require("express")
const app = express()

//app.use( someFun) - someFun będzie wykonywana dla każdego zapytania przed
// - w naszym przypadku - wykonaniem res.send("Witaj świecie")

// w projekcie mam folder /public/ w którym
// jest index.html
// oraz podfolder CSS z css
app.use( express.static("public")) //some ExpressJS będzie dbał o poprawne type MIM

app.disable("X-Powered-By")

app.get('/', (req,res)=>{
    res.send("Witaj świecie") // to nie będzie brane pod uwagę
})  

app.listen(9090, ()=>console.log("localhost:9090"))
```

# Routing zapytań



takie adres nie zadziała, bo brakuje `:id` : `http://localhost:9090/2023-09-11`
















