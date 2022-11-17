
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
```
export default function Button(props){
  return (
    <button>{props.children}  </button>
  ) ;
}
```

Card.jsx



# Simple List App

