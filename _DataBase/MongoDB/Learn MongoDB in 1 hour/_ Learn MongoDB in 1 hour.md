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

## `sort` and `limit` data
`test> db.students.find().sort({name:1})` alfabetycznie od a do z
`test> db.students.find().sort({name:-1})` od z do a
`test> db.students.find().sort({agee:1})` od  1 do ...
`test> db.students.find().sort({agee:-1})` od ... do 1

dwóch najstarszych 
`test> db.students.find().sort({age:-1}).limit(2)`

trzech najmłodszych
`test> db.students.find().sort({age:1}).limit(3)`


## `find({query}, {projection})`

#### `db.students.find()` returns all documents in the collection `students`

#### `db.students.find({name:"ola"})` any documents with name ola
```bash
test> db.students.find({name:"bolo"})
[
  {
    _id: ObjectId("6564fe2f6a756d36383dc6b4"),
    name: 'bolo',
    age: 33,
    city: 'olsztyn'
  },
  { _id: ObjectId("6565019f6a756d36383dc6b8"), name: 'bolo' }
]
```

```bash

test> db.students.find({name:"bolo", age:33})
[
  {
    _id: ObjectId("6564fe2f6a756d36383dc6b4"),
    name: 'bolo',
    age: 33,
    city: 'olsztyn'
  }
]
```

### `projection`
use it when you don't want all information
`db.students.find({}, {name:true})` return all documents, but display only the `name`
```bash
test> db.students.find({}, {name:true})
[
  { _id: ObjectId("6564fdf06a756d36383dc6b2"), name: 'aki' },
  { _id: ObjectId("6564fe2f6a756d36383dc6b3"), name: 'aki' },
  { _id: ObjectId("6564fe2f6a756d36383dc6b4"), name: 'bolo' },
  { _id: ObjectId("6564fe2f6a756d36383dc6b5"), name: 'acharit' },
  { _id: ObjectId("6565000d6a756d36383dc6b6"), name: 'Karu' },
  { _id: ObjectId("6565000d6a756d36383dc6b7"), name: 'robert' },
  { _id: ObjectId("6565019f6a756d36383dc6b8"), name: 'bolo' }
]
```

```bash
test> db.students.find({}, {_id: false, name:true})
[
  { name: 'aki' },
  { name: 'aki' },
  { name: 'bolo' },
  { name: 'acharit' },
  { name: 'Karu' },
  { name: 'robert' },
  { name: 'bolo' }
]
```


## update 
### `updateOne(filter, update)`
`db.students.updateOne({name:"bolo"`

### change one document
#### change the value
`school> db.students.updateOne({_id: ObjectId("6563ab7106064b272945f975")}, {$set:{age:44}})` find a document by id and change the field `age` to `44`

#### add a new filed/attribute
`db.students.updateOne({name:"piotr"}, {$set:{newField:12.34}})`  find document with attribute/field `name:"piotr"` and add a new field


#### remove a field/attribute
`school> db.students.updateOne({_id: ObjectId("6563ab7106064b272945f975")}, {$unset:{age:""}})`


### change many document

#### change all documents
`school> db.students.updateMany({}, {$set:{newField:false}})`

remove the `newField`
`school> db.students.updateOne({name:"bob"}, {$unset:{newField:""}})`
`school> db.students.updateOne({name:"Franio"}, {$unset:{newField:""}})`

