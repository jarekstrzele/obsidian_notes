[[_ Intro to MongoDB]]



---
# Finding documents
#mongodb/find
#### `find({query})`
returns many documents

#### `findOne({query})` 
returna one document

`{query}` a JavaScript Object

```shell
db.getCollection('posts').find({})
```
returns all docs from 'posts' collection

```shell
forum> db.getCollection('posts').findOne({})
{
  _id: ObjectId("62b1ca1d862d7809dffde9b3"),
  title: 'What is the best way to learn JavaScript from the ground up?',
  postId: 3511,
  comments: 10,
  shared: true,
  tags: [ 'JavaScript', 'programming' ],
  author: { name: 'Mike Forester', nickname: 'mikef' }
}
```
returns only one/first

```shell
forum> db.getCollection('posts').findOne({postId: 3015})
{
  _id: ObjectId("62b1df7f862d7809dffde9b6"),
  title: 'I want to start my own business. What I need to do first?',
  postId: 3015,
  comments: 25,
  shared: true,
  tags: [ 'business', 'money' ],
  author: { name: 'Bob Hutchinson', nickname: 'bob1995' }
}
```


wszystkie posty Emily Watson 
an object inside an object
```shell
forum> db.getCollection('posts').find({"author.name": "Emily Watson"})
```
>![[important]]
>dot notation put into `" . "`


array as a value of a object propery
```shell
forum> db.getCollection('posts').find({tags: "programming"})
```

----
## Query Operators Overview
```
$or   $eq   $lt   $and        
$ne   $gt   $in   $nin    $regex
```


find docs which have comments > 0
`db.getCollection('posts').find({comments: {$gt: 0}})`
`db.getCollection('posts').find({comments: {$lt: 5}})`

AND
```shell
db.getCollection('posts').find({
	$and: [
		{comments: {$lt: 5}},
		{comments: {$gt: 0}}
	]

})`

```

OR
```shell
 db.getCollection('posts').find({ 
	 $or: [ 
	 {shared: true}, 
	 {tags: "programming"} 
	 ]
})
```

IN
```shell
 db.getCollection('posts').find({ tags: {$in: [ "programming", "coding"] } } )
```



----
## sort, limit skip
`sort()` sorting the results of the query 
`limit()` limiting the results of the query
`skip()` skipping apart from the query

```shell
db.getCollection('posts').find({}).limit(2)

db.getCollection('posts').find({}).skip(3)

db.getCollection('posts').find({}).sort({comments: 1})
```
`{comments: 1}` sorts in ascending order
`{comments: -1}` sorts in desending order

`db.getCollection('posts').find({}).sort({title: 1})`


`db.getCollection('posts').find({}).skip(2).sort({shared: 1})`



