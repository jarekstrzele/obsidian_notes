https://www.youtube.com/watch?v=BqmJpFbRY2U

----
[[1  A voting system]]
[[2 Components]]
[[3 Timer]]
[[4 Val()]]
[[5 Files]]

[[10 Databases]]




----
Button to close:
```pascal
procedure TForm6.btnCloseClick(Sender: TObject);
begin
  Close ;
end;
```

`Shape` component
Brush>color, style

```pascal

implementation

{$R *.dfm}

procedure TForm6.btnCloseClick(Sender: TObject);
begin
  Close;
end;

procedure TForm6.btnDownClick(Sender: TObject);
begin
  shpCircle.Top:= 300 ;
   btnUp.Enabled := true ;
  btnDown.Enabled := false ;
end;

procedure TForm6.btnUpClick(Sender: TObject);
begin
  shpCircle.Top := 20;
  btnUp.Enabled := false ;
  btnDown.Enabled := true ;
end;
```

Comments
```
// one line
{
many line
}

(*
fefwe
*)
```




## Attributes

`Form` > `OnActivate` event > a new `FormActivate`:
```pascal
implementation

{$R *.dfm}

procedure TForm6.btnAfrikaansClick(Sender: TObject);
begin
 lblName.Caption := 'Naam' ;
 lblSurname.Caption := 'Van' ;
 lblAge.Caption := 'Ouderdom' ;
end;

procedure TForm6.btnCloseClick(Sender: TObject);
begin
  Close;
end;

procedure TForm6.btnDownClick(Sender: TObject);
begin
  shpCircle.Top:= 300 ;
   btnUp.Enabled := true ;
  btnDown.Enabled := false ;
end;

procedure TForm6.btnResetClick(Sender: TObject);
begin
   Form6.edtName.Clear ;
   Form6.edtSurname.Clear ;
   Form6.edtAge.Clear ;
end;

procedure TForm6.btnUpClick(Sender: TObject);
begin
  shpCircle.Top := 20;
  btnUp.Enabled := false ;
  btnDown.Enabled := true ;
end;

procedure TForm6.FormActivate(Sender: TObject);
begin
   Form6.edtName.Clear ;
   Form6.edtSurname.Text := ' ' ;
   Form6.edtAge.Clear ;

end;

```


## Basic Output

tMemo component
`memOut.Lines.Add('25') ''`
`IntTOStr(2+3) ;`
`showMessage('qqq') ; `


## Basic Input
`edtName.Text`


## Settings Callender Date

#delphi/calender
component `TCalender`
`TButton`, 
`TSPinEdit` (max, min maxlength) > Event > `OnActivate`
```pascal
procedure TForm6.FormActivate(Sender: TObject);
begin
  sedSetDate.MaxLength := 2 ;
  sedSetDate.MaxValue := 31 ;
  sedSetDate.MinValue := 1 ;
end;
```
property `Values` : `1`

```pascal
procedure TForm6.btnSetDateClick(Sender: TObject);
begin
 Calendar.Day := sedDay.Value ;
 Calendar.Month := sedDay.Value ;
 Calendar.Year := sedDay.Value ;
end;

procedure TForm6.btnUpClick(Sender: TObject);
begin
  shpCircle.Top := 20;
  btnUp.Enabled := false ;
  btnDown.Enabled := true ;
end;

procedure TForm6.FormActivate(Sender: TObject);
begin
  sedDay.MaxLength := 2 ;
  sedDay.MaxValue := 31 ;
  sedDay.MinValue := 1 ;


end;

```

## logical operatora
`and  not   or`

## `If`
#delphi/if
`if not((...)  and (...) )`

`if (iNum = 1) or (iNum = 2) then ` --> you can replace by `if iNum in [1 .. 9] then ` (1<=iNum <= 9)

## `case`
```pascal
case iNum of
	1 : 
		showMessage('1') ;
	2: 
		showMessage('2') ;
	3: 
		begin
			//... some code
		end ;
	4 .. 99:
		// some code
else
	begin
		showMessage('if not matched') ;
	end ;
		
```


## Case List
```pascal
case iMark of
	29: {code} ;
	1, 2, 3, 4, 5, 6, 7 : {some code} ;
	100 .. 200 : {code} ;
	23, 400, 500 .. 890 : {code}
```

## `FOR` loop













