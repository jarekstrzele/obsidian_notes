[[_Advanced SQL Topics]]

---

# INDEXES
#sql/indexes

index like order in the library
The index of a table functions like the index of a book
- data is taken from a column of the table and is stored in a certain order in a distinct place, calle ==an index==
- an index increases the speed of searches related to a table

To CREATE INDEX:
```sql
CREATE INDEX index_name
ON table_name(col_1, col_2, ...);
```

columns that you search frequantly!

```sql
CREATE INDEX i_hireDate 
ON employees(hire_date);
```

---

## composite indexes
- applied to myltiple columns, not just a single one 
```sql
CREATE INDEX index_name
ON table_name(col_1, col_2, ...);
```
carefully pick the columns that would optimize your search!


```sql
Select *
From employees
where
	first_name = 'Georgi'
    And
    last_name = 'Facello';

CREATE INDEX i_composite ON employees(first_name, last_name);


```


==primary and unique keys== are MySQL indexes

`SHOW INDEX FROM employees FROM employees;`
`SHOW INDEX FROM employees;`


---
# DROP INDEX

```sql
ALTER TABLE employees
DROP INDEX i_hireDate;
```

