[[_ SQLite]]


[[_ Łączenie tabel SQLite]]

---
# LEFT JOIN
#sql/left_join 

>do każdego rekordu z lewej tabeli staramy się dopasować rekord z prawej tabeli

```sql
SELECT ...
FROM tab1
LEFT JOIN tab2 ON condition
```

```sql
CREATE TABLE user_group (
    id INTEGER PRIMARY KEY,
    group_name TEXT NOT NULL
);


CREATE TABLE user (
    id INTEGER PRIMARY KEY,
    first_name TEXT,
    last_name TEXT,
    email      TEXT UNIQUE,
    user_group_id INTEGER NOT NULL
);

INSERT INTO user_group(group_name)
VALUES ('admin'),
          ('user'),
          ('tester'),
          ('developer');


INSERT INTO user (first_name, last_name, email, user_group_id)
VALUES ('John', 'Smith', 'js@eess.org', 1),
        ('John', 'Doe', 'jd@eess.org', 1),
        ('Philip', 'Smith', 'phs@eess.org', 1),
        ('Adam', 'Nowak', 'an@eess.org', 1),
        ('Mark', 'Govic', 'mg@eess.org', 1);
```

```sql
SELECT t1.first_name,
	   t1.last_name,
	   t2.group_name 
FROM user AS t2
LEFT JOIN user_group AS t2
     ON t1.user_group_id = t2.id;

-- zmień wartości user_group_id update, powinny być 1,2,3,10,9
```












