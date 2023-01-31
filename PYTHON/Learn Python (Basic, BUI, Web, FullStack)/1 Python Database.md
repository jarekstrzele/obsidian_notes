[[0 _ Learn Python From Zero to Hero (basic, Bui, Web, Full Stack)]]

>[!info] Database
>It is a organized collection of data that can be easily accessed and amanaged

[[#SQLite]]
[[#MySql]]
[[#Postgres]]
[[#MS Access]]



# SQLite
#python/sqlite 
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

## create table
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
### `pip install mysqlclient`



# Postgres



# MS Access













