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



# Managing States
 ```typescript
import {  useState } from "react"

function ListGroup(){
    let citiesList = ["Olsztyn", "Paris", "London", "Tokyo"]
    const [selectedIndex, setSelectedIndex] = useState(-1)
	
    return (
        <>
        <h1>List</h1>
        {citiesList.length===0 && <p>no city was found</p>}
            <ul className="list-group">
               {citiesList.map( (city, index)=><li
                        className={selectedIndex===index ? "list-group-item active" :"list-group-item"}
                        key={city}
                        onClick={()=>setSelectedIndex(index)}
                        >{city}</li>)}
            </ul>
```

# Props and interface
#react/interface

`ListGroup.tsx`
```typescript
import {useState } from "react"

interface Props{
    items: string[],
    heading: string
}

function ListGroup({items, heading}: Props){
    const [selectedIndex, setSelectedIndex] = useState(-1)

    return (
        <>
        <h1>{heading}</h1>
        {items.length===0 && <p>no city was found</p>}
          <ul className="list-group">
               {items.map( (city, index)=><li
                        className={selectedIndex===index ? "list-group-item active" :"list-group-item"}
                        key={city}
                        onClick={()=>setSelectedIndex(index)}
                        >{city}</li>)}
            </ul>
        </>
        )
}
```

`App.tsx`
```typescript
function App(){
  let citiesList = ["Olsztyn", "Paris", "London", "Tokyo"]
  return <div><ListGroup items={citiesList} heading="Cities"/> </div>
}

export default App
```


# Passing Function via Props

change `App.tsx` (add `handleSelectItem` function and a new attribute `obSelectItem`)
```typescript
function App(){

  let citiesList = ["Olsztyn", "Paris", "London", "Tokyo"]
  const handleSelectItem = (item: string )=> {
    console.log(item)
  }

  return <div><ListGroup items={citiesList} heading="Cities" onSelectItem={handleSelectItem} /> </div>

}
```

change `ListGroup` component (add a new attribute in `interface`)
```typescript
interface Props{
    items: string[],
    heading: string,
    onSelectItem: (item: string) => void
}
  

function ListGroup({items, heading, onSelectItem}: Props){
```
and add it in jsx
```typescript
{items.map( (city, index)=><li
                        className={selectedIndex===index ? "list-group-item active" :"list-group-item"}
                        key={city}
                        onClick={()=>{
                            setSelectedIndex(index)
                            onSelectItem(city)
                        }}
                        >{city}</li>)}
```


# Passing children
How to create component that accept children? — use the `children Props`

==Extension for VS Code - `ES7+`==

a new component `Alert.tsx`
```typescript
const Alert = () => {
  return (
    <div>
      <h1 className="alert alert-primary">Aleert</h1>
    </div>
  )
}

export default Alert
```

on the page `bootstrap>component>Alert`
https://getbootstrap.com/docs/5.3/components/alerts/

```typescript
interface Props{
    children: string
}

const Alert = ({children}: Props) => {
  return (
    <div>
      <h1 className="alert alert-primary">{children}</h1>
    </div>
  )
}
```


`App`
```typescript
return (
    <div>
      <Alert>
        Hello world
      </Alert>
    </div>
  )
```

If you want to pass HTML content, change the type of children to `ReactNode`.
`Alert`
```typescript
interface Props{
    children: ReactNode
}
```


`App`
```typescript
 return (
    <div>
      <Alert>
        Hello <span>world</span>
      </Alert>
    </div>
  )
```





