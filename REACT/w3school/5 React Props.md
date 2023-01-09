#react/props
[[_ 0 w3school React]]

# React Props
>[!definition] Props
>- ==they are READ_ONLY==
>- They are args passed into React components
>- They are passed to components via HTML attributes
>- they are like function args in JS and attributes in HTML


## TO SEND
use the same syntax as HTML attributes
`const myEle = <Car brand="Ford" />`
The component receives the argument as a `props` object
```jsx
function Car(props){
	return <h2> I am a  { props.brand } </h2>;
}
```

## Pass Data
Send the "brand" property from the Garage component to the Car component

```jsx
function Car(props){
	return <h2> I am a {props.brand }! <h2>;
	
}

function Garage(){
	return {
	<>
	 <h1> Who lives in my garage?</h1>
	 <Car brand="Ford" >
	
	</>
	}
}
```

a variable `carname` send to the `Car`
```jsx
function Car(props){
	return <h2>I am a { props.brand } </h2>;
}

function Garage(){
	const carName = "Ford";
	return (
		<>
		<h1> Who lives in my garage? </h1>
		<Car brand={ carName } />
	</>
	)
}


```

