[[_DataBase/SQL/SQL&PostgreSQL Tutorial/_ intro sql postgresql]]


----
# DDL
#postgres/ddl 

Database tables:
- conain columns (fields) and rows of data (records)
- each column has  a defined data type which defines what type of data can be contained within that column
- each row fo data should be unique
- each column should contain oblu one value per row
- 

## data types
#postgres/data_type
common


data type | description | example
:---: | :---: | :---: 
INT | Whole Numbers | Agem Quantity
NUMERIC(P,S) | Decimal Numbers | Height, price
SERIAL | Auto incrementing <br> whole number | Id (primary key)
CHAR(N) | fixed length string of length N | Gender, State
xxxxx| xxxxxx | xxxxxx 
VARCHAR(N)  | varying length string of max lenght N | Name, email
TEXT | Varying length string with no maxmum length| Comments, Reviews
xxxxxxxx| xxxxxxxxxxxxxxxx| xxxxxxxxxxxx
TIME | HH:MM:SS | 
DATE| YYYY:MM:DD | Date of Birth
TIMESTAMP | YYYY-MM-DD HH:MM:SS | Order Time
xxxxx| xxxxxx | xxxxxx 
BOOLEAN | True or False | In Stock
ENUM | a list of values input by the user | Gender


## Primary keys and foreign keys
### primary keys
- a column which uniquely identifies a record in a table
- must be unique and cannot be null
- only 1 primary key per table
- primary keys are not compulsory but are highly advised

### foreign keys
is used to link two tables together
is a column where the values match the values on another tables primary key column
the table with the primary key is called the reference, or parent, table and the table with the foreign key is called the child table
a table can contain multiple foreign keys


## Constraints: unique, not null, check
### unique
- a column can only contain unique values
- you can state wether a column should have a unique constraint when creating table

### not null
NULL values can not be instered into a column

### check 
check wether values in a column statisfy a specific boolean expression
an age column must containe values greater than 0



---
## CREATE table

```postgresql
create table directors(
	
	director_id SERIAL primary key,
	first_name VARCHAR(30),
	last_name VARCHAR(30) not null,
	date_of_birth DATE,
	nationality VARCHAR(20)
);
```

`DROP TABLE table_name;`


```postgresql
create table movies (

	movie_id SERIAL primary key,
	movie_NAME VARCHAR(50) NOT NULL,
	movie_length INT,
	movie_lang VARCHAR(20),
	release_date DATE,
	age_certificate VARCHAR(5),
	director_id INT references directors (director_id)

)
```



---
## Modifying table
				`ALTER TABLE .....`

#sql/alter  #postgres/alter

### adding cols
```sql
create table examples (

	example_id SERIAL primary key,
	first_name VARCHAR(30),
	last_name VARCHAR(30)

);

alter table public.examples 
add column email varchar(50) unique;

select * from examples;


ALTER TABLE examples 
ADD column nationality VARCHAR(30),
ADD column age INT not null;

```

### changing a cols data type
```sql
/* ALTER TABLE tablename
   ALTER COLUMN columnname TYPE new_data_type;
   */
   
ALTER TABLE examples
ALTER COLUMN nationality TYPE CHAR(3);

```


### changing column name
```sql
ALTER TABLE movie_revenues
RENAME COLUMN old_column_name TO new_column_name;
```

### deleting a table
`drop table table_name`



