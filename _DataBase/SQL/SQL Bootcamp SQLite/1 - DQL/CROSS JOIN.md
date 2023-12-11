[[_ SQLite]]

[[_ Łączenie tabel SQLite]]

---

# CROSS JOIN
#sql/cross_join 
>Dopasowuje każdy wiersz pierwszej tabeli do każdego wiersza drugiej tabeli
>

tab1 ma X kolumn
tab2 ma Y kolumn
to tabela wynikowa będzie miała $X+Y$ __kolumn__ 
zaś __wierszy__ będzie miała $X*Y$

`SELECT ... FROM tab1 CROSS JOIN tab2 ...;`
równoważne
`SELECT ... FROM tab1 JOIN tab2 ...;`
`SELECT ... FROM tab1, tab2 ...;`


```sql
SELECT category_name,
		quarter
FROM calendar
CROSS JOIN category
ORDER BY category_name;
```


----

## PRZYKŁADY
w nowej bazie danych
```sql
DROP TABLE IF EXISTS category;
DROP TABLE IF EXISTS calendar;

CREATE TABLE category (
	id INTEGER PRIMARY KEY,
	category_name TEXT NOT NULL
);

CREATE TABLE calendar(
	id INTEGER PRIMARY KEY,
	quarter TEXT NOT NULL
);
```

```sql
INSERT INTO category(category_name)
VALUES ('in-store'),
		('online');

INSERT INTO calendar (quarter)
VALUES ('Q1'),
		('Q2'),
		('Q3'),
		('Q4');
```

```sql
SELECT category_name, quarter
FROM category
CROSS JOIN calendar
WHERE quarter == 'Q2'
ORDER BY 2;
```

```sql
CREATE TABLE report AS
	SELECT category_name, quarter
	FROM category
	CROSS JOIN calendar;
	
SELECT * from report;
```

