[[0 _ Learn Python From Zero to Hero (basic, Bui, Web, Full Stack)]]
#python/database 

>[!info] Database
>It is a organized collection of data that can be easily accessed and amanaged

[[#SQLite]]
[[#MySql]]
[[#Postgres]]
[[#MS Access]]



# SQLite
#python/sqlite 

### `SELECT (rowid), * FROM tableName;`
in Python you don't have to use `()`


## create db
```python
import sqlite3 as lit  
  
  
def main():  
    try:  
        db = lit.connect('employee.db')  
        print("database is created")  
        db.close()
    except:  
        print("Failed to create database")  
        db.close()
  
if __name__== '__main__':  
    main()
```

use SQLiteStudio to manage your db.

## create table (sqlite)
[[#create a table (mysql)]] 
```python
import sqlite3 as lit  
  
  
def main():  
    try:  
        db = lit.connect('employee.db')  
        cur = db.cursor()  
  
        query = "CREATE TABLE users (id INT, name TEXT, email TEXT)"  
        cur.execute(query)  
        print("Table is created")  
        db.close()
    except:  
        print("Unable to create table")  
		db.close()
  
if __name__ == '__main__':  
    main()
```

## INSERT DATA
przekazując datę umieść ją w apostrofach
np.
```python
 def insert_data(self, my_hours, my_date):
        print(f"{my_hours =} {type(my_hours)}")
        print(f"{my_date =} , {type(my_date)}")
        query = f"""INSERT INTO Testy (hours_number, word_date)
                    VALUES ({my_hours}, '{my_date}')"""
        print(query)
        self.cur.execute(query)
        self.db.commit()
        print("Data inserted")
```


```python
import sqlite3 as lit  
  
  
def main():  
    mysuers = (  
        (1, 'Tom', 'tom@gom.ollk'),  
        (2, 'Jerry', 'jr@google.com'),  
        (3, 'HAKU', 'haku@wp.pl')  
    )  
  
    db = lit.connect('employee.db')  
    with db:  
        cur = db.cursor()  
        cur.executemany("INSERT INTO users VALUES (?,?,?)", mysuers)  
        db.commit()
        print("Data inserted")  
  
  
  
  
if __name__ == '__main__':  
    main()
```

## Update data
```python
import sqlite3 as lit  
  
def main():  
    db = lit.connect('employee.db')  
  
    with db:  
        new_name = "NUEW NAME"  
        user_id = 2  
  
        cur=db.cursor()  
        cur.execute("UPDATE users SET name = ? WHERE id = ?", (new_name, user_id))  
        db.commit()  
        print("Data is updated")  
  
if __name__=='__main__':  
    main()
```

## select all data
```python
import sqlite3 as lit  
  
def main():  
    db = lit.connect('employee.db')  
  
    with db:  
        cur = db.cursor()  
        query = "SELECT * FROM users"  
        cur.execute(query)  
  
        rows = cur.fetchall()  
  
        for data in rows:  
            print(data)  
  
if __name__ == "__main__":  
    main()
```

## delete data
IMPORTANT: TUPLE!!! in `execute` function
```python
import sqlite3  
  
db = sqlite3.connect('employee.db')  
  
with db:  
    user_id = 1  
    cur = db.cursor()  
    cur.execute("DELETE FROM users WHERE id = ?", (user_id,))  
    db.commit()  
    print("data deleted")
```


----
# MySql
#python/mysql 
https://pypi.org/project/mysqlclient/

### `pip install mysqlclient`

## connect to db
```python
import MySQLdb as mdb

DBNAME = "pydb"
DBHOST = "localhost"
DBPASS = "Filozofia2!@"
DBUSER = "root"

try:
    db = mdb.connect(DBHOST, DBUSER, DBPASS, DBNAME)
    print("Database is connected")
except mdb.Eroor as e:
    print(f"Database is not connected {e}")
```

## create a table (mysql)
[[#create table (sqlite)]] 
```python
import MySQLdb as mdb

DBNAME = "pydb"
DBHOST = "localhost"
BPASS = "Filozofia2!@"
DBUSER = "root"

try:
    db = mdb.connect(DBHOST, DBUSER, DBPASS, DBNAME)
    print("Database is connected")

	cur = db.cursor()
    cur.execute("DROP TABLE IF EXISTS Employee")

    query = """
    CREATE TABLE Employee (
        Name Char(20) NOT NULL,
        Email CHAR(20),
        Age INT
    )
    """
    cur.execute(query)
    print("Table is created")
except mdb.Eroor as e:
    print(f"Error {e}")
```

## Insert data
```python
import MySQLdb as mdb

DBNAME = "pydb"
DBHOST = "localhost"
DBPASS = "Filozofia2!@"
DBUSER = "root"

try:
    db = mdb.connect(DBHOST, DBUSER, DBPASS, DBNAME)
    cur = db.cursor()
 
    query = """
     INSERT INTO pydb.employee (Name, Email, Age)
     VALUES ('ToNowe', 'kipi@nowe.pl', 77);
    """
    cur.execute(query)
    db.commit()
    print("Data is inserted")
except mdb.Err as e:
    print(f"Error {e}")
```

## update data (mysql)
```python
try:
    db = mdb.connect(DBHOST, DBUSER, DBPASS, DBNAME)
    cur = db.cursor()

    query = """
     UPDATE employee SET Name="Zmienione Imię" where Age=77
    """
    cur.execute(query)
    db.commit()
    print("Data is updated")
except mdb.Err as e:
    print(f"Error {e}")
```


## select data (mysql)
```python
import MySQLdb as mdb

DBNAME = "pydb"
DBHOST = "localhost"
DBPASS = "Filozofia2!@"
DBUSER = "root"

try:
    db = mdb.connect(DBHOST, DBUSER, DBPASS, DBNAME)
    cur = db.cursor()

    query = "SELECT * from employee"
    cur.execute(query)
    results = cur.fetchall()
    print(f"Results: {results}")

    for row in results:
        print(f"Name: {row[0]}")
        print(f"email: {row[1]}")
        print(f"age: {row[2]}")
except mdb.Err as e:
    print(f"Error {e}")
```

```bash
Results: (('Kira', 'kir@kkk.com', 22), ('Turaa', 'r@oo.com', 122), ('Ooo', 'qqq@pp.pl', 33), ('Zmienione Imię', 'kipi@nowe.pl', 77))
Name: Kira
email: kir@kkk.com
age: 22
```


## delete data (mysql)
```python
try:
    db = mdb.connect(DBHOST, DBUSER, DBPASS, DBNAME)
    cur = db.cursor()

    query = "DELETE FROM employee WHERE Age=33"
    cur.execute(query)
    db.commit()
    print("Data is deleted")
except mdb.Err as e:
    print(f"Error {e}")
```



----
# Postgres
*Elephant SQL*
- create an instance of Postgres on `Elephant SQL`
- in PGAdmin create/register a new server:
	- add a name
	- hostname from ElephantSQL (`kandula.db.elephantsql.com`)
	- changed username and maintenance database (get from ElephantSQL; `fidgdqfp`)
	- from ElephantSQL copy password
	- save
	- in PGAdmin find your server (`fidgdqfp`) 

### `pip install pyscopg2`


----
# MS Access













