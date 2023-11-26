[[_SQL and Tableau]]

[[Tableau Task 2]]
[[Tableau Task 3]]
[[Tableau Task 4]]



---

# Tableau task 1
Create a visualization that provides a breakdown between the male and female employees working in the company each year, starting from 1990.

a BAR CHART to visualisation

SQL output: 
- first column calender_year
- second gender
- third num_of_employees

of course grouping by

SOLUTION
```sql
select 
	YEAR(dep.from_date) as calender_year,
    emp.gender,
    count(emp.emp_no) as number_of_employees
from t_dept_emp as dep
	join 
    t_employees  as emp on dep.emp_no = emp.emp_no
group by calender_year, emp.gender
HAVING calender_year >= 1990;
```

We have to transfer the SQL output into CSV format.
IN the Workbench you can export the data.

---
OPEN the Tableau.
Text file (choose )



