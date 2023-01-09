[[_ Node and JavaScript]]

----
# Node
#node 

## start

1. a file js  -> `hello.js` 
2. in git bash -> `$ node hello.js'

## create a server
>[!note]
>**node** 
>- allows to run JavaScript  on a server
>- is ==asynchronous==
>- can make a lot of stuff 

```javascript
var http = require('http')

http.createServer(function(req, res){
	res.writeHead(200, {'Content-Type': 'text/html'});
	res.end('<h1>Hello world</h1>');
}).listen(8080);

```
`http` module:
- built-in module
- allows node to transfer data over the internet
	- you are in your browser you're calling the server transferring a request to the server (`req`)
	- the server responds, sends response back (`res`) 
- `http.createServer` we create a server object
	- `res.writeHead` the server says "If everything will be correct (200), I send you a html text"
	- `res.end` the server says "I sends you some html text"
	- `listen` we say that server has to listen to 8080 port
	- 
----
## req, res
```javascript
var http = require('http')

http.createServer(function(req, res){
	res.writeHead(200, {'Content-Type': 'text/html'});
	res.write(req.url)
	res.end();
```
`req.url` gets the text written in the browser where we write internet addresses
	- `http://localhost:8080/fajne_gacie` -> `/fajne_gacie`
	- `http://localhost:8080/?year=2019&month=February`

### to do some stuff with url
`var url = require('url')`
```javascript
var http = require('http')
var url = require('url')


http.createServer(function(req, res){
	res.writeHead(200, {'Content-Type': 'text/html'});
	var q = url.parse(req.url, true).query;
	var dates = q.year;
	res.write(dates);
	res.end();
}).listen(8080);

```

`http://localhost:8080/?year=2019&month=June`
=> 2019

the url object:
```bash
Url {
  protocol: null,
  slashes: null,
  auth: null,
  host: null,
  port: null,
  hostname: null,
  hash: null,
  search: null,
  query: [Object: null prototype] {},
  pathname: '/dasy.html',
  path: '/dasy.html',
  href: '/dasy.html'
}

```
---
## File system and index page
file system - open, close read and write other files

- to access a file system: `fs` module
- to read file 
	```javascript
var http = require('http')
var fs = require('fs')


http.createServer(function(req, res){
	fs.readFile('index.html', function (err, data){
		res.writeHead(200, {'Content-Type': 'text/html'});
		res.write(data);
		res.end();
	})

}).listen(8080);
con

```


---
## Create Server Console Status Message
```javascript
var http = require('http')
var fs = require('fs')
var url = require('url')

http.createServer(function(req, res){
	fs.readFile('index.html', function (err, data){
		res.writeHead(200, {'Content-Type': 'text/html'});
		res.write(data);
		console.log("...Incoming request: " + req.url);
		res.end();
	})

}).listen(8080);

console.log("Node Server Listening on Port 8080....")

```


```bash
$ node hello.js
Node Server Listening on Port 8080....
...Incoming request: /?year=2019&month=June
...Incoming request: /favicon.ico
...Incoming request: /index
...Incoming request: /favicon.ico


```

---
## Show different web pages

```javascript
var http = require('http')
var fs = require('fs')
var url = require('url')

http.createServer(function(req, res){
	var q = url.parse(req.url, true);
	var filename = "." + q.pathname ;
	console.log("q: " + q + "  filename: " + filename);
	fs.readFile(filename, function (err, data){
		if(err){
			res.writeHead(404, {'Content-Type': 'text/html'});
			return res.end("<center><h1>404 Not found </h1></center>");
		}
		res.writeHead(200, {'Content-Type': 'text/html'});
		res.write(data);
		console.log("...Incoming request: " + req.url);
		res.end();
	})

}).listen(8080);

console.log("Node Server Listening on Port 8080....")

```

plus three file.html

----
##  nothing -> index.html
```javascript
http.createServer(function(req, res){
	var q = url.parse(req.url, true);
	var filename = "." + q.pathname ;

	if(filename == './'){
		filename = './index.html';
		}
	console.log("q: " + q + "  filename: " + filename);
	fs.readFile(filename, function (err, data){
	....
```

---
## page.html -> page
```javascript
http.createServer(function(req, res){
	var q = url.parse(req.url, true);
  var filename = "." + q.pathname;
	if(filename == './'){	filename = './index'; }
	filename = filename + ".html";
	console.log("filename: ", filename);
	
	fs.readFile(filename, function (err, data){
	....
```

----
## generate ssh key 
#key #ssh
on windows
1. `mkdir .shh` 
2. `cd .shh`
3. `ssh-keygen.exe` generates a public and private key and will use the public one to connect to GitHub
4. hasło: Filozoria2!@

```shell
jstrzelecki@BILL-5MZSPH2 MINGW64 ~/.ssh
$ ls
id_rsa  id_rsa.pub

jstrzelecki@BILL-5MZSPH2 MINGW64 ~/.ssh
$ cat id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCyMaShGV3bWpY+8jePxNWsmXXXInXJpPMAKok3emcHhIMIoOmW/Q0e0M+/Fz9jDr0EGutJYM/AsZ0bRZmszikZC9lh1Cj/JxYFdsukDTM7IkjJyla3AiaUgqwAVaYNEBTOQw7EaI0/SokudfS8VCGu4CJuNy0cCsiPoxpyZeuSPPaVHplBwb8rEo/BxiUUwlGphV2dFFXpPB87RIkw/7Mss1bpSrr0k+r0xWD7CTUw6oHj5r67L8MZCei50hgrsTtoAiHPX7AuwBqxUXfFzr/N3zajNU8F7Vevt0yozAln9YSlf5SEsJZ72Q64ZRhJ2bROpZlYsMu9xfAl95tFSWn4P9c6QmDCi86dL9wzopJIu91IsRX+kTgsLZMxxpYJXjc2zUI218QpcplFwMvKjqrEfUe4bOLraBOv57O7Y5Fjqwwllq45i0pA72QWCa3NRjzL7hKQiqK1Kg2SZ2uDAInlQ6BYDx30aGJYTuPs9HSgpv+fKlFNtTIRpCrm/FKKcMM= jstrzelecki@BILL-5MZSPH2

```

on Github -> account -> settings -> ssh and gps keys -> new SSH key -> paste your public key


Now you can connect your git with github
so go to the local folder with node files

some bash command:
```bash
git config --global user.name  "your name"
git config --global user.email "your eamil"
git config --global push.default matching
git config --global alias.co checkout
git init

```

How to use git?
`git add .` save all
`git commit -am "message"` confirm all

now we have to connect our local repo with github

1. return to github and add new repo
2. name the repo
3. create the repo
4. in your local terminal write: 
```bash
git remote add origin https://github.com/jarekStrzelecki/into-t--Node.git
git push -u origin master
```





you localy made some changes, you want to push them to the github, so:
1. `git add .`
2. `git commit -am "Tweaked index.html"`
3. `git push`



-----
## HEROKU
#heroku

Heroku is a cloud platform as a service (PaaS) supporting several programming languages.

https://devcenter.heroku.com/articles/heroku-cli#install-the-heroku-cli
install HEROKU CLI ()

`heroku --version`

`jarek@BILL-5MZSPH2:/mnt/c/Users/jstrzelecki/PROG$ cd nodefiles/`

Heroku:
- needs some settings files
- in our nodefiles foleder `npm init`

```bash
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (nodefiles)
version: (1.0.0) 10.19.0
description: Simple Web App
entry point: (hello.js)
test command:
git repository: (https://github.com/jarekStrzelecki/into-t--Node.git)
keywords:
author: js
license: (ISC) mit
Sorry, license should be a valid SPDX license expression (without "LicenseRef"), "UNLICENSED", or "SEE LICENSE IN <filename>" and license is similar to the valid expression "MIT".
license: (ISC) MIT
About to write to /mnt/c/Users/jstrzelecki/PROG/nodefiles/package.json:

{
  "name": "nodefiles",
  "version": "10.19.0",
  "description": "Simple Web App",
  "main": "hello.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/jarekStrzelecki/into-t--Node.git"
  },
  "author": "js",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/jarekStrzelecki/into-t--Node/issues"
  },
  "homepage": "https://github.com/jarekStrzelecki/into-t--Node#readme"
}


Is this OK? (yes)
```

in our folder appeared a new json file


NOW
we need to connect our terminal to heroku
in ubuntu terminal `heroku login` -> in browser we log in
(js100code@gmail.com Filozofia2!@)
When I logged in, I have to create an app on heroku -> `heroku create` -> 
```bash
$ heroku create
Creating app... done, ⬢ sheltered-temple-55733
https://sheltered-temple-55733.herokuapp.com/ | https://git.heroku.com/sheltered-temple-55733.git
jarek@BILL-5MZSPH2:/mnt/c/Users/jstrzelecki/PROG/nodefiles$
```

past 
https://sheltered-temple-55733.herokuapp.com/  into the browser

than we add into the package.json:
```json
...
"scripts":{
	"start":"node hello.js"
...

}
```

than we have to change a hello.js file
add: `const PORT = process.env.PORT || 5000`
change: `... .listen(PORT)`

than: git add, commit, push
and `git push heroku master`

to change a htttp address:
`heroku rename new_name`