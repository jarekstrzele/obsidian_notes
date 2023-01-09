#plurasight  #react  #house_cory

# React the big picture

## Why React?
2011 created by Facebook
2013 Open Sourced
2015 React Native
2016 React 15 released


### Flexibility
- React is a library
- where cat I use React:
	- web apps
	- static sites
	- Mobile
	- Desktop
	- server-rendered  
	- vritual reality
- React is highly versatile because the rendere is separate from React itself
	- in web apps you call `react-dom` to render your components to HTML
	- in mobile apps you call r`eact-native` to render React components into native-friendly code
	- in BR apps you use `react-vr`
	- render in servers:
		- `ReactDomServer.renderToString()`
		- libraries to render: NEXT.js, Gatsby, Phenomic
	- there are more different renderes


### Developer Experience
- React offers a simple API that's easy to learn
- to learn check a docs

#### component
```javascript
import React from 'react';

//component by function
function HellowWorld(props){
	retunr <div> Hello {props.name} </div>
}
//component by class
class HelloWorld extends React.Component{
	render() {
	//          this is JSX
		return <div>Hello {props.name} </div>
	}
  }

```

#### JSX
#jsx
`React.createElement(tag, {atribut}, content)`

`React.createElement("h1", {color: "red"}, "Heading")`
-- into html -->
`<h1 color="red">Heading</h1>` 

#### to create app
`create-react-app app_name` --> it creates a full working development environment  on my machine
`npm start` starts server on my machine

ONLINE
condeSanbox
https://codesandbox.io/

### Corporate Investment
`codemode` - a tools to update your code to the newest React

### Community
*Material-UI* - components from Google
*Fabric* - components from Microsoft
*React Bootstrap* - components to work with bootstrap
...

ECOSYSTEM
- *React Router*  - routers
- *Redux, Mobx* - to handle complex data flows 
- *Jest* to autmate tests
- *GraphQL* - Restful API, your API calls on the client
- *NEXT.js* React with Node
....


### Performance
Updating the DOM is expensive!!
Without Virtual DOM - Blindly update DOM using new state

With Virtual DOM
Update the DOM in the most efficient way.
- ==Avoids layout thrash== -> Saves battery and CPU
- enables simple programming model

**Inferno** an extremely fast Reack-like JAvaScript library for building modern user interfaces.
https://www.infernojs.org/


**PREACT** is even smaller than Inferno
https://preactjs.com/


### Testability
To test:
- little to no cinfig required
- run in-memory via Node
- Fast
- Reliable, deterministic unit tests
- easy to update
- no side-effect (pure function)
- 
Libraries:
- Mocha
- Jasmine
- Tape
- QUnit
- AVA
- Jest - the most popular!!!
- 

## Tradeoffs

### framwork vs library
FRAMEWORK
- Angular, ember
- less decision fatigue
- less setup overhead
- more cross-team consistency

LIBRARY
- React
- light-weight
- springle on existing apps
- pick what you need
- chest best tech
- 

xxx | React | Angular
---|:---:|:---:
Components | V | V
Testing | Jest, Mocha | V
HTTP library | Fetch, Axios | V
Routing | React router | V
I18n | react-intl | V
Animation|react-motion | V
Form validation | react-forms | V
CLI | create-react-app|angular-cli

### concise vs explicit
Two-way binding:
- less coding
- automatic

One-way bindinh (REACT)
- more control
- more explicit
- more code
- eeasy to debug

### Template-centric vs JavaScript-centric
In Vue, Angular, Ember "JS" in HTML (learn their unique syntax)

In REACT "HTML " in JS (learn JS)


### Separate Template vs Single File per component

#### MVC (Model View Controller)
Model -> JS
View -> HTML, CSS
Controller -> JS
Each technology is separated

#### React
Component -> JS & JSX
Each component is separated
Componenets:
- Button
- atepicker
- Accordion
- TextInput
- ...
Think of component composition like Russion dolls. React's component model works the same way (simpe components can be composed together to build rich one)
Think of the page as a set of nested components.

### Standard vs Non-standard
Use non-standard (React, Angular, ...).
Standard web components are old, not supported by all browser, ....

### Community vs Corporate Backing
React is driven by FB's needs.
but React has 1,000 contributors
50,000 components in prod

----
## Why not React?

### HTML and JSX differ
HTML | JSX
--- | ---
`for` | `htmlFor`
`class` | `className`
`<style color="blue">` | `<style={{color: 'blue'}}`
`<!--Comments-->` | `{*/Comments /*}`

#### to convert HTML to JSX
online compiler
https://htmltojsx.com/


htmltojsx on npm 
comand line tool

### Build Step Required
With any JS libraries:
1. Minify - your code to save bandwithd
2. Transpile - your code so that you can use
3. Test and lint
TRANSPILERS: *Babel*, *TypeScript* (translate JSX -> HTML)

### Version Conflicts
You can't run two versions of React at the same time on the same page.
so
All components have to be on the same version for given page.

==Tips to avoid conflicts:==
- standardize on a version
- upgrade React when upgrading libraries
- upgrade as a tean
- 

### Old stuff Online
Old
- `import {render} from 'react';`
- `React.createClass`
- `import {PropTypes} from 'react';`
New
- `import {render} from 'react-dom';`
- `var crc = require('create-react-class');`
- `import PropTypes from 'prop-types';`

docs, docs, docs

### Decision Fatigue

#### Dev environment
use:
`create-react-app` or `create-react-native-app`

#### Classes or functions
Most people prefer functions


#### Types
three popular ways to handle types"
- *PropTypes* (check at runtime)
- *TypeScript* (check compile time)
- *Flow* is a static type checker for Javascript

Use PropTypes (25%) or TypeScript (55%)

#### States
**state** - is app data
- Plain React
- Flux
- redux
- MobX (observable State)

React handles stComponents handle state on their own
==Redux== 
- is the most popular state management librar for working in React
- centralized state 

#### Styling
- CSS-in_JS (43%)
- Plain CSS/Sass/Less (34%)





















