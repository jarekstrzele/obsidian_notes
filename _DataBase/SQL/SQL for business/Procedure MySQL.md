[[SQL Stored routines]]
[[User-Defined Functions in MySQL]]


---

# Procedure MySQL
#sql/procedure

## SYNTAX

### stored procedures
`;` is a:
	- statement terminator.
	- delimiters (technically)


`;` is a delimiter, but to use properly routines you have to temporely change a symbol of delimiter 

```sql
DELIMITER $$
CREATE PROCEDURE procedure_name(par1, par2, ...)
BEGIN
	SELECT * FROM employyes
	LIMIT 1000;
END $$
DELIMITER ; // For this moment on, $$ will not act as a delimiter

```

>__parameters__ represent certain values that the procedure will use to complete the calculation it is suposed to execute

> You can attach any parameters, but you have to use `()`


---

## NON_PARAMETRIC


### Create procedure 

>When dropping a nonparameterized procedure, we should not write the parentheses at the end!!!
>

```sql
USE employees;
DROP PROCEDURE IF EXISTS select_employees;

DELIMITER $$
CREATE PROCEDURE select_employees()
BEGIN

		SELECT * FROM employees
        LIMIT 1000;
END$$
DELIMITER ;
```

In SCHEMAS employees -> Stored Procedures (remember to refresh!!).

__Another way__:
In the Workbench "employees" > Stored Procedures > right button "Create ..." ... after "Apply" button

---

### Invoke the procedure

There are three main ways:
1. `CALL database_name.procedure_name();`
2. `CALL procedure_name();` if we selected a database
3. In the Schema use a button.


```sql
use employees;

DROP PROCEDURE IF EXISTS avg_salary;

DELIMITER $$
CREATE PROCEDURE avg_salary()
BEGIN
	SELECT AVG(salary) FROM employees.salaries;
END$$
DELIMITER ;

CALL avg_salary;
CALL avg_salary();

```

---

### DELETE procedure
`DROP PROCEDURE procedure_name;`

or

in the Wokrbench in the Stored Procedures select your procedure > right click and "Drop Stored ..."


---

## PARAMETRIC
```sql
DELIMITER $$
CREATE PROCEDURE procedure_name(IN parameter_name data_type)
BEGIN
	SELECT...;
END$$
DELIMITER ;
```

```sql
USE employees;
DROP procedure IF EXISTS emp_salary;

DELIMITER $$
USE employees $$
CREATE PROCEDURE emp_salary(IN p_emp_no INTEGER)
BEGIN
SELECT
	e.first_name, e.last_name, s.salary, s.from_date, s.to_date
FROM
	employees e
		JOIN
	salaries s ON e.emp_no = s.emp_no
WHERE
	e.emp_no = p_emp_no;
END $$

DELIMITER ;

```
(jakies problemy z tymi kodami)

procedures with one input parameter can be used with aggregate functions too:
```sql
DELIMITER $$
USE employees $$
CREATE PROCEDURE emp_avg_salary(IN p_emp_no INTEGER)
BEGIN
SELECT
	e.first_name, e.last_name, AVG(s.salary)
FROM
	employees e
		JOIN
	salaries s ON e.emp_no = s.emp_no
WHERE
	e.emp_no = p_emp_no;
END $$

DELIMITER ;
```


---
###  Procedures with an output parameter

```sql
DELIMITER $$
CREATE PROCEDURE proc_name(IN parameter, OUT parameter)
BEGIN
	SELECT * FROM employees
	limit 1000
END$$

DELIMITER ;
```

`out parameter` will represent the variable containing the output value of the operation executed by the query of the stored procedure

```sql
USE employees;
DROP procedure IF EXISTS emp_avg_salary_out;

DELIMITER $$
CREATE Procedure emp_avg_salary_out(in p_emp_no INTEGER, out p_avg_salary DECIMAL(10,2))
BEGIN
SELECT
	AVG(s.salary)
INTO p_avg_salary FROM
	employees e
		JOIN
	salaries s ON e.emp_no = s.emp_no
WHERE
	e.emp_no = p_emp_no;
END$$

DELIMITER ;





```


>every time you create a procedure containing both an IN and an OUT parameter
>->
>use the SELECT-INTO structure


```sql
USE employees;
DROP PROCEDURE IF EXISTS emp_info ;

DELIMITER $$
CREATE PROCEDURE emp_info(in p_first_name TEXT, in p_last_name VARCHAR(255), out p_emp_no INTEGER)
BEGIN
	SELECT e.emp_no 
    INTO p_emp_no FROM employees e
    WHERE e.first_name = p_first_name and e.last_name = p_last_name;
END$$
DELIMITER ;
```
