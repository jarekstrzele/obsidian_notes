[[0-MySQL W3school]]


---

# JOIN

> A `JOIN` clause is used to combine rows from two or more tables, based on a related column berween them.


- `inner join` returns records that have matching values in both tables
- `left join` returns all records from the left table, and the matched records from the right table
- `right join` returns all records from the tight table, and the matched records from the left table
- `cross join` returns all records from both tables

---

## INNER JOIN

```sql
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

> The `INNER JOIN` keyword selects all rows from both tables as long as there is a match between the columns. 


---


## LEFT JOIN
```sql
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;

```


---

## RIGHT JOIN
```sql
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```

---

## CROSS JOIN 
```sql
SELECT column_name(s)
FROM table1
CROSS JOIN table2;
```

If you add a `WHERE` clause (if tab1 and tab2 has a relationship), the cross JOIN will produce the same result as the `INNER JOIN` clause:

```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
CROSS JOIN Orders
WHERE Customers.CustomerID=Orders.CustomerID;
```


---

## Self Join
```sql
SELECT cols,
FROM tab1 T1, tab2 T2
WHERE conditions
```
T1, T2 are different table aliases for the same table!













