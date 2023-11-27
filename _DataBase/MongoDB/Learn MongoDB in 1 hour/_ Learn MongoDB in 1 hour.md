#mongodb  #youtube #bro_code 

https://www.youtube.com/watch?v=c2M-rlkkT5o

--------
# Intro

- a document is like a single row  in SQL
-  data are store in a document as *key-value* pair (`BSON`)
- a principle: *data which is frequently accessed together is stored together*  

## document
It is a group of field `key-value` pairs to represent an object
```JSON
{
	"name": "Sponge",
	"age": 22
}
```

## collection
It is a group of one or more document
e.g. *students*, *teachers*, *courses*

## database
It is a group of one or more documents

# Basic commands

## database
### show databases
`show dbs` - to show databases

### use database
`use admin` - to use an existing database `admin`

### create database
`use newDB` - to create and use a new db, but if it is empty, it is invisible

### delete database
`db.dropDatabase()`

## collection
`db.createCollection("students")` - to create a collection

`show collections` - to view all collections in db

```mongosh
admin> use school
switched to db school
school> db.createCollection("students")
{ ok: 1 }
school> db.dropDatabase()
{ ok: 1, dropped: 'school' }
```


## document
#### add one document
`db.students.insertOne({name:"alo", age:22})` - of the collection `students` does not exit, it will be created

#### show all documents
return all documents:
`db.students.find()`
`test> db.students.find().pretty()`

#### add many documents
`school> db.students.insertMany([{name:"piotr", age:38, gpa:22.1}, {name:"sandy", age:22}]`

```
school> db.students.insertOne(
{ 
	name:"Franio", 
	age:21, 
	gpa:2.3, 
	isGenious: false, 
	date: new Date(), 
	courses: ["Biologia", "Cjhemistry"], 
	address: {street:"123 ", city:"Bikini", zip:123} 
}
)
```

## sort and limit data
 




