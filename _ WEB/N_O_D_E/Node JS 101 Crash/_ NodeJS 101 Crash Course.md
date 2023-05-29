#youtube  #node #javascript  
#zero_to_master 

https://www.youtube.com/watch?v=fUJ3ULyyA-Y

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

frontend | backend
-- | --
client  | server
what you see on the screen as a user | what happens behind the scenes ; security features, input validation, business logic
www.google.com ("hi server, can you give me data?"" **REQUEST**) | **RESPONSE** "sure, here it is data"

