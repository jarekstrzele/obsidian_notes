#youtube #postgresql/function 
https://www.youtube.com/watch?v=3K32mdb6h5E


```sql
create [or replace] function func_name(parms)
	return return_type
	language plpgsql
	as
$$
declare
-- variable declaration
begin
	--logic
end ;
$$
```

to call
`select func_name(args) ;`

### named notation
```
select func_name(
	len_from => 40,
	len_to => 90
) ;
```

### mixed notation
*position notation first*
```
select func_name(
	40,
	len_to => 90 
) ;
```

example
```sql
CREATE TABLE book( 
	isbn INT NOT NULL,
	title VARCHAR(30),
	total_copies int,
	price float4
) ;

INSERT INTO book (isbn, title, total_copies, price)
VALUES (1006, 'Pan Włodyjoski', 11, 234.21);

```

defining a function
```sql

create or replace function book_copies(min_copies int)
returns INT 
as 
$$
declare 
	copies int;
begin 
	select count(*) into copies from book where total_copies > min_copies;
	return copies ;
end ;
 
$$ language plpgsql

```

to use
`select book_copies(5)`



