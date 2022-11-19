<<<<<<< HEAD
[[REACT/plurasight/React 17 Getting Started/_ 0 Getting Started]]
=======
[[REACT/plurasight/React 17 Getting Started/_ 0 Getting Started]]
>>>>>>> remotes/origin/master


---
# The basics

## Why React?

>[!React]
>a JavaScript library for building user interfaces

**library** - small
**build user interface** - descripe what you want as a UI, React is DECLARATIVE for dynamic data(HTML is declarative for static content)

React plus:
- performance
- just JS
- mobile app (React Native)
- Battle-tested
- ==Declarative language (model UI and state)==
- 

## React's Basic Conepts
1. **Components**
	1. like functions
	2. Input: props (immutable), state | Output: UI
	3. Reusable and composable
	4. <Component />
	5. Can manage a private state
	6. types:
		1. function component
		2. class component
2. **React updates**:
	1. When the state of React component (the input), changes, the user interface it represents (the output) changes as well
	2. React will simply reacts to the changes in a component's state and automatically update the PARTS of the DOM that need to be update
3. **Virtual views in memory**:
	1. generate HTML using 
	2. No HTML template language
	3. Tree reconciliation (virtual DOM)
4. 

---
## First app
https://jscomplete.com/playground
`document.getElementById("mountNode").innerHTML = "hell";`
ctr+enter -> execute
Extention for Chrome `React`

https://jscomplete.com/playground/rgs1.1
```javascript
// simple React component named 'Hello'
// It's a pure component (has no input)
function Hello() {
	// return JSX
	// JSX will be executed by the JSX extension and compiled to something else that the browser can understand
	// Babel a special compuler converts JSX into React API calls
	return <div>Hello React!</div>;
}

// To display component in a browser we need
// to instruct the ReactDOM library on how to do that
// function below takes two args
// the first is the component to render
// the second one is the DOM element in the browser where we wish The React component to show up
ReactDOM.render(
  // '<Hello />' is a JSX
  // '<Hello />' <=> 'React.createElement(Hello, null)'
  <Hello />, 
  document.getElementById('mountNode'),
);
```

BABEL
#babel
https://babeljs.io/

`https://babeljs.io/` 
-->
`React.createElement("div", null, "Hello React!");` <- React API calls

`React.creactElement(tag, attr, content/child_of_the_tag)`

---
>[!important!!!]
>Always name your components with an uppercase first letter!

```javascript
function Button() {
	return <button>TEST </button>;
}

ReactDOM.render(
  <Button />, 
  document.getElementById('mountNode'),
);
```

### State object
We want to increment a counter every time it's clicked => we need a ==STATE OBJECT==

To use a state object React has a special function `useState()` (it returns an array so you can use ARRAY DESTRUCTURING)
Our useState() results:
- state object (getter)
- updater function (setter)
`const [counter, setCounter] = useState(0);`

> [!important] Structure of  `useState`
> `const [currentStateValue, functionToSetNewStateValue] = useState(initialStateValue)

React support `{expression}` syntax!!!!
`return <button onClick={functionRef}> {expression} </button>`
It can be a function inside the `{}`
`return <button onClick={() => 'something_to_do'}> {expression} </button>`

```javascript
function Button() {
  const [counter, setCounter] = useState(0);
	return <button onClick={() => setCounter(counter+1)}> {counter} </button>;
}

ReactDOM.render(
  <Button />, 
  document.getElementById('mountNode'),
);
```


The function `useState` is called a hook in the react world

some improvments:
```javascript
function Button() {
  const [counter, setCounter] = useState(0);
  const handleClick = () => setCounter(counter+1);
	return (
    <button onClick={handleClick}>
    {counter}
  </button>
    );  
}

function Display(){
  return (
    <div> ... </div>
  )
}

//App
function App(){
  return (
  <div>
      <Button />
      <Display />
  </div>
  );
}


ReactDOM.render(
  <App />, 
  document.getElementById('mountNode'),
);
```


### One-way Data Flow
counter value as a Display message (click on the component button will change the display component)

>[!State]
>The state in a React component can be accessed only by that component itself and no one else

so  move `counter` to the parent (`App`)
How `Display` can have an access to the value of `counter`? (We need to flow the value of the counter state into the Display component --> a props object)

#### Prop object
#props
To pass a prop to a component, you specify an attribute here, just like in HTML
`<Display message={counter}` -> now the `Display` can use its props object to, which is an arg of the function (All function components receive this object even when they have no attributes)

>[!One-way flow data]
>Parent components can flow their data down to children components.
>Parent components can also flow data down behavior to their children.


>[!Where to define the state?]
>Down in a tree as close as posiible to the children who need to access that value on the state

```javascript
function Button(props) {
 return (
    <button onClick={props.onClickFunction}>
    +1
  </button>
    );  
}

function Display(props){
  return (
    <div> {props.message} </div>
  )
}

//App
function App(){
  const [counter, setCounter] = useState(0);
  const incrementCounter = () => setCounter(counter+1);
  return (
  <div>
      <Button onClickFunction={incrementCounter}/>
      <Display message={counter} />
  </div>
  )
}

ReactDOM.render(
  <App />, 
  document.getElementById('mountNode'),
);
```

----------
### Components Reusability
```javascript
function Button(props) {
 const handleClick = () => props.onClickFunction(props.increment) 
 return (
    <button onClick={handleClick}>
    +{props.increment}
  </button>
    );  
}

function Display(props){
  return (
    <div> {props.message} </div>
  )
}

//App
function App(){
  const [counter, setCounter] = useState(0);
  const incrementCounter = (incrementValue) => setCounter(counter+incrementValue);
  
  return (
  <div>
      <Button onClickFunction={incrementCounter} increment={1}/>
       <Button onClickFunction={incrementCounter} increment={5}/>
       <Button onClickFunction={incrementCounter} increment={10}/>
       <Button onClickFunction={incrementCounter} increment={100}/>
      <Display message={counter} />
  </div>
  )
}


ReactDOM.render(
  <App />, 
  document.getElementById('mountNode'),
);
```

------
## Tree reconciliation in Action
React algorthms:
- it only regenerates in its DOM node what actually needs to be regenerated
- it keeps everything else the same
































