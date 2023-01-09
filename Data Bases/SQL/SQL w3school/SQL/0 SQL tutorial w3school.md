


#  SQL tutorial w3school
#w3school   #sql 

[[SQL Statements]]
[[SQL Clauses]]
[[SQL JOINS]]
[[LIKE SQL]]

https://www.w3schools.com/sql/default.asp

>SQL is a standard language for storing, manipulating and retrieving data in databases.


Important commands:
- __database__:
	- `CREATE DATABASE db_name`
	- `ALTER DATABASE`
- __table__:
	- `CREATE TABLE table_name`
	- `ALTER TABLE`
	- `DROP TABLE`
-  __index__:
	- `CREATE INDEX`
	- `DROP INDEX`
- __data__:
	- `SELECT ... FROM ...`
	- `UPDATE`
	- `DELETE`
	- `INSERT INTO`

---
## NULL
#sql/null

>A field with a NULL value is a field with no value.

Null is not Zero or string Space.

You can't test for NULL values with comparison operators:
- `=`
- `<`
- `<>`

You have to use operators:
- `IS NULL`
- `IS NOT NULL`

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```


---












