#sqlite   

# Wyzwalacze Trigger
gdy potrzeba walidacji danych, gdy chcielibyśmy wrócić do poprzednich wartości po update

> wyzwalacze ==TRIGGER== to operacje wykonywane automatycznie na bazie danych po wystąpieniu określonego zdarzenia

wyzwalacz jest uruchamiany dla każdego wiersza (**for each row**)

```sql
CREATE TRIGGER trigger_name [BEFORE | AFTER] [DELETE | INSERT | UPDATE]
ON table_name
BEGIN
	-- logic
END;

```

DELETE -> OLD
INSERT -> NEW
UPDATE -> NEW, OLD

wyzwalacze są automatycznie usuwane poskasowaniu tabeli, z którą są skojarzone

`DROP TRIGGER trigger_name;`

---
Przykłady
np. chcemy wprowadzić zabezpieczenie przed błędym adresem mejlowym wprowadzonym do tabeli

```sql
CREATE TRIGGER validate_email BEFORE INSERT
on stock
BEGIN
 SELECT CASE
  WHEN NEW.contact_email NOT LIKE '%_@__%.__%'    
  THEN RAISE(ABORT, 'Invalid email')
 END;
END;
```

o funkcji [[raise SQLite | raise ]]

stosowanie `case` ([[SELECT CASE SQLIte | TU ]]):


śledzenie zmian w adresach mejlowych
```sql

CREATE TABLE stock_logs(
    id                  integer primary key,
    old_id              int,
    new_id              int,
    old_contact_email   text,
    new_contact_email   text,
    action_type         text,
    created_at          text
);
 

CREATE TRIGGER logs_update_email AFTER UPDATE
ON stock WHEN OLD.contact_email != NEW.contact_email
BEGIN
    INSERT INTO stock_logs(old_id, new_id,  old_contact_email, new_contact_email, action_type, created_at)
    VALUES(
        OLD.id, NEW.id, OLD.contact_email, NEW.contact_email, 'UPDATE', DATETIME('now'));
END;

SELECT * FROM stock;
SELECT * FROM stock_logs;

UPDATE stock SET contact_email = 'ir@NOWY.com' WHERE id ==2;
```

o funkcji [[datetime sqlite | datetime` ]]


















