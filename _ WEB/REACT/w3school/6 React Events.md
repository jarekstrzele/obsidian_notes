[[_ 0 w3school React]]



# React Events
#react/events
React has the same events as HTML: click, change ....

>React events are written in camelCase syntax
>e.g. `onClick`
```jsx
<button onClick={shoot}> Take the shot!</button>
```

```html
<button onclick="shoot()">Take the shot!</button>
```


## Passing arguments
To pass an arg to an event handler, use an arrow function
```jsx
function Football(){
const shoot = (a) => {
	alert(a);
}
	return (
		<button onClick={
			()=> shoot("Goaal!")}>
			Take the shot! </button>
		
	);
}
```

## React Event Object
Event handlers have accesss to the React event that triggered the function

```jsx
function Football(){
	const shoot = (a, b) => {
	alert(b.type);
	// b represents the React event that triggered the function, in this case the 'click' event
	}


	return (
		<button onCLik={(event)=>shoot("Goal", event)}>
		take the shot</button>
	)
}
```








