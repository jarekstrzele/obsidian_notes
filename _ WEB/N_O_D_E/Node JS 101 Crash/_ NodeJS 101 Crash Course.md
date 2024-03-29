#youtube  #node #javascript  
#zero_to_master 
https://www.youtube.com/watch?v=fUJ3ULyyA-Y

-----------
[[1. synchronous vs asynchronous]]
[[2. what is node.js best at]]
[[3 Observer design pattern]]

------
[[#REPL Read Eval Print Loop]]
[[#VS Code]]
[[#global]]
[[#Node vs JS]]
[[#Backend vs Frontend]]
[[#What does Node.Js Do?]]
[[#Node internals Deep Dive]]
[[#`libuv` internals deep dive]]

---
# REPL Read Eval Print Loop
```node
$ node
Welcome to Node.js v16.20.0.
Type ".help" for more information.
> hello
Uncaught ReferenceError: hello is not defined
> console.log("hello")
hello
undefined
> .exit
> 

```

It is good for quick testing

# VS Code
plugin:
- intellicode
- 

# global
## process
### `process.argv`
```node
$ node
> process.argv
[ '/home/jarek/.nvm/versions/node/v16.20.0/bin/node' ]
```


```js
const mission = process.argv[2] ;

if (mission === 'learn') {
        console.log('Time to write some Node code!');
} else {
        console.log(`Is ${mission} really more fun?`) ;
}
```

```node
$ node hello.js learn
Time to write some Node code!

$ node hello.js explore
Is explore really more fun?


```

------
# Node vs JS
JavaScript
JS code -> JS engine -> Browser (`window`)

NodeJs - (`global.process`, `global.console.log("eh"`)

DINO - JS runtimes that use V8 engine similarly to node.js

------
# The global object
https://nodejs.org/docs/latest-v16.x/api/globals.html

browser | node 
---  | ---
window | global
document | process
history | module
location | `__filename`
navigation | require()


-------
# Backend vs Frontend

the language to send **request** and **response** is *http*/*https*

frontend | backend
-- | --
client  | server
what you see on the screen as a user | what happens behind the scenes ; security features, input validation, business logic
www.google.com ("hi server, can you give me data?"" **REQUEST**) | **RESPONSE** "sure, here it is data to display the web page" `JS, HTML, CSS` ora `JSON, TXT, XML`

**back-end** 
- serves us the data that we need on the front-end  on the client side to show something useful to the user 
- does things that we can't do on the front-end side (security logging, input validation., ...)

--------
# What does Node.Js Do?
- it has a *V8* engine to run JavaScript codes
- is is the entire environment
	- maths
	- get args
	- ...
 so 
 
![[NODEJS-inside.excalidraw | 800]]

JS code -> NODEJS -> User Output

------
# Node internals Deep Dive
Node project is hosted by GitHub
In GitHub - important folder:
- `lib`     (JavaScript)(`pocess, console, fs, path ,...` - `.js`)
- `src`    (C++, low level, NodeJs Bingings; e.g. in `fs.js` from lib you can find `binding.open()` function -that function convert the values between JS in fs  module  and C++; in folder `src` you find `node_file.cc`, this is a C++ code)   

--------
# `libuv` internals deep dive
http://libuv.org/
This library is connected with JS by `binding`. Other languages ca use `libuv`
Python, C#, PHP, Go, R, Haskell, Delphi , ...
"tokio" biblioteka zapewnia wydajny model programowania asynchronicznego dla Rusta

https://github.com/libuv/libuv
`/src` folder in subfolder `unix` you find `fs.c`
































