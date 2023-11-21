
[[0-MySQL W3school]]




---
## HAVING
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

`where` cannot be used wuth aggregate functions


the number of customers in each country. Only include countries with more than 5 customers:
```sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5;
```



