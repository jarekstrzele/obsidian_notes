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







