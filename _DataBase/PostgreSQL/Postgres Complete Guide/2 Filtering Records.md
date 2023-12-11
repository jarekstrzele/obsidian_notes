[[_0 Strat PostgreSql CompleteGuide]]

# Filtering Rows with `WHERE`
`SELECT name, area FROM Cities WHERE area > 4000 ;`
FIRST: `From Cities`
SECOND: `WHERE area > 4000`
THIRD: `SELECT name, area`

Is equal? ` area = 8821`
In not equal? `area != 8821`


## Where
```sql
SELECT name, area 
FROM Cities 
WHERE 
	area BETWEEN 2000 AND  4000 ;
```
```sql
SELECT name, area 
FROM Cities 
WHERE  
		 name	IN ('Delhi', 'Shanghai') ;
```

```sql
SELECT name, area 
FROM Cities 
WHERE  
	area NOT IN (3043, 4000)  AND name='Delhi';
```


```sql
SELECT
	name,
	population / area AS population_density
FROM
	cities
WHERE population / area > 6000 ;
```

## Update Rows












