#udemy #node #Maximilian_Schwarzmuller  

>[!note] Node
>It is a javascript runtime.
>It use V8 (a javascript engine  built by Google that runs JS in the browser)
>	- V8 complies a js code to Machine Code
>	- V8 is written in C++
>- Node add some new feature to the V8 (for example working with local files )
>
 
VS Code:
- material icon 

## First app
- make a new file.js
- in the terminal `node thatfile.js`

to act with the system file `const fs = require('fs')`
```js
const fs = require('fs') ;

fs.writeFileSync("hello.txt", "Witam z pliku wygenerowanego przez Node fs") ;

console.log("done") ;
```
----
==WE USE NODE TO RUN A SEVER CODE== BUT NODE IS SOME MORE THAN JUST ONLY server

NodeJS  Role (in Web Dev):
	- **run server** 
		- create  server & 
		- listen to incoming Requests
	- **business logic** 
		- handle requests
		- Validate input
		- connect to DB
	- **response**
		- return responses
			- render HTML
			- render JSON
			- ...



