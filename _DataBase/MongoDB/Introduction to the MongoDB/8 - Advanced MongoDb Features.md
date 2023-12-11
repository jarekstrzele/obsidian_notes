[[_ Intro to MongoDB]]


---
# Advanced MongoDB Features

## Aggregation framework
**purpose**:
	1. you can **take** docs in your collection,
	2. you can **find** a subset of the docs and then
	3. **produce** brand new document at the end

e.i. 
	- you can find all distinct values of tags in the tags array in all docs or
	- you can find all values of the comments fields or 
	- you can find all titles in the docs ....

```shell
forum> db.posts.findOne({})
{
  _id: ObjectId("62b3fc65295f536946ef2b36"),
  title: 'What is the best way to learn JavaScript from the ground up?',
  postId: 3511,
  comments: 10,
  shared: true,
  tags: [ 'JavaScript', 'programming' ],
  author: { name: 'Mike Forester', nickname: 'mikef' }
}
#########################################3

forum> db.posts.aggregate([ {$group: {_id: "$author.name"}}])
[
  { _id: 'Mike Forester' },
  { _id: 'Emily Watson' },
  { _id: 'Bob Hutchinson' }
]
# output -> three new docs with one filed "_id" each 

# -------------------------
forum> db.posts.aggregate([ {$group: {_id: "$comments"}}])
[ { _id: 10 }, { _id: 3 }, { _id: 25 }, { _id: 0 } ]

```


## Indexes
```shell
forum> db.posts.getIndexes()
[ { v: 2, key: { _id: 1 }, name: '_id_' } ]

```

## Utilities

### mongoexport
is used to export specific data from certain collection
in a normal terminal:
	`mongoexport -d forum -c posts -o posts.txt  `
		`-d` specifies a name of the database
		`-c` specifies a name of the collection
		`-o` specifies a name of the file
in my docker container:
```shell
$ docker exec -it mymongo /bin/bash
root@dfeebc1bace0:/# mongoexport -d forum -c posts -o posts.txt
2022-06-23T13:28:20.897+0000	connected to: mongodb://localhost/
2022-06-23T13:28:20.904+0000	exported 5 records
root@dfeebc1bace0:/# ls


```
### mongoimport
is used to import data into the MongoDB database



### mongodump
create dump from the mongoDB database
```shell
root@dfeebc1bace0:/# mongodump
2022-06-23T13:30:02.582+0000	writing admin.system.version to dump/admin/system.version.bson
2022-06-23T13:30:02.584+0000	done dumping admin.system.version (1 document)
2022-06-23T13:30:02.586+0000	writing forum.posts to dump/forum/posts.bson
2022-06-23T13:30:02.587+0000	done dumping forum.posts (5 documents)

```
### mongorestore
s used to restore data from the MondoDB 




## Replica sets
If you want to use MongoDB in production you must setup MongoDb Replica Set

It has:
- only one **primary** server (**write** oprtation)
- many **secondary** servers (only **read** operation)

if you change something in the primary server, this is propagate into secondery servers

If primary will crash, one of the secondary become a primary

MongoDB Cluster consists of a few server



----
# MongoDB drivers
They are needed if you want to use MongoDB in full stack or backend apps

- php
- node
- java
- python
- ....











