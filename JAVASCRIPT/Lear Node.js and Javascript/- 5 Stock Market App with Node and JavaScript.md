#node  #javascript 

[[_ Node and JavaScript]]



----
# Stock Market App with Node and JavaScript
0. folder `/c/nodestock`
1. create `index.js`
2. create a project `npm init -y` -> package.json file
3. to start project `node index.js`
4. install `ExpressJS` -> `npm install express --save 
5. na stronie  `Express` > API reference 
```javascript
const express = require('express')
const app = express()
```
tak stworzymy instancję *express* w naszej aplikacji

> any time you have a node app and you want to serve up web pages, you need to run the node server and you have to tell your app which port to listen on

```JavaScript
const express = require('express')
const app = express()

const PORT = process.env.PORT || 5000 //use some port or use 5000

app.listen(PORT, () => console.log("server is listening on port " + PORT))
```

----
## First web page
in folder `nodestock` create a new subfolder i.e. `public`
in this subfolder create a new file `index.html`
template from bootstrap

to connect html with the node file we will use express:
```javascript
...
const path = require('path');
...
// set static folder
app.use(express.static(path.join(__dirname, 'public')));
```
next pages? put into `public` folder html files and in the browser `localhost:5000/filename.html`

## Nodemon
#nodemon
so you don't have to manually restart your server
`npm install -D nodemon`
next
	change your `package.json`
```json
	...
	  "scripts": {
    "start": "node index",
    "dev": "nodemon index"
  },
```
and now if you want to run your project you have to write in your terminal `npm run dev`

----
# Handlebars
to build dynamic web pages
#handlebars
`npm install express-handlebars`

<iframe src="https://www.npmjs.com/package/express-handlebars" height="400" width="700"></iframe>
you have to add to you js file
`import { engine } from 'express-handlebars';`

#### view folder and layout folder
> general rule:
> one file and its code will be used in many pages


`layout` is a template:
- `main.handlerbars` stuff that we want on every page of our web site
- form `index.html` copy the content to this `main`
and in the `main`:
```
....
<body>
    <div class = "container">
        {{{body}}}

    </div>
    ...
```
and in the `view>home.handlebars` write some tag text
so 
in the `{{{body}}}` will be put the content of  this  `home`
index.js
```javascript
const express = require('express')
const path = require('path');
var exphbs  = require('express-handlebars');

const app = express()
const PORT = process.env.PORT || 5000

// register handlebars
app.engine('handlebars', exphbs.engine({defaultLayout: 'main'}));
// set routes
app.set('view engine', 'handlebars');
 
app.get('/', function (req, res) {
   
    res.render('home');
});

app.listen(PORT, ()=> console.log("sever is listening on port " + PORT))

app.use(express.static(path.join(__dirname, 'public')));

```

In the `res.render('home')` we can add a new content that will be display on the page:
`res.render('home', { stuff: "This is stuff...});"`
and in the `home` file write `<p> {{{ stuff }}} </p>`
the value of `stuff` can be anything

----
# git
[[JAVASCRIPT/Lear Node.js and Javascript/git]]


---
## Adding a new page
in `view` a new file `about.handlebars`
Inside this file `<div class = "container"> ABOUT mE </div>`

in `index.js`:
```javascript
app.get('/about.html', function (req,res){
    res.render('about');
})

```
`

---
## API
use https://iexcloud.io/
#iexcloud
Filozofia2!@
jscode100@gmail.com
Go to API TOKENS
Copy PUBLISHABLE pk_c26c395107d94a3396460e9c0f321733
and return to the `index.js`
`// API KEY pk_c26c395107d94a3396460e9c0f321733`

## Request API
`npm install request`
so in `index.js` add:
`const request = require('request')`
```javascript
// API KEY pk_c26c395107d94a3396460e9c0f321733
request('https://cloud.iexapis.com/stable/stock/fb/quote?token=pk_c26c395107d94a3396460e9c0f321733', {json: true}, (err, res, body)=> {

    if(err){return console.log(err);}
    console.log(body);
    if(res.statusCode ===200){
        console.log(body);
    }
});
```

change that code adding call_api function
```javascript
function call_api(){
    request('https://cloud.iexapis.com/stable/stock/fb/quote?token=pk_c26c395107d94a3396460e9c0f321733', {json: true}, (err, res, body)=> {

        if(err){return console.log(err);}
        if(res.statusCode ===200){
            //console.log(body);
            return body
        }
    });
}
// ...

app.get('/', function (req, res) {
   const api = call_api()
   console.log(api)
    res.render('home', {
        stuff: api
    });
});

```
but this code doesn't work well, because `api` const is undefined, because `call_api()` need a few time to manage its process but the program doesn't wait, so you have to make some changes:
```javascript
function call_api(finishedAPI){
    request('https://cloud.iexapis.com/stable/stock/fb/quote?token=pk_c26c395107d94a3396460e9c0f321733',
             {json: true}, (err, res, body)=> {

        if(err){return console.log(err);}
        if(res.statusCode ===200){finishedAPI(body)};
        }
    );
};

app.get('/', function (req, res) {
    call_api( (doneAPI) => {
        res.render('home', {
        stock: doneAPI
        });
    })
});

```

now you can display all infromation from `stock`
in the file `/view/home.handlebras` (add each loop):
```handlebars
{{#each stock}}
    {{@key}}-> {{this}}<br/>
{{/each}}
```

output
```
avgTotalVolume-> 28038966
calculationPrice-> close
change-> 0.99
changePercent-> 0.00506
close->
closeSource-> official
closeTime->
companyName-> Meta Platforms Inc - Class A
currency-> USD
delayedPrice->
....
```

you can use key-pair to display info what you want
```
<h1>
    Company name <strong> {{ stock.companyName }}</strong> ({{stock.symbol}})
</h1>
```

## Forms
in `views/layout/main.handlerbars` :
```html
<!-- ... -->
<form class="form-inline my-2 my-lg-0" role="search" action="/" method="POST">
        <input class="form-control me-2" type="search" placeholder="Lookup Stock Quote" aria-label="Search" name="stock_ticker">
        <button class="btn btn-outline-secondary" type="submit">Lookup</button>
      </form>
<!-- ... -->
```

in `index.js` you have to add post function
(but first `npm install body-parser` ; (`..  name="stock_ticker">`))
```javascript
const bodyParser = require('body-parser');
app.use(bodyParser.urlencoded({extended: false}));
```

---
We want to work not only with FB api but with every api transmitted by the user
`request('https://cloud.iexapis.com/stable/stock/fb/quote?token=pk_c26c395107d94a3396460e9c0f321733',`

instade of `fb` we could use any  others api, so we will use `stock` key


---
# Heroku
#heroku 
js100code

https://devcenter.heroku.com/articles/heroku-cli
install heroku cli on ubuntu
in terminal go to yuor project
next: heroku and node: https://devcenter.heroku.com/articles/getting-started-with-nodejs
	`sudo snap install heroku --classic`
	
>[!define a Procfile]
>Use a Procfile, a text file in the root directory of your application, to explicitly declare what command should be executed to start your app.
>
	so in the root path add Procfile with the content:
	`web: npm start`
	this file tells Heroku that has to run a node app
	
		
- log in heroku
- in yout laptop terminal genretate ssk key `heroku keys:add` in your project folder and add ssk key (`/home/jarek/.ssh/id_rsa.pub`)
- `heroku create` 
	it generated
```
https://stark-shore-13601.herokuapp.com/ | https://git.heroku.com/stark-shore-13601.git

```
this is a address to a heroku app
you can rename your app `heroku rename new_name`
`heroku rename nodestock`

`git push heroku master`


### Heroku change a domain of your web app
go to settings of your app on your heroku account -> scroll down and find 'Domains' add domain
namecheap for heroku






