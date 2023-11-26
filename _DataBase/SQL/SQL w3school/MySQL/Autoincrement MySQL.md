[[0 - CRUD Databases MySQL]]


---


# AUTOINCREMENT
allows a unique number to be generated automatically when a new record is inserted into a table.

`AUTO_INCREMENT`

```sql
CREATE TABLE Persons (
    Personid int NOT NULL AUTO_INCREMENT,
    ...
```

To let the `auto_increment` sequence start with another value, use:
```sql
ALTER TABLE Persons AUTO_INCREMENT=100;
```

```sql
INSERT INTO Persons (FirstName,LastName)
VALUES ('Lars','Monsen');
```




