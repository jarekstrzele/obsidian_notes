[[_ SQLite]]
[[_ Groupowanie danych SQLite]]

[[HAVING SQLite]]

----
# GROUP BY
Po klauzuli `WHERE`

```sqlite
SELECT employee_id,
		SUM(amout) as total_sales,
		COUNT(employee_id) as transactions,
		AVG(amount) AS avg_transaction
FROM website.sales_012021
GROUP BY employee_id;

```

- można grupować po jednej kolumnie, ale i powiększej liczbie kolumn też
- w `group by` można używać aliasów

----
PRZYKŁAD
```sqlite
CREATE TABLE sales_012021 (
    id             INTEGER PRIMARY KEY,
    employee_id    INTEGER NOT NULL,
    amount         REAL    NOT NULL
);

INSERT INTO website.sales_012021(employee_id, amount)
VALUES (325, 109.0),
       (335, 9.89),
       (336, 40.0),
       (325, 210.0),
       (336, 39.89),
       (431, 15.89),       
       (325, 10.89),
       (431,32.00);
```


```sqlite
SELECT employee_id,
       SUM(amount)  as total_sales,
       COUNT(employee_id) as trans,
       AVG(amount) as avg_trans,
       MIN(amount) as min_amount,
       MAX(amount) as max_amount
FROM sales_012021 
GROUP BY employee_id
ORDER BY employee_id;
```


