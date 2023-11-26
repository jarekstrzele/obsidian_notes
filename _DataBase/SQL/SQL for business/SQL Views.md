[[_Wprowadzenie SQL]]


---

# Using SQL Views
#sql/views

> __SQL view__ a virtual table whose contents are obtained from an existing table or tables, called base tables

The retrieval happens through an SQL statement, incorporated into the view.
> - a view object is as _a view_ into the base table
> - the view itself does not contain any real sata; the data is phisically stored in the base table!!!
> - the view simply shows the data contained in the base table


```sql
CREATE OR REPLACE VIEW view_name AS
SELECT
	col1, col2, ..., coln
FROM table_name;

```

SQL View acts as a _dynamic table_ because it instantly reflects data and structural changes in the base table.

You can't insert or update the information in the view.


task
>Create a view that will extract the average salary of all managers registered in the database. Round this value to the nearest cent.
If you have worked correctly, after executing the view from the “Schemas” section in Workbench, you should obtain the value of 66924.27.

Solution:
```sql
CREATE VIEW v_manager_avg_slary AS
	SELECT ROUND(avg(salary), 2) 
	FROM 
	  salaries s
		JOIN	  
      dept_manager m
	ON s.emp_no = m.emp_no;
```














