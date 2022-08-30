

# Widoki
- używamy, gdy chcemy zapisać  zapytanie często używane, najczęściej złożone
- są dynamiczne (są aktualizowane)
- do widoków możemy odwoływac się w zapytaniach jak do zwykłych tabel
- w SQLite są tylko do odczytu
- jest bytem logicznym (nie przechowuje fizycznie danych), są jedynie odniesieniem do tabel źródłowych
- używane:
	- chcemy skomplikowane często używane zapytanie spakować w wygodniejszą formę (każdy używający widoku będzie otrzymywał ten sam wynik)
	- do tworzenie przyjaźniejszych dla użytkownika tabel
- 
```sql
CREATE VIEW viewName AS 
SELECT .... FROM ...;


DROP VIEW viewName
```


Mamy skomplikowane zapytanie
```sql
SELECT t1.id, t1.OrderId, t1.ProductId, t2.ProductName, t1.UnitPrice, t1.Quantity, t1.Discount
FROM OrderDetail AS t1 
left join Product AS t2 on t1.ProductId = t2.id;
```

będziemy go często używać, więc dla ułatwienia stworzymy sobie widok
```sql
CREATE VIEW OrderSimpleDetails_V AS
SELECT t1.id, t1.OrderId, t1.ProductId, t2.ProductName, t1.UnitPrice, t1.Quantity, t1.Discount
FROM OrderDetail AS t1 
left join Product AS t2 on t1.ProductId = t2.id;
```

teraz możemy:
```sql
Select * from OrderSimpleDetails_V;
```

```sql
Select * from OrderSimpleDetails_V LIMIT 10;
```

























