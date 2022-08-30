
#sql/ggregate_function 
**aggregate functions**
the gather data from many rows of a table, then aggregate it into a single value  

INPUT  the information contained in multople rows       --> OUTPUT the single values the provide  

aggregate functions typically ignore null values throughout the field to which they are applied  
  

CAN BE APPLIED TO ANY GOUP OF DATA VALUES WITHIN A CERTAIN COLUMN                **G R O U P  B Y**  

---


**C O U N T ( )**  

is applicable to both _numeric_ and _non-numeric_ data  

  

      COUNT ( DISTINCT )    helps us find the number of times unique values are encountered in a given column  

SELECT   COUNT(DISTINCT  from_date)FROM        salaries;  

  

COUNT(*)         returns the number of all rows of the table, NULL values included  

---

  

**S U M ( )**  

SUM(*)                  ->   ERROR  

only numeric data  

  

SELECT sum(salary)   

FROM employees.salaries  

where from_date > '1997-01-01';  

---

  

**MIN() and MAX()**  

SELECT MIN(salary) FROM employees.salaries;SELECT MAX(salary) FROM employees.salaries;  

  

---

  

  

**A V G ( )**  

Which is the average annual salary the company's employee received?  

SELECT AVG(salary)   

FROM  

salaries;  

  

---

  

  

**R O U N D ( )**  

usually applied to the single values that aggrefate functions return  

SELECT ROUND(AVG(salary))   

FROM  

salaries;  

  

ROUND( number,  decimal_places)  

---

  

  

I F N U L L ( )   and   C O A L ES C  E  ( )              do not make any changes to the data set!!!  

  

IFNULL(expression1, expression2)  -> expression1 if not null else expression2  

SELECT   

   dept_no,  

   IFNULL(dept_name, 'Department name not provided) as dept_name  

FROM departments_dup;      

  

**COALESCE**(exp_1, exp_2, ..., exp_n)  as IFNULL() with more than two parameters  

will always return a ungle value of the ones we have within parentheeses, and this values will be the first _non-null_ value of this list, reading the values from left to tight  

  

SELECT   

   dept_no,  

   COALESCE(dept_name, 'Department name not provided) as dept_name  

FROM departments_dup;    

  

SELET dept_no, dept_name,  

      COALESCE('department manager name') as fake_col  

FROM   

     departments_dup;  

  

  

> Select the department number and name from the ‘departments_dup’ table and add a third column where you name the department number (‘dept_no’) as ‘dept_info’. If ‘dept_no’ does not have a value, use ‘dept_name’.  
> 
>   
> 
> **SELECT    dept_no,    dept_name,    COALESCE(dept_no, dept_name) AS dept_info**  
> 
> **FROM    departments_dup**  
> 
> **ORDER BY dept_no ASC;**  

> Modify the code obtained from the previous exercise in the following way. Apply the IFNULL() function to the values from the first and second column, so that ‘N/A’ is displayed whenever a department number has no value, and ‘Department name not provided’ is shown if there is no value for ‘dept_name’.  
> 
>   
> 
> **SELECT    IFNULL(dept_no, 'N/A') as dept_no,**  
> 
>                  **IFNULL(dept_name,  'Department name not provided') AS dept_name,**                    **COALESCE(dept_no, dept_name) AS dept_info  
> FROM    departments_dup  
> ORDER BY dept_no ASC;**

