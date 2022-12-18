[[_0 Node Complete Guide]]


## How the Web works

client/user/browser (enters some http address) 
	sends *request* to the server
server (Node, PHP, .NET ...)  do something
	sends *response* to the client (e.g. HTML)

*http*, *https* protocols

----

## Create a Node server
#node/server

there are some core modules:
- http
	- launch a server
	- send requests
- https
	- launch a SSL server
- fs
- path
- os
- ....
- 
to use them:
`const  http = require('http') ;`

#### to create s server
`createServer` method takes request listener as an arg.
**A request listener** is a function that will execute for every incoming request
The requst listener takes two args:
- a *request* object (NodeJs gives that object)
- a *response* object (NodeJs gives that object)
```jsx
const http=require('http');

function rqListener(req, res){

}

http.createServer(rqListener)
```

or with anonimous  
```jsx
const http=require('http');

http.createServer(function(req,res){
	//...
})
```

```jsx
const http=require('http');

http.createServer((req,res) =>{
	console.log(req) ;
}) 
// the script will start and immediatally end!!!!!
```

but if you want server running, you have to add at the end of the file:
```jsx
const http = require('http') ;

const server = http.createServer((req,res)=>{
console.log(req) ;
})

server.listen(3000); 
```
and now open browser on `localhost:3000`
and then you will see in the console result of `console.log(req)`

------
## Node Lifecycle and Event Loop
#node/event_loop

>[!info] Event Loop
>a loop process which is managed by nodejs which keeps on running as long as there is work to do (keeps on running as long as there are event listeners registered)

to quit `process.exit()`

---
## Request object
It is the object that nodejs generetes for us with all the data of the incoming request when we visiting e.g. `localhost:3000`

some important attributes
```js
    console.log(req.url, 
						    req.method,
						    req.headers) ;

```


### Routing Requests
```js
const http = require('http') ;

const server = http.createServer((req,res) => {
    const url = req.url ;
    if (url==='/'){
        res.setHeader('Content-Type', 'text/html') ;
        res.write('<html>') ;
        res.write('<head> <title> First page </title></head>') ;
        res.write('<body><form action="/message" method="POST"><input type="text" name="msg"><button type="submit">Send</button> </form></body>') ;
        res.write('</html>') ;
    return res.end();
    }
    res.setHeader('Content-Type', 'text/html') ;
    res.write('<html>') ;
    res.write('<head> <title> First page </title></head>') ;
    res.write('<body><h1>Hello fro my Node.js Server</h1> </body>') ;
    res.write('</html>') ;
    res.end();
})

server.listen(3000) ;
```

### Redirecting Requests

```js
const http = require('http') ;
const fs = require('fs') ;

const server = http.createServer((req,res) => {
    const url = req.url ;
    const method = req.method ;

    if (url==='/'){
        res.setHeader('Content-Type', 'text/html') ;
        res.write('<html>') ;
        res.write('<head> <title> First page </title></head>') ;
        res.write('<body><form action="/message" method="POST"><input type="text" name="msg"><button type="submit">Send</button> </form></body>') ;
        res.write('</html>') ;
    return res.end();
    }
    if(url==='/message' && method === 'POST'){
        fs.writeFileSync('./message.txt', 'DUMMY');
        res.statusCode=302
        res.setHeader('Location', '/');
        return res.end()
    }
    res.setHeader('Content-Type', 'text/html') ;
    res.write('<html>') ;
    res.write('<head> <title> First page </title></head>') ;
    res.write('<body><h1>Hello fro my Node.js Server</h1> </body>') ;
    res.write('</html>') ;
    res.end();
})

server.listen(3000) ;
```

#### Streams and Buffers
the request is simply read by Node in **chunks**
	stream ---Request part 1---Request part 2-- ... --> Fully Parsed

**buffer** is a construct which allows you to hold multiple chunks and work with tem before ther are released.

`req.on('<event>', <functionThatWillBeExecuted>)` it turns on some listener e.g. `req.on('data', (chunk) => { ... })` (data event will be firefd whenever a new chink is ready to be read)















----

## Response object

```js
const http = require('http') ;

const server = http.createServer((req,res) => {
    console.log(req.url, req.method, req.headers) ;
    res.setHeader('Content-Type', 'text/html') ;
    res.write('<html>') ;
    res.write('<head> <title> First page </title></head>') ;

    res.write('<body><h1>Hello from my Node.js Server</h1> </body>') ;
    res.write('</html>') ;
    res.end();

})

server.listen(3000)
```














