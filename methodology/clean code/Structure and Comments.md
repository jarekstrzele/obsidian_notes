[[_ Clean Code]]

# Structure & Comments

## Bad Comments

>[!important]  Avoid comments
>the names should be self-explanatory, so
>if it is possible, avoid comments

### redundant information
 ```js
 if (driver === 'sql'){
	 // connect to the SQL Driver if "driver is et to SQL"
	 this.dbEngine = sqlDriver;
} else {
	// otherwise, connect to MongoDB
	this.dbEngine = mongoDbDriver;
}
```

### Dividers / Block Markers
```js
// ############
// GLOBALS
// ############
let sqlDriver;
let mongoDBDriver;

// ##########
// CLASSES
// ##########
class Database{
//...
}
```

### misleading comments
```js
insertData(data){
 this.dbEngine.insert(data); //update a user
}
```

### commented-out code
```js
findOne(id){
 //todo: needs to be implemented
}

// this commented function should be deleted
// findMany(filter){           
//	this.dbDriver.find(filter);
//}
```


## Good Comments
### Legal comments
```
// (c) Jan Kowalski / Technikum 9
// Created in 2022

```

### Explanations which can't be replaced by good naming
```js
// accepts [text]@[text].[text], i.e. it simply requires an "@" and a dot
const emailRegex = /\S+@\S+\.\S+/;
```

### Warnings
```js
// Only works in browser environemtn
localStorage.setItem('user', 'test@text.com');
```

### Todo notes
```js
findOne(id){
// Todo: Need to be implemented
}
```

### Documentation Strings
```python
def foo():
""" documentation strings """

```



## Code Formatting
> Code Formatting Imporves Readability & Transports Meaning

### Vertical Formatting
- space between lines
- grouping of code

> Code should be readable like an essay - top to bottom without too many "jumps" - SMOOTH READING FLOW

General Rules:
- consider splitting files with multiple concepts (e.g. classes) into multiple files
	- e.g. one class per files
- in one file: 
	- different concepts ("areas"; e.g. mutiple methods within one at the same class) should be separated by spacing
```python
class User:

	def __init__(self, name, age):
		self.name=name
		self.age=age

	def talk(self):
		print(f"I am {user.name});
```
-			  
	- similar concepts ("areas") should not be separated by spacing
```js
const logStorage = new DiskStorage('logs');
const userStorage = new DiskStorage('user');
```
-
	- Related concepts should be kept close to each other
 ```js

const path = required('path');
const fs = require('fs');

class DiskStorage{

	constructor(storageDirectory){
		this.storagePath=path.join(_dirname, storageDirectory)
		this.setupStorageDirectory();
	}

	setupStorageDirectory(){
		if(!fs.existsSync(this.storagePath)){
			this.createStorageDirectory();
		} else {
			console.log('Directory exists already.');
		}
	}

 }
```


### Horizontal Formatting
- indentation
- space between code
- line width

> Lines of code should be readable without scrolling - avoid very long "sentences"

##### use indentation - even if not required technically

BAD
```js
class DiskStorage{

constructor(storageDirectory)this.storagePath=path.join(_dirname,storageDirectorytthis.setupStorageDirectory();}
```

GOOD
```js
class DiskStorage{

	constructor(storageDirectory){
		this.storagePath=path.join(_dirname, storageDirectory)
		this.setupStorageDirectory();
	}
```

##### Break ling statements into mutiple shorter ones

BAD
```js
createStorageDirectory(){
	fs.mkdir(path.join(__dirname, 'temp', '2022-10', 'image'), this.handleOperationCompletion);
}
```

GOOD
```js
createStorageDirectory(){
	const storagePath = path.join(__dirname, 'temp', '2022-10', 'image');
	fs.mkdir(storagePath,
			 this.handleOperationCompletion);
}
```

##### Use clear but not unreadably long names
```js
createStorageDirectory(){
	const storagePathForStoringImagesInATemporaryFolderFor2022 = path.join(__dirname, 'temp', '2022-10', 'image');
	fs.mkdir(storagePathForStoringImagesInATemporaryFolderFor2022, this.handleOperationCompletion);
}
```





















