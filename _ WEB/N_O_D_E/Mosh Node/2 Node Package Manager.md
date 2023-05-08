
[[_ 0 Node (Mosh)]]

https://www.npmjs.com

to install  `npm`
`npm -i npm@5.5.1`


# Package.json
It includes some basic information about your app (metdata):
- name
- version
- authors
- git repo 
- ...
`npm init`

==Before adding any node packages to your project , you need to create a package.json file==

#### `npm init --yes`  -> create `package.json` 


# Installing a Node Package
How to add third party packages?
www.npmjs.com
`npm i underscore` (*underscore* is popular JS labray)
```shell
> npm i underscore
npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead.

added 1 package, and audited 2 packages in 1s

found 0 vulnerabilities
```

in package.json
```json
//...
 "author": "",
 "license": "ISC",
 "dependencies": {
   "underscore": "^1.13.6"
  }
```



# Using a Package
index.js
```js
var _ = require('underscore') ;
//order to find:
//1. core moduel
//2. File or folder
//3. node_modules
var result = _.contains([1,2,3], 3) ;
console.log(result);
// true
```



# Package Dependecies
`npm i mongoose` installs a mongoose module

I have in package.json
```json
//....
  "license": "ISC",
  "dependencies": {
    "mongoose": "^6.8.1",
    "underscore": "^1.13.6"
  }
```
so I can easily restore these dependencies, if I delete `node_modules` folder inside my project by writing `npm i`


## git
add `.gitignore` file and write:
`node_modules/` 
git will ignore that folder

# Semantic Versioning -> `^`
```json
//....
   "mongoose": "^6.8.1",
    "underscore": "^1.13.6"
  }
  //...
```
















