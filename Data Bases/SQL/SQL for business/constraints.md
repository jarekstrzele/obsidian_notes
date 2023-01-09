 **section 6 MYSQL constraints**   

**c o n s t r a i n t s**      specific rules or limits that we define in our tables  

> the role of constraints is to outline the existing relationships between different tables in our database  

AUTO_INCREMENT  
PRIMARY KEY:  
                       

CREATE TABLE sales {
      customer_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
      ....      
}  

CREATE TABLE sales{
      ....
      PRIMARY KEY (customer_id)
} 

---
  

**f o r e i g n    k e y**  points to a column of another table and, thus, links the two tables  
id defined through a foreign key contraint  

table with foreign key ==child table, referencing table==
table that column is in other table ==parent table, referenced table==

CREATE TABLE tablename(
      ...
      FOREIGN KEY (column_name) REFERENCES tableName(column_name) ON DELETE CASCADE
);  

> ON DELETE CASCADE  
> 
> if a specific value from the parent table's primary key  has been deleted.  
> 
> all the records from the child table referring to this value will be removed as well  

adding new column to an existing table:  

ALTER TABLE sales ADD FOREIGN KEY (customer_id) REFERENCES customers(customer_id) ON DELETE CASCADE;  

to delete this constraint:  
`ALTER TABLE sales DROP FOREIGH KEY sales_ibfk_;  `

---
  
**u n i q u e   k e y**             used whenever you would like to specify  

                                           that you don't want to see duplicate data in a given field  

                                           is impemented in SQL through a constraint, the UNIQUE constrint  

     

CREATE TABLE table_name(  

      ...  

      PRIMARY KEY (customer_id),  

      UNIQUE KEY (email_address)  

);  

           

if you want to chane an existing table:  

  

ALTER TABLE  table_name
ADD UNIQUE KEY (column_name);

  

           

  

**i n d e x e s**             an organizational unit that helps retrieve data more easily  

                                 _unique keys_ in MySQL have the same role as _indexes_, but revers isn;t true  

  

to delete index  

ALTER TABLE table_name  

DROP INDEX unique_key_field;  

ALTER TABLE customers  

ADD UNIQUE KEY (email_address);  

ALTER TABLE customers
DROP INDEX email_address;  

  

  

**D E F A U L T   ** Constraint            help us addign a [articular default value to every row of a column  

CREATE TABLE customer(  

      ...
      number_of_compaunts INT DEFAULT 0,  

...
  

If you want to change an existing table  

ALTER TABLE table_name  

CHANGE COLUMN ...;

ALTER TABLE customers  

CHANGE COLUMN number_of_complaints number_of_complaints INT DEFAULT 0  

to delete  

ALTER TABLE table_name
ALTER COLUMN column_name DROP DEFAULT;  

  

p r i m a r y  k e y    have to have a value  

u n i q u e     k e y     can have no value  

  

**n o t   n u l l**   

to change to NULL  

ALTER TABLE table_name  

MODIFY      table_name TYPE  NULL;
  

  

to add NOT NULL to an existing column  

ALTER TABLE table_name  

CHANGE COLUMN column_name new_column_name TYPE  NOT NULL;  

  

NULL             a null value is a missing value  

                        assigned by the computer  

  

0/ NONE         assigned by the user                      NULL != 0 or NULL != NONE  

---

---