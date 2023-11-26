[[_Wprowadzenie SQL]]


---


# Subqueries
#sql/subqueries

subqueries = inner queries = nested queries

they are part of another query, called an OUTER QUERY
a subquery should always be placed within parentheses


```sql
# select the first and last name from the Employees table for the same employee numbers that can be found in the Department Manger table

SELECT
	e.first_name, e.last_name
FROM
	employees e  
where e.emp_no IN(
	select dm.emp_no
	from 
		dept_manager dm);

```


- the SQL engine starts by running the inner query
- then it uses its returned output, which is intermediate, to execute the outer query


task:
>Extract the information about all department managers who were hired between the 1st of January 1990 and the 1st of January 1995.

```sql
SELECT   *
FROM
    dept_manager
WHERE
    emp_no IN (SELECT
            emp_no
        FROM
            employees
        WHERE
            hire_date BETWEEN '1990-01-01' AND '1995-01-01');

```




## EXISTS OPERATOR
> checks whether certain row values are found within a subquery
> this check is conducted _row by row_
> 

If a row values of a subquery *exists*  -> TRUE -> the corresponding record of the outer query is extracted

If a row values of a subquery *doesn't exist* -> FALSE -> no row value from the outer query is extracted


### exists  vs in

| EXISTS  |   IN    |
|---------|---------|
|tests row values for existence  | searches among  values |
|quicker in retrieving large amounts of data      | faster with smaller datasets   |


```sql
SELECT
	e.first_name, e.last_name
FROM
	employees e 
WHERE
	EXISTS( select *
    from
		dept_manager dm
	where
		dm.emp_no = e.emp_no)
ORDER BY emp_no;
```


**subqueries**
- allow for better _structuring_ of the outer query
- thus, each inner query can be thought  of in isolation
- in some situations, the use of subqueries is much *more intuitive* comapred to the use of complex joins and unions
- many users prefer subqueries simply because they offer *enhanced code readability*

task:
Select the entire information for all employees whose job title is “Assistant Engineer”.
```sql
SELECT *
FROM
 employees e
WHERE
 EXISTS( SELECT *
	FROM
		titles t
	WHERE
		t.emp_no = e.emp_no
	AND title = 'Assistant Engineer');
```


```sql
SELECT
	e.emp_no as employee_ID,
MIN(de.dept_no) as department_code,
(SELECT
		emp_no
	FROM dept_manager
	WHERE
		emp_no = 110022) AS manager_ID
FROM
  employees e
join dept_emp de on e.emp_no = de.emp_no
where e.emp_no <= 10020
group by e.emp_no
Order by e.emp_no;
```

#sql/exists

```sql
DROP TABLE IF EXISTS emp_manager;
CREATE TABLE emp_manager(
	emp_no INT(11) NOT NULL,
    dept_no CHAR(4),
    manager_no INT(11) NOT NULL
);

```



















