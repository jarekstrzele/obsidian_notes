[[_ DDL SQLite]]

----
# Modyfikacja tabli ALTER

w SQLite jest ograniczone
Można:
- dodac nową kolumnę `ALTER TABLE stock ADD COLUMN price REAL;`
- zmiana nazwy kolumny (od 3.25.0) `ALTER TABLE stock RENAME COLUMN full_name TO company_name;`
- zmiana nazwy tabeli `ALTER TABLE stock RENAME TO stock_market`


NIE MOŻEMY:
- zmodyfikować istniejącej kolumny tablei
- usunąć kolumny w tabeli

**Zamiast tego możemy**:
1. zmienić nazwę starej tabeli (user na user_old)
2. utworzyć nowa tabele o pożądanej nazwie (user)
3. skopiowac dane do nowej tabeli
4. usunąć starą tabelę (user_old)

```sql
CREATE TABLE stock (
    id    INTEGER PRIMARY KEY,
    ticker    TEXT NOT NULL,
    full_name TEXT NOT NULL
    );
    

INSERT INTO stock (ticker, full_name)
VALUES ('CDR', 'CD Projekt'), ('PLW', 'PlayWay');


-- same warunek NOT NULL nie zadziała
-- bo SQLite wypełnia puste pola istniejących
-- rekorów wartości NULL, więc dodajemy
-- DEFAULT 0 i wszystko pasuje
ALTER TABLE stock ADD COLUMN price REAL NOT NULL DEFAULT 0 CHECK(price > 0); 
```














