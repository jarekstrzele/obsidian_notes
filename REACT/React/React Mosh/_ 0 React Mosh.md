#react #mosh 

[[2 ES6 Refresh]]
[[3 Components]]
[[3.1 Component vidly project]]
[[4 Composing Components]]





---
# React Intro Mosh

**component** a piece of the UI:
- independent
- isolated
- reusable
- it is a JS class:
	- `states = {}`;
	- `render(){}` describes how UI should look like
		- the output of this method is a ==React Element== (it is a JS object that React maps to a DOM element)
		- React keeps a lightweight representation of the DOM in memory  ==Virtual  DOM===

Programming in React: composing components 
Every React application has a root component `APP`; it contains others child components
Every React App is a tree of components

> REACT reacts to state changes

## INSTALL:
- nodejs
- npm
- `sudo npm -i -g create-react-app@1.5.2` it is a package to create a new React app #react/create
- VS Code: Simple React Snippets, Prettier (Settings>`editor.formatOnSave: true`)


## First app

`npx create-react-app app_name`
`create-react-app react-app` - will be installed:
- development server
- webpack (bundling files)
- Babel for compiling our JS code

in the folder of app (`react-app`) `npm start` it launch development server on 3000 port

**structure**
- `node_modules`
- `public`  assets of our app (favicon, index.html )
- `src` basic component - `App.js`
our code JSX --> Babel --> code that a browser can understand (JS code)
https://babeljs.io/repl

JSX | JS
---| ---
`const element = <h1> Hello </h1>;` | `"use strict"; var element = React.createElement( "h1", null, "Hello");

- `index.js` entrypoint 

`ReactDOM.render(what_element, where_render_this_element)`
e.g.
`ReactDOM.render(element, document.getElementById('root'))`


### first `index.js`
```javascript
import React from 'react'; // allows Babel to convert JSX to JS
import ReactDOM from 'react-dom';

const  element = <h1>Hello World</h1>;
ReactDOM.render(element, document.getElementById('root'))


```


## Custom Configs
#react/config

in `package.json`:
```json
...
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  ...
```
`eject` this command is responsible for configuration

## Full-stack Architecture

CLIENT, Front-end
- basically the UI (what the user sees and interacts with)
- React
	/ \
	 |
 HTTP
     |
    \\ / 
SERVER, Back-end
- basically storing and processing the data
- Node + Express or Firebase (from Google)



