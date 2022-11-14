[[_ SQLite]]

[[_ Łączenie tabel SQLite]]

---
# SELF JOIN
> łączenie tabeli samej z sobą


```sql
CREATE TABLE sales (
    id INTEGER PRIMARY KEY,
    quarter TEXT NOT NULL,
    revenue REAL NOT NULL CHECK (revenue > 0)
    
);

INSERT INTO sales (quarter, revenue)
VALUES ('Q1', 150000),
       ('Q2', 180000),
       ('Q3', 210000),
       ('Q4', 250000);
       

```


zapytanie typu [[CROSS JOIN | cross join]]
```sql
SELECT *
FROM sales AS t1
JOIN sales AS t2;
```

połączenie kwartału z kwartałem po nim następującym
```sql
SELECT *
FROM sales AS t1
JOIN sales AS t2 ON t1.id = t2.id -1;
```

wyświetl kolumnę z `Q` oraz kolumnę z przychodem dla każdego `Q`
```sql
SELECT t1.quarter || ' ~ ' || t2.quarter as period,
       t1.revenue AS revenue_Q1,
       t2.revenue AS revenue_Q2
FROM sales AS t1
JOIN sales AS t2 ON t1.id = t2.id -1;


```


```sql
SELECT t1.quarter || ' ~ ' || t2.quarter as period,
       t1.revenue AS revenue_Q1,
       t2.revenue AS revenue_Q2,
       (t2.revenue - t1.revenue) AS quarter_change,
      round( ((t2.revenue - t1.revenue) / t1.revenue) * 100) AS pct_chanege
FROM sales AS t1
JOIN sales AS t2 ON t1.id = t2.id -1
```
