[[SQL Stored routines]]

---





## Variables
#sql/variable
`SET @variable_name=value;`
`CALL procedure_name( , @variable_name);`
`SELECT @variable_name;`


```sql
SET @v_emp_no=0;
CALL emp_info('Aruna', 'Journel', @v_emp_no);
SELECT @v_emp_no;
```
