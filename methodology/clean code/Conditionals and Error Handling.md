[[_ Clean Code]]



# Control Structures and Errors

==ARROW CODE==  you have to ==avoid it==
```
if
	elif
		elif
			elif
				elif
				else
			else
		else
	else
else

```

## General concepts
1. avoid deep nesting
2. use factory fuctions and polymorphism
3. prefer Positive chacks (`if isEmpty` vs `if isNotEmpty`)
4. utilize errors


## GUARDS -> to fail fast
a first example:
```js
function someFN(){
//...
	if (email.includes('@')){
		// ....
		}
	//...
}
```
change to a code with a guard:
```jsx
function someFN(){
// ... 
// this If is a gard
if (!email.includes('@')){
	return; // fail fast
	}
//...
}
```

a second example:
```js
//...
if (user.active){
	if (user.hasPurchases()){
		// ....
	}
}
//...
```
change to a code with two guards:
```js
if (!user.active){
	return; // fast fail
}

if (!user.hasPurchase()){
	return; // fast fail
}

```
**INDICATOR for a GUARD**
Your `if` statement with a lot of code inside it where you maybe have a `else` statement with some error msg

**How make a guard**
Inverse the check
`if (<condition>) { // do sth}`
--> ` if not(<condition>) { return ;} `, `break`, `continue`
OR
`if not(<condition>) { // do sth }`
--> ` if (<condition>) { return ;} `, `break`, `continue`

## Extraction control struc & preferring positive
Simpler to read: positive statement 

```js
// ....
function processTransactions(transactions){

	if (transactions || transactions.length===0){
		console.log("No transactions provided!") ;
	return ;
 }
//...
} ...
```

extract (Level of Abstraction)
```js
function isEmpty(transactions){
	return transactions || transactions.length===0 ;
}

function showErrorMessage(msg){
	console.log(msg) ;
}

function processTransactions(transactions){
	if (isEmpty(transactions)) { 
		showErrorMessage("No transactions provided") ;
		return ;
	}
	//....
```

TIP
If you have nested `if` maybe one "big" `if` transform to a function
```
...
else if
	if
		else if
		else if
		else
	else
...

```

maybe transform into
```
...
else if
	aNewFunction() ;
	else
...

function aNewFunction(){
	if
		else if
		else if
		else
}
```

```js
function registerNewUser(user){
	if (user.firstName && user.lastName){
		if (user.account > 10000) {
			if (user.city==="New York"){
				user.level = "Super Gold" ;
			}
			else if (user.city === "Los Angeles"){
				user.level = "Gold" ;
			}
			else {
				user.level = "Silver" ;
			}
		}
	}
.///
}

```
transform ->

```js
function mapFromCityToLevel (city){
	cityLevel = {"New York": "Extra Golds", "Los Angeles":"Super Gold"}
	return cityLevel[city]
	
}

function addGoldAttr(user){
	user.level = mapFromCitytoLevel(user.city);
	//if (user.city==="New York"){
	//			user.level = "Extra Gold" ;
	//		}
	//		else if (user.city === "Los Angeles"){
	//			user.level = "Super Gold" ;
	//		}
	//		else {
	//			user.level = "Gold" ;
	//		}
}


function registerNewUser(user){
	if (user.firstName && user.lastName){
		if (user.account > 10000) {
			addGoldAttr(user);
		}
	}

//....
}
```


## Embrace error and Error  Handling

> Throwing + handling  errors  can replace `if` statements and leads to more focus functions

>[!rule] Simple rule
>If something is an error ---> make it error

constructing errors without using built-in errors
```js
if(!isEmail){
	return {code: 422, message: 'Inavalid Input!'} ;
}
```

better way
```js
if(!isEmail){
	const error = new Error('Input valid') ;
	error.code = 422 ;
	throw error ;
}
```
`throw error` stops the program

example
```js

try{
	processTransactions(transactions)
}catch(error){
	showErrorMessage(error.message) ;
}


function processTransactions(tranactions){
	if (isEmpty(transactions)){
		const error = Error('No transactions provided!') ;
		error.code = 1 ;
		throw error ;
	}

//....
}
```

second transformation

```js

try{
	processTransactions(transactions)
}catch(error){
	showErrorMessage(error.message) ;
}


function processTransactions(tranactions){
	validateTransactions(transactions);
	//if this function thows an error, the program will stop 

//....
}

function validateTransactions(transactions){
	if (isEmpty(transactions)){
		const error = Error('No transactions provided!') ;
		error.code = 1 ;
		throw error ;
	}
}
```


## Using factory functions and polimorphism

>[!important] factory function
>It is a function that produce something (objects, arrays, ...).
>

example
```js
function buildUser(name, age){
	return {name: name, age: age};
}
```

>[!important] polimorphism
>What a method does depends on some other factors

```js
function feedCat(){
	console.log("Prepere milk") ;
	
}

function feedDog(){
	console.log("Prepere beef") ;
}

function feedRabbit(){
	console.log("Prepere salad") ;
}

function feedAnimal(animal){
	if (animal.species === "dog") {
		feedDog();
	}
	else if (animal.species === "cat") {
		feedCat() ;
	} 
	else {
		feedRabbit() ;
	}
}

let c = {animal.species === "cat"} ;
feedAnimal(c);

```

refactoring
```js
function feedingFactory(animal){
	const feeding = { feed: null } ;
	if (animal.species === "dog") {
		feeding.feed: feedDog;
	}
	else if (animal.species === "cat") {
		feeding.feed=feedCat ;
	} 
	else {
		feeding.feed = feedRabbit ;
	}
	return feeding;
}

let c = {animal.species === "cat"} ;
let d = {animal.species === "dog"} ;

c.feeding = feedingFactory(c);
c.feeding.feed();

d.feeding = feedingFacotry(d)
d.feeding.feed();

```
















