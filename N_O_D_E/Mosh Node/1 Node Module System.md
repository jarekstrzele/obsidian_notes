[[_ 0 Node (Mosh)]]

# Global objects

## in node `global`
- `console.log();`
- `setInterval()
- ....

`globale.console.log`, `global.setInterval`, ....

BUT:
```js
var msg = '';
console.log(globale.msg) ; // -> undefined
```
because `msg` is visible only in tha file not globaly



## in browser `window`
in a browser global objects are hidden inside the `window` object: `window.console.log`, `window.setItnerval`, ....


# Modules
==Every file in a Node app is considered a MODULE==

You have to export variables, functions, ...  explicity
`console.log(module)`


## Create a module
logger.js
```js
var url = 'http://mylogger.io/log';

function log(msg){
//send an HTTP request
 console.log(msg);
}
print(module);

module.exports.log = log;
// module.exports.endPoint = url;
```
if you want to export only single function:
`module.exports = log ;`
than in the app.js: `logger("some message")`


## Load a module
app.js
```js
const logger = require('./logger') ;
console.log(logger) ;

logger.log("some info") ;

```

## Module Wrapper Function
Node wraps w module inside the function
```js
(function (exports, require, module, __filename, __dirname){
	 var url = 'http://mylogger.io/log';

	function log(msg){
		//send an HTTP request
		console.log(msg);
}
	module.exports = log;

}) ;
```


## Path Module

```js
const path = require('path') ;
var pathObj = path.parse(__filename);
console.log(pathObj) ;
```

```bash
PS C:\Users\jarek\Prog\NODE> node .\moshmodule.js
{
  root: 'C:\\',
  dir: 'C:\\Users\\jarek\\Prog\\NODE',
  base: 'moshmodule.js',
  ext: '.js',
  name: 'moshmodule'
}
```


## OS Module
```js
const os = require('os') ;
var totalMemory = os.totalmem() ;
var freeMemory = os.freemem();
console.log(`Total Memory ${totalMemory}, freeMemory ${freeMemory}`)
```

```bash
PS C:\Users\jarek\Prog\NODE> node .\moshmodule.js
Total Memory 29909643264, freeMemory 15869329408
```


## FileSystem Module
[[_0 Node Complete Guide#First app]]

### Sync
```js
const fs = require('fs') ;

const files = fs.readdirSync('./') ;

console.log(files);
```

```bash
PS C:\Users\jarek\Prog\NODE> node .\moshmodule.js
[
  'first.js',
  'hello.txt',
  'message.txt',
  'moshmodule.js',
  'server.js'
]
```

### Async
> all asynchronous methods take a function as their last arg. Node will call this function  when that asynchronous completes -- this function is *call back*
> 

```js
const fs = require('fs') ;

const files = fs.readdir('./', function(err,  files){
    if (err) console.log("Error ", err)
    else
        console.log(files) ;
}) ;
console.log(files);
```


```bash
PS C:\Users\jarek\Prog\NODE> node .\moshmodule.js
undefined
[
  'first.js',
  'hello.txt',
  'message.txt',
  'moshmodule.js',
  'server.js'
]
```


## Event Module

>[!info] EVENT
>A signal that something has happened

### EventEmitter
```jsx
const EventEmitter = require('events') ;
const emitter = new EventEmitter();

//Register a listener
emitter.on('messageLogged', ()=> console.log('Listener called')) ;

// Raise an event
emitter.emit('messageLogged') ;
```

```bash
PS C:\Users\jarek\Prog\NODE> node .\moshmodule.js
Listener called
```

### Event args
When we want to send some data

































