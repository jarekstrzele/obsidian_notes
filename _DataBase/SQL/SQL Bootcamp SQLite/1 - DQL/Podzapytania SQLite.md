[[_ SQLite]]


---
# Podzapytania

```sql
SELECT *
FROM OrderDetail
WHERE ProductID IN
	(SELECT Id
	FROM Product
	WHERE UnitsInstock > 0);

```

Wybierz wszystkie rekordy z tabeli `OrderDetail`, których wartość `ProductId` należy do zbioru tych produktów, które są w magazynie (`UnistsInStock > 0`)
```sql
Select *
FROM OrderDetail
WHERE ProductId IN
(
	SELECT Id FROM Product
	WHERE UnitsInStock > 0
);
```

---
Koleiny przykład:

_Id_ klientów z krajów, których nazwa zaczyna się na _U_
```sql
SELECT Id FROM Customer
WHERE Country LIKE 'U%';
```

W tabeli `order` jest kolumna z `id` klienta
pokaż wszystkie informacje o zamówieniach klientów, którzy pochodzą z krajów, których nazwa zaczyna się na listerę _U_
```sql
SELECT *
FROM "Order"
WHERE CustomerId IN
(
	SELECT Id FROM Customer
	WHERE Country LIKE 'U%'
);
```


