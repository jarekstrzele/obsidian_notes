[[_ 0 React Mosh]]

#react/create  #bootstrap  
# Components (Counter app)
I had some problems, to solve them:
```shell
 npm install -g react-scripts
 npm install
```


## Create an app
`npx create-react-app counter-app`
to start app `npm start`

## add bootstrap
To install bootstrap:
`npm i bootstrap@4.1.1`

To import bootstrap to the app:
in the `index.js` file write:
`import 'bootstrap/dist/css/bootstrap.css'`

## a first component
In `src` folder  add `components` folder 
 In this new folder create a file `counter.jsx`

VS extention: *Simple React Snippet*:
- `imrc` (`import React, { Component } from 'react'`)
- `cc` -> 
```jsx
class Counter extends Component {
    state = {  } 
    render() { 
        return ();
    }
}
 
export default Counter;
```


in the `index.js` file import that `Counter`:
`import Counter from './components/counter';`

## add button
**JSX** element can have only ONE PARENT ELEMENT, because method `React.createElemen(only_one_tag, ...)`
You can solve this issue wrapping multiple element into one e.g. `return ( <div> ....  </div>  );`
Parentheses are importent because JS changes `return`  to `return ;` automatically

If you don't want to have `<div>` that do nothing, you can use `React.Fragment` instead
ctr+d find another acurrent if the selection (you can write in to place simultaneously)
```jsx
...
render() {
 return (
	 <React.Fragment>
	        <h1>Hello World </h1>
	        <button> Increment </button>
	 </React.Fragment>
	);
}
```
now you have only `<div id="root">`

## Embedding Expressions
`state ={}` the special object that includes any data that this components needs
```jsx
render() { 
        return (
        <React.Fragment>
            <span>{this.formatCount()} </span>
            <button> Increment </button>
        </React.Fragment>
        );
    }

    formatCount() {
        const { count } = this.state;
        return count === 0  ? "Zero" : count;
    }
```

## Setting Attrs
One method:
```jsx
<span className="badge badge-primary m-2">{this.formatCount()} </span>
<button className="btn btn-secondary btn-sm"> Increment </button>
```

or use `style={ {} }` attribute
```jsx
 styles={
        fontSize: 50,
        fontWeight: "bold"
     };


    render() { 
        return (
        <React.Fragment>
           
            <span style={ this.styles } className="badge badge-primary m-2">{this.formatCount()} </span>
```

or one-line style
```jsx
 render() { 
        return (
        <React.Fragment>
           
            <span style={ { fontSize:30 } } className="badge badge-primary m-2">{this.formatCount()} </span>
            
```

## Rendering Classes Dynamically

counter.jsx
```javascript
import React, { Component } from 'react'

class Counter extends Component {
    state = { 
        count: 1,
     } ;

    render() { 
        
        return (
        <React.Fragment>
           
            <span style={ { fontSize:30 } } className={this.getBadgeClasses()} >{this.formatCount()} </span>
            <button className="btn btn-secondary btn-sm"> Increment </button>
        </React.Fragment>
        );
    }

    getBadgeClasses() {
        let classes = "badge m-2 badge-";
        classes += (this.state.count === 0) ? "warning" : "primary";
        return classes;
    }

    formatCount() {
        const { count } = this.state;
        return count === 0  ? "Zero" : count;
    }
}
 
export default Counter;
```

## Rendering Lists
```javascript
lass Counter extends Component {
    state = { 
        count: 0,
        tags: ['tag1', 'tag2', 'tag3']
     } ;

    render() { 
        
        return (
        <React.Fragment>
           
            <span style={ { fontSize:30 } } className={this.getBadgeClasses()} >{this.formatCount()} </span>
            <button className="btn btn-secondary btn-sm"> Increment </button>
            <ul>
               { this.state.tags.map(tag => <li key={tag}>{ tag }</li>)}
            </ul>
        </React.Fragment>
        );
    }
```
`key` is like a `id` thanks that React can easily identify each`<li>`

## Conditional Rendering
e.g. We have a list and we want to display items of the list or a msg if there are no items.
1. First way: define a method we these two conditions and in render method return `{this method with two condition}`
2. Second way 
`cond1 && cond2` if the first is true, JS checks the second, if this is true, return this last, so `true && "Hi"` returns `Hi` and `true && "Hi" && 1` returns `1`
`{this.state.tags.length === 0 && "Please create a new tag"}`

## Handling Events

```javascript
  handleIncrement(){
        console.log("Increment Clicked");
    }

 render() { 
        
        return (
        <React.Fragment>
           
            <span  className={this.getBadgeClasses()} >{this.formatCount()} </span>
            <button 
                onClick={this.handleIncrement} 
                className="btn btn-secondary btn-sm">
            Increment 
            </button>
            
        </React.Fragment>
        );
    }
```

## Binding Event Handlers
Some problemes with references of `this`. To solve them:
**first solution** `.bind(this)`:
```javascript
	constructor(){
        super();
        this.handleIncrement = this.handleIncrement.bind(this);
     }

    handleIncrement(){
        console.log("Increment Clicked", this);
    }
```


**second solution**
use arrow function
```javascript

handleIncrement = () => {
        console.log("Increment Clicked", this);
    }
```


## Updating a state
`this.setState( {[object] })`  this method tells React that we're updating the state 
- and it will figure out what part of the state has changed
- and based on that it will bring the DOM in sync with the virtual DOM

```javascript
  handleIncrement = () => {
        this.setState({ count: this.state.count + 1 })
    }

```


## What happens when state changes
We are calling `this.setState...` this method is telling - 
- React that the state of this component is going to change
- React schedule a call to the render method (==async== call)
- this method return a new React element (Virtual DOM)
- React check what has changed (the new React element and the old one)
- React changes in the DOM only what has been  changed


## Passing Event args
e.g. `onClick` -  you can pass only a reference to a function, so how you can send args?

use in-line function
```javascript
// ...
handleIncrement = (prod) => {
        console.log(prod);
        this.setState({ count: this.state.count + 1 })
    }
//...
<button 
   onClick={() => this.handleIncrement({id:1})} 
   className="btn btn-secondary btn-sm">
 Increment 
</button>
//...
```













