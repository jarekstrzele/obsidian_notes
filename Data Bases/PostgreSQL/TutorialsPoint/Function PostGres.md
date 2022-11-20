[[_ 0 PostgreSQL]]

> [! info] PostgreSQL functions / Sotred Procedures
>- Allow you to carry out operations that would normally take several queries and round trips in a single function within the database.
>- Allow databse reuse as other applications can interact directly with your stored procedures instead of a middle-tier or douplicating code


## Syntax
```sql
CREATE [OR REPLACE] FUNCTION function_name (args)
RETURNS return_datatype AS $variable_name$
	DECLARE
		declaration ;
		[...]
	BEGIN
		< function_body >
		return { variable_name | value }
	END; LANGUAGE plpgsql ;
```

`[OR REPLACE]` allows to modify an existing function

EXAMPLE

testdb# select * from COMPANY;
 id | name  | age | address   | salary
---- | -------  | ----- | ----------- | --------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000

function that returns the total number f records in the COmpany table
```sql

```



