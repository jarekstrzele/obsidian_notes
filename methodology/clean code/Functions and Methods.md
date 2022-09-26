

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


### Why "Levels of Abstraction" Matter?






















