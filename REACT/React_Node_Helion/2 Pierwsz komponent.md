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

---
zmiana w Header.js
```js
import React, { Component } from 'react' ;
import MenuButton from './components/MenuButton/MenuButton';

export default class Header extends Component{

    render(){
       return (
            <div>
               <ul>
                <MenuButton>Protfolio </MenuButton>
                <MenuButton>O mnie </MenuButton>
               <MenuButton>Kontakt </MenuButton>
               </ul>
            </div>
        )
    }
}
```

nowy komponent w /src/containers/Header/components/MenuButton/MenuButton.js:
```js
import React, { Component } from 'react' ;
export default class MenuButton extends Component{
    render(){
        return (
                <li>{this.props.children} </li>
          )
    }
}
```

do stylizacji użyjemy **less** 
`npm install less less-loader --save-dev`

zmiana w `webpack.config.js`
```js
   rules: [
            {
                test: /\.js$/,
                exclude: "/node_modules/",
                use: {
                    loader: "babel-loader"
                },
            },
            {
                test: /\.less$/i,
                use: [
                  // compiles Less to CSS
                  "style-loader", // creatres style nodes from JS strings
                  "css-loader", // translates CSS into CommonJS
                  "less-loader", // compiles Less to CSS
                ],
              },
        ]
    },
```

tworzymy nowy /MenuButton/styles/menuButton.less
```less
@menuColor: #009 ;
.menu-button{
    color: @menuColor;
}
```

i zmieniamy MenuButton.js
```js

```












