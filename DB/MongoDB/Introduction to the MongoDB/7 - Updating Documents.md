[[_ Intro to MongoDB]]


---
# Updating documents

`updateOne(<query>, <update>, <option>)  `
`updateMany(<query>, <update>, <option>)`

*query* - which doc
*update* - which operations you want to perform

## update operators
- `$set` sets value of certain filed
- `$unset` delete certain field
- `$inc` increment
- `$rename`
- `$currentDate`
- `$addToSet`

## example
```shell
forum> db.posts.updateOne( { postId: 2618 }, { $set: { shared: true } })

forum>db.getCollection('posts').find({postId:2618})

forum> db.posts.updateOne({postId: 1151}, { $set: {title: "What is the average salary of the senior fronted developer?"}})


```

```shell
forum> db.posts.updateOne({postId: 1151}, { $set: {title: "What is the average salary of the senior fronted developer?"}})

forum> db.posts.updateMany(
... {tags: []},
... {$unset: {tags: 1}}
... )
# tags will be deleted

```


increment comments by 1

---
# Delete
`deleteOne()`
`deleteMany()`

`db.getCollection('posts').insertOne({postId: NumberInt(1111)})`
`db.getCollection('posts').insertOne({postId: NumberInt(2222)})`
`db.getCollection('posts').insertOne({postId: NumberInt(3333)})`


```shell
db.getCollection('posts').deleteOne({postId:1111})
```

delete many -> they that have no title
## `$exists` operator:
to find
```shell
forum> db.getCollection('posts').find({title: {$exists: false}})
[
  { _id: ObjectId("62b4567942e1c67a6581295a"), postId: 2222 },
  { _id: ObjectId("62b4567f42e1c67a6581295b"), postId: 3333 }
]

```

to delete
```shell
forum> db.getCollection('posts').deleteMany({title: {$exists: false}})
{ acknowledged: true, deletedCount: 2 }
forum> 
```



