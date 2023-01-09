[[User-Defined Functions in MySQL]]
[[SQL Stored routines]]



---
# Error Code 1418
#sql/error

>__log__ is a software component where you can save information about some events or errors theat happened during execution of a certain application


>__Binary Log__ contains database changes.'
>> - check whether a function is changing the data in the database and 
>> - what is the result to be produced
>> 

To solve this problem we need to add characteristics  to definition of the function.

`create function <function name> <function parameters> returns <type> <characteristics> ...`

Characteristics:
- `DETERMINISTIC` it states that the function will always return identical result given the same input
- `NO SQL` means that the code in our function does not contain SQL
- `READS SQL DATA` this is usually when a simple `SELECT` statement is present

If one of these characteristics is not present in our code, MYSQL assumes that our function is non deterministic and that it chages data.


The other way to solve this problem:
`SET @@global.log_bin_trust_function_creators := 1;`
This operation is not the safest one.

`DETERMINISTIC  NO SQL  READS SQL  DATA`













