[[_ SQLite]]

---
# DQL

## SELECT
`SELECT expression [AS column name] [,...];`

- służy do wydobywania danych z bazy danych
- wynikiem jest zero lub więcej wierszy
- każdy wiersz ma stałą liczbę kolumn
- jest poleceniem tylko do odczytu

```sqlite
SELECT 10 *20;
SELECT 'Sci' || ' & ' || 'Tech';
SELECT sqlite_version();
SELECT CURRENT_TIME;

```

---

`SELECT output_list FROM table_name;`

```sqlite
SELECT [DISTINCT output_lit]
FROM source_tables
WHERE filter_expression
GROUP BY grouping_expression
  HAVING filter_expression
ORDER BY ordering_expression
LIMIT number_of_rows
   OFFSET number_of_rows;
```

kolejność:
1. `FROM` 
2. `WHERE`
3. `GROUP`
4. `SELECT`
5. `HAVING`
6. `DISTINCt`
7. `ORDER`
8. `OFFSET`
9. `LIMIT`

### ORDER BY
`null` to wartość najmniejsza ze wszystkich

`ORDER BY Fax ASC NULLS FIRST;`
`ORDER BY Fax DESC NULLS LAST;`


### LIMIT
`SELECT ... FROM ... LIMIT ...`
```sqlite
SELECT ProductName,
		UnitPrice
FROM Product
LIMIT 10;
```

najtańszy produkt w tabeli
```sqlite
SELECT ProductName, UnitPrice
FROM Product
order by UnitPrice
LIMIT 1;
```

### OFFSET
tylko z `LIMIT` 
`LIMIT` określa maksymalną liczbę wierszy
`OFFSET` liczba wierszy do pominięcia przed zwróceniem wyniku zapytani

wybierz pięć produktów najtańszych, ale opuść trzy pierwsze wyniki (czyli bez trzech pierwszych najtańszych)
```sqlite
SELECT ProductName, UnitPrice
FROM Product
order by UnitPrice
LIMIT 5
OFFSET 3;
```

wybierz produkt, który jest na czwartym  miejscu, jeżeli chodzi o cenę:
```sqlite
SELECT ProductName, UnitPrice
FROM Product
order by UnitPrice desc
LIMIT 1
OFFSET 3;
```


### DISTINCT
`SELECT DISTINCT Country, City FROM Customer;` niepowtarzające się wartości kolumny `Country` `City`


---

### WHERE filtrowanie danych
służy do filtrowania danych poprzez zdefiniowanie jednego lub więcej warunków, aby uzyskać wymagane dane z bazy danych

__warunek__
- poprzez operatory porównania `==  ~= <> < <= > >=`
`SELECT * FROM Customer WHERE Country == 'Poland'`

- poprzez operatory logiczne `and  or  in  not in  betweem  exists  like  glob`

#### IN
`... where COuntry in ('Uk', 'Italy', 'Poland')`
`... where COuntry NOT IN ('Uk', 'Italy', 'Poland')`

#### BETWEEN .. AND ....
`... where Unitprice BETWEEN 10 AND 20;` jest inkluzywny
`... where Unitprice NOT BETWEEN 10 AND 20;` jest inkluzywny

#### NULL
`... where Fax IS NULL;`
`... where Fax IN NOT NULL;`

#### LIKE
nie wrażliwe na wielkośc liter!!!!
` % ` dowolna ilośc jakiś znaków
`... where CompanyName  LIKE 'bl%';`
`... where CompanyName NOT LIKE '%en';`

` _ ` dokładnie jeden jakiś znak 
` ___ ` dokładnie trzy jakieś znaki
`... where ContactName  LIKE 'J__n %'';`


#### GLOB
- filtrowanie na podstawie wzorca
- jest wrażliwy na wielkość liter!!!

` * ` dowolna ilość jakiś znaków
` ? ` dokładnie jeden jakiś znak

```sqlite
SELECT CompanyName, ContactName, Country
FROM Customer 
WHERE ContactName GLOB 'An? *';
```
Ana Trujillo Emparedados y helados	Ana Trujillo	Mexico
Eastern Connection	Ann Devon	UK

nazwy wszystkich firm, które zaczynają się na A lub B lub C lub D
`... where CompanyName GLOB '[A-D]*';`

z negacją: nazwy wszystkich firm, które NIE zaczynają się na A lub B lub C lub D
`... where CompanyName GLOB '[^A-D]*';`






















