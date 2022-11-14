[[_ 0 intro Delphi Object Pascal]]


# Fundamental of Pascal
## variable
```pascal

{ Declaration of variables }
var
   i : integer;
   x : integer;  


procedure TForm1.ShowValues;
begin
  ILabel.Caption := 'i = ' + IntToStr(i);
  XLabel.Caption := 'x = ' + IntToStr(x);
end;       
```

or
```pascal
var
  pettyCash,
  entertainmentsBudget,
  fuelMoney,
  wallet	 : integer; 
```
### `<var_name> : <data_type>`

assignment
`i := i + 1;`

## constant
```pascal
impementation
 // ...
 
const
	taxtRate = 0.2;

var
 //...

```


## comments
```pascal
{ block 
  
  comments
}

(* block
	comments
*)

// line comments
```
















