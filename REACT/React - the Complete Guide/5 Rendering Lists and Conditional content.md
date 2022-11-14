[[_ 0 React Full]]

Some changes in `App.jsx`
```jsx
//...
const addExpenseHandler = (expense) => {
  console.log('in app.js') ;
  console.log(expense) ;
}
  return (
   <div>
     
     <NewExpense onAddExpense={addExpenseHandler}/>
     {
       expenses.map((expense) =>
         <ExpenseItem 
          title={expense.title}
          amount={expense.amount}
          date={expense.date}
           />
     )
     } ;
     
    </div>
  )
```



## Using stateList
`App.jsx`:
```js
import React, { useState } from 'react'; 
import './App.css' ;
import ExpenseItem from './components/Expenses/ExpenseItem' ;
import NewExpense from './components/Expenses/NewExpense/NewExpense' ;
//import ExpensesFilter from './components/Expenses/ExpensesFilter' ;
  const init_data = [
    {id: 'e1', title: 'Toilet paper', amount: 3, date: new Date(2022,10,7)},
    {id: 'e2', title: 'Rekin', amount: 30000, date: new Date(2020,11,3)},
    {id: 'e3', title: 'Mop', amount: 30, date: new Date(972,5,24)}
]

export default function App() {

const [expenses, setExpenses] = useState(init_data) ;
const addExpenseHandler = (expense) => {
  // console.log('in app.js') ;
  // console.log(expense) ;
  setExpenses([expense, ...expenses])

}
//....
```

better way
```js
//..
const addExpenseHandler = (expense) => {
 setExpenses( (prevExpenses) => {
   return [expense, ...prevExpenses] ;
  }) ;
} ;


//...
```

## Keys Warrigns
to update and render lists efficiently 
without `keys` react render all the list, not just one item
add `key` to your component
`App.jsx`
```js
  
const addExpenseHandler = (expense) => {
 setExpenses((prevExpenses) => {
   return [expense, ...prevExpenses] ;
  }) ;
} ;

return (
   <div>
     
     <NewExpense onAddExpense={addExpenseHandler}/>
     {
       expenses.map((expense) =>
         <ExpenseItem 
          key={expense.id}
          title={expense.title}   
          amount={expense.amount}
          date={expense.date}
           />
     )} ;
     
  </div>
  )
```

## Filter component
`ExpensesFilter.jsx`
```js
import React from 'react';

import './ExpensesFilter.css';

const ExpensesFilter = (props) => {
  const expenseFilterHandler = (event) =>{
    console.log(event.target.value) ;
  } ;
  return (
    <div className='expenses-filter'>
      <div className='expenses-filter__control'>
        <label className='expenses-filter' >Filter by year</label>
        <select value={props.selected} onChange={expenseFilterHandler}>
          <option value='2022'>2022</option>
          <option value='2021'>2021</option>
          <option value='2020'>2020</option>
          <option value='2019'>2019</option>
        </select>
      </div>
    </div>
  );
};

export default ExpensesFilter;

```

sending data from the child (filter component) to parent (app component):
```js
const ExpensesFilter = (props) => {
  const expenseFilterHandler = (event) =>{
    props.onChangeFilter(event.target.value) ;
  } ;
  return ( //...
  ```

ExpensesFilter,jsx
```js
import React from 'react';
import './ExpensesFilter.css';

const ExpensesFilter = (props) => {
  const dropdownChangeHandler = (event) => {
    props.onChangeFilter(event.target.value);
  };

  return (
    <div className='expenses-filter'>
      <div className='expenses-filter__control'>
        <label>Filter by year</label>
        <select value={props.selected} onChange={dropdownChangeHandler}>
          <option value='2022'>2022</option>
          <option value='2021'>2021</option>
          <option value='2020'>2020</option>
          <option value='2019'>2019</option>
        </select>
      </div>
    </div>
  );
};

export default ExpensesFilter;

```

`App.jsx`
```js
 setExpenses((prevExpenses) => {
   return [expense, ...prevExpenses] ;
  }) ;
} ;
 
  const [filteredYear, setFilteredYear] = useState('2021') ;
  const filterChangeHandler = selectedYear => {
    setFilteredYear(selectedYear);
    
  };
  return (
   <div>
     <NewExpense onAddExpense={addExpenseHandler}/>      <div>
    <ExpensesFilter selected={filteredYear} onChangeFilter={filterChangeHandler} />
    </div>
     {
       expenses.map((expense) =>
```


using `useState`
`App.jsx`
```js
//....
const addExpenseHandler = (expense) => {
 setExpenses((prevExpenses) => {
   return [expense, ...prevExpenses] ;
  }) ;
} ;

// 
  const [filteredYear, setFilteredYear] = useState('2021') ;
  const filterChangeHandler = selectedYear => {
    setFilteredYear(selectedYear);
    
  };

  const filteredExpenses = expenses.filter(expense => {
    return expense.date.getFullYear().toString() === filteredYear ;
  })
  
  return (
   <div>
     <NewExpense onAddExpense={addExpenseHandler}/>      <div>
    
    <ExpensesFilter selected={filteredYear} onChangeFilter={filterChangeHandler} />
     
    </div>
     {
       filteredExpenses.map((expense) =>
         <ExpenseItem 
          key={expense.id}
          title={expense.title}   
          amount={expense.amount}
          date={expense.date}
           />
     )} ;
  </div>  )
}
```



## Outputting Conditional Content
`App.jsx`
```js
//...
  const filteredExpenses = expenses.filter(expense => {
    return expense.date.getFullYear().toString() === filteredYear ;
  })

let expensesContent = <p>No expenses found.</p>
if (filteredExpenses.length > 0) {
  expensesContent = filteredExpenses.map((expense) =>
         <ExpenseItem 
          key={expense.id}
          title={expense.title}   
          amount={expense.amount}
          date={expense.date}
           />
     )
}
  
  return (
   <div>
     <NewExpense onAddExpense={addExpenseHandler}/>      <div>
    
    <ExpensesFilter selected={filteredYear} onChangeFilter={filterChangeHandler} />
     
    </div>
     { expensesContent }

  </div>  )
}
```

different way -> logic inside the jsx
App.jsx
```jsx
//...
 return (
   <div>
     <NewExpense onAddExpense={addExpenseHandler}/>      <div>
    
    <ExpensesFilter selected={filteredYear} onChangeFilter={filterChangeHandler} />
     
    </div>
     { 
       filteredExpenses.length===0 ? <p> Noexpenses found.</p> :        
       filteredExpenses.map((expense) =>
         <ExpenseItem 
          key={expense.id}
          title={expense.title}   
          amount={expense.amount}
          date={expense.date}
           />
     )
     
     }

  </div>  )

```

other way
App.jsx
```js
  return (
   <div>
     <NewExpense onAddExpense={addExpenseHandler}/>      <div>
    
    <ExpensesFilter selected={filteredYear} onChangeFilter={filterChangeHandler} />
     
    </div>
     { filteredExpenses.length===0 && <p> No expenses found.</p>}   
     { filteredExpenses.length > 0 && 
       filteredExpenses.map((expense) =>
         <ExpenseItem 
          key={expense.id}
          title={expense.title}   
          amount={expense.amount}
          date={expense.date}
           />
     )
     
     }

  </div>  )
}

```

---
## Adding Conditional Return Statements

create a new file `ExpensesList.jsx` 
In that file copy all the logic with  list
```js
import React from 'react' ;
import './ExpensesList.css' ;
import ExpenseItem from './ExpenseItem' ;

const ExpensesList = (props) => {
  
  if (props.expenses.length === 0) {
    return <h2 className="expenses-list__fallback">No expenses found.</h2>
}

  return (
    <ul className='expenses-list'>
      {
      props.expenses.map((expense) =>
         <ExpenseItem 
          key={expense.id}
          title={expense.title}   
          amount={expense.amount}
          date={expense.date}
           />
     )
    }
    </ul>
  );
}

export default ExpensesList ;
```

and in the file `ExpenseItem.jsx` change `div` for `li`
```js
  
  return (
    <li className="expense-item">
       <ExpenseDate date={props.date} />
       <h2 className="expense-item__description ">{title} </h2>
       <div className="expense-item__price">{props.amount} </div>
       <button onClick={clickHandler}>Change Title!!</button>    
    </li>

  )  
```






















