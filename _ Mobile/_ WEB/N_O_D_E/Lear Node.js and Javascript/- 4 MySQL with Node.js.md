#mysql  #node 

[[_ Mobile/_ WEB/N_O_D_E/Lear Node.js and Javascript/_ Node and JavaScript]]

---
# MySQL with Node

- install node
- wamp -> linux lamp

`npm install mysql` -> and now in the a js file :
because there are some problems:
#### `npm un mysql && npm i mysql2`
mysql -> MariaDB hasło Filozofia2!@ dla roota

#phpmyadmin 
https://www.tutsmake.com/how-to-install-phpmyadmin-on-ubuntu-22-04/

```javascript
var mysql = require('mysql');
```
and now my program can connect to mysql

---
`npm uninstall mysql`

in the folder with a js file:
`npm init -y` to generate a json file

----
## docker
[[_ Mobile/_ WEB/N_O_D_E/Lear Node.js and Javascript/docker mysql node phpmyadmin]]

---

## MAKE a connection with db in the js file
[[_ mysql with python]]

```javascript
  mysql = require('mysql');
   
  var con = mysql.createConnection({
  host:"localhost",
  user:"root",
  password:""
  });
   
  con.connect(function(err){
    if (err){
     console.log("connection errro");
      throw err;
    }
    console.log("Conntected to the DB")
  });
```


## create DB

```javascript
con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to tthe database!");
    con.query("CREATE DATABASE nodeDB", function(err, result){
        if (err) throw err;
        console.log("Database created");
    });
})
```

and now:
```javascript

var con = mysql.createConnection({
    host: "localhost",
    user: "root",
    password: "Filozofia2!@",
    database: "nodeDB"
    
})
```

## create table
```javascript

con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to tthe database!");
    
    // create table
    var sql = "CREATE TABLE customers(id INT AUTO_INCREMENT PRIMARY KEY , name VARCHAR(255), email VARCHAR(255))";
    con.query(sql, function(err, result) {
        if(err) throw err;
        console.log("Table has been created....")
    })
    
})
```

## ALTER table
suppose the we have not defined id column
```javascript
con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to tthe database!");
    
    // ALTER table
    var sql = "ALTER TABLE customers ADD COLUMN id INT AUTO_INCREMENT PRIMARY KEY;";
    con.query(sql, function(err, result) {
        if(err) throw err;
        console.log("Table has been altered....")
    })
    
})
```

## insert data

#### one data
```javascript

con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to tthe database!");
    
    // INSERT table
    var sql = "INSERT INTO customers (name, email) VALUES ('Mary SMith', 'merysmith@gmail.com');"
    con.query(sql, function(err, result) {
        if(err) throw err;
        console.log("Data inserted into a table....")
    })
    
})
```


#### many data
```javascript

con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to tthe database!");
    
    // INSERT table
    var sql = "INSERT INTO customers (name, email) VALUES ?";
    var values = [
        ['Tim', 'tim@wp.pl'],
        ['KIKO', 'kio@chi.cx'],
        ['Laura', 'l@a.c'],
    ]

    con.query(sql, [values], function(err, result) {
        if(err) throw err;
        console.log("Records inserted: " + result.affectedRows); //it shows the number of added rows
    });
    
})
```


#### some msg
```javascript
con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to tthe database!");
    
    // INSERT table
    var sql = "INSERT INTO customers (name, email) VALUES ('kotka' , 'pies@p.pl')";

    con.query(sql,function(err, result) {
        if(err) throw err;
        console.log(result); //it shows the number of added rows
    });
    
})
```
**output** from `result`
```shell
Connectected to tthe database!
OkPacket {
  fieldCount: 0,
  affectedRows: 1,
  insertId: 6,
  serverStatus: 2,
  warningCount: 0,
  message: '',
  protocol41: true,
  changedRows: 0
}
```

you can `result.affectedRows` or other proprety

---
## SELECT data
```javascript

con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to tthe database!");
    
    // SELECT table
    var sql = "SELECT * FROM customers";
   
    con.query(sql,function(err, result, fields) {
        if(err) throw err;
        console.log(result); //it shows the number of added rows
    });
    
})
```
output
```shell
Connectected to tthe database!
[
  RowDataPacket { name: 'Joh Elder', email: 'js@gmail.com', id: 1 },
  RowDataPacket {
    name: 'Mary SMith',
    email: 'merysmith@gmail.com',
    id: 2
  },
  RowDataPacket { name: 'Tim', email: 'tim@wp.pl', id: 3 },
  RowDataPacket { name: 'KIKO', email: 'kio@chi.cx', id: 4 },
  RowDataPacket { name: 'Laura', email: 'l@a.c', id: 5 },
  RowDataPacket { name: 'kotka', email: 'pies@p.pl', id: 6 }
]

```

so we can:
```javascript
// ...
 console.log(result[0].email); //it shows the number of added rows
    });
```

### loop
```javascript
 con.query(sql,function(err, result, fields) {
        if(err) throw err;
        var i;
        for(i =0; i < result.length; i++){
            console.log(result[i].name)
        }
        
    });
```

### fields
```javascript
 var sql = "SELECT * FROM customers";
   
    con.query(sql,function(err, result, fields) {
        if(err) throw err;
       console.log(fields); 
    });
```

output -> array with objects `FieldPacker`  one for each row in table
for the first row:
```shell
FieldPacket {
    catalog: 'def',
    db: 'nodeDB',
    table: 'customers',
    orgTable: 'customers',
    name: 'name',
    orgName: 'name',
    charsetNr: 33,
    length: 765,
    type: 253,
    flags: 0,
    decimals: 0,
    default: undefined,
    zeroFill: false,
    protocol41: true
  },
```


### where close
```javascript
con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to the database!");
    
    // SELECT table
    var sql = "SELECT name FROM customers WHERE id < 4";
   
    con.query(sql,function(err, result, fields) {
        if(err) throw err;
       console.log(result); 
    });
    
})
```
output
```shell
Connectected to the database!
[
  RowDataPacket { name: 'Joh Elder' },
  RowDataPacket { name: 'Mary SMith' },
  RowDataPacket { name: 'Tim' }
]
```
### to use variable
```javascript

con.connect(function(err){
    if (err) throw err;
    console.log("Connectected to the database!");
    
    // SELECT table
    var name_search = 't%';
    var id_search = 2;
    var sql = "SELECT name FROM customers WHERE name like ? or id = ?";
   
    con.query(sql, [name_search, id_search], function(err, result, fields) {
        if(err) throw err;
       console.log(result); 
    });
```
output
```shell
Connectected to the database!
[ RowDataPacket { name: 'Mary SMith' }, RowDataPacket { name: 'Tim' } ]
```

## DELETE
```javascript
 var sql = "DELETE FROM customers WHERE id = 2";

```
result will be:
```shell
Connectected to the database!
OkPacket {
  fieldCount: 0,
  affectedRows: 1,
  insertId: 0,
  serverStatus: 2,
  warningCount: 0,
  message: '',
  protocol41: true,
  changedRows: 0
}
```


## UPDATE
```javascript
var sql = "UPDATE customers SET name = 'KUBUs' WHERE id = 1";
```

## DROP table
```javascript
var sql = "DROP TABLE IF EXISTS customers";
```











