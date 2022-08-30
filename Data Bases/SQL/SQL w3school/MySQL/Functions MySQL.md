[[0-MySQL W3school]]

`min()` returns the smallest value of the selected column
`Select max(col_name) FROM tab_name WHERE conditions;`


`count()` returns the number of rows that matches a specified criterion

`AVG()` 
`SUM()`


---

## `IFNULL()`
lets you return an alternative value if an expression is NULL

The example below returns 0 if the value is `NULL`
```sql
SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0))
FROM Products;
```

`COALESCE()`
```sql
SELECT ProductName, UnitPrice * (UnitsInStock + COALESCE(UnitsOnOrder, 0))
FROM Products;
```










