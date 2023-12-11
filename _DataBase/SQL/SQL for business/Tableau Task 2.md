[[_SQL and Tableau]]

[[Tableau Task 1]]
[[Tableau Task 3]]
[[Tableau Task 4]]


---
# Task 2
>Compare the number of male managers to the number of female managers from different departments for each year, starting from 1990.

>__AREA CHART__ a type of graph which can be perceived as a line chart where the area between the lines and between the lowest lin and the horizontal axis has been filled with colors
>- visually compare the proportional relationship berween the quantities examined


```sql
SELECT 
	d.dept_name,
    ee.gender,
    dm.emp_no,
    dm.from_date,
    dm.to_date,
    e.calendar_year,
    CASE
		WHEN YEAR(dm.to_date) >= e.calendar_year AND YEAR(dm.from_date) <= e.calendar_year THEN 1
        ELSE 0
	END AS active
FROM 
	(SELECT 
		YEAR(hire_date) as calendar_year
	FROM t_employees 
    GROUP BY calendar_year) as e
		CROSS JOIN
    t_dept_manager as dm
		JOIN
	t_departments as d ON dm.dept_no = d.dept_no
		JOIN
	t_employees ee ON dm.emp_no = ee.emp_no
ORDER BY dm.emp_no, calendar_year;
```

