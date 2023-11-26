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



```mongosh
admin> use school
switched to db school
school> db.createCollection("students")
{ ok: 1 }
school> db.dropDatabase()
{ ok: 1, dropped: 'school' }
```


## document
`db.students.insertOne({})` - of the collection `students` does not exit, it will be created











