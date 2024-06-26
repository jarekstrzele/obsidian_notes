[[_ 0 NodeJS - zostań fullstack]]
#express 

info o wszystkich metodach https://expressjs.com/en/4x/api.html
inne notatki na ten temat [[5 Working with Express.js]]o

[[3.1 Express - introducing]]
[[5 Working with Express.js]]

--------
[[#INSTALACJA]]
[[#pierwszy przykład]]
[[#Serwowanie statycznych plików]]
[[#Routing zapytań]]
[[#Korzystanie z szablonów]]
[[#Użycie middleware]]


----
  
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
app.use(express.static("public "))
// w projekcie mam folder /public/ w którym
// jest index.html
// oraz podfolder CSS z css

app.disable("X-Powered-By")

app.get('/', (req,res)=>{
    res.send("Witaj świecie") // to nie będzie brane pod uwagę
})  

app.listen(9090, ()=>console.log("localhost:9090"))
```

# Routing zapytań
>W kodzie programu w języku Node.js, wyrażenie `${JSON.stringify(req.query, null, 4)}` jest używane do przekształcenia obiektu `req.query` w postać tekstową w formacie JSON.
```js
const express = require("express")
const app = express()

app.get('/', (req,res)=>{
    res.send("Witaj świecie")
})

app.get('/o-nas', (req,res)=>{
    res.send("o nas")
})

//dynamiczne parametry
// JSON.stringify() przekształca obiekt JS w tekst w formacie JSON
// req.query - obiekt zawierający parametry zapytania przekazane w adresie URL
app.get('/blog/:date/:id', (req,res)=>{
   res.send(`
    wpis o id ${req.params.id} utworzony ${req.params.date}
    <pre>${JSON.stringify(req.query, null, 4)}</pre>
    <p>${JSON.stringify(req.query.mojKlucz, null, 4)}</p>     
     `)
})

app.listen(9090, ()=>console.log("localhost:9090"))
```
taki adres nie zadziała, bo brakuje `:id` : `http://localhost:9090/blog/2023-09-11`

ten adres zadziała:
`http://localhost:9090/blog/2023-09-11/2` -- wyświetli -> `wpis o id 2 utworzony 2023-09-11`

a na request `http://localhost:9090/blog/2023-09-11/22?mojKlucz=mojaWratosc` -- zwraca-->
```
wpis o id 22 utworzony 2023-09-11

{
    "mojKlucz": "mojaWratosc"
}
"mojaWratosc"
```


# Korzystanie z szablonów

### `templating engines`
różne template engines
https://github.com/expressjs/express/wiki
https://expressjs.com/en/resources/template-engines.html

## express-handlebars
#express-handlebars


https://waelyasmina.medium.com/a-guide-into-using-handlebars-with-your-express-js-application-22b944443b65


ten `engine` pod adresem https://github.com/express-handlebars/express-handlebars

to install `npm install express-handlebars`


---
umieść `styles.css` w folderze `public`
umieść `main.js` (z kodem jQuery) umieść w folderze `public`

```html
  <link rel="stylesheet" href="/styles.css"/>

  <script src="/main.js" ></script>
  
```

----
`public/css/styles.css`
`header.handlebars`
```html
 <link rel="stylesheet" href="/css/styles.css"/>
```

`app.js`
```js
//...
app.use(express.static("public"))

app.engine('handlebars', exHbrs.engine({defaultLayout: "main"})) // register a new template engine
app.set('view engine', 'handlebars')
//....
```

teraz można różne style css używać w różnych plikach

np. `fakapi.handlebars`
```js
     <h3>Lista ciekawostek</h3>
    {{#if listExists}}
         <ul>
            {{#each people}}
                <li class="mojaLista"> {{ this.name }}, {{ this.residence }}</li>
            {{/each}}
         </ul>
    {{/if}}
```

----


```js
const express = require("express")
const exHbrs = require("express-handlebars");

const app = express()

// aby móc używać styles.css, który jest w public/css
app.use(express.static("public/css"))

// `app.engine('handlebars' ...` datego potem pliki mają rozszerzenie handlebars
app.engine('handlebars', exHbrs.engine({defaultLayout: "main"})) // register a new template engine
app.set('view engine', 'handlebars')

app.get("/", (req, res) => {
// home is a view
// by default all views have to be in the folder `views`
    res.render("home", {
        title:"Strona główna",
        content: "to jest treść strony głównej"
    })
})

  

app.listen(9090, ()=>console.log("Server is listening on the 8080 port"))
```

`views/home.handlebars`
```html
<div>
     <h2> {{ title }}</h2>
     <p> {{ content }}</p>
    <p> i małe co nieco </p>
</div>
<!--
    cała ta treść będzie podstawiona
    do `body`
    w `main.handlebars`
-->
```

`views/layout/main.handlebars`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> {{ title }} </title>
</head>
<body>
    <div>
        {{{ body }}}
    </div>
</body>
</html>

```

mogę wprowadzić pewne zmiany
- tworzę nowe pliki `views/partials/header`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> {{ title }} </title>
</head>
<body>
```

oraz `views/partials/footer`
```html
</body>

</html>
```
- modyfikuję `main.handlebars`
```html
{{> header }}

    <div>
        {{{ body }}}
    </div>

{{> footer }}
```


tworzenie dodatkowego view
`views/blog.handlebars`
```html
<div>
    <h2>{{ title }} </h2>
    <p> to jest wpis z dnia {{ date }} </p>
    {{#if id }}
    <p> identyfikator wpisu: {{ id }}</p>
    {{/if }}
</div>
```

i do app.js dodajemy
```js
app.get("/blog/:date/:id?", (req,res)=>{
   // :id? - więc id jest opcjonalne
    res.render("blog", {
        title: "Blog",
        date: req.params.date,
        id:req.params.id
    })
})
```

tworzenie strony 404
`views/404.handlebars`
```html
   <h2>{{ title }} </h2>
   <p> nie znaleziono strony </p>
```

a do pliku `app.js` (koniecznie pod koniec!!!)
```js
//... pod koniec pliku po wszystkich middlewares i routings

app.use((req,res,next)=>{
    res.status(404).render('404', {title: "PAGE NOT FOUND"})
 })
 
app.listen(9090, ()=>console.log("Server is listening on the 8080 port"))
```

**fakeowe api** kolejny przykład
w głównym pliku dodać:
```js
app.get("/api/fake", (req, res)=>{

    res.render('fakeapi', {layout: "main", people: fakeApi(), listExists: true});

})
//...

fakeApi = () =>{
    return [
        {
            name:"Adrian",
            residence: "Olsztyn"
        },
        {
            name:"Dawid",
            residence: "Barczewo"
        },
        {
            name:"Zdzisław",
            residence: "Kroszynianka"
        }
    ]
}
```

`fakeapi.handlebars`
```html
<h3>Lista ciekawostek</h3>
{{#if listExists}}
  <ul>
    {{#each people}}
     <li class="mojaLista"> {{ this.name }}, {{ this.residence }}</li>
    {{/each}}
 </ul>
{{/if}}
```

styles.css
```css
.mojDiv{
    width: 400px;
    height: 200px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: burlywood;
    color:darkmagenta;
    padding: 10px;
}

  

.mojaLista{
    color:crimson;
    font-size: 19px;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;

}
```

`main.handlebars`
```html
{{> header }}
    <div class="mojDiv">
        {{{ body }}}
    </div>
{{> footer }}
```


### zdjęcia
```js
app.get("/myimages", (req, res) => {
  res.render("myimages", {
    imgs: "/images/cute.jpg",
    width: 100,
    height: 200,
  });
});
```

`myimages.handlebars`
```js
<div style=" width: 400px; height: 500px; background-color:lightblue; ">
	  <img src={{imgs}} alt="nic" width={{width}} height={{height}} />
</div>
```



-----------

# Użycie middleware

```js
const express = require("express")
const app = express()
const USER = "admin"
const PASSWORD = "abc"

//middleware - działa dla wszystkich ścieżek
// dla każdego połączenia będzie usuwany nagłówego X-Powered-By
app.use((req, res, next)=>{
    res.removeHeader("X-Powered-By");
    res.locals.data1 = "String zapisany w atrybucie data"

    // musimy wywołać next(), bo serwer nie przejdzie dalej
    next()
})

//middleware tylko dla '/admin
app.use('/admin', (req,res,next)=>{
    if(req.query.user===USER && req.query.password===PASSWORD){
        return next();
    }
    res.redirect('/') ;
})

app.get('/admin', (req,res)=>{
    res.send("Widam Cię mój wspaniały <b>administratorze</b>")
})

app.get('/', (req,res) => {

    //res.removeHeader("X-Powered-By")
    res.send(`Strona główna
        a to są dane z res.locals.data ${res.locals.data1}
    `);
})

app.listen(9090, ()=>console.log("localhost:9090"))
```


PRZYKŁAD z `serve-index`
https://www.npmjs.com/package/serve-index

instalacja:`npm install serve-index`
 
```js
const express = require("express")
const app = express()
const serveIndex = require("serve-index")
  

app.use("/images", express.static("public/images"))
app.use("/images", serveIndex("public/images"))
// też działa
// app.use("/abc", express.static("public/images"))
//app.use("/abc", serveIndex("public/images"))
//....
```
w folderze `public` mam podfolder `images`
więc pod adresem `/images` będę mógł ogląć zawartość katalogu

---
# REST API
#restapi 

### ` npm i body-parser --save`  (to jest middleware)
- musimy doinstalować, aby wysyłać w body zapytania dodatkowe informacje
- używając `get` dany wysyłamy w *query string*, ale używając innych metod (`put`, `post`) w body przesyłamy odpowiednie dane


## `someList.every()`
```js
let a = [10,20,30,40]
undefined
a.every((number)=> number > 9)
true
a.every((number)=> number > 19)
false
a.every((number)=> {
    if (number > 20) { 
        num = number
        return false ;
    }
    return true;
    
})
false
num 
30
```


## `Object.assign(oldObject, newDataToOldObject)`
```js
user = {
  id: 1,
  name: "John",
  age: 30
};

userData = {
  name: "Alice",
  age: 25
};
{name: 'Alice', age: 25}
Object.assign(user, userData)
{id: 1, name: 'Alice', age: 25}
user 
{id: 1, name: 'Alice', age: 25}
user = {
  id: 1,
  name: "John",
  age: 30
};

userData = {
  name: "Alice",
  age: 25
};
{name: 'Alice', age: 25}
user
{id: 1, name: 'John', age: 30}
Object.assign(userData, user)
{name: 'John', age: 30, id: 1}
user 
{id: 1, name: 'John', age: 30}
userData
{name: 'John', age: 30, id: 1}
```


### `splice(index, howManyElements)`
```js
let zabawki = ["samochodzik", "klocki lego", "iPhone", "piłka"]
undefined
let index = zabawki.indexOf("iPhone")
undefined
index 
2
zabawki.splice(index, 1)
['iPhone']
zabawki
 ['samochodzik', 'klocki lego', 'piłka']
```
















