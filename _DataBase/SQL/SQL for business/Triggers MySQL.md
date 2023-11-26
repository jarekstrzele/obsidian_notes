[[_Advanced SQL Topics]]


---

# MySQL Triggers
> __trigger__  is
>  - a type of stored program,
>  - associated with table
>  - be activated automatically onace a specific event related to the table
>  - must be related to:
>>  INSERT,
>>  UPDATE,
>>  DELETE,
	
>__trigger__ is a MySQL object that can "trigger" a specific action or calculation "before" or "after"INSERT, UPDATE, DELETE statement


---
## Before starting
`USE database_name;`
`commit` because the trigger we are about to create will make some changes to the stat of the data in our database (`ROLLBACK` to back)

---
## Trigger to create
### TO 

### INSERT
```sql
DELIMITER $$

CREATE TRIGGER before_salaries_insert
BEFORE INSERT ON salaries
FOR EACH ROW
BEGIN
  IF NEW.salary< 0 THEN
    SET NEW .salary = 0;
  END IF;
END $$

DELIMITER ;


```

`NEW` referes to a row that has just been inserted or updated

`SET` this keyword is used whenever a value has to be assigned to a cerain variable

### UPDATE
```sql
DELIMITER $$

CREATE TRIGGER trig_upd_salary
BEFORE UPDATE ON salaries
FOR EACH ROW
BEGIN 
	IF NEW.salary < 0 THEN 
		SET NEW.salary = OLD.salary; 
	END IF; 
END $$

DELIMITER ;

```


---
## BUILt-IN functions
#sql/buit-in_function
`select SYSDATE()` delivers the date and time of the moment at which you have invoked this function

`select DATE_FORMAT(SYSDATE(), '%y-%m-%d') as today;`


---
Create a trigger that checks if the hire date of an employee is higher than the current date. If true, set this date to be the current date. Format the output appropriately (YY-MM-DD).

```sql
DELIMITER $$

CREATE TRIGGER trig_hire_date  
BEFORE INSERT ON employees
FOR EACH ROW  
BEGIN  
 IF NEW.hire_date > date_format(sysdate(), '%Y-%m-%d') 
   THEN
  SET NEW.hire_date = date_format(sysdate(), '%Y-%m-%d');     
 END IF;  
END $$  

DELIMITER ;  

INSERT employees VALUES ('999904', '1970-01-31', 'John', 'Johnson', 'M', '2025-01-01');  
SELECT  
   *  
FROM  
   employees
ORDER BY emp_no DESC;
```































