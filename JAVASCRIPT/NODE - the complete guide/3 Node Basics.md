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
- 
```jsx
const http=require('http');

http.createServer()
```











