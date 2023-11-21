#mongodb #youtube 

https://www.youtube.com/watch?v=c2M-rlkkT5o


*Not Only Structured Query Language*
> - we store related data as a single document
> - ==document== is a group of filed value pairs to represent an object 
> - `BSON` *Binary JavaScript Object Notation*
> - ==collection== is a group of one or more documents
> - ==database== is a group of  one or more collections
> - general idea:
> 	- data which is frequently accessed together is stored together


# Download
- install server (community)  https://www.mongodb.com/try/download/community
- Compas (GUI for managing our database) https://www.mongodb.com/try/download/compass
- mongoDB shell `mongosh` https://www.mongodb.com/try/download/shell
	- extract files
	- `>bin>mongosh.exe` add the path to envirement path
	- run `mongosh.exe` and write `mongosh` it stablish a connection to the MongoDB 
	- OR VS Code, extension to *MongoDB  fo VS Code*

# Basics
```bash
> show dbs
admin    40.00 KiB
config  108.00 KiB
local    72.00 KiB```

to use the database admin  `use admin`
to create a database  `use newDB`
to create a collection `db.createCollection("nameOFCollections")` 
to exit from the data base `db.dropDatabase()`


#### `db.students.insertOne({})`
#### `db.students.find()`
#### `db.students.insertMany( [ { },{ },{ } ] )`
#### `db.students.find()`

```bash
myFirst> use school
switched to db school
school> db.students.insertOne({"name":"Songebob", age:30, gpa:3.2})
{
  acknowledged: true,
  insertedId: ObjectId("655935b54b271d73a5b93186")
}
school> db.students.find()
[
  {
    _id: ObjectId("655935b54b271d73a5b93186"),
    name: 'Songebob',
    age: 30,
    gpa: 3.2
  }
]
school> db.students.insertMany([{name:"Patric", age: 38, gpa:1.5},{name:"Sandy", age:27, gps:4.0},{name:"Gary",age:18, gpa:2.5}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("655936294b271d73a5b93187"),
    '1': ObjectId("655936294b271d73a5b93188"),
    '2': ObjectId("655936294b271d73a5b93189")
  }
}
school> db.students.find()
[
  {
    _id: ObjectId("655935b54b271d73a5b93186"),
    name: 'Songebob',
    age: 30,
    gpa: 3.2
  },
  {
    _id: ObjectId("655936294b271d73a5b93187"),
    name: 'Patric',
    age: 38,
    gpa: 1.5
  },
  {
    _id: ObjectId("655936294b271d73a5b93188"),
    name: 'Sandy',
    age: 27,
    gps: 4
  },
  {
    _id: ObjectId("655936294b271d73a5b93189"),
    name: 'Gary',
    age: 18,
    gpa: 2.5
  }
]
school>
```






