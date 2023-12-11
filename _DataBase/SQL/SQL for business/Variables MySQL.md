[[_Advanced SQL Topics]]


---



## VARIABLES
#sql/variable 
>__scope__ (= __visibility__) the region of a computer program where a phonemenon, such as a variable, is considered valid


==TYPES OF variables:==
- `local`
- `session`
- `global`


### LOCAL VARIABLEs
> a variable tha is visible only in the `BEGIN-END` block in which it was created

`DECLARE` is a keyword that can be used when creating __local__ variable only!!!!!!!!!!!!!!

```sql
begin
  var1
  begin
    var2
  end
end

var2 is visible only in its scope (second begin-end)
```


---

### SESSION VARIABLES
>__session__ a series of inormation exchange interactions, or a dialogue, between a computer and a user

- a _session_ begins at a certain point in time and terminates at another, later point
	- set up a connection -> 
	- establish a connection -> 
	- the Workbeanch interface will open immediately `SESSION is starting`
	- end a connection (`Session is terminated`)

> __session variable__ a variable that exists only for the session in which you are operating
>> declare a session variable:
>>  - `SET @_s_var_name = value;`

```sql
SET @s_var1 = 3;
SELECT @s_var1; -- -> 3
```

In the new connection `SELECT @s_var1;` -> NULL


---

### GLOBAL VARIABLES
> __global variables__ apply to all connections relatedto a specific server

`SET GLOBALE  var_name = value;`
`SET @@global.var_name = value;`

You cannot set just any variable as global.
There are some `system variables` that are suitable to be global variables

`.max_cnnections` indicates the max num of  connections to a server that can be sestablished at a certain point in time
`max_join_size()` sets the maximum memory space allocated for the joins created by a certain connection

```sql
SET GLOBAL max_connections = 1000;

```

---

## System vs User-Defined Variables

--  | local| session | global
 ---         | :----: | :---: | :----:
 user-defined| yes      |    yes   |   no
 system      | no      | yes      |   yes


BUT
some of the system variables can be defined as global only; they cannot be session variables (e.g. `max_connections`)


