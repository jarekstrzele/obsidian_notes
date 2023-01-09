[[_ SQLite]]
[[_ Łączenie tabel SQLite]]


---
# Except

> zwraca wszystkie wiersze z pierwszego zapytania `SELECT`, których nie znaleziono w drugim zapytaniu (to taki operator ODEJMOWANIA)

odejmnie z pierwszej tabeli (styczeń) te wiersze, które występują w drugiej (luty)
np. Które kursy sprzedały się w styczniu, ale nie w lutym.

> muszą się zgadzać wszystkie wartości w kolumnach, aby dany rekord nie był uwzględnion!!!!!

pracujemy na danych z przykładu [[UNION SQLite | union]]
```sql
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
EXCEPT
SELECT * FROM sales_02_2021;

```

```sql
SELECT product_name FROM sales_02_2021
EXCEPT
SELECT product_name FROM sales_01_2021;
```
output:
```
product_name
Big data
SQLite dla początkujących
```



