<<<<<<< HEAD
[[REACT/plurasight/React 17 Getting Started/_ 0 Getting Started]]
=======
[[REACT/React/plurasight/React 17 Getting Started/_ 0 Getting Started]]
>>>>>>> remotes/origin/master

-----------
# Modern JS

>[!ECMAScript]
>the official specification that JavaScript confomrs to

```javascript
{
	//Block Scope
	{ // nested block}
}

if (true){
	//Block Scope
}

function sum(a,b){
	//Function scope
	// 'var' inside the func scope is OK
	// because it doesn't leak out of the scope
	var result = a + b
}
```

`for (var i=1; i <=10; i++){//...}` but `i` is accessible out side the for loop, 
so use:
##### `let` or `const`

**OBJECT LITERALS**
```javascript
/*
	const obj = {
		key: value
	};
*/

const mystery = 'answer';
const inverseOfPI = 1/Math.PI;

const obj = {
	p1: 10,
	p2: 20,
	func1() {},
	func2: () => {},
	// dynamic
	[mystery]: 42,
	//InverseOfPI: InverseOfPI <=>
	InversOfPI
}


```

Objects are used to manage and to communicate data!!

## Desctructuring
#javascript/destructuring 

It works with objects and arrays.
```javascript
// const PI = Math.PI;
// const E = Math.E;
// const SQRT2 = Math.SQRT2;
const {PI, E, SQRT2} = Math;

// Somewhere in a React App
// const {Component, Fragment, useState} = require('react');
// useState();
```


==Destructuring also works inside function args==
```javascript
const circle ={
	label: 'circleX',
	radius: 2,
};

const cicleArea = ({radius}) => (PI * radius * radius).toFixed(2);

console.log(
	cicleArea(circle)
)
```

==ARRAY==
```javascript
const [first, second,, forth] = [10,20,30,40];

//In React the useState function returns an array of two items
const [value, setValue] = useState(initalValue);
```

==ARRAY and `...rest`===
```Javascript
//...REST
// first = 10
// restItems = [20,30,40]
const [first, ...restItems]= [10,20,30,40];

//a copy of restItems
const newArray = [...restItems];


```

==OBJECT and `...rest`==
```javascript
const data = {
	temp1:'001',
	temp2: '002',
	firstName: 'John',
	lastName: 'Doe'
}

const {temps1, temp2, ...person} = data;

//a copy of person objext
const newObject = {
	...person
}

```

## Template Strings
To define string use `" "` ors `' '` (they are equivalent)

or , in Modern JS,
` `` ` --> TEMPLATE STRINGS can be used as a template with dynamic values
You can inject any dynamic expression in JavaScript within these `${  }`


## Classes
Everything in JS is object including functions!!!!!!!!!!!!!
```JavaScript
class Person {
	constructor(name){
		this.name = name;
	}

	greet(){
		console.log(`Hello ${this.name}!`);
	}
}

class Student extends Person {
	constructor(name, level){
		super(name);
		this.level = level;
	}

	greet(){
		console.log(`Hello ${this.name} from ${this.level}`)
	}
}

const os = new Student("Mary", "2nd Grade");
os.greet = () => console.log('I am special');



```

## Promises and Async/Await
> When you need to work with asynchronus operations, you usually have to deal with promise objects.


>[!Promise object]
>It is an object that might deliver data at a later point in the program

```javascript
// const fetchData = () => {
//   fetch('https://api.github.com').then(resp => {
//     resp.json().then(data => {
//       console.log(data)
//     });
//   });
// };

const fetchData = async ()=> {
  const resp = await fetch('https://api.github.com');
  const data = await resp.json();
  console.log(data);
}

fetchData();
```















