#delphi/val

To validate use `Val(...,...,...)`
```pascal
procedure TForm6.btn1Click(Sender: TObject);
var
  sMonth: string ;
  iMonth, iCode : integer ;
  rMonth : real ;
begin
  sMonth := Edit1.Text ;
  iMonth := 0 ;
  rMonth := 0.00 ;

  Val(sMonth, iMonth, iCode) ;

  if (iCode <> 0) then
  begin
    showMessage('Data are incorrect') ;
  end else
  begin
    showMessage('Correct Data');
  end;

end;
```




