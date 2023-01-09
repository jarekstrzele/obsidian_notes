[[_ 0 intro]]
#pascal/function

# Functions
> Function is a procedure (it executes statements) that return a  value.

>Functions are described in the **Implementation** section.
> When you declare a function, you specify
> - its name,
> - the number type of parameters it takes,
> - the type of its return value.
> 
> 

### Syntax of a function definition
```pascal
Function <name of function> (<list of params>): <type of return value>;
	<local delarations >
	begin
		<statements>
	end;
```
```pascal
Function tg(x: real): real;
var y: real; //local variable
begin
	y:=x/180*pi;
	tg:=sin(y)/cos(y);
end ;
```



