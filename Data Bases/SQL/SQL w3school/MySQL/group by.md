[[Statement MySQL]]

## GROUP BY
It groups rows that have the same values into summary rows.
It is often used with aggregate function to group the result-set by one or more columns

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

the number of customers in each country
```sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY COUNT(CustomerID) DESC;
```


the number of orders sent by each shipper:
```sql
SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders FROM 
	Orders
  LEFT JOIN 
    Shippers 
  ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;
```

List the number of customers in each country, ordered by the country with the most customers first.

```sql
SELECT
	COUNT(CustomerID),
	Country
FROM 
	Customers
GROUP BY Country
ORDER BY 
	COUNT(CustomerID) DESC
;
```


