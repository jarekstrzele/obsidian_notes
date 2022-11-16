#react #youtube 


```jsx
import './App.css';

const App= ()=> {
  const name = 'John' ;
  const isNameShowing = false ;

	return (
    <div className="App">
      <h1> Hello React {isNameShowing ? name : 'someone else'}</h1>
    </div>
  );
}

export default App;
```