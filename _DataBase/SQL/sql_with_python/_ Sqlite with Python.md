
https://www.tutorialspoint.com/sqlite/sqlite_python.htm


----
# Intro SQLite with Python
#python/sqlite #udemy  #elder_john 

## connection
[[Sqlite to connect with db]]


---
## INSERT info from db
```python
import sqlite3

conn = sqlite3.connect("customer.db")
cursor = conn.cursor()

cursor.execute("INSERT INTO customers values ('Jan', 'Kowalski', 'js@kk.pl')")
cursor.execute("INSERT INTO customers VALUES('Karol', 'Hobbit', 'kh@kk.pl')")
cursor.execute("INSERT INTO customers VALUES('Mary', 'Nowak', 'mn@kk.pl')")
cursor.execute("INSERT INTO customers VALUES('Zosia', 'Kosialska', 'zz@kk.pl')")

# EXECUTE MANY
many_customers = [
				  ("Chan", "Shing", "chsz@china.com"),
				  ("Xiao", "Ming", "ming@china.com"),
				  ("Po", "Pong", "pp@china.com"),
]
cursor.executemany('''
	INSERT INTO customers 
	VALUES (?, ?, ?)	
''', many_customers)

conn.commit()
conn.close()
```

---
## SELECT data from db
```python
import sqlite3

conn = sqlite3.connect('customer.db')
cursor = conn.cursor()

cursor.execute("SELECT * FROM customers")
# cursor.fetchone()
# cursor.fetchmany(3)
items = cursor.fetchall()
print(items)
print()
for item in items:
	print(f'name: {item[0]}\tlast_name: {item[1]}\t email: {item[2]}' )

conn.commit()
conn.close()
```

`cursor.fetchone()`  This method fetches the next row of a query result set, returning a single sequence, or None when no more data is available.

`cursor.fetchmany(<number>)` This routine fetches the next set of rows of a query result, returning a list. An empty list is returned when no more rows are available. The method tries to fetch as many rows as indicated by the size parameter.

----
## row ID 
It is added automatically

---
## where

```python
...
cursor.execute("SELECT * FROM customers where first_name LIKE '__' ")

for i in items:
  print(i)
```

---
## update

```python
cursor.execute("""

  UPDATE customers SET first_name = "BOB" 
  WHERE rowid = 1
  """)

conn.commit()
cursor.execute("SELECT * FROM customers")
items = cursor.fetchall()
for i in items:
  print(i)
```

---
## delete record

```python
cursor.execute("""
  DELETE FROM customers  
  WHERE rowid = 2
""")

conn.commit()
cursor.execute("SELECT rowid, * FROM customers")
items = cursor.fetchall()
for i in items:
  print(i)

```

---
## order
```python
cursor.execute("SELECT rowid, * FROM customers ORDER BY rowid DESC")

items = cursor.fetchall()

for i in items:

  print(i)
```


---
## delete
```python
cursor.execute("SELECT rowid, * FROM customers ORDER BY rowid DESC")
conn.commit()
```







