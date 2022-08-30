[[_ SQLite]]
[[_ Łączenie tabel SQLite]]


---
# Union 
[[Union All SQLite | union all]]
[[EXCEPT | except]]
[[INTERSECT | intersect]]


>łączenie wielu select ze sobą

```sql
SELECT ... FROM ...
compound_operator
SELECT ... FROM ...
[...]
ORDER BY ... LIMIT ... OFFSET ...
```

## union
- likwiduje wszystki duplikaty
- dwa `select` muszą mieć tę samą liczbę kolumn
```sql
SELECT * FROM sales_01_2021
UNION
SELECT * FROM sales_02_2021;
```

## przykład
```sql
CREATE TABLE sales_01_2021(
    product_name TEXT NOT NULL,
    price REAL NOT NULL,
    quantity INTEGER NOT NULL
);

CREATE TABLE sales_02_2021(
    product_name TEXT NOT NULL,
    price REAL NOT NULL,
    quantity INTEGER NOT NULL
);


INSERT INTO sales_01_2021 (product_name, price, quantity)
VALUES ('Programowanie obiektowe', 39.00, 1),
        ('Paradygmat funkcyjny', 39.00, 2),
        ('JavaScript podstawy', 39.00, 3),
        ('Python dla każdego', 159.00, 1);
        


INSERT INTO sales_02_2021 (product_name, price, quantity)
VALUES ('Programowanie obiektowe', 39.00, 2),
        ('Paradygmat funkcyjny', 39.00, 3),
        ('JavaScript podstawy', 39.00, 1),
        ('Python dla każdego', 159.00, 1),
        ('Big data', 39.00, 3),
        ('SQLite dla początkujących', 39.00, 1);
    
```

```sql
SELECT * FROM sales_01_2021
UNION
SELECT * FROM sales_02_2021;
```

Jakie były unikalne nazwy kursów sprzedane w styczniu i lutym:
```sql
SELECT product_name FROM sales_01_2021
UNION
SELECT product_name FROM sales_02_2021
```



