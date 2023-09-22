#helion

strona Reacta > stwórz aplikację w REact ->
Trzy elementy, aby stworzyć aplikację webową:
- **menadżer pakietów** `npm`, `yarn`
- **bundler** (np. `webpack`, `parcel`) umożliwia pisanie kodu modułowego i pakowanie go w małe pakiety, aby zoptymalizować czas ładowania
- **kompilator** (np. `Babel`) pozwala na stosowanie nowych wersji JS przy zachowaniu kompatybilności  ze starszymi przeglądarkami

Zainstaluj dla Windowsa terminal `Conemu`


- `npm init -y ` -> package.json (nazwa od folderu)
- `npm install webpack --save-dev` (tryb deweloperski) (`--save` tylko na produkcji) -> aliasy
	- `-D` tylko deweloperski tryb,
	- `-S` w każdym trybie)


`npm i`  sprawdza *package.json* i kompiluje wszystkie paczki, jakie odnajdzie (==pliki json nie moga mieć przecinków na końcu bloków!!==)
add to package.json
```json
"license": "ISC",
   "devDependencies": {
   "webpack": "^5.75.0",
   "webpack-cli": "5.0.1"
  }
```

- `"webpack-cli": "5.0.1"` ręcznie dopisałem do `package.json`a, a potem `npm i`, aby do instalował `cli`
potem: 
#### `npm i react  react-dom -S`
czyli doinstalujemy `react` i `react-dom` w trybie deweloperskim oraz trybie produkcyjnym


### Checking `webpack`
add /src/index.js (`console.log("Hey") ;`)

in package.json:
```json
//..
 "main": "index.js",
  "scripts": {
    "start": "webpack --mode development"
  },
//...
```

w terminalu: `npm start` -> nowy folder `dist` > `main.js`


### aby aplikacja była dostępna w sieci bez możliwości sprawdzenia kodu:
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
`> npm i html-webpack-plugin -D`  -- OK (skopiuje /src/index.html do /dist/index.html)
oraz zmiana w `webpack.config.js`

```js
const HTMLWebPackPlugin = require("html-webpack-plugin")  ;

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
    },

    plugins: [
        new HTMLWebPackPlugin({
            template: './src/index.html',
            filename: './index.html'
        })
    ]
}
```

---
teraz potrzebujemy paczki
### `webpack-dev-server`
https://github.com/webpack/webpack-dev-server

`npm install webpack-dev-server --save-dev`

teraz zmiana w *package.json*:
```json
  "scripts": {

    "start": "webpack-dev-server --mode development --open",

    "build": "webpack --mode development"

  },
```

a instrukcja `npm start` uruchomi aplikację wraz z serverem (otworzy domyślną przeglądarkę)

























