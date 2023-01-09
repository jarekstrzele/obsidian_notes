
[[0-Modern JS from the Beginner]]

[[3 _DOM Manipulation & Events]]

---
# JavaScript Language Fundamentals


```js
console.time("Start")
	console.log({a:1, b:2});
	console.table({a:100, b:21});
	console.error('This is some error');
	console.clear();
	console.warn("THis is waring");
console.timeEnd("End")


```


## Data types
==primitive data type==
stored directly in the location the variable accesses
stored on the stack
	- string
	- number
	- boolean
	- null
	- undefined
	- symbols (ES6)

==reference data type==
Accessed by reference
objects that are stored on the heap
a pointer to a location in memory
	- arrays
	- object literals
	- funcitons
	- dates
	- anthing else

```js
const name = "John Dow";

console.log(typeof name); //-> string

const sym = Symbol();
typeof sym //-> symbol

```


---

## Type Conversion

`String(5)` -> '5'    
`(5).toString()`

String(new Date())
(new Date()).toString()

String([1,2,3])-> `1,2,3`
([1,2,3]).toString()


Number('5')
Number(true)
Number(null) //->0
Number('hell0') // -> NaN
parseInt('100')
parseFloat('10.21')

string + number -> string

---


`Math.floor(Math.random() * 20 +1)` -> random int (0/1-20)

#javascript/string
```js
s = "Something new"
s.toUpperCase();
s.toLowerCase();
s.indexOf(1); //-> -1
s.indexOf('t');// -> 4
s.lastIndexOf('3'); // -> 11

s.charAt(0); // -> S
s.charAt(s.length-1);// -> w

s.substring(0,4); // -> 'Some'
s.slice(0,4); //-> 'Some'
s.slice(-3); //-> 'new'


// split returns a list
s.split(' '); //-> ['Something', 'new']

s.replace('new', 'old'); // ->'Something old'
// but: s -> 'Something new'

s.includes('new'); //-> true

```

---
## Template literals
#javascript/template_literals

use backsticks!!  ``

` ${ variable_name }  `
`${ expression } -> ${2+2} ` 
` ${ function } -> ${hello()} `
` ${condition} -> ${age > 30 ? 'Over 30' : 'Under 30'}`


---
## Arrays
#javascript/array 

```js
const n = [12,2];
const n2 = new Array(1,True);

Array.isArray(n); //-> true
Array.isArray('3'); // -> false

// find index of value
n.indexOf(2);// -> 1

// mutating arrays
// add on to end
n.push(233);
// add on to front
n.unshift(22);
// take off from end
n.pop();
// take of from front
n.shift()

// splice /cut
n.splice(start_index, end_index);

# sorting
# inscending
n.sort(function(x,y){return x-y;})
# descending
n.sort(function(x,y){return y-x;})

n.find(some function);

```

---
## Object literals
```js
const person ={

	key: value,
	...
	func_name: function() { 
		//this 
	}

}

```


---
## Date & Time
```js
const today = new Date(); // typeof today -> object

const birthday = new Date('9-10-1981 11:25:00');
const b = new Date('Semptember 10 1981');
const c = new Date('9/10/1981');

c.getMonth() // setMonth
c.getDate() // setDate
c.getDay() // setDay
c.getFullYear(); //setFullYear
birthday.getHours(); //getMinutes, getSeconds, ..

```

---
## Function 
### function declarations
```js
function foo(ar=21){
	// do something
	// maybe something return
}

foo(122)
```

### function expressions
```js
const square = function(x){
// do something
}

square(8)

```

### Immediatley Invokable Function Expressions - IIFEs
```js
(function(){
	console.log('IIFE Run...');
})()

(function(name){
	console.log('Hello ' + name);
})('Brad');

```

---
## Loops

```js

const cars=['Ford', 'Chevy', 'Honda', 'Toyota'];

for(let i=0; i <cars.length; i++){
	console.log(cars[i]);
}
// forEach
cars.forEach(function(car){
	console.log(car);
})

cars.forEach(function(car, index){
	console.log(`${index} : ${car}`);
})

//////////////
// MAP
const users = [
	{id:1, name:'John'},
	
	{id:2, name:'Sara'},

	{id:2, name:'Karen'},
]

const ids = users.map(function(user){
	return user.id;
});
// returns a list of id

// FOR IN LOOP
const user = {
	firstName: "Joe",
	lastName: "Doe",
	age: 40
}
for(let x in user){
	console.log(`key=${x} : value=${user[x]} `);
}

```

---
## A look At the Window Object
```js
windows.alert("Attantion")l
alert("dq");

const input = prompt();
console.log("jes");

window.outerHeight;
window.outerWidth;


window.innerHeight;
window.innerWidth;

// scroll points
window.scrollY;
window.scrollX;

// location object
window.location

window.location.hostname;
window.location.port;
window.location.href;
window.location.href='http://google.com';;
window.location.search;

window.history.go(-2);
window.history.length;

//Navigator Object
window.navigator;
window.navigator.appName;
window.navigator.userVersion;
window.navigator.platform;
window.navigator.language;
```


---
## SCOPE
```js
// global
var a = 1;
let b = 2;
const c= 3;

// function scope
function test(){
	var =a 4;
	let b = 5;
	const c = 6

}

// block scope
// if, loop
if(true){
	 var a = 4;//still global scope
	 let b = 5;
	 const c = 6;
}

for(let =; a <10; a++){
//do something
// 'a' stays block scope

}

for(var =; a <10; a++){
//do something
// 'a' still global

}

```





