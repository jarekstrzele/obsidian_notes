[[_ DDL SQLite]]

---

# PRIMARY KEY (`PK`) i ROWID
> klucz główny to kolumna lub kilka kolumn, które jednoznacznie identyfikują wiersz w tabeli (wartości są unikalne)
>    - to co najmniej jedna kolumna
>    - w tabeli może być co najwyżej jeden klucz główny
> 

**Dwa sposóby definiowania klucza głównego**
- klucz główny `PRIMARY KEY` możemy zdefiniować na poziomie kolumny (gdy składa się z jednej kolumny)
- klucz główny `PRIARY KEY` ,możemy zdefiniować na poziomie całej tabeli (gdy skład się z jednje lub więcej kolumn)

W SQLite klucz główny jest opcjonalny w przypadku zwykłych tabel, ale jest wymagany wprzypadku tabel bez `ROWID` (`WITHOUY ROWID`)

- ograniczenie klucza głównego `PRIMARY KEY` implikuje ograniczenie `UNIQUE` (automatyczny ideks zostaje utworzony)
- ograniczenie `PRIMARY KEY` **NIE** implikuje ogranicznia `NOT NULL` (tak jest tylko w SQLite!!!)
- kolumnę `INTEGER PRIMARY KEY` można opcjonalnie oznaczyć jako `AUTOINCREMENT`


```sql
CREATE TABLE stock(
	stock_id INTEGER PRIMARY KEY,
	company TEXT NOT NULL
	[,...]
);

CREATE TABLE stock(
	stock_id INTEGER,
	company TEXT NOT NULL
	[,...]
	PRIMARY KEY (stock_id)
);
```
 
---
## ROWID
- SQLite dodaje niejawną kolumnę o nazwie `ROWID`, a jeżeli w tabeli występuje `INTEGER PRIMARY KEY` to ta klumna staje się aliasem dla kolumny  `ROWID` oraz dizała tutaj ograniczenie `NOT NULL`
- `ROWID` przechowuje 64-bitową liczbę całkowitą ze znakiem, ta kolumna jednocznanie identyfikuje wiersze w tabeli
- wykonywanie zapytań i sortowanie danych w tabeli z `ROWID` jest szybsze niż użycie klucza głównego, który nie jest aliasem dla kolumny `ROWID`


np.
```sql
CREATE TABLE stock_makret(
	ticker TEXT NOT NULL,
	company TEXT NOT NULL 
	price REAL NOT NULL
);				  
```

`SELECT rowid, * from stock_market;`

szybko (skanowanie binarne):
`SELECT * FROM stock_market WHERE rowid == 5;`
`EXPLAIN QUERY PLAN SELECT * FROM stock_market WHERE rowid =5;`

wolno (skanuje całą tabelę):
`SELECT * FROM stock_market WHER ticker == 'BBT';`
`EXPLAIN QUERY PLAN SELECT * FROM stock_market WHER ticker == 'BBT';`








