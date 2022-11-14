[[_ 0 React Full]]

# React State and Working with Events

## Listening to event
prefix `on`  - it is a event handler
`<button onClick > Change Title </button>`
replit.com:
```js
import './App.css'

export default function App() {
  const clickHandler = () => {
    console.log("Click!!!") ;
  }
  return (
    <main>
      <button onClick={clickHandler}> click me</button> 
    </main>
  )
}

```

To change something in DOM is more complicated. Components are functions, so they have to be called.



```js
import React, { useState } from 'react';
import './ExpenseItem.css';
import ExpenseDate from './ExpenseDate';
import Card from './Card';

function ExpenseItem(props) {
// first title=props.title ;

  // useState(props.title) creates a special variable and returns it
  //useState() also returns a function which 
  // we can call to assign a new value to that variable
  //useState() return a list [a_special_variable, a_updating_function]
  const [title, setTitle] = useState(props.title) ;
  
  // title = value from props.title
  // setTitle = function to update title

  const clickHandler = () => {
    // thanks of this function the entire component will be executed again
    //first // title="New title" ;
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

Each using of ExpenseItem will create a new `useState()`.

## State can be updated in many ways!

Thus far, we update our state **upon user events** (e.g. upon a click).

That's very common but not required for state updates! **You can update states for whatever reason you may have**.

Later in the course, we'll see Http requests that complete (where we then want to update the state based on the Http response we got back) but you could also be updating state because a timer (set with `setTimeout()`) expired for example.


## Adding Form Inputs

components > Expenses > [all Expenses file]
Add new subfolder in `components` > `NewExpense`

#### `NewExpense.jsx`
```js
import React from 'react' ;
import './NewExpense.css' ;
import ExpenseForm from './ExpenseForm'

const NewExpense = () => {

  return <div className="new_expense">
          <ExpenseForm />
        </div>
  } ;

export default NewExpense ;
```

#### `ExpenseForm.jsx`
```js
import React from 'react' ;
import'./ExpenseForm.css' ;

const ExpenseForm = () => {

  return (
    <form>
      <div className="new-expense__controls">
        <div className="new-expense__control">
          <label> Title</label>
          <input type="text" />
        </div>

         <div className="new-expense__control">
          <label> Amount </label>
          <input type="number" min="0.01" step="0.01" />
        </div>

         <div className="new-expense__control">
          <label> Date</label>
          <input type="date" min="2022-09-01" max="2024-12-31"/>
        </div>
         <div className="new-expense__actions">
          <button type="submit"> Add Expense</button>
         </div>
       </div>
    </form>
  ) ;
} ;

export default ExpenseForm ;
```

add to `App.jsx`
```js
//..
 return (
    <div>
     <NewExpense />
     //...
```


### Listining to User Input
in `ExpenseForm`
```js
const ExpenseForm = () => {
  const titleChangeHandler = () => {
    console.log("title change") ;
  } ;

  return (
    <form>
      <div className="new-expense__controls">
        <div className="new-expense__control">
          <label> Title</label>
          <input type="text" onChange={titleChangeHandler} />
        </div>
```

`onChange` and `titleChangeHandler`

to get data from `text input `
```javascript
  const titleChangeHandler = (event) => {
    console.log(event.target.value) ;
  } ;
```
`event` is built-in



## Working with Mutliple States
`event.target.value` -> always stores a string
so `useState('')` as a initial value

in file `ExpenseForm.jsx`
```js

const ExpenseForm = () => {
  const [enteredTitle,  setEnteredTitle] = useState('');
  const [enteredAmount, setEnteredAmount] = useState('');
  const [enteredDate, setEnteredDate] = useState('');
  
  const titleChangeHandler = (event) => {
    setEnteredTitle(event.target.value) ;
    console.log("ok") ;
  } ;

  const amountChangeHandler = (event) => {
      setEnteredAmount(event.target.value) ;
    console.log("ok2") ;
  } ;  
 
  const dateChangeHandler = (event) => {
      setEnteredDate(event.target.value) ;
    console.log("ok3") ;
  } ;
  
  return (
    <form>
      <div className="new-expense__controls">
        <div className="new-expense__control">
          <label> Title</label>
          <input type="text" onChange={titleChangeHandler} />
        </div>

         <div className="new-expense__control">
          <label> Amount </label>
          <input type="number" min="0.01" step="0.01" onChange={amountChangeHandler}/>
        </div>

         <div className="new-expense__control">
          <label> Date</label>
          <input type="date" min="2022-09-01" max="2024-12-31" onChange={dateChangeHandler}/>
        </div>
         <div className="new-expense__actions">
          <button type="submit"> Add Expense</button>
         </div>
       </div>
    </form>
  ) ;
} ;

export default ExpenseForm ;
```


### To use  only ONE STATE in a component
You have to use a JS object.
```js

const ExpenseForm = () => {
 // const [enteredTitle,  setEnteredTitle] = useState('');
 // const [enteredAmount, setEnteredAmount] = useState('');
 // const [enteredDate, setEnteredDate] = useState('');
	const [userInput, setUserInput] = useState({
		enteredTitle: '',
		enteredAmount: '',
		enteredDate:'',
	}) ;


  const titleChangeHandler = (event) => {
    //setEnteredTitle(event.target.value) ;
    //console.log("ok") ;
    setUserInput({
	    ...userInput,
	    enteredTitle: event.target.value ,
    })
  } ;
//...
  
```

### Updating State that Depends On the previous State

>[!important] 
> Whenever your state update depends on the previous state, use the function syntax form:
> `setUserInput( (prevState) => { return {...prevState, enteredTitle: event.target.value } ; });`

This syntax guaranties that all changes will be done correctely (React doesn't react instantianly, so when you will have a lot of updates, you can have some problems)

### Handeling Form Submission
A `<form>` has  a built-in `onSubmit={somefunctionHandler}`
by default a browser sends a request when the button is clicked

ExpenseForm.jsx
```js
  const submitHandler = (event) => {
    event.preventDefault() ;
  } ;
  
  return (
    <form onSubmit={submitHandler}>
```

a new version
```js
  const submitHandler = (event) => {
    event.preventDefault() ;

    const expenseData = {
      title: enteredTitle,
      amount: enteredAmount,
      date: new Date(enteredDate)
    }
    console.log(expenseData) ;
  } ;
  
```


### Two-Way Binding
> for inputs we don't just listen to changes but  we can also pass a new value back into the input (we can reset or change the input programmatically)

To make `two-way binging` add attribute `value` to the `<input value='' />`
we can use state variables from `useState`

ExpenseForm.jsx
```js
<label> Title</label>
<input 
	type="text"
	value={enteredTitle}
	onChange={titleChangeHandler} 
/>
        
```

and now we can add to our `sumbitHandler` function `setEnteredTitle('')`

so all the `ExpenseForm.jsx`
```js
import React, { useState } from 'react' ;
import'./ExpenseForm.css' ;


const ExpenseForm = () => {
  const [enteredTitle,  setEnteredTitle] = useState('');
  const [enteredAmount, setEnteredAmount] = useState('');
  const [enteredDate, setEnteredDate] = useState('');
  
  const titleChangeHandler = (event) => {
    setEnteredTitle(event.target.value) ;
    console.log("ok") ;
  } ;

  const amountChangeHandler = (event) => {
      setEnteredAmount(event.target.value) ;
    console.log("ok2") ;
  } ;  
 
  const dateChangeHandler = (event) => {
      setEnteredDate(event.target.value) ;
    console.log("ok3") ;
  } ;

  const submitHandler = (event) => {
    event.preventDefault() ;

    const expenseData = {
      title: enteredTitle,
      amount: enteredAmount,
      date: new Date(enteredDate)
    }
    console.log(expenseData) ;
    setEnteredTitle('') ;
    setEnteredAmount('') ;
    setEnteredDate('') ;
  } ;
  
  return (
    <form onSubmit={submitHandler}>
      <div className="new-expense__controls">
        <div className="new-expense__control">
          <label> Title</label>
          <input 
            type="text" 
            value={enteredTitle}
            onChange={titleChangeHandler} />
        </div>

         <div className="new-expense__control">
          <label> Amount </label>
          <input 
            type="number" 
            min="0.01" step="0.01" 
            value={enteredAmount}
            onChange={amountChangeHandler}/>
        </div>

         <div className="new-expense__control">
          <label> Date</label>
          <input 
            type="date" 
            min="2022-09-01" max="2024-12-31" 
            value={enteredDate}
            onChange={dateChangeHandler}/>
        </div>
         <div className="new-expense__actions">
           <button type="submit"> Add Expense</button>
         </div>
        
       </div>
      
    </form>
  ) ;
} ;

export default ExpenseForm ;
```


## Child to Parent Component Comunication

You need to pass data from ExpenseForm component to App component

You can use ==props== to send data from a parent to a child.
How sends data in the other direction???

The `<input />` jsx is a some built-in component and it sends data to its parent.
so
we can create our own 'event props' and we can expect functions as values and that would allow us to pass a function from a parent component

PATTERN
 - in the parent create a function with some param,
 - to the child in the parent add a new attribute `on<Somethin>={<functionName}`
 - in the child component you can call this function and you can send a argument to this function

From `ExpenseForm` to `NewExpense`:

==NewExpense==
```js
import React from 'react' ;
import './NewExpense.css' ;
import ExpenseForm from './ExpenseForm'

const NewExpense = (props) => {
const saveExpenseDataHandler = (enteredExpenseData) => {
  const expenseData = {
    ...enteredExpenseData,
    id: Math.random().toString() 
  };

  console.log(expenseData) ;
  
}
  return <div className="new_expense">
          
          <ExpenseForm onSaveExpenseData={saveExpenseDataHandler} />
        </div>
} ;


export default NewExpense ;
```


==ExpenseForm==
```js

const ExpenseForm = (props) => {
//..


  const submitHandler = (event) => {
    event.preventDefault() ;

    const expenseData = {
      title: enteredTitle,
      amount: enteredAmount,
      date: new Date(enteredDate)
    }
    props.onSaveExpenseData(expenseData) ; //!!!!!
    setEnteredTitle('') ;
    setEnteredAmount('') ;
    setEnteredDate('') ;
  } ;
  
  return ( //..


```


NOW from `NewExpense` to `App`
In the `App` add a new function 
==App==
```js
//..
const addExpenseHandler = (expense) => {
  console.log('in app.js') ;
  console.log(expense)
}
  //...

return (
    <div>
     <NewExpense onAddExpense={addExpenseHandler}/>
     <ExpenseItem 
     //..

```



==NewExpense==
```js
//...
const NewExpense = (props) => {
const saveExpenseDataHandler = (enteredExpenseData) => {
  const expenseData = {
    ...enteredExpenseData,
    id: Math.random().toString() 
  };
//...
```



## Lifting the State Up

You can't send data between sibling components. 
Data can be send only parent<--->child.

Lifiting the state up - sending data from child to partent
the parent sends that data to other its child by props.
`ExpenseForm` generates data and lifts it up to `NewExpense` 
	->
`NewExpense` sends that data to `App` 
	-> 
`App` sends that data to `ExpenseItem`











