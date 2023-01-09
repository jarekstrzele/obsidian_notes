[[_0 Good Parts of JS]]


---
# And thenthere was JavaScript

## History of JavaScript
Mosaic > Netscape > LiveScript (Java, Scheme, Self) -> JavaScript (subset of Java) -> JScript (from Microsoft) -> develop a standard ECMAScript
ECMAScript
- 1999 THird Edition ES3
- 2009 Fifth Edition  ES5
	- default
	- strict
- 2015 Sixth Edition ES6


## Objects
>[!object]
>an object is a dynamic collection of properties
>Every property has a key string that is unique within that object
> #### [keys] must be strings

- get 
	- `object.name`
	- `object[expression`
- set
	- `object.name = value;`
	- `object[expression] = values;`
- delete
	- `delete object.name;`
	- `delete object[expression]`
### object literals
an expressive notation for creating objects
```javascript
var my_object = {
	foo: bar,
	name: "value",
	"@#$%**": "refrw"
}
```

### Classes v Prorotypes
**Objects inherit from objects** - there are no classes
##### working with prototypes:
- make an object that you like
- create nw instances that inherit from that object
- customize the new object
classification and taxnonomy are not necessary


### delegation
differential inheritance (ob1 can't do something so it calls other object that can do it)

### Prototypal Inheritance
`Object.create(prototype)`

```javascript
var mother = {
 a: 1,
 b: 2
}
```
there will be also invisible pointer to `Object.prototype`

```javascript
var daughter = Object.create(mother);
```
daughter is empty but has a pointer to `mother` object that has a pointer to `Object.prototype`
`daughter.b += 2;` -> `b=4` will be store in `daughter` ==storing operators will always go into the top most object== but ==reading operators== always down


We can 
##### `Object.create(null)`

## Numbers
Every things in JS are objects
only one number type

**Associative Law does not hold**
`(a + b) + c === a + (b + c)`
produces false for some values of a,b,c
(above nine quadrillion)

#### methods
numbers are objects so have their methods (toExponential, toFixed, toPrecision, toString, ...)

new method:
```javascript
if (!Number.prototype.trunc) {
	Number.prototype.trunc = 
		function trunc(number){
			...
		}
}
```


#### are first class objects
can be:
- sotrd in a variable
- passed as a parameter
- return from a function
- stored in an object

have methods

#### Math object
abs, log, max, min, pow random, round, sin, floor, exp, cos, ceil ....

#### NaN
#javascript/nan
is a number (but is named 'Not a Number')
- special number
- result of undefined or erroneous operations
- toxic: any arithmetic operation with NaN as an input will have Nan as a result
- NaN is not equal to anything, including NaN
- `NaN === NaN` false
- `Nan !== NaN` true
- `isNaN(NaN)` true
- 
#### Infinity
`x = x + 1`
`Number.MAX_VALUE` 9007199252740992

## Booleans

`true    false`

## Strings
- a sequence of 0 or more 16-bit Unicode characters (UCS-2)
- immutable
- similar stings are equal
- `"` for external strings
- `'` for internal strings and characters

Convert numer to a string
```javascript
str = num.toString();
str = String(num); // better
```

String to number
```javascript
num = Number(str);
num = +str;

// or use the parseInt function
parseInt(str, 10)
// - convrts the value into a number
// - stoprs at the first non-digit character parseInt("12em") === 12
// parseInt("08") === 0
// paresInt("08", 10) === 8

```

Strings have a lot of methods


## Arrays
- array inherits from Object
- indexes are converted to strings and used as names for retrieving values
- very efficient for sparse arrays
- not very efficient in most other cases
- one advantage: no need to provide a length ot rype when reating an array

array literals
- `[]`

it has a lot of method

deleting by `spice` not by `delete`



## Dates, RegEx, and Types
### date
this finction is based on Java's Date class

### ReEx
http://jex.im/regulex helps to understands

### Types
All values are objects
EXCEPT `null` and `undefined`
	Use rather one of them
He recomends use `undefined`:
- it is the default value for variables and parameters
- it is the value of missing members in objects and arrays

#### FALSY VALUES:
- false
- null
- undefined
- ""
- 0
- NaN

#### Loosely typed
- any of these types can be stored in an variable, or passed as a parameter to any function
- the language is not *untyped*

#### Reference
- objects can be passed as arguments to functions, and can be returned by functions
	- objects are passed by referemce
	- objects are not passed by value
- the `===` operator comares object references not value (true only if both operands are the same object)

## JavaScript Syntax
JavaScript is syntactically a C family language

be careful with `+` as a concatenation operator:
if both operands are numbers:
	add them
else
	convert them both to strings
	`'$' + 3 + 4 = '$34'`

`+"42" = 42`
`Number("42") = 42`
`parseInt("42",10) = 42`

Division
`10/3` 3.333333333333

`%` it is the remainde operator not the modulo operator
`-1 % 8 // -1, not 7`

## Statements

### `trow`
You can throw any value
```javascript
throw new Error(reason);

throw {
	name: exceotionName;
	message: reason
};
```


### `try`
```javascript
try{
	plan_a();
} catch (ignore){
	plan_b()''
}
```



### `forEach`

### `for (name in object)`
don't use it
#javascript/for_in



