[[_ DDL SQLite]]



---
# CREATE TABLE
typy danych w SQL są opcjonalne


## CREATE
```sql
CREATE TABEL table_name(
	column_name column_type,
	[...]
);

CREATE TABEL IF NOT EXISTS table_name(
	column_name column_type,
	[...]
);

CREATE TABEL table_name(
	column_name column_type col_constraints,...,
	[...]
	table_constraints,
	[...]
);

CREATE TABLE IF NOT EXISTS user (
	id INTEGER PRIMARY KEY,
	name TEXT
);

CREATE TABLE IF NOT EXISTS user (
	id INTEGER,
	name TEXT,
	PRIMARY KEY (id)
);
-- definiowanie *table constraints* pozwala odnieść się do więcej niż jednej kolumny
CREATE TABLE stock (
	company TEXT NOT NULL,
	stock_exchange TEXT NOT NULL,
	price REAL,
	PRIMARY KEY (company, stock_exchange)
);
-- tuple (company, stock_exchange) jest unikalna, ale company czy stock_exchange nie muszą mieć wartości unikalnych w tabeli

```


```sqlite
CREATE TABLE IF NT EXISTS user(
	id         INTEGER PRIMARY KEY,
	first_name TEXT,
	last_name  TEXT,
	email      TEXT
);

```

### tabele tymczasowe
`CREATE TEMP TABLE ...` taka tabela będzie stworzona w specjalne bazie `temp`
`CREATE temporary TABLE ...`
`DROP TABLE temp.nazwa_tabeli;`

### tworzenie tabel z zapytania
`CREATE TABLE new_tab AS SELECT * FROM old_tab;` 
późniejsze prowadzenie zmian w `old_tab` nie wpływa na zawartość `new_tab`












## DROP
`DROP TABLE IF EXISTS user;`

```sqlite
CREATE TABLE IF NT EXISTS user(
	id         INTEGER,
	first_name TEXT,
	last_name  TEXT,
	email      TEXT,
	PRIMARY KEY (id)
);
```

- przy usuwaniu tablei trwale usuwane są także dane w niej zwarte
- powiązane z tabelą indeksy oraz wyzwalacze również są usuwane
- widoki, które odwołują się do usuwane tabeli, nie są usuwane
- usunięcie tabeli spowoduje zwolnienie miejsca w bazie danych, ale nie zminiejszy rozmiaru plikuy bazy danych. aby zmniejszyć rozmiart tego pliku należy użyć polecenia `VACUUM`










