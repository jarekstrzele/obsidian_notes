#javascript/express

[[_0 Node Complete Guide]]
Server logic is complex, but you want to focus on your Buisness Logic, not on the nitty-gritty Details

>[!info] FRAMEWORK
>helper functions, tools, rules that help you build your application

Alternatives to Express.js: Vanilla Node.js, Adonis.js, Koa, Sails.js

# install
`npm install --save express` 

```js
const express = require("express")
const app = express()

app.listen(8080, ()=>console.log("Server is running on 8080"))
```


# Middleware

![[middleware]]

==Express is all about middleware ==

>[!info] moddleware
>it means that an incoming request is automatically funneled through a bunch of functions

![[middleware_Draw.excalidraw| 700 ]]


`app.use( (req, res, next)=> {} )` will be executed for every incoming request and this function will receive three arguments:
- `req`
- `res`
- `next` - it is a function that will be passed to this function by expressjs, it allows the request to continue to the next middleware in line











