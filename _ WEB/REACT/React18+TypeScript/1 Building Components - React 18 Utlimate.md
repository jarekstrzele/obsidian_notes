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
a new folder `components` inside a new file `ListGrou`





