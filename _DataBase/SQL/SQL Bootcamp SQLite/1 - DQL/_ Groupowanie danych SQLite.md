[[_ SQL Bootcamp - SQLite cz. 1]]
[[_ SQLite]]

[[SQLite DQL]]

---

# Grupowanie danych
[[funkcje agregujące SQLite]]
[[funkcje tekstowe SQLite]]
[[GROUP BY SQLite]]
[[HAVING SQLite]]

gdy nazwa tabeli jest identyczna z jednym z poleceń SQL:
np. mamy tabelę o nazwie `Order`
```sqlite
select * from "order";
select * from `order`
select * from [order];

```


```sqlite
SELECT  CustomerId, 
        count(CustomerId) as NumOfOrders
FROM "Order"
GROUP BY CustomerID
ORDER BY NumOfOrders DESC
LIMIT 10
OFFSET 4;
```








