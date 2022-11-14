https://www.youtube.com/watch?v=xeFMZTGZsyQ&list=PLxAS51iVMjv-pwFzwVzguLwIKSmqrJtu3


# More Delphi Basics
## DIV, MOD, CONSTANTS
### `DIV` dividing integers
`iNum := 10 DIV 3 ;` -> 3
`eNum := 10 / 3 ;` -> 3.3333

### Mod
`iNum := 9 MOD 3 ;` -> 0
`iNum := 15 MOD 5 ;` -> 2

### Constants
```pascal
const
	VATPerc = 0.15 ;
	MaxAmt = 120 ;
```


### Convertor
```pascal

implementation

{$R *.dfm}

procedure TForm5.btnConvertClick(Sender: TObject);
const
  iHour = 60 ;

var
  iMinutes, iTotalHours, iLeftOver  : Integer ;

begin
  iMinutes := sedMinutes.Value ;
  iTotalHours := iMinutes DIV iHour ;
  iLeftOver := iMinutes MOD iHour ;

  ShowMessage(IntToStr(iTotalHours) + ' hour(s) and '
              + IntToStr(iLeftOver) + ' minutes.') ;
end;


procedure TForm5.btnObliczClick(Sender: TObject);
var
  iKwota, iPiec, iDwa, iJeden,  iReszta : Integer ;

begin
  iKwota := sedKwota.Value ;
  iPiec := iKwota DIV 5;
  iReszta := iKwota MOD 5 ;
  iDwa := iReszta DIV 2 ;
  iJeden := iReszta MOD 2 ;

  edt5.Text := IntToStr(iPiec) ;
  edt2.Text := IntToStr(iDwa) ;
  edt1.Text := IntToStr(iJeden) ;

end;


```

---
## Mathematical Functions & Procedures

### Converting Reals to Integers
there is not `FloatToInt()` function!!

`iNum := Round(3.3333) ;` -> 3
`iNum := Round(3.666) ;` -> 4

`iNum := Trunc(3.6666) ;` -> 3 
`iNum := Trunc(-2.76) ;` -> -2

`rNum := Frac(3.6666) ;` -> 0.6666
`rNum := Frac(-2,78) ;` -> -0.78

`iNum := Sqr(3) ;` -> 3^2=9 (integer)
`rNum := Sqr(5.5.) ;` -> 30.25 (real)

sqrt -> always return Real Number:
`rNum := sqrt(49) ;` -> 7

`iNum := Abs(-7) ;` -> 7
`rNum := Abs(-7.32) ;` -> 7

`rNum := PI *12`

### Random Numbers
`iNum := Random(4) ;` (0,1,2,3)

#### DICE: `iDice := Random(6) + 1 ;`

#### number in a range
`:= Random(<range>) + start_value`
8-12
`:= Random(5) + 8`

### Procedures
`ProcedureName(Args);`

#### increase
`iNum := 5 ;` -> `Inc(iNum) ;` -> `iNum: 6 ;`
the same result `iNum := iNum + 1 ;`
`iNum := 5 ;` -> `Inc(iNum, 3) ;` -> `iNum: 8 ;`
the same result `iNum := iNum + 3 ;`

#### decrease
`iNum := 5 ;` -> `Dec(iNum) ;` -> `iNum: 4 ;`
the same result `iNum := iNum - 1 ;`
`iNum := 5 ;` -> `Dec(iNum, 3) ;` -> `iNum: 2 ;`
the same result `iNum := iNum - 3 ;`

----------
## Extra Math functions
```pascal
unit Unit1;

interface

uses
	Winapi.WIndows, ....,
	..., Math;
```
#### add `Math`

`Ceil(6.001) ;` -> 7
`Floor(8.999) ;` -> 8

`rNum := RoundTo(148.256, 2) ;` -> 100
$148.256$
`210-1-2-3` 2:1, 1:4, 0:8, -1:2, -2:5, -3:6

`rNum := Power(5,4)` -> 5^4
`rNum := Power(5, -3)` -> 5^(-3) root

`Max( , )`, `Min( , )`, 

`iNum := RandomRange(4, 9)` 4 - start, 9 - before (4,5,6,7,8)

-----------
## Local & Global variables
### local
a local variable is define inside a procedure and "is alive" only in that procedure
```pascal
procedure SomeProc();
var iValue : Integer ; //local var
begin
end;


procedure SomeOtherProc();
var iValue : Integer ; // a new local var
//...
```

### Global
```pascal
//...
	private
	{ Private declations }
	iTemp : Integer ; // only be used inside this unit

	public
	{ Public declaration }
	iTemp2 : Integer ; // can be used by other units
end;

var 
	iValue : Integer ; //global var, by default = 0

implementation

{$R *.dfm*}

//....
```

If you declare a globale variable and a local variable with the same name, the procedure will use this local one.




