[[_ SQLite]]
[[_ Łączenie tabel SQLite]]


---
# Intersect
>CZĘŚĆ WSPÓLNA
>zwraca przecięcie dwóch tabel, czyli zwraca rekordy, które występują zarowno w jedenj jak i drugiej tabeli, bez powtarzających się rekordów

czyli wybiera te rekordy, które w dwóch tabelach w zadanych kolumnach mają takie same wartości

```sql
SELECT * FROM sales_02_2021
INTERSECT
SELECT * FROM sales_01_2021;
```

```sql
SELECT * FROM sales_02_2021
INTERSECT
SELECT * FROM sales_01_2021
```
output:
Python dla każdego	159	1


ale
```sql
SELECT product_name FROM sales_02_2021
INTERSECT
SELECT product_name FROM sales_01_2021
```
output:
JavaScript podstawy
Paradygmat funkcyjny
Programowanie obiektowe
Python dla każdego



