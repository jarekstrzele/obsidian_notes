
<<<<<<< HEAD
[[_ Clean Code]]
=======
[[Clean Code]]
>>>>>>> remotes/origin/master

>[!imortant] Clean Code
>- it is not about whether code works
>- it is a code 
>	- easy to **read** and **understand**
>	- concise
>	- avoid 
>		- unintuitive names
>		- complex nesting
>		- big code blocks
>	- follow common best practices and patterns

>CLEAN CODE IS EASY TO UNDERSTAND

>your code is like an essay


# Names
>[!imporant] overarching rule
>Names should be meaningful !!!!! (to be readable)
>```python
>p = X();
>p.save()
>
>#####
>user = User()
>user.save()
>```

## Name Casing
### snake_case
- `is_valid`, `send_response`
- Python
- variables, functions, methods

### camelCase
- `isValid`, `sendResponse`
- Java, JavaScript
- variables, functions, methonds

### PascalCase
- `AdminRole`
- Python, Java, JavaScript
- classes

### kebab-case
- `<side-drawer>`
- HTML
- Custom HTML Elements




## Variables, Constants, Properties
They are DATA CONTAINERS, 
so 
use ==nouns== or ==short phrases with adjectives==
```JavaScript
const userData = {};
const isValid = false;
```

object | number or string | boolean
---|---|---
describe the value | decribe the value | answer a true/false question
`user`, `database`|`name`, `age`| `isActive`, `loggedIn`
some details without redundancy | some details without redundancy |some details without redundancy 
`authenticatedUser`, `sqlDataBase` | `firstName` |`isActiveUser`

what is stored | bad names | okay names | good names
---|---|--- |---
a user object | `u`, `data` | `userData`, `person` |  `user`, `customer`
user input | `v`, `val` | `correct`, `validatedInput` | `isCorrect`, `isValid`



## Functions & Method
They are COMMANDS or CULCULATED VALUES
so
use ==verbs== or  ==short phrases with adjectives==
```js
sendData();
inputIsValid();
```

function performs an operation | function computes a Boolean
--- | --- 
describe the operation | Answer a true/false question
`getUser()`, `response.send()` | `isValid`, `purchase.isPaid()`
with more details | with more details
`getUserByEmail()` | `emailIsValid()`

what does the function do? | bad names | okay names | good names
---|---|---|---
save user data to database | `process()`, `handle()` | `save()`, `storeData()` | `savrUser()`, `user.store()`
validate the user input | `process()`, `save()` | `validateSave()`,`check` | `validate()`, `isValid()`
``

## Classes
Use classes to create "things" (classes are typically instanstiated)
so
use ==nouns== or ==short phrases with nouns==
```js
class User {}

class RequestBody{}
```

classes:
- describe the object: `User`, `Product`
- more details: `Customer`, `Course`

Which object is describe? | Bad Names | Okay Names | Good Names
---|---|---|---
a User | `class UEntity`, `class ObjA` | `class UserObje`, `class AppUser` | `class User`, `class Admin`
a database | `class Data` ,`class DataStorage` | `class Db`, `class Data` | `class Database`, `class SQLDatabase` 


## Errors and Pitfalls
- ==redundant information  in names==
	- bad: `userWithNameAndAge = User('Max', 33)`
	- good: `user = User('Max', 31)`, newUser, loggedInUser
- ==slang, unclear abbreviations&disinformation==
	- slang: `product.diePlease()` (good: `product.remove()`), `user.facePalm()`(good:`user.send.ErrorMessage()`)
	- ==abbreviations==: `message(n)` (good: `message(newUser)`), `ymdt='20220121CET'`(good: `dateWithTimezone='20220121CET'`)
	- ==disinformation==: `userList = {a:.., b: ...}` (good: `userMap={...}`), `allAccounts = accounts.filter()` (good: `filteredAccounts=accounts.filter()`)
- ==indistinctive names==:
	- `analytics.getDailyData(day)`(good:`analytics.getDailyReport(day)`)
	- `analytics.getDayData()` (good: `analytics.getDataForToday()`)

>==Be Consistent==
>- at the beginning you can use: `getUsers(), fetchUsers(), retrieveUsers()` (all good)
>- stick  with the name that you choose throughout your entire program












