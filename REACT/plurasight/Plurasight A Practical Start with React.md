#react  #plurasight  #guijt_roland

---
# Practical Start with React

## Intro
### element tree
```html
<div class="split">
<input />
<p> Sunday 4:00
pm</p>
</div>
```
React doesn't use HTML directly. It uses a tree of JS objects to define the UI
```javascript
React.createElement(
 "div",
 { className: "split"},
 React.createElement("input"), 
 React.createElement("p", null, "Sunday 4:00pm")

);
```
THis tree is then used to create the HTML that the browser will undersand

## Tree reconciliation
React comares the two trees (new (with 4:01pm) and old (with 4:00pm)), and instructs the renderer to only redraw the element that changed (4:00->4:01)


## JSX
Its syntax is easier for human brain. The JS code above will be:
```jsx
<div className="split">
<input/>
Sunday 4:01pm
<p>
</div>
```

#babel
Babel is specialized in converitng one syntax to another. It can translate this JSX code to JS code.


### The react Workflow
1. you write a code in ==JSX== to define a UI
2. ==Babel== translate this code into JS (e.i. with React.createElement)
3. Each time the app has to render to the browser ==ReactDOM== (JS library) uses this elements to generate the HTML elements for the browser in a way that only the updated elements are rendered

### Components
>[!React]
>- React is a javascript library to create and compose components.
>- React App is a composition of components with top-level component often called `app`

Each component has a NAME and has THREE disctict CHARACTERISTICS:
	- It can accept INPUT from other components by using what is called PROPS (in JSX they are written like HTML attributes)
	- it can maintain an INTERNAL STATE
	- it knows how to RENDER ITSELF


REACT:
- components
- library
- Facebook
- MIT
- 1 way data-binding
- UI in JavaScript

--------
# 3 Getting Ready

- install nodejs
- install npm `npm install npm@latest -g`
- `mkdir ReactApps` `cd ReactApps`
- `npx create-react-app globomantics `
It configures a complete envirenment to develop in 

> for the lastest version of node `sudo n latest`
#node/latest_version

- start development web server by typing `npm start` (`start` is a script that gets executed by npm )
```hsell
  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd globomantics
  npm start

Happy hacking!

```

`cd globomantics`
`npm start` 'start' is a script that gets executed by npm

#webpack
Webpack is a smart bundler that packages up our components

----
## Production
to build an app in a production mode (without debug information)
`npm run build` -> creates a build folder which contains everything that is needed to run the app on a web server 

----
~~chrome debug - extention for VS Code~~
In VS Code > Run Debug button > create a lauch json choose 'chrome'
and  change ` "url": "http://localhost:8080",` onto ` "url": "http://localhost:3001",` and run -> a new instance of React app starts

## Reat Developer Tools 
Chrome>more tools>extentions>chrome web store 
add `React Developer Tools` #react/chrome
inspect>component

------------
# Application Structure

## `public` folder
Everything that is in public will not be processed by Webpack.

content:
- favicon.ico
- index.html
	- it is a template
	- it has `href="%PUBLIC_URL%/..."`
	- it can refrence all files that oare in the public folder
- manifest.json
- ....
- 

>
>all content will be copied to the output folder untouched!
>

## `src` folder
everything that is in the src folder will be processed by Webpack and made available to it.

What Webpack does?
`npm start `
> Webpack bundles all JavaScript contained in the `src` folder
> It allows to import also CSS, images 


`main.chunck.js` => application code
`vendor-main.chunk.js` => library code
`bundle.js` => module logic

## Entrypoint
`index.js` is a entrypoint

`import './index.css'` the symbol `./` is necessary, becuse `index.css` is in the same folder as `index.js` and Webpack knows that has to look for this file in this folder

`import React from 'react'` there is no `./` because `react` is installed as a npm package with a specifified name and Webpack looks for `'react'` in these packages


ACTUAL ENTRYPOINT in `index.js`:
```javascript
ReactDOM.render(
	<React.StrictMode>
	<App/>
	</React.StrictMode>,
	document.getElementById('root')
);
```
`ReactDOM` is an object that was exported from the `react-dom` module

**render**:
- the first arg of `render` specifies the top-level component of our app that should be rendered
- the second arg is an HTML element where the App component should be render in (in `index.html` there is a `div` with `id='root'`)
 
## Module
module.js:
```javascript
class component{
	doSomething() {
	}
}

export component;
```

anotherModule.js
```javascript
import {component} from "./module"

component.doSomething()
```


#### **default**
module.js:
```javascript
class component{
	doSomething() {
	}
}

export default component;
```

anotherModule.js
```javascript
import comp from "./module"

comp.doSomething()
```

#### **mix**
module.js:
```javascript
class component{
	doSomething() {
	}
}
const x = 10;
export default component, x;
```

anotherModule.js
```javascript
import comp, {x} from "./module"

component.doSomething()
console.log(x)
```

## The root component
index.js
```javascript
...
import App from  './App'; // App is a default value because there are no { }

ReactDOM.render(
	<React.StrictMode>
		<App />
	</React.StrictMode>,
	document.getElementByUd('root')
);
```
the root component is `<App />`, but before it there is a `<React.StrictMode` component that is responsible to warn us about potential problems in the code 

`App` is imported from `App.js`

`App.js`:
This component itself is a function, which is typical for a React component
```javascript
...

function App(){
	return (
		<div className="App">
		...
		<img src={logo} ...
		
	);
}
```
the function return JSX
`<img src={logo} ...` `src` is not HTML attribute but this ia a `prop`  (something that hte component gets as an argument)

## Importing External Modules
e.g.
`npm install bootstrap@5`
now in `index.js` you have to import bootstrap
`import 'bootstrap/dist/css/bootstrap.min.css'` now bootstrap will be available in all child components in the hol app

## Placing Components in Folder
- in the `src` folder create a subfolder (e.g.) `main-page`
- move `App.css`, `App.js`,  `logo.svg` to this subfolder
- rename `App.js` to `index.js`
- in main `index.js` change importing path for `App` (`App` is a name of function in renamed file `index.js`)
`import App from './main-page';` (Webpack wiil automatically understand that it has to use the `index.js`)
- change name of css file to `main-page.css` (remember to also  change the name in `import` statement)

----
# COMPONENTS

## a simple component
adding a header to the main page
- in the subfolder `main-page`
	- add file `header.js`
	- add logo from the course source

header.js
```javascript
import logo from "./GloboLogo.png"

const Header = () => (
    <header className="row">
        <div className="col-md-5">
            <img src={logo} className="logo" alt="logo" />

        </div>
        <div className="col-md-7 mt-5 subtitle">
            Providing houses all over the world
        </div>
    </header>
)

export defaul Header;
```

a new content oc main-page.css
 now you can import `Header` in the main `index.js` in subfolder `main-page`
 clear the function `App`:
 ```javascript
 function App() {
  return (
    
  )
}
```
 add new content
 










