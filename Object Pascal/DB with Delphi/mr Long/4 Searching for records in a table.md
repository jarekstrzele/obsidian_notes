[[_ 0 DB (local .mdb) in Delphi]]



# 4 Searching for records in a table

Use the ADO table `tblCD`

```pascal
procedure TForm5.SearchClick(Sender: TObject);
var
  sInput : string ;
begin
memDisplay.Clear ;
sInput := edtInput.Text ;


with dmDB do
  begin
    tblAnimal.First ;
    while not tblAnimal.eof do
      Begin
           if tblAnimal['Category'] = sInput then
           begin
             memDisplay.Lines.Add(tblAnimal['Breed'] + ' ('+ tblAnimal['Gender']  +')')
           end;

      tblAnimal.Next ;
      End   ;
  end;

end;
```













