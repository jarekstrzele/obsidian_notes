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









