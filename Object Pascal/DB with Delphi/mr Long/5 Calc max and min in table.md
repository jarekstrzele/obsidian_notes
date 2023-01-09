[[_ 0 intro Delphi Object Pascal]]o


# Calc max and min in table
```pascal
procedure TForm5.MaxClick(Sender: TObject);
var
  iMax, iMin : real ;
  sMaxData, sMinData : string ;

begin
  memDisplay.Clear ;

with dmDB do
  begin
    iMax := -999 ;
    tblAnimal.First ;
    while not tblAnimal.eof do
      Begin
           if tblAnimal['ListPrice'] > iMax  then
           begin
             iMax := tblAnimal['ListPrice'] ;
           end;

      tblAnimal.Next ;
      End   ;
      sMaxData := FloatToStr(iMax) ;
      memDisplay.Lines.Add('Max: ' + sMaxData) ;
  end;

end;
```








