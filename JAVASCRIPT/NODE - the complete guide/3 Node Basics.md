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
and then you will see in the cons



















