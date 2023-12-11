[[_ SQLite]]
[[_ Groupowanie danych SQLite]]

[[GROUP BY SQLite]]

---
# HAVING
`HAVING` filtruje dane już po filtrowaniu (dodatkowa opcja do `group by`)
w `WHERE` fitlrujemy dane przed grupowaniem

można użyć w jednym zapytaniu `where` i `having`
```sqlite
SELECT employee_id,
		SUM(amount) AS total_sales
FROM website.sales_012021
WHERE employy_id != 431
GROUP BY employee_id
HAVING total_sales > 50.0
ORGDER BY 2 DESC;
```


```sqlite
SELECT employee_id,
       SUM(amount)  as total_sales,
       COUNT(employee_id) as trans
FROM sales_012021 
GROUP BY employee_id
HAVING total_sales > 50.0
ORDER BY employee_id
```



