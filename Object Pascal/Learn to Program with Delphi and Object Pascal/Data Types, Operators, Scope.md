[[_ 0 intro Delphi Object Pascal]]



# Data Types
Typying is very important!!

`double`, `integer`, `string`, `char`, `boolean`
`IntToStr()`
`string + string ` concatantion
`int + int` add

>[!important] Pascal
>Pascal is a strictly typed programming language
>(compile will check data types)

boolean -> `-1` default string representation of  of a true value
 

# Operators
+, -, * / , div, mod



# Scope
## global variable
It is declare in the unit but outside the procedures/functions.
It is available in all the procedurs/functions in this code unit.
```pascal
var
	Form1: TForm1 ;
	realWeapon : string ; // GLOBAL

implementation
/...
```

## local variable
It is declare in a procedure / function.
It is available only in this procedure/function.
```pascal
// ...
implementation

{$R *.lfm*}

procedure TForm1.GoToHoloDeck;(Sender: TObject) ;
var
	holoWeapon: string ; //LOCAL
	
begin
// ...
```

In this Unit all procedures have access to `realWeapon` but only the `GoToHoloDeck` procedure has access to `holoWeapon`

You can have the same var name declare gobaly and localy (e.g. `i` global, `i` local).
If in the procedure you declare `var i`, Delphi use a local `i`.
If you don't declare `i` in a procedure, Delphi use a global `i`.






