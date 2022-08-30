[[_ DDL SQLite]]


---
# Klucz obcy
`PRAGMA foreign_keys;` jeżeli zwróci jedynkę, to SQLite obsługuje klucze obce

> ==klucz obcy== to kopia klucza głównego przechowywana w innej tabeli 


```sql
CREATE TABLE user_group(
	id INTEGER PRIMARY KEY,
	group_name TEXT NOT NULL
	);


```

```sql
CREATE TABLE user()
	id INTEGER PRIMARY KEY,
	first_name TEXT,
	last_name TEXT,
	email TEXT UNIQUE,
	user_group_id INTEGER NOT NULL REFERENCES user_group(id)
	);
	-- inna końcówka:
	-- ... ( ...
	-- user_group_id INTEGER NOT NULL
	-- FOREIGN KEY (user_group_id) REFERENCES user_group (id)
	-- );
```

---
Gdybśmy chcieli zmienić tabelę `user_group`, wówczas silnik bazodanowy wykona działanie domyślne (domyślnie: zabronienie zmian)

Można zmienić to domyślne działanie przez `on delete` lub `on update`



## ON DELETE ...
- `ON DELETE SET NULL` gdy będzie kasowanie, to wstaw w to miejsce  wartość `NULL`
- `... SET DEFAULT`
- `... RESTRICT` nie pozwala na zmianę ani usunięcie wartości klucza nadrzędnego
- `... NO ACTION` podobny efekat jak RESTRICT
- `... CASCADE` propaguje zmiany z tabeli nadrzędznej do tabeli podrzędnej

np. usuwamy jakąś grupę, więć `CASCADE`, czyli usunięte będą wszystkie rekordy z tabeli `user`, w których występuje taka sama wartość jak usuwana grupa z tabeli `user_group`

`... FOREIGN KEY (user_group_id) REFERENCES user_group(id) ON DELETE CASCADE`

`DELETE FROm nazwaTabeli WHERE warunek;`


## ON UPDATE ...
- `ON DELETE SET NULL` gdy będzie kasowanie, to wstaw w to miejsce  wartość `NULL`
- `... SET DEFAULT`
- `... RESTRICT` nie pozwala na zmianę ani usunięcie wartości klucza nadrzędneto
- `... NO ACTION` podobny efekat jak RESTRICT
- `... CASCADE` propaguje zmiany z tabeli nadrzędznej do tabeli podrzędnej

`... FOREIGN KEY (user_group_id) REFERENCES user_group(id) ON UPDATE CASCADE`

`UPDATE nazwaTabeli SET id=5 WHERE id ==4;`

----

# Przykłady

----
klauzula `IF EXISTS` lub klauzula `IF NOT EXISTS`
```sql
DROP TABLE IF EXISTS uczen_bez_klucza;
DROP TABLE IF EXISTS klasa_bez_klucza;
DROP TABLE IF EXISTS uczen;
DROP TABLE IF EXISTS klasa;


CREATE TABLE IF NOT EXISTS table_name(...);
```

---
## kasowanie oraz zmiana wartości w rekordach w tabelach bez klucza obcego
baza: klucze
```sql
CREATE table uczen_bez_klucza(
    id_uczen INTEGER  PRIMARY KEY,
    name TEXT,
    id_klasa INTEGER
);

CREATE TABLE klasa_bez_klucza(
    id_klasa INTEGER PRIMARY KEY,
    nazwa TEXT
);


INSERT INTO klasa_bez_klucza(nazwa)
VALUES ("Ia"), ("IIb"), ("Ic"), ("IId");

select * from klasa_bez_klucza;

INSERT INTO uczen_bez_klucza(name, id_klasa)
VALUES("Wedźmin", 1), ("Frodo", 1), ("Kapitan Ameryka", 4), ("Janko Muzykant", 1);

select * from uczen_bez_klucza;

DELETE FROM uczen_bez_klucza where id_uczen = 2;
DELETE FROM klasa_bez_klucza WHERE id_klasa == 1;

UPDATE klasa_bez_klucza SET id_klasa = 100 WHERE id_klasa = 4;

```

---

## kasowanie oraz zmiana wartości w rekordach w tabelach z kluczem obcym

### ustawienia domyślne
```sql

CREATE TABLE klasa(
    id_klasa INTEGER PRIMARY KEY,
    nazwa TEXT
);

INSERT INTO klasa(nazwa)
VALUES ("Ia"), ("IIb"), ("Ic"), ("IId");

select * from klasa;

INSERT INTO uczen(name, id_klasa)
VALUES("Wedźmin", 1), ("Frodo", 1), ("Kapitan Ameryka", 4), ("Janko Muzykant", 1);

select * from uczen;

DELETE FROM uczen where id_uczen = 2;
DELETE FROM klasa WHERE id_klasa == 1;
UPDATE klasa SET id_klasa = 100 WHERE id_klasa = 4;


```

---
### ON SET NULL
zmianie ulegnie tylko:
```sql
CREATE table IF NOT EXISTS uczen(
    id_uczen INTEGER  PRIMARY KEY,
    name TEXT,
    id_klasa INTEGER,
    FOREIGN KEY (id_klasa) REFERENCES klasa(id_klasa) ON DELETE CASCADE
);

```



### ON CASCADE
nowa definicja tabeli uczen
```sql
CREATE table IF NOT EXISTS uczen(
    id_uczen INTEGER  PRIMARY KEY,
    name TEXT,
    id_klasa INTEGER,
    FOREIGN KEY (id_klasa) REFERENCES klasa(id_klasa) ON DELETE SET NULL ON UPDATE CASCADE
);
```














