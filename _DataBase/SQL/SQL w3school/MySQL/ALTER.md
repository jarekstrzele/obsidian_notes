[[Statement MySQL]]


---



# ALTER
#sql/alter
`ALTER TABLE` statment is used to:
- add, delete, modify columns in an existing table
- add and drop various constraints on an existing table


## add column
#sql/add
```sql
ALTER TABLE table_name
ADD column_name datatype;


ALTER TABLE Customers
ADD Email varchar(255);

```


## delete column
#sql/delete
TO delete a column in a table:
```sql
ALTER TABLE tab_name
DROP COLUMN col_name;
```

```sql
ALTER TABLE Customers
DROP COLUMN Email;
```


## modify column
#sql/modify
To change the data type of a column in a table:
```sql
ALTER TABLE tab_name
MODIFY COLUMN  col_name datatype;

```

---

