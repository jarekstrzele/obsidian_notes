## Section 9  SELECT statement
 

in SQL, there are many linking keywords and symbols, called OPERATORS, that you can use with the WHERE clause  

```sql
AND  
OR  
IN              NOT IN  
LIKE            NOT LIKE  
BETWEEN ...     AND .....  
EXISTS          NOT EXISTS  
IS NULL         IS NOT NULL  
```
...  
```sql
SELECT
    *  
FROM  
    employees  
WHERE  
    first_name IN ('Cathie','Mark', 'Nathan');  
```  

pattern matching  MySQL is **case insensitive**  

where ... LIKE (patter)  

where .. NOT LIKE(patter)  

%        a substitute for a sequence of characters   LIKE('Mar%')  

_           a single character  

*           will deliver a list of all columns in a table         


BETWEEN          ... AND ...  (inclusive)     
NOT BETWEEM ... AND ...  (not inclusive)  

helps us designate the interval to which a given value belongs  
select **distinct** genderfrom employees;  

---
#sql/aggregate_function

**aggregate function**         they are applied on multiple rows of a single column of a table and return an output of a single value  
  

COUNT()      non-null records in a field  

SELECT COUNT(column_name) FROM table_name;SELECT DISTINCT COUNT(**DISTINCT** first_name )FROM employees;  

SUM()           non-null values  

MIN()  

MAX()  

AVG()  
  

### **G R O U P    B Y**   
When working in SQL, results can be grouped according to a specific field or fields  

**GROUP BY** must be placed immediately after the WHERE conditions, if any, and just before the ORDER BY clause  
```sql
SELECT column_name(s)  

FROM table_name  

WHERE _conditions_  

GROUP BY  column_name(s) 

ORDER by Column_names()  

  ```

WHen you need an aggregate function, you must add a GROUP BY clause in your query too  
```sql
SELECT first_name, count(first_name)  

FROM employees  

GROUP BY first_name;  
```
**ALWAYS INCLUDE THE FIELD
YOU HAVE GROUPED YOUR RESULTS BY IN THE  S E L E C T  STATEMENT**

### HAVING
```sql
SELECT   col_name  

FROM     tab_name  

WHERE     conditions  

GROUP BY  col_name  

HAVING conditions
ORDER BY col_names  
```
  

HAVING is like WHERE but applied to the GROUP BY block  

after HAVING, you can have a condition with an aggregate function  

for WHERE it is forbiden  

SELECT ....WHERE      COUNT(first_name_ > 250  <-- this is incorrect  

Extract all first names that appear more than 250 times in the "employees" table:  
```sql
SELECT  
	first_name, COUNT(first_name) as names_count
FROM   
      employees  

GROUP BY first_name
HAVING COUNT(first_name)> 250
ORDER BY first_name;  
```
  

#### WHERE   vs HAVING  

**where**       allows us to set conditions that refer to subsets of individual 
			  rows  

    is applied BEFORE re-organizing the output into group  
  

where  -->  group by  ---->   HAVING  

  

  

task: extract a list of all names that are encountered less than 200 time. Let the data refer to people hired after the 1st January 1999.  

SELECT  

      first_name, count(first_name) as names_count  

FROM employees  

WHERE hire_date > '1999-01-01'  

GROUP BY first_name  

HAVING count(first_name) < 200;  

  

> **prohibited**:   having non-aggragated condition   hire_date > '1999-01-01'    +  aggregated condition  e.g. count()    
> 
> **allowed**:       having non-aggragated condition  
> 
>                           aggregated condition  

  

---
 
**I N S E R T**

```sql
INSERT INTO table_name (co1, col2, ..., coln)

VALUES (val1, val2, ..., valn);  
```

> PLEASE REMEMBER TO TYPE INTEGERS AS PLAIN NUMBERS, WITHOUT USING QUOTES.  

  
***inserting many values***
```sql
INSERT INTO departments_dup(dept_no) 
VALUES ('d010'), ('d011');  
  

//inserting data into a new table

INSERT INTO tab_2 (col1, col2, ...)  

SELECT col1, col2, ..FROM table_1where condition;  

  ```
  


**C O M M I T     statement**  

-   save the transaction in the database  
-   changes cannot be undone  
  

**R O L L B A C K     clause**  

-   allows you to take a step back  
-   the last change(s) made will not count  
-   reverts to the last non-committed state  
-   will have an effect on the last execution you have performed  
 

**U P D A T E**  
```sql
UPDATE table_name  

SET col1=va1, col2=val2, ...  

WHERE conditions;  
```
  

**D E L E T E**  
```sql
DELETE FROM table_name  

WHERE conditions;  
```
  

**D R O P**         
- deletes all records and all other information (indexes, constraints, table structure, ..)  
-  you wnon't be able to roll back to its initial state, or to the last commit statement  


**TRUNCATE**       
- (delete without where) removes all records but structure remain intact  
- auto-increment values will be reset  


**DELETE**   
- removes records row by row   (WHERE!!!)  
- auto-increment values will not be reset
 