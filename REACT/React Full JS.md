#react #youtube 
#react #javascript  #youtube 

https://www.youtube.com/watch?v=b9eMGE7QtTk

----
>[!info] React
>a front-end JavaScript library for building user interfaces
> ---
> React JS is a component-based front-end library
> ---
> Components are  independent and reuseable



MERN Stack
Singe Page

>[!info] Virtual DOM
>It is a JS object `VD={key:value, key:value}`
>It is a lightweight representation of DOM (is faster)


class component


function component
```jsx
import React from 'react' ;

const Example = () => {
	return <div> Hello World </div> ;
}

```


>[!info] JSX
>It is used in React to describe what the User Interface should look like


## Create React App

### `npx create-react-app my-app`

you need a Node JS
>[!info] Node 
>It is a JS runtime that allows us to execute JS code on the server


###  `npm start`

`index.html -> <div id="root"></div>` 
`index.js` start point for all React apps


# First app


```jsx
import './App.css';

const App= ()=> {
  const name = 'John' ;
  const isNameShowing = false ;

	return (
    <div className="App">
      <h1> Hello React {isNameShowing ? name : 'someone else'}</h1>
    </div>
  );
}

export default App;
```












