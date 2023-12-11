
[[0-MySQL W3school]]
[[Statement MySQL]]


---


# Operators

## Arithmetic
`+  -  *  /  %   `

---

## Logical
```
ALL
AND
ANY
Between
EXISTS
IN
LIKE
NOT
OR
SOME
```


## WHERE

```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

---

## IS [NOT] NULL
#sql/null 
> A field with a NULL value is a field with no value/

>A NULL value is different from a zero value or a field that contains spaces. A field with a NULL value is one that has been left blank during record ceeation!


```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

---
## LIKE
```sql
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;

```

`WHERE CustomerName LIKE '_r%'` Finds any values that have"r" in the second position

`WHERE ConstaktName LIKE "a%o"` Finds aby values that start with "a" and ends with "o"

---

## IN
The `IN` operator allows you to specify multiple values in a `where` clause; is a shorthand for multiple `OR` conditions.

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

---

## BETWEEN
is inclusive: bgin and end values are included

`SELECT * FROM Products WHERE Price NOT BETWEEN 10 AND 20;`


```sql
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20
AND CategoryID NOT IN (1,2,3);
```

```sql
SELECT * FROM Products
WHERE ProductName NOT BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```


---

## UNION
The `UNION` operator is used to combine the result-set of two or more `SELECT` statements


```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

- every `SELECT` statement within `UNION` must have the same number of columns
- the columns must also have similar adat types
- the columns in every `SELECT` statement must also be in the same order

 The `UNION` operator selects only distinct values by default. To allow duplicate values, use  `UNION ALL`

```sql
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```


German cities (only distinct values) from bouth table:
```sql
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
```

---
# EXISTS
- is used to test for the existence of any record in a subquery.
- returns TRUE if the subquery returns one or more records
```sql
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```

```sql
SELECT SupplierName
FROM Suppliers
WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND Price < 20);
```


---

## ANY
- returns a boolean value as a result
- return TRUE if ANY of the subquery values meet the condition

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY
  (SELECT column_name
  FROM table_name
  WHERE condition);

```

## ALL 
returns TRUE if ALL of subquery values meet the condition

```sql
SELECT ALL column_name(s)
FROM table_name
WHERE condition;
```

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ALL
  (SELECT column_name
  FROM table_name
  WHERE condition);
```

he following SQL statement lists the ProductName if it finds ANY records in the OrderDetails table has Quantity equal to 10 (this will return TRUE because the Quantity column has some values of 10):
```sql
SELECT ProductName
FROM Products
WHERE ProductID = ANY
  (SELECT ProductID
  FROM OrderDetails
  WHERE Quantity = 10);
```

The following SQL statement lists the ProductName if it finds ANY records in the OrderDetails table has Quantity larger than 99 (this will return TRUE because the Quantity column has some values larger than 99):

```sql
SELECT ProductName
FROM Products
WHERE ProductID = ANY
  (SELECT ProductID
  FROM OrderDetails
  WHERE Quantity > 99);
  ```


The following SQL statement lists ALL the product names:
```sql
SELECT ALL ProductName
FROM Products
WHERE TRUE;
```


The following SQL statement lists the ProductName if ALL the records in the OrderDetails table has Quantity equal to 10. This will of course return FALSE because the Quantity column has many different values (not only the value of 10):

```sql
SELECT ProductName
FROM Products
WHERE ProductID = ALL
  (SELECT ProductID
  FROM OrderDetails
  WHERE Quantity = 10);
```

