[[Data Bases/MongoDB/Master MongoDB/_ 0 Start]]


---
# MongoDB Shell
- based on JAvaScript
- starting from v3.2 uses SpiderMonkey JavaScript engine - to check which engine is used:
	- `interpreterVersion()`  (on the MongoDB shell)
```shell
> interpreterVersion()
MozJS-60
```

- `db.serverBuildInfo()` (on the server side)
`"javascriptEngine": "mozjs",`

- support ECMAScript 6 starting from v3.2
- supports mongo shell and server-side JavaScript

from shell you can connect to server and perform cetains tasks


---
## MongoDB server vs MongoDB Shell

### verify  MongoDB Server Version
`mongod --version`
`db.version()`
`db.serverBuildInfo()`
```shell
$ docker exec mymongo mongod --version
db version v5.0.9
...
```

on AWS
```shell
ubuntu@ip-172-31-91-234:~$ mongod --version
db version v5.0.9
```

### Verify MongoDB Shell Version
`mongo --version`
`version()`
```shell
$ docker exec mymongo mongo --version
MongoDB shell version v5.0.9

```

on AWS:
```shell
ubuntu@ip-172-31-91-234:~$ mongo --version
MongoDB shell version v5.0.9
```

----

## Help
#mongodb/help
`help`
`db.hel()`
`db.` + twice tab

----
## MongoDB Shell JavaScript Syntax

`db.version()`
`db` - object
`.` - object property access
`version` object method - function stored as object property
`()` invoke object method

```shell
> typeof db
object

> db.version
function() {
    return this.serverBuildInfo().version;
}

> db.version()
5.0.9
```

---
## Arguments in the MongoDB Methods

`db.getCollection("test").insertOne({a:10, b:true})`

`"test"` string argument passed to the getCollection Method

`db.getCollection("test")` returns Object with it's own Properties
this object has a method `insertOne()`
`{a:10, b:true)` object argument passed to the `insertOne` method














