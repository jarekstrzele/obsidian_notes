#react 
[[_ 0 React Full]]


# React Basics

React makes building complex, interactive and reactive user interfaces simpler

React is all about "Component", because all user interfaces in the end are made up of components:
- reusability --> ==don't repeat yourself==
- separation of concerns -->  ==don't do too many things in one and the same place (function)==

## How is a component built?
We combine HTML, CSS and JS in all these components and then we combine all of theses components together  to build the entire user interface

> [!important] In React you define the desired target state(s) and let React figure out the actual JS DOM instructions


# To start a project
### `create-react-app`

```bash
$ npx create-react-app my_app
$ cd my_app
$ npm start
```

In your project folder:
```bash
$ npm install # to install dependencies from package.json
			  # => new folder node_modules
```

Sturcture of project
`App.jsx`
`index.css` (you can't import css into "normal" JS code)
`index.jsx` it wil be injected into the html file
`package.json` some important dependecies

index.jsx
```jsx
//...
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```
`App` it is a React component!


>
>`index.html` is in `public` folder  (SPA, Single Page Application), this is the place where React-driven user interface should be rendered
>

`App.jsx`
```jsx
function App() {
	return (
		<div>
			<h2> Let's get started</h2>
		</div>
	)
}

export default App;
```


## JSX
JSX stands for JavaScript XML.


## How does React work?

React allows you to create re-usable and reactive components consisting of HTML and JavaScript (and CSS)  => Declarative Approach  => Define the desired target state(s) and let React figure out the actual JavaScript DOM instructions.


## Build a First Custom Component
Add a new folder  `components`.

Component Tree
![[React Component Tree.excalidraw | 500]]

In `components` folder create a new JS file, it will be a new component (naming file: PascalCase, a name of a component the same as the file name (this is convention))

>[!important] Component
>A Component in React is just a JavaScript function!!
>It returns JSX code.
>To use it, you have to export it.

ExpenseItem.js
```jsx
function ExpenseItem(){
	return <h2> Expense Item </h2>
}

export default ExpenseItem;
```

in `App.jsx`
```jsx
import ExpenseItem from './components/ExpenseItem';

function App(){
	return (
		<div>
			<h2> Let's get started </h2>
			<ExpenseItem />
		</div>
	)

}
```

SETPS:
1. Create a component
2. Export the component
3. Import it in the file where you want to use it


---
## More complex component

>[!important] GENERAL RULE
>There is only ONE ROOT  element per return statement/per JSX code

for example:
with error:
>[!bug]
>```jsx
>function App(){
>	return <div> Sth </div>  <p> Sthh </p>   <div> another </div>
 >}
>```

----
Why?
This JSX code will be translate to JS code in that way:
```JSX
<h1 className="a class name"> ...text... </h1>
```

```js
React.createElemen('h1', {className: 'a class name'}, '... text ...');
```
---

To fix this bug wrap your JSX into one HTML tag

```jsx 
function App(){
  return (
  <div>
    <div> Sth </div>
    <p> Sthh </p>
  <div> another </div>
  );
}
```

Now change your ExpenseItem file:
ExpenseItem.js
```jsx
function ExpenseItem(){
	return (
	<div>
		<div> 01.09.2022 </div>
		<div>
			<h2> Lapton Legion </h2>
			<div> 5134 PLN </div>
		</div>
	</div>
	);
}

export default ExpenseItem;
```


## Some Styling - CSS
There will be good if the name of a component file will be the same as a CSS file.

In the component file you have to import its CSS file
```jsx
import './ExpenseItem.css';

function ExpenseItem(){
  return (
  <div className="container">
		<div> 01.09.2022 </div>
		<div>
			<h2 id="description"> Lapton Legion </h2>
			<div className="price"> 5134 PLN </div>
		</div>
	</div>
   )
}
      
export default ExpenseItem;
```

ExpenseItem.css
```css
.container {
   display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
  padding: 0.5rem;
  margin: 1rem 0;
  border-radius: 12px;
  background-color: #99c1f1;
  
}

.price {
  font-size: 1rem;
  font-weight: bold;
  color: white;
  background-color: #40005d;
  border: 1px solid white;
  padding: 0.5rem;
  border-radius: 12px;
}

#description {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: flex-end;
  flex-flow: column-reverse;
  justify-content: flex-start;
  flex: 1;
}
```

## Dynamic data
> Components have to reusable!!!! 
> You can't hard code data!!

ExpenseItem.jsx use `{ expression }`:
```jsx 
//...
/h2>
			<div className="price"> {200+12} PLN </div>
//...
```

a simple example
```jsx
import './ExpenseItem.css';

function ExpenseItem(){
  const expenseDate = new Date(2022,10,10).toString();
  const expenseTitle = 'Legion';
  const expenseAmount = 5678;
  
  return (
  <div className="container">
		<div> {expenseDate} </div>
		<div>
			<h2 id="description"> {expenseTitle} </h2>
			<div className="price"> {expenseAmount} PLN </div>
		</div>
	</div>
    
 )

}
       
export default ExpenseItem;
```

## Passing Data via "props"
#react/props 

> [!warning]
>Components can't just use data stored in other components.
>e.g. Parent stores `a='some data'` but child can't have direct access to this variable `a`
>You can use ==PROPS== :
>	- you can pass data to the custom component  by adding a attribute 
>	- inside of that component you can get access to all these attrs

In App.jsx add inside the component dummy data:
```js
// ...

export default function App() {

const expenses = [
  { id: 'e1',
    title: 'Toilet paper',
    amount: 10,
    date: new Date(2022,11,10).toString(),
  },
  { id: 'e2',
    title: 'Car ',
    amount: 12345,
    date: new Date(2021,3,12).toString(),
  },
  { id: 'e3',
    title: 'New Desk',
    amount: 223,
    date: new Date(2021,4,11).toString(),
  },
];

  
  return (
    <div>
        <div>
          hej to ja
        </div>
        <div>
        drugi div
        </div> 
      <ExpenseItem 
        title={expenses[0].title}
        amount={expenses[0].amount}
        date={expenses[0].date} />
      <ExpenseItem
        title={expenses[1].title}
        amount={expenses[1].amount}
        date={expenses[1].date} />
      <ExpenseItem
        title={expenses[2].title}
        amount={expenses[2].amount}
        date={expenses[2].date} />
    </div>
  )
}

```
``
Now you have to change sth in your `ExpenseItem.js` .
>[!important] Parameter in component `PROPS`
> React ensures that you get one parameter in  every component `props`
> This is an object which holds all the receuved attributes as properties

in ExpenseItem.jsx
```js
import './ExpenseItem.css';

function ExpenseItem(props){
// const expenseDate = new Date(2022,10,10).toString();
// const expenseTitle = 'Rekin';
// const expenseAmount = 15678;
  
  return (
  <div className="container">
    <br/>
    <div> {props.date} </div>
    <div>
      <h2 id="description"> {props.title} </h2>
      <div className="price">{props.amount}</div>
    </div>
  </div>
  )
}

export default ExpenseItem;
```

## Formating date
`toLocaleString()` https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString

```js
function ExpenseItem(props){
  const month = props.date.toLocaleString('pl-PL', {month: 'long'});
  const day = props.date.toLocaleString('pl-PL', {day: '2-digit'});
  const year = props.date.getFullYear();

  return (
  <div className="container">
    <br/>
    <div>
        <div> {month} </div>
        <div> {day} </div>
        <div> {year} </div>
      </div>
    <div>
      <h2 id="description"> {props.title} </h2>
      <div className="price">{props.amount}</div>
    </div>
  </div>
  )
}

export default ExpenseItem;
```


## Spliting components into multiple components
There are no hard rules to split component into mutiple components.
We can split from our component a date components.

in the folder `components` a new fils `ExpenseDate.jsx`:
```jsx
function ExpenseItem(props){
  const month = props.date.toLocaleString('pl-PL', {month: 'long'});
  const day = props.date.toLocaleString('pl-PL', {day: '2-digit'});
  const year = props.date.getFullYear();
}

return (
	<div>
        <div> {month} </div>
        <div> {day} </div>
        <div> {year} </div>
      </div>
)


export default ExpenseItem;
```

and in `ExpenseItem` add `import ExpenseDate from './ExpenseDate' ;` and `<ExpenseDate />`
and even `<ExpenseDate date={props.date}`

In App component we use ExpenseItem component 
In ExpenseItem component we use ExpenseDate component

css to ExpenseDate
```css
.expense-date {
display: flex;
flex-direction: column;
width: 5.5rem;
height: 5.5rem;
border: 1px solid #ececec;
background-color: #2a2a2a;
color: white;
border-radius: 12px;
align-items: center;
justify-content: center;

}

.expense-date__month {
font-size: 0.75rem;
font-weight: bold;
}

.expense-date__year {
font-size: 0.75rem;
}

.expense-date__day {
font-size: 1.5rem;
font-weight: bold;
}
```

## "Composition" ("children props")
Building UI from smaller building blocks is called COMPOSITION.

We want to build a component that will be only a shell/ a container.

We make a `Card.jsx`
```js
import React from 'react' ;

const Card = () => {
  return <div className="card"> </div> ;
}

export default Card ;
```
`Card.css` (from other css files (ExpenseItem) cut some settings)
```css
.card{
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
}
```
In `ExpenseItem.jsx` change `<div>` into `<Card> </Card>`
but you can't user custom components as a wrapper. To build such a wrapper component we have to use `props.children` (`children` is a key word).
```js
import React from 'react' ;
import './Card.css'


function Card(props) {
    return <div className="card"> {props.children} </div>;
}

export default Card ;
```

one more thing
```js
import React from 'react' ;
import './Card.css'


function Card(props) {
    const classes = 'card ' + props.className ; // any class from outside is added to that string
    return <div className={classes}> {props.children} </div>;
}

export default Card ;
```


## Event Listener
ExpenseItem.jsx:
```js
//....
<button onClick={()=>console.log("Okki")}>Change Title!!</button>
  </Card>
  )
  }
```

or
```js
//...

function ExpenseItem(props){
  
  const clickHandler = () =>
    console.log("clicked!!") ;
  
  return (
  <Card className="container">
    <br/>
    <div>
     
      <ExpenseDate date={props.date}/>
      <h2 id="description"> {props.title} </h2>
      <div className="price">{props.amount}</div>
      
    </div>
    <button onClick={clickHandler}>Change Title!!</button>
  </Card>
  )
}
```

## Function in component
```js
  let title = props.title;
  const clickHandler = () =>
    title = "update!!!" ;
```
Nothing change!!
Components are function, so they have to be called.
React evalutate components by calling them.
We have to tell React that some components has been changed and it has to re-evaluate them. => STATE

## STATE
`import React, {useState} from 'react'` -> `State` is a function
directely INSIDE THE COMPONENT WE CAN CALL `State()` function 
(this function is so-called ==REACT HOOK==)
`const [<startValue> , <setFunction>] = useState(<initial value>)`
```js
import React, { useState } from 'react';
import './ExpenseItem.css';
import ExpenseDate from './ExpenseDate';
import Card from './Card';

function ExpenseItem(props) {
  // useState(props.title) creates a special variable and returns it
  //useState() also returns a function which 
  // we can call to assign a new value to that variable
  //useState() return a list [a_special_variable, a_updating_function]
  const [title, setTitle] = useState(props.title) ;
  
  // title = value from props.title
  // setTitle = function to update title

  const clickHandler = () => {
    // thanks of this function the entire component will be executed again
    setTitle('Update') ;
    console.log(title);
  }
  
  return (
    <Card className="container">
      <br />
      <div>

        <ExpenseDate date={props.date} />
        
        <h2>{title}</h2>
        <div className="price">{props.amount}</div>

      </div>
      <button onClick={clickHandler}>Change Title!!</button>
    </Card>
  )
}

export default ExpenseItem;



```

















