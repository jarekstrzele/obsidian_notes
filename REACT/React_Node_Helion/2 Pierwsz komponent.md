[[_ 0 React Node]]

tworzymy `/src/containers/App/App.js`:
```jsx
import React, { Component } from 'react' ;

export default class App extends Component{
    render(){
        return (
            <div>
                Przykładowa treść
            </div>
        )
    }
}
```


index.js:
```js
import React from 'react' ;
import ReactDOM from 'react-dom' ;
import App from './containers/App' ;

ReactDOM.render(<App/>, document.getElementById("app"));
```


--------------
nowy `'src/container/Header/Header'`
```jsx
import React, { Component } from 'react' ;

export default class Header extends Component{

    render(){
        return (
            <div>
               <ul>
                <li>Protfolio </li>
                <li>O mnie </li>
                <li>Kontakt </li>
               </ul>
            </div>
        )
    }
}
```

zmiana a App.js
```js
import React, { Component } from 'react' ;
import Header from '../Header/Header' ;
export default class App extends Component{

    render(){
        return (
            <div>
                <Header />
            </div>
        )
    }
}
```








