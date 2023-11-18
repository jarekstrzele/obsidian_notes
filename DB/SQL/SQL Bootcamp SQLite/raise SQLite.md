https://www.sqlite.org/syntax/raise-function.html


`RAISE(IGNORE)`
`RAISE(ROLLBACK, error-message)`
`RAISE(ABORT, error-message)`
`RAISE(FAIL, error-message)`

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




