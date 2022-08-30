[[_SQL and Tableau]]o


[[Tableau Task 1]]
[[Tableau Task 2]]
[[Tableau Task 3]]


---
# Task 4
Create an SQL stored procedure that will allow you to obtain the average male and female salary per department within a certain salary range. Let this range be defined by two values the user can insert when calling the procedure.

Finally, visualize the obtained result-set in Tableau as a double bar chart

```sql
DROP PROCEDURE IF EXISTS filter_salary;
DELIMITER $$  
CREATE PROCEDURE filter_salary (IN p_min_salary FLOAT, IN p_max_salary FLOAT)
BEGIN  
SELECT
	e.gender, d.dept_name, AVG(s.salary) as avg_salary  
FROM
	t_salaries s
		JOIN
	t_employees e ON s.emp_no = e.emp_no  
		JOIN  
	t_dept_emp de ON de.emp_no = e.emp_no  
		JOIN  
	t_departments d ON d.dept_no = de.dept_no  
	WHERE s.salary BETWEEN p_min_salary AND p_max_salary  
GROUP BY d.dept_no, e.gender;  
END$$
```





