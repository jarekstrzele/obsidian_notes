[[0-MySQL W3school]]


---

# Constraints

SQL constraints are used to specify rules for fata in a table.

Constraints are used to limit the type of data that can go into a table.

Constraints are commonly used in SQL:
- `NOT NULL` 
	SELECT column_names
	FROM table_name WHERE column_name IS NOT NULL;```

- `UNIQUE` ensures that all values in a column are different

---

## PRIMARY KEY
`PRIMARY KEY` not null+unique
To create a PRIMARY KEY constraint on the "ID" column when the table is already created, use the following SQL:
```sql
ALTER TABLE Persons
ADD PRIMARY KEY (ID);
```


```sql
ALTER TABLE Persons
DROP PRIMARY KEY;
```

---

## FOREIGN KEY
`FOREIGN KEY` prevents actions that would destroy links between tables
```sql
CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);
```




To create a FOREIGN KEY constraint on the "PersonID" column when the "Orders" table is already created, use the following SQL:
```sql
ALTER TABLE Orders
ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
```
```sql
ALTER TABLE Orders
DROP FOREIGN KEY FK_PersonOrder;
```

---

- `CHECK` ensures that  the values statisfies a specific condition
```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CHECK (Age>=18)
);
```

```sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255),
    CONSTRAINT CHK_Person CHECK (Age>=18 AND City='Sandnes')
);
```

```sql
ALTER TABLE Persons
ADD CHECK (Age>=18);
```

```sql
ALTER TABLE Persons
DROP CHECK CHK_PersonAge;
```

---

- `DEFAULT` sets a default value for a column if no value is specified

```sql
CREATE TABLE...

	City varchar(255) Default `Sandnes`
```

The DEFAULT constraint can also be used to insert system values, by using functions like CURRENT_DATE():
```sql
CREATE TABLE Orders (
    ID int NOT NULL,
    OrderNumber int NOT NULL,
    OrderDate date DEFAULT CURRENT_DATE()
);
```

```sql
ALTER TABLE Persons
ALTER City SET DEFAULT 'Sandnes';
```

```sql
ALTER TABLE Persons
ALTER City DROP DEFAULT;
```

---

- `CREATE INDEX` used to create and retrieve data from the database very quickly
>Updating a table with indexes takes more time than updateing a table without (because the indexes also need an upadate). So, only create indexes on columns that will be frequently  searched against


```sql
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```

```sql
CREATE INDEX idx_lastname
ON Persons (LastName);
```

```sql
CREATE INDEX idx_pname
ON Persons (LastName, FirstName);
```












