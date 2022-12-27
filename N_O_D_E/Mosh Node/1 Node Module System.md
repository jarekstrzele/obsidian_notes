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

function log(ms)
```














