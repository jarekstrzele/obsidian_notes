[[_DataBase/SQL/SQL PostgreSQL Tutorial/_ intro sql postgresql]]


---
# DML
- insert data into a table
- u[[_DataBase/SQL/SQL PostgreSQL Tutorial/4 - DML Postgres]]pdate data in a table
- delete table from a table

## INSERT
```sql
INSERT INTO examples (first_name, last_name, email, nationality, age)
VALUES ('David', 'Mietchell', 'dmitch@gmail.com', 'GBR', 43),
		('Emily','Watson', 'ewatson@gmail.com', 'USA', 29),
		('Theo','Scott', 'tscot@gmail.com', 'AUS', 33),
		('Emilu','Smith', 'esmith@gmail.com', 'GBR', 29),
		('Jim','Burr', 'jbuurr@gmail.com', 'USA', 54);
```

## Update
#sql/update 
```sql
UPDATE tablename
SET columnname = 'newvalue'
WHERE columname = 'value';
```

```sql
-- one column
UPDATE examples
SET email = 'davidmitchell@gmail.com'
WHERE example_id = 1;

-- many records
UPDATE examples
SET nationality = 'CAN'
WHERE nationality = 'USA';

-- many columns
UPDATE examples 
SET first_name = 'James', age = 55
WHERE example_id = 5;
```

```sql
UPDATE pets
SET age=3
where full_name='Fluffy';
```
musi być `'Fluffy'` a nie `"Fluffy"`


## Delete
#sql/delete 
```sql
DELETE FROM tablename
Where columnName = 'value';
```

delete all rows of data
`delete from tablename;`

## Insert
#sql/insert 
`INSERT INTO table name(col_names, ... ) VALUES (...) `


DATABASE movie_data














