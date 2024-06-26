
### `npx create-react-app login_app`

Na szczęście dla nas, moduły CSS są obsługiwane przez `Create-react-app` domyślnie. Jedyne, co mamy do zrobienia, to nadanie odpowiedniej nazwy naszym plikom CSS. Jeśli zaimportujemy plik z rozszerzeniem `.module.css`, to `createe-react-app` automatycznie potraktuje go jako moduł CSS.

>"height: 100vh" jest wartością CSS, która oznacza, że wysokość elementu powinna być ustawiona na 100% wysokości okna przeglądarki. VH jest jednostką, która reprezentuje 1% wysokości okna przeglądarki. W ten sposób `height: 100vh` oznacza, że element powinien być wysoki jak całe okno przeglądarki.

components
	- UI
	- Users
		- AddUser.js


App.jsx
```js
import './App.css';
import AddUser from './components/Users/AddUser'
function App() {
  return (
    <div>
     <AddUser />
    </div>
  );
}
export default App;
```

AddUser.jsx
```js
import React from 'react'
const AddUser = () =>
{
    const addUserHandler = (event) => {
        event.preventDefault() ;
    }

    return (
        <form onsSubmit={addUserHandler}>
            <label htmlFor="username">Username</label>
            <input id="username" type="text" />
            <label htmlFor="age">Age (Years)</label>
            <input id="age" type="Number" />
            <button type="submit">Add user</button>
        </form>
    )
};

export default AddUser;
```

index.css
```css
  html {
  font-family: sans-serif;
  background-color: #1f1f1f;
}
```

---
## Adding Card component


>[!important] IMPORTANT
>You always need to import what you want use

UI>Card.js
```jsx
import React from 'react' ;
import classes from './Card.module.css' ;

const Card = props => {
    return (
    <div className={classes.card}>
        {props.children}
    </div>
    )
}

export default Card ;
```

UI>Card.module.css
```jsx
.card {
    background: white;
    box-shadow: 0 2px 8px rgba(0,0,0,0.26);
    border-radius: 10px;
}
```



Our own components can interact only with their props, so they don't know e.g. `className` component

in the Card component we want have two classes:
- one from Card.module.css
- second from the parent (App.js), so we can use props and `${..}` template literal

#### UI> Card.jsx
```js
import React from 'react'
import classes from  './Card.module.css'


const Card = props =>{
    return(
        <div className={`${classes.card} ${props.className}`}> {props.children} </div>
    );
}

export default Card;
```
UI>Card.module.css
```css
.card{
    background-color: white;
    box-shadow: 0 2px 8px rgba(0,0,0,0.26);
    border-radius: 10px;
}
```

AddUserjs.
```js
import React from 'react' ;
import Card from '../UI/Card' ;
import classes from './AddUser.module.css' ;

const AddUser = () =>
{
    const addUserHandler = (event) => {
        event.preventDefault() ;
    }

    return (
        <Card className={classes.input}>
            <form onsSubmit={addUserHandler}>
                <label htmlFor="username">Username</label>
                <input id="username" type="text" />
                <label htmlFor="age">Age (Years)</label>
                <input id="age" type="Number" />
                <button type="submit">Add user</button>
            </form>
        </Card>
    )
};
export default AddUser;
```

AddUser.module.css
```css
.input {

    margin: 2rem auto;
    padding: 1rem;
    width: 90%;
    max-width: 40rem;
  }

  .input label {
    display: flex;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  .input input {
    font: inherit;
    display: flex;
    width: 100%;
    border: 1px solid #ccc;
    padding: 0.15rem;
    margin-bottom: 0.5rem;
  }
  .input input:focus {
    outline: none;
    border-color: #4f005f;
  }
```
instead of `flex` you can use `block`







