https://www.w3schools.com/python/python_mysql_getstarted.asp


# MySQL with Python
#python/mysql  #w3school  

1. Install MySQL Driver
`python -m pip install mysql-connector-python`

2. Import mysql connector 
`import mysql.connector`

3. Create Connection
```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword"
)

print(mydb)
```

4. create a cursor
`mycursor = mydb.cursor()`

5. execute some sql requests
```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword"
)

mycursor = mydb.cursor()

mycursor.execute("CREATE DATABASE mydatabase")
```

---
## Show all databases
```python
mycursor.execute("SHOW DATABASES")

for db in mycursor:
	print(db)
```
```shell
('information_scheme',)
('mydatabase',)
('performance_schema',)
('sys',)
```


---
## show all tables
```python
mycursor.execute("SHOW TABLES")

for table in mycursor:
	print(table)
```
```shell
('customers',)
```

