[[_ SQLite]]
[[_ Łączenie tabel SQLite]]


---
# Union All
[[UNION SQLite]]

wybierze wszystkie wiersze, nawet duplikujące się wartości
```sql
SELECT * FROM sales_01_2021
UNION ALL
SELECT * FROM sales_02_2021;
```

Jaki kursy były sprzedane w 01 i 02:
```sql

SELECT product_name FROM sales_01_2021
UNION ALL
SELECT product_name FROM sales_02_2021;
```



