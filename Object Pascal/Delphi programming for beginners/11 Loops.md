[[_ 0 intro]]


# Loops
>Loop is a repeatedly executed sequence of statements.

## Precondition loop

### 'While'
```pascal
While <logical expression> do
	<statements>;
```

```pascal
While <logical expression> do
begin
	<statement 1>;
	<statement 2>;
	<statement 2>;
end;
```

### `For`

```pascal
for <loop counter>:=<initial value> To <final value> 
do
	<statement>;

```
or
```pascal
for <loop counter>:=<initial value> DownTo <final value> 
Do
	<stamement>;
```

`To` sept 1
`DownTo` step -1

You can use `begin..end` after `do`


## Postcondition loop
Repeat ... Until...
```pascal
Repeat
	<statement 1>;
	<statement 2>;
	...
Until <logical expression>
```
## examples
tm1: TMemo
```pascal
 for var i:=0 to 10 do
        tm1.Lines[i]:=i.ToString();
```


