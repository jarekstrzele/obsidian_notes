#react/component
[[_ 0 React  Start]]


# Components
Nowy projekt
`create-react-app cunter-app`

Install bootstrap
`npm i bootstrap@4.1.1`

in the `index.js` `import 'bootstrap/dist/css/bootstrap.css'`


## First component
in `src` folder add a new subfolder `components` next create `counter.jsx`

You installed a plagin to VS Code `Simple React Snippets`.
It have a lot of shortcuts. `imrc` import React component
counter.jsx:
```jsx
import React, { Component } from 'react';


class Counter extends Component {
	render() {
//<h1> cos </h2> -> React.createElement('h1', 'cos')
		return <h1>Hello From Component Counter</h1>;
	}
}

export default Counter;
```

index.js:
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
//import App from './App';
import './index.css';
import 'bootstrap/dist/css/bootstrap.css';
import Counter from './compopnents/counter';


ReactDOM.render(
	<Counter />,
	document.getElementById('root')
);
```

## a new Counter component
```jsx
import React, { Component } from 'react';

class Counter extends Component {

	state ={
		count : 0
	};

  render() {
    return (
      <React.Fragment>
        <h1>Hello From Component Counter</h1>
        <button>BATON</button>
      </React.Fragment>
);
}
}

export default Counter;
```

>ctr+d in VS Code -> you can simultaneously edite two or more the same pieces of code


## `state`
`state = {}`  an object (a special property) that includes any data that this component needs

 > `{  < expression > }` expression, this is  sth that produces a value

```jsx
import React, { Component } from 'react';

class Counter extends Component{
  state = {
    count: 123
  };
  
  render() {
    return (
      <>
        <span> {this.state.count} Hello World </span> 
        <button> Button </button>
      </>
    );
  }
}

export default Counter;
```




```jsx
class Counter extends Component {
	state = {
		count: 0,
		imageUrl: 'https://piscum.photos/200'
	}
	render() {
		return (
		 <div>
		 <img src={this.state.imageUrl} alt='image' />
			<span>{this.formatCount()}</span>
			<button>BATON</button>
			</div>
		);
	}
 

formatCount(){
	const { count } = this.state
	return count === 0 ? <h1>Zero</h1> : count;
	}
}
```


## attributes
```jsx
import React, { Component } from 'react';
 class Counter extends Component {
  state = {
   count: 0,
   imageUrl: 'https://picsum.photos/200'
};

// styles = {
// fontSize: '15px',
// fontWeight: 'bold'
// }
// <span style={this.styles} className="badge badge-primary m-2">{this.formatCount()}</span>

  
 render() {
  return (
   <div>
    <img src={this.state.imageUrl} alt="" />
    <span style={ {fontSize: 30}} className="badge badge-primary m-2">{this.formatCount()} 
    </span>
    <button className="btn btn-secondary btn-sm">Increment</button>
   </div>
 );
}

formatCount(){
 const { count } = this.state
 return count === 0 ? <h1>Zero</h1> : count;
 }
}
export default Counter;
```

## Rendering Classes Dynamically







