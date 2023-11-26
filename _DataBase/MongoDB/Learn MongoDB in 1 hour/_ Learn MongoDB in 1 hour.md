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
`show dbs` - to show databases

`use admin` - to use an existing database `admin`
`use newDB` - to create and use a new db, but if it is empty, it is invisible

## collection
`db.createCollection("")`












