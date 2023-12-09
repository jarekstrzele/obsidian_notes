[[0 SQL tutorial w3school]]


---

# SQL Statements


## Select

`SELECT DISTINCT col1, ... FROM table_name;`

The following SQL statement lists the number of different (distinct) customer countries:
`SELECT COUNT(DISTINCT Country) FROM CUstomers;`

(this stetment is not supported in Microsoft Access databases)


---

## INSERT INTO
```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```


only specific columns
```sql
INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway');

```


---

## UPDATE

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

```


__WHERE__ clause determines how many records will be updated.


---
## DELETE
```sql
DELETE FROM table_name WHERE condition;
```

To delete all records without deleting the table:
```sql
DELETE FROM table_name;
```















