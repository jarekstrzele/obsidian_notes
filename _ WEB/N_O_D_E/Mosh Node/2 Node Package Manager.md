#node 
[[_ 0 Node (Mosh)]]
https://www.npmjs.com

----
[[#Package.json]]
[[#Installing a Node Package]]
[[#Using a Package]]
[[#Package Dependecies]]
[[#Semantic Versioning -> ` ` (`caret`)]]
[[#upgrade node package]]
[[#outdated packages]]
[[#Devdependecies]]
[[#uninstall package]]
[[#global package]]
[[#Publishing your package]]
[[#Updating your own packages]]
[[#Recap]]


-----
to install  `npm`
`npm -i npm@5.5.1`


---
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
so I can easily restore these dependencies, if I delete `node_modules` folder inside my project by writing
### `npm i`


## git
add `.gitignore` file and write:
`node_modules/` 
git will ignore that folder

# Semantic Versioning -> `^` (`caret`)
```json
// 
   "mongoose": "^6.8.1",
    "underscore": "^1.13.6"
  }
  //...
```

the first number `6` / `1` is called the major version
the second one `8` / `13` is called the minor version 
the third one `1` / `6` is call the patch version (for bugs fixes)

e.g.
- developers find a bug in mognoose, they fix it and release a new version `6.8.2`
- the second number **minor version** add a new feature but not break the existing API (they add a new feature without breaking API, so a new version will be `6.9.0` - zero because in that version there is no bugs)
- the first number **major version** add a new feature and break API
- `^6.8.1` tells npm  that you want to use any mongoose that has the major version `6` (the same will be `6.x`)
- `~6.8.1`  the major version `6` and the minor version `8` (the same will be `6.8.x`)
- `6.8.1` only that version

--------
### `npm list` to see all installed dependencies
```js
$ npm list 
npm-demo@1.0.0 /home/jarek/Desktop/Prog/node_mosh/npm-demo
├── mongoose@7.1.0
└── underscore@1.13.6
```

```js
$ npm list --depth=1
npm-demo@1.0.0 /home/jarek/Desktop/Prog/node_mosh/npm-demo
├─┬ mongoose@7.1.0
│ ├── bson@5.2.0
│ ├── kareem@2.5.1
│ ├── mongodb@5.3.0
│ ├── mpath@0.9.0
│ ├── mquery@5.0.0
│ ├── ms@2.1.3
│ └── sift@16.0.1
└── underscore@1.13.6
```



------
### `npm view libraryName` to see all dependencies for that library
`npm view mongoose`

```js
$ npm view mongoose dependencies
{
  bson: '^5.2.0',
  kareem: '2.5.1',
  mongodb: '5.3.0',
  mpath: '0.9.0',
  mquery: '5.0.0',
  ms: '2.1.3',
  sift: '16.0.1'
}
```

`npm view mongoose dependencies`


----
# upgrade node package


`npm i install mongoose@2.4.2` install that version

-----
# outdated packages
I installed two outdated packages.
```js
$ npm outdated
Package   Current Wanted Latest Location           Depended by
mongoose  2.4.2  2.9.10   7.1.0  node_modules/mongoose    npm-demo
underscore 1.4.0  1.13.6  1.13.6  node_modules/underscore  npm-demo
jarek@jarek-legion:~/Desktop/Prog/node_mosh/npm-demo$ 
```

#### `npm update` 
this works only **with minor and patch** version!!!
--->
```js
$ npm update
//..
$ npm outdated
Package   Current  Wanted  Latest  Location               Depended by
mongoose   2.9.10  2.9.10   7.1.0  node_modules/mongoose  npm-demo
```


#### `npm install -g npm-check-updates `
```js
o$ npm i -g npm-check-updates
npm WARN deprecated @npmcli/move-file@2.0.1: This functionality has been moved to @npmcli/fs

added 334 packages, and audited 335 packages in 11s

66 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

```js
$ npm-check-updates
Checking /home/jarek/Desktop/Prog/node_mosh/npm-demo/package.json
[====================] 2/2 100%

 mongoose    ^2.4.2  →   ^7.1.0
 underscore  ^1.4.0  →  ^1.13.6

Run ncu -u to upgrade package.json
```

==dependecies are not installed==, only `package.json` is updated

### `npm install`
```js
$ npm install

added 21 packages, removed 1 package, changed 3 packages, and audited 26 packages in 1s

1 package is looking for funding
  run `npm fund` for details

found 0 vulnerabilities
jarek@jarek-legion:~/Desktop/Prog/node_mosh/npm-demo$ ncu -u
Upgrading /home/jarek/Desktop/Prog/node_mosh/npm-demo/package.json
[====================] 2/2 100%

All dependencies match the latest package versions :)
```

----------
# Devdependecies
You will install `jshint` (library to analyse a js code), but in the  development mode:
#### `npm i jshint --save-dev`
```js
$ npm i jshint --save-dev

added 31 packages, and audited 57 packages in 639ms

4 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

and `package.json` :
```json
//...
"dependencies": {
	"mongoose": "^7.1.0",
	"underscore": "^1.13.6"
},
"devDependencies": {
	"jshint": "^2.13.6"
}
//...
```


------
# uninstall package

`npm uninstall mongoose`


----
# global package

`npm install -g <name_of_package>`

example: `npm`, `ng`

`npm install -g npm` - upgrade your npm to the latest version


```js
$ npm -g outdated
Package   Current  Wanted  Latest  Location               Depended by
corepack   0.17.0  0.17.2  0.17.2  node_modules/corepack  global
npm        8.19.4   9.6.6   9.6.6  node_modules/npm       global
```

--------
# Publishing your package

- `mkdir lion-lib`
- `cd lion-lib`
-`npm init --yes`
- add a new file `index.js` (the entry point to your package )
index.js:
```js
module.exports.add = function(a,b){return a + b } ;
```

- create an account on npmjs (`npm adduser`) or login `npm login`
- `npm publish` (if you get an error, change the name in the `package.json` (add some random numbers))

If you publish your library, now in another project you can simply write  `npm i lion-lib` to install this library in the new project
```js
let lion = require("lion-lib") ;
let result = lion.add(1,2) ;
console.log(result) ;
```


----
# Updating your own packages
- you made some changes in your `lion-lib`
- in the terminal `npm version major` or `minor` or patch (you simple add a new function, so you have to change the minor number ==> `npm version minor`



---
# Recap



## NPM 
- Every Node application has a package.json file that includes metadata about the application. This includes the name of the application, its version, dependencies, etc. 
- We use NPM to download and install 3rd-party packages from NPM registry: 
- All the installed packages and their dependencies are stored under node_modules folders. 
- This folder should be excluded from the source control.
- Node packages follow semantic versioning: *major*.*minor*.*patch*
- Useful NPM commands are: 
	-  Install a package `npm i <packageName>`
	- Install a specific version of a package `npm i <packageName>@<version>`
	- Install a package as a development dependency `npm i <packageName> —save-dev`
	- Uninstall a package `npm un <packageName>`
	- List installed packages `npm list —depth=0`
	- View outdated packages `npm outdated`
	- Update packages `npm update`
	- To install/uninstall packages globally, use `-g` flag.













