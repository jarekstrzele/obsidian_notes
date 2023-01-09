[[_ 0 React Mosh]]


---
# Composing components
code from the end of [[3.1 Component vidly project]]

Add a new component "counters"
```jsx
import React, { Component } from 'react';
import Counter from './counter' ;

class Counters extends Component{
	state={};
		render() {
			return(
				<>
					<Counter />
					<Counter />
					<Counter />
					<Counter />
				</>
				)
		}
}

export default Counters ;
```

change
```jsx
  

class Counters extends Component{
	state={
		counters: [
		{id: 1, value:0},
		{id: 2, value:0},
		{id: 3, value:0},
		{id: 4, value:0},
		]
	};
	
	render() {
		return(
		<>
		{this.state.counters.map(counter => <Counter key={counter.id} />) }
		</>
)
}
}
```

a new change
```jsx
{this.state.counters.map(counter => <Counter key={counter.id}
						value={counter.value}
						selecte={true}
/>) }
```
and change in Counter.jsx
```jsx
  

render() {

console.log('poprs', this.props)

return (
```

and now you can delete this `console.log`
and poperty state change-> `{ count: this.props.value}` and in COunters.jsx change one  of values












