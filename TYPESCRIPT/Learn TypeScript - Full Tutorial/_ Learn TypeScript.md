#freeCodeCamp  #typescript 
https://www.youtube.com/watch?v=30LWjhZzg50

>[!info] TypeScript
>- a superset of JavaScript
>- it doesn't add more features
>- it is about type safety
>	- not safety in JS:
>		- 2+"2" -> 22
>		- null + 2 -> 2
>		- undefined + 2 -> NaN
>- it is a development tool (the project still runs JS, in production it is JS)

**What Type Script does**:
- ==static checking== - whenever you are writing the code, the parser of the language or the entire of the language is constantly being analyzed by the IDE's.

development fow:
- you write your code in `.ts` (in React `.tsx`),
- that code is being transpiled into JS

Online TypeScript:
https://www.typescriptlang.org/play


-----
# Install TypeScript

In Windows use `GitBash`

- you can install global
`npm install -g typescript`
```bash
$ npm install -g typescript

added 1 package, and audited 2 packages in 22s

found 0 vulnerabilities
jarek@jarek-legion:~$ tsc -v
Version 5.1.6
```

- you can install loca (to that project)
``npm install typescript --save-dev``

---
# A First File

`intro.ts`
```ts
var user = { name: "jan", age: 10 };

var user_name = user.name;

console.log(user_name);
```

`tsc intro.ts` -> `intro.js`

---
# Types
- number
- string
- boolean
- null
- undefined
- void
- object
- array
- tupes
- ...
- any
- never

DOCUMENTATION
https://www.typescriptlang.org/docs/

the basics
https://www.typescriptlang.org/docs/handbook/2/basic-types.html


TS is very useful with function (it checks args as a input, and value that are returns)

`let varName: <lowercaseTypeName> = value`

```ts
let greetings: string = "Hello world" l

let num1: number = 6;
let num2: number = 6.23;

let isLoggedIn: boolean = false

greetings.toLowerCase() ;
console.log(greetings) ;

export {}
```


TS can automatically detect the type of a variable
```ts
let greetings = "Hello world" l

let num1 = 6;
let num2 = 6.23;

let isLoggedIn: boolean = false

greetings.toLowerCase() ;
console.log(greetings) ;

export {}
```













