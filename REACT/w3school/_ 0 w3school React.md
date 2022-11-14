
[[1 ES6]]
[[2 React Render HTML]]
[[3 JSX]]
[[4 React Components]]
[[4.1. React Class Components]]
[[5 React Props]]



---

# Intro React
#react
>__React__ :
>- is a JavaScript library for building user interfaces
>- is used to build single-page  applications
>- allows us to create reusable UI components
- you need Node.js 
- to `create-react-app appName`  to create React apps
-  `npm start` to start a React app

> React creates a VIRTUAL DOM in memor.
> React only changes what needs to be changed.

React is created by Facebook by Hordan Walke.

To use React in production, you need npm which is included with Node.js.

---
## For testing:
The first two ler us write React code in our JavaScript.
The third, Babel, allows us to write JSX syntax and ES6.


```html
<!DOCTYPE html>
<html>
  <head>
    <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  </head>
  <body>

    <div id="mydiv"></div>

    <script type="text/babel">
      function Hello() {
        return <h1>Hello World!</h1>;
      }

      ReactDOM.render(<Hello />, document.getElementById('mydiv'))
    </script>

  </body>
</html>

```

For __production__ you need to set up a __React environment__.
`npx` + `Node.js`

### to create an app
To create a React application named _my-react-app_:
`npx create-react-app my-react-app`

### to run the app
`cd my-react-app`
`npm start`

The app file `App.js` in `src` folder.
 
---
index.js:
```js
import React from 'react';
import ReactDOM from 'react-dom';

const myfirstelement = <h1>Hello React!</h1>

ReactDOM.render(myfirstelement, document.getElementById('root'));
```










