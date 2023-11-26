[[0 SQL tutorial w3school]]
[[SQL Wildcard  Characters]]


---

# LIKE
`LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column.

Two wildcards:
- `%`    represents zero, one, or multiple characters (MS Access `*`)
- `_`    represents one, single character

> You can also combine any number of conditions using `AND` or `OR` 

```sql
SELECT cols
FROM tab
WHERHE col_name LIKE `pattern`;
```

