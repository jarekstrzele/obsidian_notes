#react/props  
https://www.youtube.com/watch?v=JpM9hiQTlAk&t=2s

# Some new issues
## `props.children`

> You can use props.children in React in order to access and utilize what you put inside the open and closing tags when you are creating an instance of a component.
> 

App.jsx
```jsx
import './App.css'
import Button from './Button' ;

export default function App() {
  return (
    <div>
      <Button> hej </Button>
      <Button> Hello </Button>
    </div>
  )
}
```

Button.jsx
```jsx
export default function Button(props){
  return (
    <button>{props.children}  </button>
  ) ;
}
```

---
Card.jsx
```jsx
export default function Card(props){

  const cardStyle = {
    width: '200px',
    height:'100px',
    border: '1.5px solid gray',
    borderRadius: '2px',
    padding: '4px',
    margin: '4px'
  }
  
  return (
    <div style={cardStyle}>
      {children}
    
    </div>
  ) ;
}
```

new App.jsx
```jsx
import './App.css'
import Button from './Button' ;
import Card from './Card' ;
export default function App() {
  return (
  <div>
    <Card>
      <Button> hej </Button>
      <Button> Hello </Button>
    </Card>

     <Card>
      Lorem ipsumLorem ipsumLorem ipsumLorem ipsum
       Lorem ipsumLorem ipsumLorem ipsumLorem ipsumLorem ipsum
       Lorem ipsumLorem ipsumLorem ipsumLorem ipsum
    </Card>
   </div> 
  )
}
```
# Simple List App

