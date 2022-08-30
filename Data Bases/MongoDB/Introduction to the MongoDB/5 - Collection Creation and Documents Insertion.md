[[_ Intro to MongoDB]]


---
# Collection Creation and Documents Insertion

### create db
1. create a db
`use new_db_name` - it is not created untill you create a collection

### create collection
2. create a collection`db.createCollection("name_of_the_collection")`

### insert doc
#mongodb/insert

3. insert a document into the collection
`inserOne({...})`
`insertMany([{...}, {...}, {...}])`

```shell
local> show dbs
admin    40.00 KiB
config  108.00 KiB
local    40.00 KiB
local> use forum
switched to db forum
forum> db.createCollection("posts")
{ ok: 1 }
forum> show collections
posts
forum> 
```

----
> You can easily use JavaScript objects in the MongoDB Shell because MongoDB shell is based on JavaScript

```shell
forum> const doc = {
...   title: "What is the best way to learn JavaScript from the ground up?",
...   postId: NumberInt(3511),
...   comments: 10,
...   shared: true,
...   tags: [
...     "JavaScript",
...     "programming"
...   ],
...   author: {
.....     name: "Mike Forester",
.....     nickname: "mikef"
.....   }
... }

forum> db.insertOne(doc)
TypeError: db.insertOne is not a function
forum> db.posts.insertOne(doc)
{
  acknowledged: true,
  insertedId: ObjectId("62b1ca1d862d7809dffde9b3")
}
forum> 
```

#### `db.collection_name.insert....`

