[[_ 0 React 18 Utlimate , TypeScript]]


# install `boostrap`

#bootstrap 
- install BOOTSTRAP (inside your project `npm install bootstrap`)
- delete the content of App.css
- delete the file `index.css` (it is a global style)
- in `main.tsx` change `import './index.css` na `impoer 'bootstrap/dist/css/bootstrap.cs`

`main.tsx`
```typescript
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.tsx'
import 'bootstrap/dist/css/bootstrap.css'

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
)
```

# make first component
a new folder `components` inside a new file `ListGroup.tsx`
```typescript
function ListGroup(){
    return <h1>List Group</h1>
}

export default ListGroup
```

go to the boostrap page to docs and find `List group`  copy the code
```
<ul class="list-group">
  <li class="list-group-item">An item</li>
  <li class="list-group-item">A second item</li>
  <li class="list-group-item">A third item</li>
  <li class="list-group-item">A fourth item</li>
  <li class="list-group-item">And a fifth one</li>
</ul>
```

and add it to the *ListGroup* component
```typescript
function ListGroup(){

    return (
        <ul className="list-group">
            <li className="list-group-item">An item</li>
            <li className="list-group-item">A second item</li>
            <li className="list-group-item">A third item</li>
            <li className="list-group-item">A fourth item</li>
            <li className="list-group-item">And a fifth one</li>
      </ul>
        )
}
```


# fragments
#react/fragments
`import {Fragment} from "react"`
and use `<Fragment> ... </Fragment>`

you can use better syntax -> simply `<> </>`

```typescript
function ListGroup(){

    return (
        <>
        <h1>List</h1>
            <ul className="list-group">
                <li className="list-group-item">An item</li>
                <li className="list-group-item">A second item</li>
                <li className="list-group-item">A third item</li>
                <li className="list-group-item">A fourth item</li>
                <li className="list-group-item">And a fifth one</li>
            </ul>
        </>
```


# Rendering List
```typescript
function ListGroup(){

	let citiesList = ["Olsztyn", "Paris", "London", "Tokyo"]
	citiesList = []
    return (
        <>
        <h1>List</h1>
        {citiesList.length === 0 && <p>No city was found</p>}
            <ul className="list-group">
               {citiesList.map(city=><li  className="list-group-item" key={city}>{city}</li>)}
            </ul>
        </>
        )
}
```

# event handler
after a click event in the console will be written the name of a city
```typescript
function ListGroup(){
    let citiesList = ["Olsztyn", "Paris", "London", "Tokyo"]
    //citiesList = []
    return (
        <>
        <h1>List</h1>
        {citiesList.length===0 && <p>no city was found</p>}
            <ul className="list-group">
               {citiesList.map( (city, index)=><li
                        className="list-group-item"
                        key={city}
                        onClick={(event)=>console.log(city, index)}
                        >{city}</li>)
                }
            </ul>
        </>
        )
}
```

**with an event object**
`event` is an object of `MouseEvent` class => `import { MouseEvent } from "react"`

```typescript
import { MouseEvent } from "react"

function ListGroup(){
    let citiesList = ["Olsztyn", "Paris", "London", "Tokyo"]
    function handleClick(event: MouseEvent){
        console.log(event)
    }

    return (
        <>
        <h1>List</h1>
        {citiesList.length===0 && <p>no city was found</p>}
            <ul className="list-group">
               {citiesList.map( (city, index)=><li
                        className="list-group-item"
                        key={city}
                        onClick={handleClick}
                        >{city}</li>)}
            </ul>
        </>
        )
}

export default ListGroup
```
















