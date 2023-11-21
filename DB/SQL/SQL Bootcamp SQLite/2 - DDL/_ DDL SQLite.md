[[_ SQL Bootcamp - SQLite cz. 1]]
[[_ SQL Bootcamp - SQLite cz. 2]]
[[_ SQLite]]

---
[[Create i DROP table SQLIte]]
[[typy danych]]
[[PRIMARY KEY i ROWID]]
[[Indeksy]]
[[Ograniczenie]]
[[Klucz obcy]]
[[Relacje]]
[[Modyfikacja tabeli ALTER]]



---
# DDL Data Definition Language
#sqlite #ddl

definiowanie strukutry obiektów w db

**CREATE**
	`CREATE TABLE ...`
	`CREATE VIEW ...`
	`CREATE INDEX ...`
`CREATE TABLE IF NOT EXISTS ...`

**ALTER**
	`ALTER TABEL ...`

**DROP**
	`DROP ...` usuwanie obiektu w DB
	`DROP TABLE ...`
	`DROP VIEW ...`
	`DROP INDEX ...`
`DROP TABLE IF EXISTS ...`

## Konwencja nazewnictwa
- przyjąć jedną konwencję dla całego projektu (PascalCase, snake_case), czyli zamiat *First_Name* -> *first_name*
- unikać nazw identyfikatorów zwierających spację
- uniać przesadnych skrótów
- unikamy używania słów kluczowych
- używać krótkich nazw, które są opisujące
- nazwy tabel w formie pojedycznej (w całym projekcie
- rekomendacje:
	- *id* to klucz główny
	- *nazwa_tabeli_id* klucz obcy










