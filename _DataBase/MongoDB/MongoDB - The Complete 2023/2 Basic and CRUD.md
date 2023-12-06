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

MongoDB drivers convert JSON to BSON (binary data) - O
## see documents
`db.flightData.find()` show all documents in the collection `flightData`














