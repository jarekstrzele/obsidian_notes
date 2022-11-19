<<<<<<< HEAD
[[REACT/plurasight/React 17 Getting Started/_ 0 Getting Started]]
=======
[[REACT/plurasight/React 17 Getting Started/_ 0 Getting Started]]
>>>>>>> remotes/origin/master


--------
# The GitHub Cards App
#react/class_component


Creating a React app:
1. What is a component structure?
2. How many components?
3. What each component should describe?

## Class syntax
```javascript

class App extends React.Component{
  //constructor
  // this
  // props and states are manange of the instance of the class!!
  
  // each React component must have a render function
  // render return the Virtual DOM description of your component
  render(){
    return  <div className="header">{this.props.title}</div>
  }
}

// const App = ({title}) => (
//   <div className="header">{title}</div>
// );

ReactDOM.render(
	<App title="The GitHub Cards App" />,
  mountNode,
);
```

## Styling React Components
To style React components you can use global CSS or use property `style`, but it is not like the HTML style property (we pass not string but `{{ }}`)

`<div className="github-profile" > ...`  + style.css with the definition of the class
but you can use `style`
`<div className="github-profile" style={{ margin: '1rem' }}> ...`

This is JS code, so you can use conditional statements in `style` prop:
```javascript
class ConditionalStyle extends React.Component{
  render(){
    return (
      <div style={{ color: Math.random() < 0.5 ? 'red' : 'green'}} >
          How do you like this?
      </div>
    );
  }
}

ReactDOM.render(
  <ConditionalStyle />,
  mountNode,
)
```

CSS in JS

## Working with Data

>[!What is an instance/object in a React app]
> - Every time we use a class component, React internally creates an instance from this component and uses it to render the element
> - that instance is something that React keeps in memory for each rendered element
> - in the browser we see the result of the DOM operation React came up with using that instance render method
> 

```javascript
const testData = [
			{name: "Dan Abramov", avatar_url: "https://avatars0.githubusercontent.com/u/810438?v=4", company: "@facebook"},
      {name: "Sophie Alpert", avatar_url: "https://avatars2.githubusercontent.com/u/6820?v=4", company: "Humu"},
  		{name: "Sebastian Markbåge", avatar_url: "https://avatars2.githubusercontent.com/u/63648?v=4", company: "Facebook"},
	];

const CardList = (props) => (
  <div>
    {testData.map( profile => <Card {...profile}/>)}
  </div>
);
//<Card {...testData[0]} />
//<Card {...testData[1]} />
// map-> [<Card />, <Card />, <Card />]
// [React.createElement(), React.createElement(),React.createElement()]

class Card extends React.Component {
	render() {
    const profile = this.props;
  	return (
    
    	<div className="github-profile">
    	  <img src={profile.avatar_url} />
    	<div className="info">
        <div className="name">{profile.name}</div>
        <div className="company">{profile.company}</div>
    	</div>
    	</div>
    );
  }
}

class App extends React.Component {
	render() {
  	return (
    	<div>
    	  <div className="header">{this.props.title}</div>
        <CardList />
    	</div>
    );
  }	
}

ReactDOM.render(
	<App title="The GitHub Cards App" />,
  mountNode,
);
```


## State Object

>[!important]    
> ONE COMPONENT ONE RESPONSABILITY
> 
> Components should avoid reading global variables!!
> 
```javascript
const testData = [
    {name: "Dan Abramov", avatar_url: "https://avatars0.githubusercontent.com/u/810438?v=4", company: "@facebook"},
    {name: "Sophie Alpert", avatar_url: "https://avatars2.githubusercontent.com/u/6820?v=4", company: "Humu"},
    {name: "Sebastian Markbåge", avatar_url: "https://avatars2.githubusercontent.com/u/63648?v=4", company: "Facebook"},
];

const CardList = (props) => (
	<div>
    
  	{props.profiles.map(profile => <Card {...profile}/>)}
	</div>
);

class Card extends React.Component {
	render() {
  	const profile = this.props;
  	return (
    	<div className="github-profile">
    	  <img src={profile.avatar_url} />
        <div className="info">
          <div className="name">{profile.name}</div>
          <div className="company">{profile.company}</div>
        </div>
    	</div>
    );
  }
}

class Form extends React.Component{
  render(){
    return (
      <form action="">
        <input type="text" placeholeder = "GitHub username" />
        <button>Add card</button>
      </form>
    );
  }
}


class App extends React.Component {
  // constructor(props){
  //   super(props);
  //   this.state = {
  //     profiles:testData,
  //   };
  // }
  state = {
    profiles: testData,
  };
  
	render() {
  	return (
    	<div>
       
    	  <div className="header">{this.props.title}</div>
         <Form />
        <CardList profiles={this.state.profiles} />
    	</div>
    );
  }	
}

ReactDOM.render(
	<App title="The GitHub Cards App" />,
  mountNode,
);
```

#react/setState
#react/class_component 
`setState()` a func that allows us to change the state of a React class component


## Input from the User
To take input from the user, we need to define an event handler in the React UI.

`onSubmit={}` you can utilize native form submission features (for example: you can make this input required)

==Every React event function receives an event argument==
This arg is just a weapper around the native JavaScript event object
` event.preventDefault();` it is imporant to use this code, because without it, when you press button your page will be refreshed

React has a special property named `ref` that we can use to get a reference to the element with this prop (like a fancy ID that React keeps in-memory and associates with every rendered element) <- use it with `React.createRef()`

`this.userNameInput.current`:
- a current value from the object pointed by the reference stored in `userNameInput`
- this value is the HTML input element itsels
`this.userNameInput.current.value` read this value
```javascript
class Form extends React.Component{
    handleSubmit = (event) => {
    event.preventDefault();
    console.log(this.userNameInput.current.value)
  }
  userNameInput = React.createRef();
  render(){
    return (
      <form onSubmit={this.handleSubmit}>
        <input 
          type="text"
          placeholeder = "GitHub username"
          ref={this.userNameInput} required
        />
        <button>Add card</button>
      </form>
    );
  }
}

```

but you can control the input using React itself not by the JS DOM.
this method is labeled as ==controlled components==
`state={}` to handle the input value of the userName field
`value={this.state.userName} ` this immediately creates a controlled element
`onChange={}` (event) now the DOM can tell React that something has changed in this input and you should relfect it in the UI as well
```javascript
class Form extends React.Component{
  state = { userName: ''};
    handleSubmit = (event) => {
    event.preventDefault();
   console.log(this.state.userName)
  }
  userNameInput = React.createRef();
  render(){
    return (
      <form onSubmit={this.handleSubmit}>
        <input 
          type="text"
          value={this.state.userName} 
          onChange={event => this.setState({userName: event.target.value })}
          placeholeder = "GitHub username"
          required
        />
        <button>Add card</button>
      </form>
    );
  }
}
```

---------
## Working with Ajax Calls
`fetch` call (a native fnc available in browsers to do an AJAX call) -> in React `axios` (return a promise)
`axios.get('https://api.github.com/users/gaeron')`
dynamic version
```
axios.get(`https://api.github.com/users/${this.state.userName}`)
```
```javascript
class Form extends React.Component {
	state = { userName: '' };
	handleSubmit = async (event) => {
  	event.preventDefault();
    const resp= await axios.get(`https://api.github.com/users/${this.state.userName}`)
    console.log(resp);
  };
```

If the App component passes a functionr eferenc to the Form component, we can change the state of the App component in that function and the Form component will be able to invoke that function because it will be part of its props object
,

Handle errors
jscomplete.com/react-beyond-basics

```javascript
// gaearon, sophiebits, sebmarkbage, bvaughn


const CardList = (props) => (
	<div>
  	{props.profiles.map(profile => <Card key={profile.id} {...profile}/>)}
	</div>
);

class Card extends React.Component {
	render() {
  	const profile = this.props;
  	return (
    	<div className="github-profile">
    	  <img src={profile.avatar_url} />
        <div className="info">
          <div className="name">{profile.name}</div>
          <div className="company">{profile.company}</div>
        </div>
    	</div>
    );
  }
}

class Form extends React.Component {
	state = { userName: '' };
	handleSubmit = async (event) => {
  	event.preventDefault();
    const resp= await axios.get(`https://api.github.com/users/${this.state.userName}`)
    this.props.onSubmit(resp.data);
    this.setState({userName:''});
  };
	render() {
  	return (
    	<form onSubmit={this.handleSubmit}>
    	  <input 
          type="text" 
          value={this.state.userName}
          onChange={event => this.setState({ userName: event.target.value })}
          placeholder="GitHub username" 
          required 
        />
        <button>Add card</button>
    	</form>
    );
  }
}

class App extends React.Component {
  state = {
    profiles: [],
  };
  
  addNewProfile = (profileData) => {
   this.setState(prevState => ({
     profiles: [...prevState.profiles, profileData],
   }));
  };
  
	render() {
  	return (
    	<div>
    	  <div className="header">{this.props.title}</div>
        <Form onSubmit={this.addNewProfile}/>
        <CardList profiles={this.state.profiles} />
    	</div>
    );
  }	
}

ReactDOM.render(
	<App title="The GitHub Cards App" />,
  mountNode,
);
```











