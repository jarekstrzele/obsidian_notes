#udemy #sql
#databases 

[[constraints]]
[[Data Bases/SQL/SQL for business/clean code]]
[[aggragate function]]
[[base statement]]
[[joins]]
[[SQL Views]]
[[SQL Stored routines]]


---
# SQL Wprowadzenie
[[#SECTION Basic database terminology]]

**record**    row in a table   <-- **horizontal entity**                                                                                        **entity instance**  
  
**field** (column)   a column in a table containing 
						 specific information about every 
						 record in the table  <-- **vertical entity**  

**table**     stored tabular data     <-- **entity**   **database object**  

**relational algebra**     allows us to retrieve data efficiently  

**entity**   the smallest unit  that can contain a meaningful set of data  
  

*S Q L*   as a declarative language  to create  and manipulate relational databases  

 
**DDL**      data definition Language  
**DML**      data manipulation language  
**DCL**      data control language  
**TCL**      transaction control language  

---

## DDL  
```sql
CREATE TABLE object_name(column_name    data_type);  

CREATE TABLE sales(purchase_number  INT);  

  
ALTER TABLE sales 
ADD COLUMN date_of_purchase DATE;

DROP TABLE object_type object_name;
DROP TABLE customers;
```

RENAME allows you to rename an object  
```sql
RENAME object_type object_name TO new_object_name;  

RENAME TABLE cutomers to costomers_data;

# TRUNCATE instead of deleteing en entire table through DROP, we can also remove its data and continue to have the table as an object in the database  

TRANCATE TABLE customers; => the table will be empty  
  
```
---

## DML  
```sql
SELECT ... FROM  ...;

INSERT... INTO.. VALUES;
INSERT INTO table_name(colm1, colm1) VALUES(val1, val2);

UPDATE
UPDATE tableName
SET columnName = new_value
WHERE columnName = value;

DELETE FROM 
DELETE FROM tablename = TRUNCATE tableName
but
DELTE FROM tbaleName
WHERE columnName = value;

```

---

## DCL
allow us to manage the rights users have in a database  
  

`GRANT` statement  
gives( grants) certain permissions to users
`GRANT type_of_permission ON database_name.table_name to 'username'@'localhost'`

`GRANT SELECT ON sales.customers To 'frank'@'localhost';` only select  

`GRANT ALL ON Sales.* TO 'frank'@'localhost';` all privileges  

`REVOKE` statement
`REVOKE type_of_permission ON database_name.table_name to 'username'@'localhost'`
`REVOKE ALL ON Sales.* TO 'frank'@'localhost';` all privileges  
 

`CREATE USER 'user'@'loclahost' IDENTIFY BY 'here _password'; ` 
`CREATE USER 'frank'@'localhost' IDENTIFY BY 'password';`  

---
## T C L    

Transaction Control Language  
-   not every change you make to a database is saved automatically  

### COMMIT statement  
	-   related to `INSERT, DELETE, UPDATE  `    
-   will save the changes you've made      
-   will let other users have access to the modified cersion of the database  
    
```sql
UPDATE customers  
SET last_name = 'Johnson'  
WHERE cusomer_id = 4  
COMMIT;*  
```
  

### ROLLBACK clause  
-   will let you make a step back  
-   allows you to undo any changes you have made but don't want to be saved permanently  
-   revert to the last non-committed state   


`ROLLBACK;` the last committed state will be revert  

---

# SECTION  Basic database terminology   
  

**relational database**  
-   must be compact and well-structure (organized)  
-   is a huge amounts of data  
-   that can be quickly retrieve (efficient)  
    

columns = fields  

RDBMS - relational database management system  

  

**database vs spreadsheets**  

spreadsheets             an electronic ledger, an electronic version of paper accounting worksheets  

  

differeneces:  

DB data **integrity**:  

-   pre-set the type of data conained in a certain field in DB  
    
-   data stored in a record of table in DB ( in spreadsheet data can be stored in a cell)  
    
-   in DB data are raw ,        in SS are formatting  
    
-   in DB  all calculatrion are done after data retrieval  (you can do calculations in "views"     , in SS cells can contain calculations   
    
-     
    
-   in DB are relations, in SS no  
    

DB data **consistency**  

provide a stable structure, controlling acces permissions and user restrictions  

  

- - - - - - - -  

**I database design**           plot the entire database system on a canvas using a visualization tool  

                                          two ways of doing that:  

1.   ER                                   Entity-Relationalship diagram  
    
2.  Relational Schema       an existing idea of how the database must be organized       
    

              table name                                    second table name  

|----------------------------|                        |--------------------------------|  

| column name1 PK |                         |  

| column name2  FK | --------->           |  

| .....                            |                          |  

|--------------------------- |      

database schema = relational schema + other relational schema + ...  

  

**II database creation**  

  

  

**III data base manipulation**  

  

  

**database management** = database design + creation + manipulation  

-------------------------------------------------------------------------------------------------------------------------------------  

  

**database administration** =      maintance od DB  

  

  

---

**P R I M A R Y   K E Y  **
#sql/primary_key
each unique value  
-   a column   (or set of columns) whose value exists and is unique for every record in a table is called a PRIMARY KEY  
-   in the table there are one and only one PK  
-   *field with unique value can has null bu PK can't!!!!!!!!!!!!!!!!!*    
-   *a table can have a lot of unique value fields, but only one PK*  
    

F O RE I G N    K E Y  
#sql/foreign_key
A Customers table has a PK and its PK are in a Sales table but there it is FK.  

**FK**            **identifies the relationships between tables, not the tables themselves**  

  

---

  

ONE-TO-MANY TYPE OF RELATIONSHIP  
#sql/one-to-many_reletionships 
**one** value from the _customer_id_ column under the "Customers" table can be found **many** time in the _customer_id_ column in the "Sales" tabble  

  

Sales   ->|----------------------------Customers (   | one (min),      -> many (max) from Cusomers to Sales ) one-to-many  

Sales   ->|------------------------||-Customers (   ||  one (min),  one  (max) from Sales to Customers )      many-to-one  

  

cardinality constraints:  

||  

->  

|>  

M  

N  

O  

---

---

---

  

 **SECTION 5 First steps in SQL**   

  

CREATE DATABASE [if not exists] databasename;  

CREATE SCHEMA [IF NOT EXISTS] name;  

USE databaseNaem;  

  

  

**Data types**  

  

CHAR (n)                  fixed storage datatype                  (alway n)  255 50%faster  

VARCHAR(n)            variable storage datatyped          65,000  

ENUM                        ENUM('M','F')  

  

***********  

**numeric**:                  are written without quotes - only them  

**********  

                        integers:         are 'signed' by default (uwzględniają znak minusa)   

                                          TINYINT  

                                          SMALLINT  

                                          MEDIUMINT  

                                          INT  

                                          BIGINT  

         **precision**      refers to the number of digits in a number (10.523 -> precision 5)  

         **scale**               refers to the number of digits to the right of the decimal point in a number (10.523 -> scale 3)  

  

                      **  DECIMAL(precision, scale)**  

                        DECIMAL(7) <=> DECIMAL(7,0)  

  

                      fixed-point data     represent exact values  

                                                            DECIMAL(5,3)  10.523, 10.500  

                                                            NUMERIC  

  

                      floating-point data      used for approximate values only  

                                                                 FLOAT(5,3)      10.56789  =>  10.567  

                                                                  DOUBLE()  

  

  

****************  

**use DATATYPE**            must be written within quotes  

****************  

DATE                  used to represent a date in the format YYYY-MM-DD   (1000 - 9999)  

DATETIME         YYYY-MM-DD HH:MM:SS[.fraction]  

TIMESTAMP       used for a well-defined, exact point in time                   (01.01.1970      19.01.2038)  

                          records the moment in time as the number of seconds passed after the 1st of January 1970 00:00:00 UTC  

                         25.06.2018   ->   1.535.155.200  

  

  

************************  

BLOB    Binary Large OBject  

************************  

refers to a file of binary data - data with 1s and 0s   

involve saving files in a record  

.doc, .xml, .jpg, .wav  

  

CREATE TABLE table_name (   

      colm1 data_typ constraints,  

      colm2 data_typ constraints,   

      ...  

 );  

**SQL Objects:**  

-   sql table  
    
-   views  
    
-   stored procedures  
    
-   functions  
    
-     
    

to refer to an SQL onject in a query you must SPECIFY the  DATABASE to which it is applied:  

-   set a default database  
    

-   use database_name  
    
-   _select * from table_name_  
    

-   call a table from a certain database  
    

-   database_object.slq_object  
    
-   _select * from sales.customers;_  
    

  

                                            

QUERY  

-   a command to ro retrieve information from the database  
    
-   a command to insert, update, delete data from the database  
    
-   ;   
    
-     
    

  

      DROP TABLE table_names;  // delete all the table  

      DROP TABLE sales;i

