#react 
[[1 ES6 refresher]]



----

# React
***component** is essentially a piece of the UI

## a react app
- is a tree of components
- is built of independent, isolatedm reuable components

## NodeJS
 `sudo npm i -g create-react-app@1.5.2 `

## VS Code
plugin: 
- simple react snippet
- Prettier - Code formatter ; > VS Code settings `editor.formatOnSave: true`

## Create APP
`create-react-app react-app`

## Run APp
`npm start`

## Babel:
`const element = <h1> Hello Wolrd </h1>` --- babel ---> `var element = React.createElement("h1", null, "Hello World");`

## an App from  scrach
`react-app` > `src` > create `index.js`
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

const element = <h1> Hello worl </h1> ;
ReactDOM.render(element, document.getElementById('root'))
```
there is `index.html` with `<div id=root ...`

---
## Config
`package.json`



