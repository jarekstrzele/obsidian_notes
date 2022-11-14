[[_ DDL SQLite]]





---
# Ograniczenia


## DEFAULT
- domyślna wartość ograniczeń to `NULL`
- klauzula `DEFAULT` pozwala zmienić/określić domyślną wartość dla kolumny
- wartość domyślna także może przyjmować specjalne słowa kluczowe: `CURRTENT_TIME  CURRENT_DATE CURRENT_TIMESTAMP`

```sql
DROP TABLE IF EXISTS user;

CREATE TABLE user(
    id INTEGER PRIMARY KEY,
    fn TEXT,
    ln TEXT,
    email TEXT,
    country TEXT
);


INSERT INTO user (fn, ln, email)
VALUES ('pawel', 'nowak', 'pw.@wp.pl');

INSERT INTO user (fn, ln, email)
VALUES ('jan', 'nowak', 'jw.@wp.pl');

INSERT INTO user (id, fn, ln, email)
VALUES (10, 'pawel', 'nowak', 'pw.@wp.pl');
INSERT INTO user (fn, ln, email)
VALUES ('pawel', 'kowalski', 'pk.@wp.pl');
```

wszędzie w kolumnie `country` będzie wartość `NULL`
ale możemy to zmienć

```sql
DROP TABLE IF EXISTS user;

CREATE TABLE user(
    id INTEGER PRIMARY KEY,
    fn TEXT,
    ln TEXT,
    email TEXT,
    country TEXT DEFAULT "Poland"
);


```
teraz, o ile nie będzie określona wartość kolumny `country` Sqlite wstawi wartość "Poland" a nie `NULL`


można też używać:
```sql
....

	created_at TEXT DEFAULT CURRENT_TIME
```


## AUTOINCREMENT
- wymaga więcej CPU, pamięci, przestrzeni dyskowej i jeżeli nie jest konieczne powinniśmy tego unikać,
- w SQLite kolumna `INTEGER PRIMARY KEY ` jest aliasem dla `ROWID`, któr jest 64-bitową liczbą calkowita ze znakiem
- w SQLite `INTEFER PRIMARY KEY` jest automatycznie wypełniona nieużtywaną liczbą cąłkowitą, zwykle o jeden większą niż aktualna wartość dla `ROWID`
- `INTEGER PRIMARY KEY AUTOINCREMENT` zapobiego ponownemy wykorzystaniu `ROWID` z wcześniej usuniętych wierszy

## UNIQUE
- kolumna może mieć więcej niż jedną kolumnę w tabeli z `UNIQUE`
- SQLite dla `UNIQUE` automatycznei tworzy indeks
- 

## CHECK
#sqlite/check

- sprawdza dane przed wrzuceniem do tabeli
- może być dołączone do definicji kolumny lub jako ograniczenie na poziomie tabeli
- za każdym razem, gdy nowy wiersz jest wstawiany lub istniejący wiersz jest aktualizowany wyrażenie związane zograniczniem CHECK jest sprawdzane i rzutowane na wartość numeryczną

```sql
CREATE TABLE stock(
   id INTEGER PRIMARY KEY,
   ticker TEXT CHECK (LENGTH(ticker) == 3),
   full_name TEXT CHECK (full_name != ''),
   price REAL CHECK (price > 0)
);


```
wartość `ticker` musi składać się z 3 znaków
wartość `full_name` nie może być pustym stringiem
wartość `price` musi być liczbą dodatnią

## NOT NULL
dla SQLit wszystkie wartości `UNIQUE` mogą być różnymi nullami, więc trzeba łączyć not null z unique, aby mieć unikalne wartości wykluczające możliwość pojawienia się wartości NULL
























