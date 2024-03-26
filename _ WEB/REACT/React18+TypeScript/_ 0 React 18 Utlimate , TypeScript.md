#mosh  #react 

-------
[[1 Building Components - React 18 Utlimate]]





------

`npm creact vite@latest app-name -- --template react`

`npm run dev`

in this project:
- `npm create@latest app-name`
- select React
- select TypeScript  `.ts` or `.tsx`

# First Component
`App.tsx`
```typescript
import Message from "./Message"

function App(){
  return <div><Message /> </div>
}

export default App
```

`Message.tsx`
```typescript
function Message(){

    const name = "tom"

    if(name) return <h1>Hello {name}</h1>
    else return <h2>Hello World!</h2>
}

export default Message
```






