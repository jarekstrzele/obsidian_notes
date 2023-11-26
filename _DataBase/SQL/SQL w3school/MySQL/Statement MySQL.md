[[0-MySQL W3school]]
[[Operators MySQL]]




---

# Statement MySQL
[[ALTER]]



## SELECT
`SELECT DISTINCT col1, ... FROM ...` returns  only distinct (different) values.


`SELECT * FROM Customers WHERE NOT City='Berlin';`


---

## INSERT INTO

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```


---
## UPDATE
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
> Be careful when updating records. If you omit the WHERE clause, ALL records will be updated!


---

## DELETE

The `DELETE` statement is used to delete existing records in a table.
```sql
DELETE FROM table_name WHERE condition;
```

Delete all records:
`DELETE FROM table_name;`




---





---

## MySQL INSERT INTO SELECT
`INSERT INTO SELECT`:
- copies data from one table and inserts it into another table
- requires that the data types in source and target tables matches

>THe existing records in the target table are unaffected

```sql
INSERT INTO table2
SELECT * FROM table1
WHERE condition;
```

```sql
INSERT INTO table2 (column1, column2, column3, ...)
SELECT column1, column2, column3, ...
FROM table1
WHERE condition;
```


The following SQL statement copies "Suppliers" into "Customers" (the columns that are not filled with data, will contain NULL):
```sql

INSERT INTO Customers (CustomerName, City, Country)
SELECT SupplierName, City, Country FROM Suppliers;
```


The following SQL statement copies only the German suppliers into "Customers":

```sql
INSERT INTO Customers (CustomerName, City, Country)
SELECT SupplierName, City, Country FROM Suppliers
WHERE Country='Germany';
```



---
## CASE
The `CASE` statement goes through conditions and returns a value when the first condition is met
than it will stop reading and return  the result.
If no conditions are true, it returns the value in the `ELSE` clause
(no `else` -> `NULL`)

```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```

The following SQL goes through conditions and returns a value when the first condition is met:
```sql
SELECT OrderID, Quantity,
CASE
    WHEN Quantity > 30 THEN 'The quantity is greater than 30'
    WHEN Quantity = 30 THEN 'The quantity is 30'
    ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails;
```


The following SQL will order the customers by City. However, if City is NULL, then order by Country:

```sql
SELECT CustomerName, City, Country
FROM Customers
ORDER BY
(CASE
    WHEN City IS NULL THEN Country
    ELSE City
END);
```


