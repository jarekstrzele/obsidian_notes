[[_ Sqlite with Python]]

---
# connection with db

```python
import sqlite3

# if you want to have a db only in memory
# conn = sqlite(":memory:")

# make a connection, if your db doesn't exist, it will be created
conn = sqlite.connect("customer.db") 

# you have to create an object that will be manage your db
# this object is called 'cursor'
cursor = conn.cursor()

# Create a table
cursor.execute("""
	CREATE TABLE customers(
		first_name TEXT,
		last_name TEXT,
		email TEXT
		)
""")
# Type in SQLite: NULL, INTEGER, REAL, TEXT, BLOB

# You have to commit your command
conn.commit()

# You have to close the connection
conn.close()
```





