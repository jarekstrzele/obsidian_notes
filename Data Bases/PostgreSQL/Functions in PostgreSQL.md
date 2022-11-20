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

you can use named notation
```
select func_name(

)
```

