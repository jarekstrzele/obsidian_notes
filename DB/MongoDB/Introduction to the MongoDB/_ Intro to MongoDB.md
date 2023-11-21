#mongodb #databases  #udemy #billennium 

#stashchuk_bogdan


----
# Introduction MongoDB
[[MongoDB Installation]]
[[4 - Data Formats in MongoDb]]
[[5 - Collection Creation and Documents Insertion]]
[[6 - Finding Documents]]

content of this note:
[[#MongoDB Structure]]
[[#MongoDB Shell and MongoDB Server]]

It is used in the full stacl web apps.
**stack** several technologies that are utilized

stack:
	==MERN==
		- **M** ongoDB
		- **E** xpress
		- **R** eact
		- **N** ode.js
	==MEAN==
		- **M** ondoDB
		- **E** xpress
		- **A** ngular
		- **N** ode.js

> MongoDB uses Mozilla's **SpiderMonkey** JavaScript Engine


Relational DB | Document DB
--- | ---
MySQL, Oracle | MongoDB
data stored in tables | data stored <br> in separate documents <br> and are independent
fixed schema  | flex schema
relations between tables | all information <br> in one document
join request | no join request 

---
## MongoDB Structure
- Each MongoDB database consists of databases
	- each database consists of collections
		- each collection consists of documents
			- usually documents are grouped into the same collection by common fields

---
## MongoDB Shell and MongoDB Server

`mongod` to launch MongoDB SERVER
	- stores data into  MongoDB database
	- it is the main point of data storage
`mongo` to launch MongoDB Shell
	- is used for management of  the mongo server
	- to insert/update/delete  docs into the mongo server, 
	- CRUD
### "Warning: the "**mongo**" shell has been superseded by "**mongosh**","

#### ``docker exec -it mymongo bash

#### `docker exec -it mymongo mongosh`
#docker/exec #mongosh 

in mongosh:
`db.version()`

----
## mongosh
`db.version()` 
`db` - object
`.version()` property/method/function of this object 

`db.help()`
`show dbs`
`use admin`
`show collections`

`db.stats()` statistics about mongodb server


















