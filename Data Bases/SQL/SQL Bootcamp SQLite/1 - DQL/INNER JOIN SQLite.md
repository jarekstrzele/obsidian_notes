[[_ SQLite]]
[[_ Łączenie tabel SQLite]]


---
# INNER JOIN
> służy do parowania rekordów z dwóch tabel

`SELECT ... FROM t1 INNER JOIN t2 ON condition`

w zasadzie jak [[CROSS JOIN | cross join ]]
```sql
SELECT *
FROM user INNER JOIN user_group;
```

poprawnie:
```sql
SELECT *
FROM user 
CROSS JOIN user_group 
	  ON user.user_group_id = user_group.id;
```

porównaj z [[LEFT JOIN SQLIte | left join]]
```sql
SELECT t1.id,
       t1.first_name,
       t1.last_name,
       t2.group_name
FROM user AS t1
CROSS JOIN user_group AS t2 
	  ON t1.user_group_id = t2.id;
```






