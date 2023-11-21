[[SQL Stored routines]]
[[Procedure MySQL]]


---
# User-Defined Functions
[[_Advanced SQL Topics]]


```sql
DELIMITER $$
CREATE FUNCTION func_name(parameter data_typ) RETUNRS data_type
DECLARE var_name data_type
BEGIN
	SELECT ...
RETURN var_name
END$$

DELIMITER ;
```


__Function vs Procedure__
- in parantheses you don't define `out` parameters
- all params are `in` so you need not explicitly indicate it with the word `in`
- you need to use `return`

---
[[Error Code 1418]]
If error binary log, write between `create` and `begin` one of:
`DETERMINISTIC  NO SQL  READS SQL  DATA`
eventually seperate them by `,`


## to run function
`SELECT func_name(params);`

or 
lighting button in the work bench


example of function
```sql
USE employees;
DROP procedure IF EXISTS f_emp_avg_salary_out;

DELIMITER $$
CREATE FUNCTION f_emp_avg_salary_out(p_emp_no INTEGER) RETURNS DECIMAL(10,2)
DETERMINISTIC NO SQL READS SQL DATA
BEGIN
DECLARE v_avg_salary DECIMAL(10,2);

SELECT
	AVG(s.salary)
INTO v_avg_salary FROM
	employees e
		JOIN
	salaries s ON e.emp_no = s.emp_no
WHERE
	e.emp_no = p_emp_no;
    
RETURN v_avg_salary;
END$$

DELIMITER ;

```

---

```sql
DELIMITER $$

CREATE FUNCTION emp_info(p_first_name varchar(255), p_last_name VARCHAR(255)) RETURNS DECIMAL(10,2)
DETERMINISTIC NO SQL READS SQL DATA
BEGIN
  DECLARE v_max_from_date date;
  DECLARE v_salary decimal(10,2);
SELECT
  MAX(from_date)
INTO v_max_from_date FROM
  employees e
    JOIN
  salaries s ON e.emp_no = s.emp_no
WHERE 
  e.first_name = p_first_name
  and e.last_name = p_last_name;
  
SELECT 
 s.salary
INTO v_salary FROM 
  employees e 
   join
  salaries s ON e.emp_no = s.emp_no
where
 e.first_name = p_first_name
  and e.last_name = p_last_name
  and s.from_date = v_max_from_date;
  
return v_salary;

```
