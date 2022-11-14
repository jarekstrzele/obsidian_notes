

# Functions & Methods

## Number of parameters

> Calling the function should be readable 

>[!important] 
>MINIMIZE  the number of  parameters

the more parameters a function uses, the harder it  gets to call them 

### no params
function with ==no parameters== is easy to call `user.save()` - easy to understand and easy to call BEST POSSIBLE OPTION



### 1 param
==One parameter== `log(msg)` easy to understand and easy to read GOOD POSSIBLE OPTION

good
```js
function square(number){
	return number*number;
}

function emailIsValid(email){
	return email.includes('@');
}

function log(msg){
	console.log(msg);
}
```


### 2 params
 ==Two parameters== `Point(20,50)` - decent to understand, accaptable to call, USE WITH CAUTION 

good:
```js
function login(email, password){
	//...
}

login('jan@test.com', `topsecret`)

// ***********************
class Point{
	constructor(x,y){
		this.x=x;
		this.y=y;
	}
}

const point = new Point(5, 10)
```

bad:
```js
function log(msg, isError){
	if (isError){
		console.error(msg);
	} else {
		console.log(msg)
	}
}

log('Hi', false);
```

after refactorization
```js
function log(msg){
	console.log(msg);
}

function logError(errorMsg){
	console.error(errorMsg);
}
log('Hi');
logError('An eroor');

```


### 3 params
 ==three== parameters `calulate(3,2,'add')` challenging to understand and challenging t call , AVOID IF POSSIBLE

bad:
```js
class User{
	constructor(name, age, email){
		this.name = name;
		this.age = age;
		this.email = email;
	}
}

const user = new User('Jan', 31, 'jan@nowa.pl')
```

better:
```js
class User{
	constructor(userData){
		this.name=userData.name;
		this.age=userData.age;
		this.email=userData.email;	
	}
}

const user = new User({name: 'Jan', email:'jan@nowa.pl', age:34})
```

 
 ### >3 params
 ==more than three== `coords(10,3,21,1)` difficult to read & understand, difficult to call  , ALWAYS AVOID

EXAMPLE
okay:
```js
function saveUser(email, password){
 const user = {
		 id: createID(),
		 email: email,
		 password: password
	 };

	db.insert('users', user);
}

saveUser('ala@makota.pl', 'alamakota')
```

better
```js
function saveUser(user){
	db.insert('users', user)
}

saveUser(newUser);

```


### Dynamic Number of Parameters
These functions can have a lot of paramterers and are still easy to understand.

```js
function sumUp(...nums){
	let sum = 0;
	for(let num in nums){
		sum += num;
	}
	retrun sum;
}
const total1 = sumUp(10,20,30,40,-100);
const total2 = sumUp(2,3);
```

```python
def sumUp(*args):
	sum = 0
	for num in args:
		sum += num
		
	return sum

total1 = sumUp(10,20,30,40,-100)
total2 = sumUp(2,3)
```


### Problems with output parameters

>[!important] output
>Try to avoid output arguments
>Try to avoid side-effects

bad:
```js
function createId(user){
	user.id = 'u1';
}

const user = {name:'Jan'};
createId(user); // object User will be modified!!
```

okay (by modifying the function name):
```js
function addId(user){
	user.id = 'u1';
}

const user = {name:'Jan'};
addId(user); // object User will be modified!!
```

good:
```js
class User{
	constructor(name){
		this.name  = name;
	}

	addId(){
		this.id = 'u1';
	}
}

const = customer = new User('Jan');
customer.addId();
```

---
## Functions Should be Small & Do One Thing - Clean Body Function

>[!important] Clean Body Function
>Clean functions should be small, so split long functions into multiple functions
>==Functions Shoudl Do Exactly One Thing==

### What is One Thing?

>[!important] Different LEVELS od ABSTRACTION
>e.g. `email.includes('@') + saveUser(email, password)`
>- `includes` is a low-level API operation on a string
>- `saveUser` is a high-level, developer-defined function


High Level | Low Level
-- | --
`isEmail(email)` | `email.includes('@')`
We don't control how the email is validated <br> - we just want it to be validated | We control how the email is validated <br>  (`includes` is a method we can call on any string)
This is easy to read - <br> there is no room for interpretation | This might be technically clear but <br> the interpretation must be added by the reader


HIGH LEVEL  < ====  ======> LOW LEVEL




### Why "Levels of Abstraction" Matter?
>[!important]
>Functions should do work  in a level of abstraction below their name

good:
```js
function emailIsValid(email){
	retrun email.includes('@');
}
```
this function should return yes/no (true//false) based on the email validity


bad:
```js
// saveUser doesn't add any interpretation to the low level code
// there is a too huge gap between LoA in the function name and the if condition
function saveUser(email){
	if(email.includes('@')){
		...
	}
}
```
this function should orchestrate all the steps that are required to save a user


---
>[!important]
>Try Not to Mix Levels of Abstraction in one of the same function

bad:
```js
if(!email.includes(`'@'`)){
	console.log('Invalid email!')
} else {
	const user = new User(email)
	user.save()
}
```

`includes` - a low level
`save` - a very heigh level


good:
```js
if(isEmail(email)){
	showError('Invalid email');
} else {
	saveNewUser(email)
}
```



## When Should You Split?

## Rule of Thumb

### 1. extract code that works on the same functionality
```js
user.setAge(31)
user.setName("Jan")
```

remove a block of code from one function and put it into another function
change into
```js
user.update({age:31, name:"Jan"})
```

### 2. Extract code that requires more interpretation than the surrounding code

```js
if(!email.include('@')){
	saveNewUser(email);
}
```

change into:
```js
if(!isValid(email)){
	saveNewUser(email);
}
```

EXAMPLE
bad (mixed level of abstraction)
```js
function createUser(email, password){
 if(!email || !email.includes('@') || !password || password.trim() === ''){
	 console.log('Invalid input!')
	 return;
 }


const user = {
	email:email,
	password: password,
};
	database.insert(user);

}
```

REFACTOR

new functions
```js
function inputIsNotValid(email, password){
	return !email || !email.includes('@') || !password || password.trim() === ''
}

function showErrorMsg(msg){
	console.log(msg);
}

function saveUser(email, password){
	const user = {
		email: email,
		password: password,
	};
database.insert(user);
}

function validateINput(email, password){
	//if(inputIsNotValid(email, password)){
	 //showErrorMsg('Invalid input');
	 //return;
	 thow new Error('Invalid input!');
 }

}
```


after refactorization:
```js
function createUser(email, password){
 
  validateInput(email, password);
  saveUser(email, password);
}

function handleCreateUserRequest(request){
 try {
	 createUser('test@text.pl', 'Tester');
 } catch(error){
	 showErrorMessage(error.message);
 }
}
```




### Stay DRY  - Don't Repeat Yourself
You might want to split function into smaller pieces because REUSABILITY matters!!

>[!important] Don't Repeat Yourself
>	Don't write the same code more than once.
>- whenever you need to change something about that code (logic, error) and you repeated yourself, you need to make this change in multiple places

To recognise that your code "is not DRY":
- you find yourself copy & pasting code
- you need to apply the same change to multple places in your codebase

---
==MAKE REASONABLE DECISIONS AND DON'T SPLIT IF==
- you are just renaming the operation
- finding the new function wil take longer than reading the extracted code
- can't produce a reasonable name for the extracted function


----
### Try Keeping  Your Functions PURE

> [!note] Pure Function
>This is a function which for the same input generates the same output.
>No side effects.


PURE
```js
function generateid(userName){
	const id = 'Id_'+userName;
	return id;
}
```

IMPURE
```js
function generateId(UserName){
	const id = userName + Math.random().toString();
	return id;
}
```



> [!note] side effect
> a side effect is an operation which does not just act on function inputc and change the function output but which instead **changes the overall system/rogram state**.

PURE without side effects
```js
function createuser(email, password){
 cont user = new User(email, password);
	reutn user;
}
```

IMPURE with side effects
```js
function createuser(email, password){
 cont user = new User(email, password);
	startSession(user);
	reutn user;
}
```

another side effect
```js
let lastAssignedId;

function generatedId(userName){
	const id ='id_' + userName;
	lastAssignedId = is;
	return id;
}
```


AVOID UNEXPECTED SIDE EFFECTS
- the name of a function should signal or imply that a side effect is like to occur
	- `saveUser()` side effect expected
	- `isValid()` side effect not expected (so `console.log` inside this function will make a side effect)
	- `showMessage()` side effect expected  (show msg has to change the state of the program)
	- `createUser()` side effect not necessarily expected ("create" has a lot of interpetation)
- move the side effect into another function/place


### Unit Testing Help

1. Can you easily test a function?
	1. YES -> Great, probably you have a clean code
	2. NON -> Consider splitting your function, and return to firtst point

















