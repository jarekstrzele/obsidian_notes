#postgresql  #plurasight  #browning_jason


# Understanding the Relational Model
Data comes in many forms.
Data is stored in many forms, but most often in a relational database.
Relational db are tools that allow us to store large quantities of information

SQL (structured query language) exists solely to interact with data

## SQL
- SQl plarforms comply with ANSI
- allows for use across databases
- databases can add additional feature
- aids learning  other query languages

## PostgrSQL
- it complies with ANSI standards
- open-source and freely available
- pgAdmin

## Structure of a Database
**table** contains all records for a particular set of data
**column** is the field or varable in the dataset
**rows** record within a table


---
# SELECTing data
When you want to retrieve information from db 
we query the db for that information.

## `SELECT`:
- allows us to retrieve data
- can perform calculations without a table (`SELECT 2+2;`)

## Framework
`SELECT` specify cols of interest
`FROM` where these cols are stored
`WHERE` criteria to filter matching rows
`;` SQL statements should be terminated

`SELECT * FROM performance;` select all data from table `performance`

`SELECT <keyword specifies field of interes>`
`FROM <specifies table where records are stored>`


## Distinct Values
```sql
  SELECT DISTINCT first_name FROM students;
```


---
# Limiting Your Results
## `WHERE`
criteria in the `WHERE` clause is case-sensitive
```sql
SELECT first_name, age 
FROM student 
WHERE first_name="Joe";
```


## Comparison operators
`=  <>  >   <   >=   <= `


You can use `AND`


## Patching  Patterns
Relational operators match fields to a specific value
**`LIKE` matches fields to a specific ==pattern==**

### pattern wildcards
Pattern to match can include wildcards
`%` represents zero or more characters
	`WHERE first_name LIKE 'Jo%'`
`_` represents exactly one character
   `WHERE origin_city_name LIKE '____, %'`

`WHERE` criteria to filter matching rows
`LIKE` specify the pattern to compare against field
`NOT` find those fileds that do not match the pattern

<<<<<<< HEAD
## Operator Precedence
- `AND` has higher ioerator precedence than `OR` <   (... and ...) or ...     >
- 
=======
>>>>>>> remotes/origin/master

