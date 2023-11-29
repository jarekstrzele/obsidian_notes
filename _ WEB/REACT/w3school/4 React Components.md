[[_ 0 w3school React]]


---
# React Components
>[!definition]components
>- they are idependent and reusable bits of code
> - they serve the same purpose as JavaScript functions but wirk in isolation and return HTML

## Two types of components
==When creating a React component, the copmponent's name MUST start with an upper case latter==

### class components
```javascript
class Car extends React.Component {
 render(){
		 return <h2>HIIii</h2>
	 }
}
```
### function components
Preferable
```javascript
function Car(){
	return <h2>HIIii</h2>;
}
```
## Rendering a component
To use this component in your application, use similar syntax as normal HTML: `<Car />`
```javascript
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car />);
```


## Props 
Components can be passed as `props`, which stands for properties.
Props are like function arguments and you send them into the component as attributes
```javascript
function Car(props){
	return <h2>I am a {props.color} Car!</h2>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car color="red"/>);
```


## Components in Components
We can refer to components inside other components:
```javascript
function Car(){
	return <h2> I am a Car </h2>;
}

function Garage(){
	return (
		<>
			<h1>Who lives in my Garage?</h1>
			<Car />
		</>
	)
}

const root = ReactDOM.createRoot(document.getElementById('root)'))
root.render(<Garage />);
```

## Components in Files
Cars.js:
```javascript
function Car() {
	return <h2> Hi, Iam a Car!</h2>;
}

export default Car;
```
other.js
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import Car from '.Car.js';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car />);
			
```


