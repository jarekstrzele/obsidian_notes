components>
	- UI
	- Users
		- AddUser.jsx


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





