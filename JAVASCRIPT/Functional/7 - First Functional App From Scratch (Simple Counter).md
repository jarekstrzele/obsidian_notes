[[0- Intro functional programming (beginner udemy)]]


[[7 Counter App vs1]]

---
# Functional App Simple Counter
Configuration:
- install nodejs (on linux also Node Version Manager  ;  https://github.com/creationix/nvm)
- clone repo: https://github.com/knowthen/fpjs
- cd counter > atom . > `package.json` containts all dependencies, so to intall them `npm install`, after that npm creates a `node_modules` folder
- `webpack.xonfig.json` contains the configuration information web will use to build our app
- `index.js` is the single file we'll use to build the counter app

---
# Fundamental Building Blocks
## ==(immutable) DATA== and ==(pure) FUNCTIONS==

**For Counter app** we need:
- data: Number (count)
- functions
	- view
	- update

`npm install hyperscript hyperscript-helpers --save-dev`

`--save-dev` adds these dependencies to the list of dependencies in the package that json file

in the index.js:
```javascript
import h from 'hyperscript';
import hh from 'hyperscript-helpers'
```

`hyperscript-helpers` is the actual library that provides all the different html functions (i.e. `div` function to create *div tag* and `button` function to create *button tags*)
this library depends on some other libraries, so we also use `hyperscript`

`hh(h)` -- `hh` returns an object with properites for all the tag writing functions ->
`const { div } = hh(h);`





