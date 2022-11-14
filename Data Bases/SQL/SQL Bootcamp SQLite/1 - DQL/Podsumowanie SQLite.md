[[_ SQLite]]


Wyświetlenie wersji SQLite
`SELECT sqlite_version();

Wyświetl aktualny czas:
`select current_time;`

Dzielenie
`select 23/4.0` 5.75
`select 23/4`  5

wyszystko, też `ROWID` z Customer
`SELECT ROWID, * FROM CUSTOMER;`

wyświetl tablę order posortowaną po kolumnie ShippedDate rosnąco, braki danych pozostaw na końcu sortowani
```sql
select *
from "order"
order by ShippedDate NULLS LAST;
```


```sql
select *
from "Order"
WHERE OrderDate != '2014-05-05'
```

```sql
select *
from "Order"
WHERE ShippedDate IS NULL
```

```sql
select *
from "Order"
WHERE ShipCountry NOT LIKE 'F%'

```

```sql
select *
from "Order"
WHERE LENGTH(ShipCountry) == 5
```

nazwy zaczynają się od litery P lub L lub N lub O
```sql
select *
from "Order"
WHERE ShipCountry GLOB '[P, L, N, O]*'
```

wyświetl liczbę niepuistych rekordów w tabeli Order
```sql
select COUNT(*)
from "Order";
```

liczba unikalnych klientów w tabeli Order 
```sql
select COUNT(DISTINCT CustomerId) as numOfCustomers
from "Order"
```

liczba w procentach unikalnych klientoów
```sql
select COUNT(*),
  COUNT(DISTINCT CustomerId) as numOfCustomers,
  COUNT(DISTINCT CustomerId)/(count(*) *1.0) as PctOfUniqueCustomers
from "Order";
```


procent brakujących danych
```sql
select    count(*),
          COUNT(ShippedDate),
          (COUNT(*) - count(ShippedDate)) / (count(*) * 1.0) as PctOfMissingShippedDate
from "Order"
```


najstarsza data
```sql
Select min(OrderDate) from "Order";
```

---

## GROUP
Pogrupuj dane z tabeli Order na poziomie CustomerId i wyznacz dla każdego klienta liczbę zamówień i posortuj malejącej po liczbnie zamówień
```sql
select CustomerId, 
       count(*) as NumOfOrders
from "Order"
GROUP BY CustomerId
ORDER by NumOfOrders DESC;
```

pogrupuj dane z tabeli Order na poziomie OderDate i wyznacz dla każdej daty liczbę zamówień. Wynik posortuj majeąco po liczbie zamówień i ogranicz do 10 pierwszych rekordów
```sql
select OrderDate, 
       count(*) as NumOfOrders
from "Order"
GROUP BY OrderDate
ORDER by NumOfOrders DESC
LIMIT 10
```

tab Order, grupowanie po ShipCountry oraz ShipCity i wyznacz dla każdej pary kraj<->miasto liczbę zamówień. Wynik posortuj malejąco po liczbie zamówień
```sql
select ShipCountry, 
       ShipCity,
       count(*) as NumOfOrders
from "Order"
GROUP BY ShipCountry, ShipCity
ORDER by NumOfOrders DESC
```

---
## CASE
z tabeli Product wyświetl kolumnę UnitsInStock. Dodatkowo dodaj drtugą kolumnę o nazwie UnitsInStocklevel, która podzieli wartoś w kolumnie UnitsStock na cztery poziomy:
	UnitsInStock == 0 -> 'none'
	                      < 20 'low'
	                      20 a 50 'medium'
	                      > 50 'high'
```sql
select UnitsInStock,
        CASE 
            WHEN UnitsInStock == 0 THEN 'none'
            WHEN UnitsInStock < 20 THEN 'low'
            WHEN UnitsInStock BETWEEN 20 and 50 THEN 'medium'
            ELSE 'high'
        END as UnitsInStockLever
from Product
```

z powyższego + pogrupuj dane w kolumnie Product na poziomie UnitsInstockLevel i policz liczbę wystąpień dla każdej grupy
```sql
select UnitsInStock,
        CASE 
            WHEN UnitsInStock == 0 THEN 'none'
            WHEN UnitsInStock < 20 THEN 'low'
            WHEN UnitsInStock BETWEEN 20 and 50 THEN 'medium'
            ELSE 'high'
        END as UnitsInStockLever,
        COUNT(*) As NumofProductes
from Product
GROUP BY UnitsInStockLever;
```

---
## JOIN
połączenie LEFT JOIN, tab: Product, Category (bez aliasów), warunek połączenie CategryId z Product i Id z tab Category
```sql
SELECT *
FROM Product 
LEFT JOIN Category ON Product.CategoryId == Category.Id
```


LEFT JOIN na Order i Customer po Order.CustomerId oraz Customer.Id, wyświetlamy kolumny CustomerId z Order, Id z Customer, Freight, COmpanyName, ContactName
```sql
SELECT o.CustomerId, 
	   c.Id,
	   Freight,
	   CompanyName, 
	   ContactName
FROM "Order" as o
LEFT JOIN Customer as c ON o.CustomerId == c.Id
```
(to zapytanie można zmienić na inner zamieniając `LEFT JOIN` na `INNER JOIN`)
do powyższego dodaj warunek `where` (wiersze gdzie kolumna c.Id ma wartość NULL)
```sql
SELECT o.CustomerId, c.Id, Freight, CompanyName, ContactName
FROM "Order" as o
LEFT JOIN Customer as c ON o.CustomerId == c.Id
WHERE c.Id is NULL
```














