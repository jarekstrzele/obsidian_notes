[[_ SQLite]]


---
# SELECT CASE

```sql
SELECT CASE
	WHEN con1 THEN va1
	WHEN con2 THEN val
	ELSE default_value
	END;
```


```sql
SELECT ProductName,
		UnitPrice,
		CASE
			WHEN UnitPrice < 28.0 THEN 'low'
			ELSE 'high'
		END AS PriceLevel
FROM Product;
```


```sql
SELECT CompanyName,
		ContactName,
		ContactTitle,
		CASE
			WHEN ContactTitle == 'Owner' THEN 'OWNER'
			ELSE 'OTHERS'
		end as IsOwner
FROM Customer;
```

```sql

SELECT ProductName, UnitPrice,
    CASE
        WHEN UnitPrice >= 40 THEN "expensive"
        WHEN UnitPrice BETWEEN 20 and 39 THEN "MIDDLE"
        ELSE "cheap" 
        END AS 'expen_level'
FROM Product;
```

