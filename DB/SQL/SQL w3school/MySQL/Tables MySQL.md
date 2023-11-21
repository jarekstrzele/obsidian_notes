[[0 - CRUD Databases MySQL]]

---
# Tables
## Create
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);

```

## create table using another table
```sql
CREATE TABLE new_table_name AS
    SELECT column1, column2,...
    FROM existing_table_name
    WHERE ....;
```

```sql
CREATE TABLE TestTable AS
SELECT customername, contactname
FROM customers;
```


---
## DROP table

`DROP TABLE tablename;`


## Truncate

`TRUNCATE TABLE` statement is used to delete the data inside a table, but not the table itself
`TRUNCATE TABLE table_name`

---

## ALTER TABLE
`ALTER TABLE ` 
- is used to add, delete, or modify columns in an existing table
- is used to add and drop various constraints on an existing table

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

```sql
ALTER TABLE Customers
ADD Email varchar(255);
```

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```
