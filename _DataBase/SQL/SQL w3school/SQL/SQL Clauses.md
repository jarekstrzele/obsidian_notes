[[0 SQL tutorial w3school]]



# SQL Clauses



## WHERE

---


## SELECT TOP ,    LIMIT
`SELECT TOP` clause is used to specify the number of records to return

__MYSQL__ suports `LIMIT` clause to select a limited number of records;
__Oracle__ uses `FETCH FIRST n ROWS ONLY`

```sql
/*SQL Server/ MS Access)*/
SELECT TOP 3 * FROM Customers;

/*MySQL*/
SELECT * FROM Customers
LIMIT 3;


/*Oracle*/
SELECT * FROM Customers
FETCH FIRST 3 ROWS ONLY;

```

with `WHERE`
```sql
SELECT TOP 3 * FROM Customers
WHERE Country='Germany';

SELECT * FROM Customers
WHERE Country='Germany'
LIMIT 3;

```









