[[0-MySQL W3school]]


---

# Alias
- Aliases are used to give a table, or a column in a table, a temporary name
- Aliases are often used to make column names more radable
- An alias onlu exists for the diration of that query.
- An alias is created with the `AS` keyword.

## column aliases

```sql
SELECT column_name AS alias_name
FROM table_name;
```


```sql
SELECT CustomerName, CONCAT_WS(', ', Address, PostalCode, City, Country) AS Address
FROM Customers;
```


## table aliases
```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName
FROM Customers AS c, Orders AS o
WHERE c.CustomerName='Around the Horn' AND c.CustomerID=o.CustomerID;
```



