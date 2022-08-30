[[_ SQL Bootcamp - SQLite cz. 1]]
[[_ SQL Bootcamp - SQLite cz. 2]]

---
# DML Data Manipulation Language
#sqlite   #dml

wstaw, zmieniać, usuwać

### INSERT INTO
#sql/insert
`INSERT INTO table_name(col, [,...]) VALUES (new_value [, ..]);`
>[!note] zalecenie
>wstawiaj nazwy kolumn, do których będziesz wpisywał wartości
```sql
INSERT INTO stock (id, ticker, full_name, market)
VALUES (1, 'CDR', 'CD Project', 'GWP');
```


#### Wstawiawanie wierszy przy użyciu zapytania
```sql
INSERT INTO table_name (col_name [, ...])
SELECT query_statement;

CREATE TABLE company(
	id INTEGER PRIOMARY KEY,
	company_name TEXT NOT NULL
);

INSERT INTO company (company_name)
SELECT full_name FROM stock;

```

----
## MODYFIKACJA DANYCH
#sql/update
```sql
UPDATE table_name
SET column_name = new_value [, ...]
WHERE expression;
```

```sql
UPDATE stock
SET ticker = 'CDR.PL'
	full_name = 'CD project REd'
WHERE id == 1;

```
lepiej wykorzystywać kolumnę z kluczem głównym, bo jest szybsze, chyba że utworzymy [[Indeksy | Indeks]]

`where` trzeba dodawać, bo inaczej zmienimy wartości w całej kolumnie

----
## Usuwanie danych
#sql/delete 

`DELETE FROM table_name WHERE expresion;`
`DELETE FROM table_name;` usuwa całą zawartość tabeli, ale tabelę pozostawia

`DELETE FROM stock where id ==5`













