[[_ DDL SQLite]]


---
# INDEKSY
To tabela, która pozwala na przyspieszyć wyszukiwanie (to pomocnicza struktura danych, aby przyspieszyć otrzymywanie odpowiedzi; unikamy skanowania całych tabel )

Tworzymy indeks na kolumnie `a1`, więc rekordy są sortowane zgodnie z wartościami występującymi w tej kolumnie.

Jeżeli zmianie ulega pierwotna tabela, musimy te zmiany uwzględnić w indeksie.

- indeks może być utworzony z jednej lub kilku kolumn
- indeksy zachowują kolejność sortowania kolumny lub kilku kolumn, umożliwia to pobranie zbioru wartości bez sanowania całej tabeli 
- SQLite automatycznie tworzy indeksy dla każdej kolumny z wartościami unikalnymi 
- dodawanie danych do tabeli z indeksami jest nieco wolniejsze niż do tabeli bez indeksów

`CREATE [UNIQUE] INDEX index_Name ON table_name (col_name [,..]); `

`DROP INDEX index_name;` dane w tabeli pozostaną nienaruszone

```sql
CREATE TABLE srock_market (
  ticker TEXT NOT NULL,
  company TEXT NOT NULL,
  price REAL NOT NULL
);

CREATE INDEX idx_ticker ON stock_market (ticker);
-- -> powstanie tablica z przyporządkowaniem id do ticker, a uporządkowana po kolumnie ticker
```

teraz zastosowane będzie wyszukiwanie binarne (dwa wyszukiwania binarne: jedno na indeksie, drugie na tabeli)
`SELECT price FROM stock_market WHERE ticker =='BBT';`











