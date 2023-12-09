[[_Wprowadzenie SQL]]



# SECTION 14 SQL JOINS
[[subquery]]

**j o i n s**  
- we must find a related column from the two tables that contains teh same type of data  
- we will be free to add columns from these two tables to our output     


---------------------  
#sql/inner_join
**I N N E R   J O I N**            
extract only records in which the values in the related cols match (**e.g. without NULL values**)  

część wspólna dwóch zbiorów ---    result set, INNER JOIN can help us extract this **result set**  

matching values = matching records  
rest non-matching values = non=matching records  

```sql
SELECT 
	 tab1.col_name(s),  tab2.col_name(s)  
FROM
	tab1  
JOIN 
	tab2    ON    tab1.col = tab2.col;  
```

```sql
SELECT
 t1.col_name(s),  t2.col_name(s)  
FROM tab1 t1  
JOIN tab2 t2   ON    t1.col = t2.col;  
```

```sql
SELECT   
    m.dept_no, m.emp_no, d.dept_name  
FROM  
    dept_manager_dup m  
        INNER JOIN  
    departments_dup d ON m.dept_no = d.dept_no  
ORDER BY m.dept_no;  
```

```sql
SELECT    
	e.emp_no, e.first_name, e.last_name,
	dm.dept_no, e.hire_date  
FROM
	employees e
JOIN
	dept_manager dm
	ON e.emp_no = dm.emp_no;
```

**DUPLICATE RECORDS / ROWS **            identical rows in an SQL table  

you cannot allow yourself to assume there are no duplicate rows in your 

## Left Join
#sql/left_join 
#sql/one-to-many_reletionships
1. all matching values of the two tables
2. all values from the left table that match no values from the right table

```sql
SELECT 
    m.dept_no, m.emp_no, d.dept_name
FROM
    dept_manager_dup m
       left JOIN
    departments_dup d ON m.dept_no = d.dept_no
ORDER BY m.dept_no;
```

## Right Join
#sql/righ_join
#sql/one-to-many_reletionships 
> their functionality is identical to LEFT JOINs, with the oly difference being that the direction of the operatio is inverted

```sql
select
	m.dept_no, m.emp_no, d.dept_name
from
	dept_manager_dup m
		RIGHT JOIN
	departments_dup d 
		ON m.dept_no = d.dept_no
order by m.dept_no;
```

## The Old Join Syntax
```sql
SELECT
	t1.co, t1.col, .., t2.col, ...
FROM
	table_1 t1,
	table_2 t2
WHERE
	t1.col = t2.col;
```
This more time-consuming

old way
```sql
SELECT 
	e.emp_no,
    e.first_name,
    e.last_name,
    m.dept_no,
    e.hire_date
FROM 
	employees e,
    dept_manager_dup m
where
	e.emp_no = m.emp_no;
```

new way
```sql
SELECT 
	e.emp_no,
    e.first_name,
    e.last_name,
    m.dept_no,
    e.hire_date
FROM 
	employees e
    join
    dept_manager_dup m
	on
	e.emp_no = m.emp_no;
	
```

## JOIN and WHERE
```sql
SELECT
	e.emp_no, e.first_name, e.last_name, s.salary
FROM
	employees e
		JOIN
	salaries s ON e.emp_no = s.emp_no
WHERE
	s.salary > 145000;


---


SELECT 
	e.emp_no, 
    e.first_name, 
    e.last_name, 
    e.hire_date, 
    t.title
FROM 
	employees e
    join
    titles t
    on e.emp_no = t.emp_no
where 
	e.first_name = 'Margareta' and e.last_name='Markovitch';
```


## CROSS JOIN
#sql/cross_join

>a __cross join__ will take the values from a certain table and connect them with all the values from the tables we want to join it with

> - connects all the values, not just those that match
> - the Cartesian product of the values of two or more sets
```sql
SELECT 
	dm.*, d.*	
FROM 
	dept_manager dm
CROSS JOIN
	departments d
WHERE
 d.dept_np = 'd009'
ORDER BY d.dept_no;
```

Task:
>Return a list with the first 10 employees with all the departments they can be assigned to.
_Hint: Don’t use LIMIT; use a WHERE clause._

Solve:
```sql
SELECT e.*, d.*
FROM employees.employees e
		cross join
	departments d
where
	e.emp_no <10011
order by e.emp_no, d.dept_name;
```




## Aggragate Functions with joins
#sql/aggregate_functions


Task: 
> Find the average salaries of men and women in the comapny
```sql
SELECT
	e.gender, AVG(s.salary) AS average_salary
FROM
	employees e
JOIN
salaries s on e.emp_no = s.emp_no
GROUP BY gender;

```


Task
>Select all managers’ first and last name, hire date, job title, start date, and department name.
```sql
SELECT
	e.first_name, e.last_name, e.hire_date, 
	t.title,
	m.from_date,
	d.dept_name
FROM
	employees e
JOIN
   dept_manager m ON e.emp_no = m.emp_no
JOIN
	departments d ON m.dept_no = d.dept_no
JOIN
	titles t ON e.emp_no = t.emp_no
	AND m.from_date = t.from_date**
ORDER BY e.emp_no;
```


## Tips and Tricks for joins

#tips_tricks
- one should look for key columns, which are common between the tables involved in the analysis and are necessary to solve the task at hand
- these columns do not need to be foreign or private keys

```sql
SELECT 
	d.dept_name, avg(salary) AS avg_salary
FROM
	departments d 
		JOIN
	dept_manager m ON  d.dept_no = m.dept_no
		JOIN
	salaries s ON m.emp_no = s.emp_no
GROUP BY d.dept_name
HAVING avg_salary > 6000
ORDER BY avf_salary DESC;
```


## UNION
#sql/union

*UNION ALL*
- used to combine a few SELECT statements in a single output
- you can think of it as a tool that allows you to unify tables

```sql
SELECT
	N columns
FROM
	tab_1
UNION ALL SELECT
	N columns
FROM
	tab_2;

```

**columns shoud have**:
- the same name,
- the same order,
- related data types
```sql
SELECT
	e.emp_no,
	e.first_name,
	e.last_name
	NULL AS dept_no,
	NULL AS from_date
FROM
	employees_dup e
WHERE
	e.emp_no = 10001
UNION ALL SELECT
	NULL AS emp_no,
	NULL AS first_name,
	NULL AS last_name
	m.dept_no,
	m.from_date

```



>when uniting two identically organized tables:
>- UNION display only distinct values in the output and uses more MySQK resources (computatuinal power and storage space)
>- UNION ALL retrieves the duplcates as well



---

## SQL Self Join
- applied when a table must joint itself
- think about that like you want to join virtual projections of the base table
- so data will come from a single source 
- __you have to use alisases__
- __using alisases is _obligatory___ 

> you can either filter both in the join, or you can filter one of them in the WHERE clause, and the othe one - in the join

Task:
From the map_manager table, extract the record data only of those emploees who are managers as well

Solve -> two ways:
```sql
SELECT DISTINCT  e1.*
FROM emp_manager e1
JOIN emp_manager e2
ON e1.emp_no = e2.manager_no;



SELECT DISTINCT  e1.*
FROM emp_manager e1
JOIN emp_manager e2
ON e1.emp_no = e2.manager_no
WHERE 
	e2.emp_no IN (SELECT
					manager_no
				  FROM emp_manager);


```



























