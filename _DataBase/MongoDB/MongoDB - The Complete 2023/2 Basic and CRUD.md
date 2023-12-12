#mongodb 

[[_ MongoDB Complete]]

----------

# Understanding Databases, collections, documents

DATABASE:
	- collection
		- document
		- document
		- ....
	- collection
		- document `{ }` - it is a document / json 
		- document
		- ....
	- ...

## create db, collection,  document
dbs, collections, documents are all automatically and implicitly  created for you when you start working with them

`sudo mongod`
`sudo mongod --port 27018` for example


on the MongoDB documentation webpage, you can find various **drivers** for different programming languages. These drivers enable you to connect to MongoDB

`show dbs` - to show existing databases
`use notExistingDataBase` - you create a db
	- `db.notExistingYetCollection.insertOne({})` - Create a collection and and populate it with an empty document

## JSON vs BSON

```json
{
	"attr1": "some value",
	"attr2": 123,
	"attr3": true,
	"attr4":  [],
	"attr5": {}
	
}

```

MongoDB use BSON to store data
but
`db.flightData.insertOne({<json>})`

MongoDB drivers convert JSON to BSON (binary data) -`ObjectId("efewfwef")`  it is not valid JSON value 

in `insertOne` you can omit the  `""` for attribute
## see documents
`db.flightData.find()` show all documents in the collection `flightData`
see also: [[_ Learn MongoDB in 1 hour]]

------------
# CRUD
#mongodb/crud

## create
##### `insertOne(data, option)`
##### `insertMany(data, options)`

## read
##### `find(filter, options)`
##### `findOne(filter, options)` 
first matching

## update
##### `updateOne(filter, data, options)`
##### `updateMany(filter, data, options)`
##### `relaceOne(filter, data, options)`

`mytest> db.flightData.updateOne({distance:12000}, {$set: {marker: "delete"}})`





## delete
##### `deleteOne(filter, options)`
##### `deleteMany(filter, options)`

`mytest> db.flightData.deleteOne({departure: "TXL"})`






















