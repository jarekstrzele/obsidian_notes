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



