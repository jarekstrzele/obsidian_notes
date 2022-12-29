#helion

- `npm init -y ` -> package.json (nazwa od folderu)
- `npm install webpack --save-dev` (tryb deweloperski) (`--save` tylko na produkcji) (`-D` tylko deweloperski tryb, `-S` w każdym trybie)

`npm i`  sprawdza *package.json* i kompiluje wszystkie paczki, jakie odnajdzie (==pliki json nie moga mieć przecinków na końcu bloków!!==)
add to package.json
```json
"license": "ISC",
   "devDependencies": {
   "webpack": "^5.75.0",
   "webpack-cli": "5.0.1"
  }
```
`npm i react  react-dom -S`

### Checking `webpack`
add /src/index.js (`console.log("Hey") ;`)

in package.json:
```json
//..
 "main": "index.js",
  "scripts": {
    "start": "webpack ==mode development"
  },
//...
```

w terminalu: `npm start` -> nowy folder `dist` > `main.js`


### aby app była dostępna w sieci bez możliwości sprawdzenia kodu:
do package.json dodaj:
```json
  "scripts": {
    "start": "webpack --mode development",
    "build":  "webpack --mode development"

  },
```

`npm run build`

to install Babel:
https://medium.com/@JedaiSaboteur/creating-a-react-app-from-scratch-f3c693b84658
```bash
npm install --save-dev @babel/core@7.1.0 @babel/cli@7.1.0 @babel/preset-env@7.1.0 @babel/preset-react@7.0.0
```

teraz plik konfiguracyjny dla Babela
- w głównej ścieżce projektu `.babelrc`
- z w/w/ strony wklej do pliku, jakich paczek chcesz używać
```
{

"presets": ["@babel/env", "@babel/preset-react"]

}
```


teraz nowy plik `webpack.config.js` (główna ścieżka) (definicja sposobu korzystania z bibliotek babela)
```js
module.exports = {
    module: {
        rules: [
            {
                test: /\.js$/,
                exclude: "/node_modules/",
                use: {
                    loader: "babel-loader"
               }
            }
        ]
    }
}
```

teraz w pliku /src/`index.js` tworzymy pierwszą app:
```js
import React from 'react' ;
import ReactDOM from 'react-dom' ;

const Index = () => {
    return <div>Hello React </div> ;
}

	ReactDOM.render(<Index/>,   document.getElementById("app"));
```

nowy plik index.html
```html
<!DOCTYPE html>
<html lang="pl" dir="ltr">
    <head>
        <meta charset="utf-8" />
    </head>
    <body>
        <div id="app">
        </div>
    </body>
</html>
```

`> npm i babel-loader -D`  -- OK
`> npm start `

aby /src/index.html został skopiowany do /dist/ jeszcze:
`> npm i html-webpack-plugin -D`
oraz zmiana w `webpack.config.js`


































